# 딥러닝을 통한 남/여 분류 모델 만들기
* 직접 데이터를 만들고 테스트하는데 의의
* 개발 환경: Google Colaboratory

## 데이터 셋
* 최대한 다양한 인종과 나이 대에 대해 적용시킬 수 있게 조원 간에 이미지 수집 분야를 나눔
* 크롤링 한 데이터를 직접 확인하고 적합하지 못한 사진은 수작업으로 제거
* 'case1: 전신, case2:얼굴' case를 둘로 나누어 진행
* 모델에 이미지를 넣기 위해선 모두 같은 크기의 사진으로 설정해 주어야 하기에 이미지 분포를 확인하고 최빈값을 가지는 값으로 리사이징(400x300)
* 원핫인코딩으로 남성인지 여성인지 라벨링(원핫인코딩은 저장공간 측면에선 비효율이지만 본 프로젝트에선 분류해야 하는 경우의 수가 2가지이므로 선택)
* 학습/테스트 데이터 셋 분리
* 데이터 셔플

## 모델링
* CNN을 기반으로하는 VGGNET 모델(2014년 ImageNet이라는 1000개의 이미지를 구별하는 대회에서 좋은 성적을 낸 모델
* Batch normalization 추가
* 손실함수: Cross-entropy
* 최적화함수: Adam optimizer (gradient와 learning rate 둘 다 고려해서 방향을 찾는 함수)
* Cross-entropy로 구한 cost를 Adam optimizer를 통해 최소화하며 훈련을 진행

## 평가
* case1: accuracy 72.6% (300 epoch)
* case2: accuracy 72.3% (300 epoch)

## 한계
* 남자/여자 분류하는 모델이라는 문제의 난이도에 비해 낮은 정확도
-> 분석하기 용이하게 정제되어 있는 데이터를 사용하지 않고 직접 데이터를 만들고 테스트하는 데 의의
-> 실제 현장에선 데이터를 정제하는 것이 모델링 하는 것에 못지않게 중요하다는것을 배움
* male에대해 과적합
