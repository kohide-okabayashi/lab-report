# 実験名: EngeTOF

- 担当: <岡林>
- 目的: <EngeTOFの時間幅をPHcorrectionで補正し、そこから各シンチの時間分解能を出す>

# 26/06/26
## 1. 前提・条件
- calib2.ccを元に手直しして、以下のようなことができるようにした(calib3.cc)
  - PiTOF8本を対象に、PHcorrection
    - $TDC_{corrected} = TDC_{raw} + ({c_1}/{\sqrt{ADC}} + c_2/ADC)$
  - TMinuitで、4通りのTOFの時間幅の和を最小化
    - ${\chi}^2 = \sum\limits_{i=1}^4 (TOF_i - \overline{TOF_i})^2$
  - TOFをプロットして時間幅が得られるので、以下のような式4つで、4つのシンチの時間分解能を出す
    - $\sigma_{TOF_{1X4-2X4}}^2 = \sigma_{1X4}^2 + \sigma_{2X4}^2$

- データと解析コード:/data/Users/okabayashi/mine/


## 2. 実行コマンド
```bash
# 例
python train.py --dataset xxx --lr 1e-3 --seed 42
```

## 3. 結果
- 指標: 
- ベースライン比較:
- 生成物(図・重み・ログ)の保存先:

## 4. 考察
- うまくいった点:
- 失敗要因:

## 5. 次アクション
- [ ] 
- [ ] 
