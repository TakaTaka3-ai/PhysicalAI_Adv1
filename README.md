# PhysicalAI_Adv1

このリポジトリは、ROS 2 環境でロボットアームの関節動作を制御するための Python スクリプトを含みます。

## 概要

[Code](Code) は、`/crane_plus_arm_controller/joint_trajectory` トピックへ `JointTrajectory` メッセージを送信し、ロボットの姿勢を順番に切り替えるノードです。

動作シーケンスは以下の順です。

- stand
- hand_up
- squat
- 末尾に達したら先頭へ戻る

## 含まれるファイル

- [Code](Code): ROS 2 ノード本体
- [README.md](README.md): プロジェクト説明

## 動作内容

`RobotActionPublisher` クラスは、起動時に最初の姿勢 `stand` を送信し、その後タイマーにより各姿勢を 3 秒ごとに切り替えます。

送信される関節名は以下です。

- crane_plus_joint1
- crane_plus_joint2
- crane_plus_joint3
- crane_plus_joint4

## 必要条件

- ROS 2 (ROS 2 Humble など)
- Python 3
- `trajectory_msgs` と `builtin_interfaces` が利用可能な環境
- 対応するロボット制御ノード / トピックが起動済み

## 実行方法

1. ROS 2 環境を有効化します。
2. このリポジトリのルートでスクリプトを実行します。

例:

```bash
source /opt/ros/humble/setup.bash
python3 Code
```

必要に応じて、ワークスペースの環境を追加してから実行してください。

```bash
source /opt/ros/humble/setup.bash
source /path/to/your_ws/install/setup.bash
python3 /path/to/PhysicalAI_Adv1/Code
```

## 補足

このスクリプトは、ロボットの制御用トピックに対して軌道指令を出すための簡易サンプルです。実機やシミュレータのトピック名が異なる場合は、`joint_names` やトピック名を実環境に合わせて調整してください。
