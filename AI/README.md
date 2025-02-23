# 필기해줘 AI engine
1. 필요한 python package 다운
2. wget으로 pretrained model down
3. python craft --test_folder로 실행

## 모델설명
```
detection craft 이용
recongition trocr/naver CRNN 이용

type : 한글, 영어
```


```
# 서버가 아니라면 / cpu 이용
pip3 install pybind11
pip3 install -r requirements.txt
```
### 기타 추가 패키지 및 필요한 것 있으면 다운


## pretrained model download
#### craft pretrained model download
##### craft.pth - detect
```
wget --load-cookies ~/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies ~/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1RT-UkFLIyd2CkeReTKvD4xri6FTjvK5p' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1RT-UkFLIyd2CkeReTKvD4xri6FTjvK5p" -O craft.pth && rm -rf ~/cookies.txt
```
##### recog.pth - recognition english
```
wget --load-cookies ~/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies ~/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1yim_nfaYOKD6jRns3YKMPcCmUYtrVYF0' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1yim_nfaYOKD6jRns3YKMPcCmUYtrVYF0" -O recog.pth && rm -rf ~/cookies.txt
```
##### korcog.pth - recognition korean
```
wget --load-cookies ~/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies ~/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1h2QsOCcMH10QRA0P8yGogwX8P71lRnwA' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1h2QsOCcMH10QRA0P8yGogwX8P71lRnwA" -O kocrnn.pth && rm -rf ~/cookies.txt
```

### kocrnn_final.pth
```
wget --load-cookies ~/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies ~/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1jp1PeFm6BhkZrZjBy9V_G4TXlffjgOqn' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1jp1PeFm6BhkZrZjBy9V_G4TXlffjgOqn" -O kocrnn_final.pth && rm -rf ~/cookies.txt
```

#### trocr pretrained model donwload
###### doc - recognition document with SROIE dataset
```
wget --load-cookies ~/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies ~/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1IMPRjohaw-Pc1BLTZOGRmRzs84MsBQfh' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1IMPRjohaw-Pc1BLTZOGRmRzs84MsBQfh" -O trocr.pt && rm -rf ~/cookies.txt
```
###### htr - recognition handwriting with IAM Dataset
```
wget --load-cookies ~/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies ~/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=1sJ_i_n04p1GXcfZQ0nSv8QEmdQ40aqKm' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=1sJ_i_n04p1GXcfZQ0nSv8QEmdQ40aqKm" -O trhtr.pt && rm -rf ~/cookies.txt
```


### 만약 gpu 없다면
```
detect_model : 이미지에서 텍스트 위치 탐지기, recog_model : 해당 위치 이미지 크롭 후 인식하기

#한국어
python craft_kor.py --test_folder {경로} --cuda n --recog_name {trocr 또는 **naver** 선택} --recog_model {경로} --detect_model {경로} --detect_text {htr or ocr}
#영어
python craft_eng.py --test_folder {경로} --cuda n --recog_name {**trocr** 또는 naver 선택} --recog_model {경로} --detect_model {경로} --detect_text {htr or ocr}
```
### ex)
```
python craft_eng.py --test_folder ./data --cuda n --recog_name trocr --recog_model ./downloads/models/htr.pth --detect_model ./downloads/models/craft.pt --detect_text htr
```
