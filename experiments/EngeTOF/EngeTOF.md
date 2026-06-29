# 実験名: EngeTOF

- 担当: <岡林>
- 目的: <EngePiTOFの時間幅をPHcorrectionで補正し、そこから各シンチの時間分解能を出す>

# 26/06/27
## 1. 前提・条件
- calib2.ccを元に再設計、簡素化して、以下のようなことができるようにした(calib4.cc)
  - PiTOF8本を対象に、PHcorrectionのパラメータを与える
    - $TDC_{corrected} = TDC_{raw} + ({c_1}/{\sqrt{ADC}} + c_2/ADC)$
  - TMinuitで4通りのTOFの時間幅の和を最小化し、16パラメータを最適化
    - ${\chi}^2 = \sum\limits_{i=1}^4 (TOF_i - \overline{TOF_i})^2$
- ここからは自分で計算する      
  - TOFをプロットして時間幅が得られるので、以下の式からシンチごとの時間分解能を出す
    - $\sigma_{TOF_{1X4-2X4}}^2 = \sigma_{1X4}^2 + \sigma_{2X4}^2$
    - $\sigma_{TOF_{1X4-2X5}}^2 = \sigma_{1X4}^2 + \sigma_{2X5}^2$
    - $\sigma_{TOF_{1X5-2X4}}^2 = \sigma_{1X5}^2 + \sigma_{2X4}^2$
    - $\sigma_{TOF_{1X5-2X5}}^2 = \sigma_{1X5}^2 + \sigma_{2X5}^2$
- PiTOFの4組だけだと連立して解けないことに気づく。ので、上段と下段それぞれで分解が一緒だと仮定してみる

- データ:/data/Users/okabayashi/mine/etoftest2026_run_47.root

## 2. 実行コマンド
- 解析コード:/data/Users/okabayashi/mine/calib4.cc

## 3. 結果
- 以下のようなTOF時間幅が得られた。
  - $\sigma_{TOF_{1X4-2X4}}^2 = 162ps
  - $\sigma_{TOF_{1X4-2X5}}^2 = 171ps
  - $\sigma_{TOF_{1X5-2X4}}^2 = 206ps
  - $\sigma_{TOF_{1X5-2X5}}^2 = 159ps
- 整合性を確認すると明らかにおかしい。なんでや。
  - $\sigma_{1X5}^2 - \sigma_{1X4}^2 = 206^2 - 162^2 = 159^2 - 171^2$

![TOF時間幅（横軸はns）](images/etoftest2026_run_47_tof_resolution.pdf)

![補正によるadc-adc分布の変化](images/etoftest2026_run_47_timewalk.pdf)

## 4. 考察
- 1X5-2X4:{4,5,10,11}の組み合わせだけ元の分解能が悪すぎたりデータ数が半分以下しかなかったりと怪しい。ここが160psくらいまで抑えられれば上の話も辻褄が合う、、？本当は上の式が0になってくれると「上段と下段それぞれで分解が一緒」という過程が信憑性を増すわけだが、、、

## 5. 次アクション
- 正直よくわかんないので聞く。
