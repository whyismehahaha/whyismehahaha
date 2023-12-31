# 2023全國智慧製造大數據競賽初賽
透過資料清洗、資料擴增的方式過濾需要的資料後，套入模型以預測題目給定日期內各爐累積壞掉的燈管數。

# 架構

## 資料前處理
- Python
- Microsoft Excel

## 使用模型預測
- DNN Regression

# 安裝

## python
(實驗環境為google colab)
  ### *pandas*
    pip install pandas==1.5.3 
  ### *numpy*
    pip install numpy==1.23.5
  ### *scikit-learn*
    pip install scikit-learn==1.2.2
  ### *matplotlib*
    pip install matplotlib==3.7.1
  ### *seaborn*
    pip install seaborn==0.12.2
  ### *random*
    pip install random
  ### *scipy*
    pip install scipy==1.10.1
  ### *datetime*
    pip install datetime
  ### *tensorflow*
    pip install tensorflow==2.13.0
    pip install tensorflow-datasets==4.9.2
    pip install tensorflow-estimator==2.13.0
    pip install tensorflow-gcs-config==2.13.0
    pip install tensorflow-hub==0.14.0
    pip install tensorflow-io-gcs-filesystem==0.33.0
    pip install tensorflow-metadata==1.14.0
    pip install tensorflow-probability==0.20.1
  ### *keras*
    pip install keras==2.13.1
    
## Excel
[請支持正版，點擊前往Microsoft Excel官網](https://www.microsoft.com/zh-tw/microsoft-365/excel)

# 實作過程
## Step 1 資料前處理
   使用pandas過濾不合理的資料以及填補缺失的欄位，並匯聚整理為總表！
## Step 2 隨機取樣
   針對燈管損壞紀錄，隨機選取於損壞日期之前的燈管作為樣本，並取樣該燈管的特徵。
## Step 3 推算預期壽命
   換算被取樣燈管之功率及累積使用時間，由於已知損壞日期，以此可以換算燈管剩餘壽命。
## Step 4 平衡
   為了避免少數資料出現極端狀況，我們使原始資料*(故障燈管總數/該爐故障燈管數)，以此方法作為平衡。
## Step 5 迴歸
   使用DNN Regression計算燈管特徵與預期壽命之關係，並藉由多個特徵，整理出目標日期前1天每個燈泡的特徵。
## Step 6 結論
   由層佔空比推算目標日期前1天每個燈泡的累積使用時數，若燈泡預期壽命小於該層累積時數，則標記為損壞。最終加總，可得出各爐位燈管損壞數量。

