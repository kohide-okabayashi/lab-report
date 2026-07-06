# 実験名: EngeTOF

- 担当: 岡林
- 目的: EngePiTOFの時間幅をPHcorrectionで補正し、そこから各シンチの時間分解能を出す

# 26/07/06
## 1. 変更
- ETOFを含めればE1,E2,1X4,1X5,2X4,2X5それぞれ導出できることに気づく

## 2. 実行コマンド
- 解析コード:/data/Users/okabayashi/mine/calib4.cc
- データ:/data/Users/okabayashi/mine/etoftest2026_run_47.root
- cut条件: adc - ped > (pedの右端), -50 < tdc_raw < 0
  - pedは各chのadcヒストグラムでのペデスタルピークの中心adc
    
## 3. 結果
- 以下のようなTOF時間幅が得られた。

## 4. 考察




