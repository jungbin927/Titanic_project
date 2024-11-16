# Titanic_project



## 1. 분석 목적:
본 프로젝트는 Titanic 승객 데이터를 바탕으로, 변수들의 특성을 파악하여 숨겨진 의미를 파악하는 프로젝트이다.
또한 의미있는 특성을 활용하여 모델을 학습시키고, 탑승객의 생존 여부를 예측하는 머신 러닝 프로젝트이다.


## 2. 구체적 구현 내용:
### 2-1.EDA
1. 단일 변수 분석
 
Survived, Pclass, Sex, SibSp, Parch, Embarked: 범주형 변수들을 원 그래프와 히스토그램을 이용해, 전반적인 분포와 비율을 확인하였다.

그리고, Survived 변수의 사망/생존 비율을 기준으로, 어떠한 특성,상황에서 생존률이 높고 낮은지 'barplot','countplot'을 이용해 파악하였다.

Age: 수치형 변수인, Age를 나이의 분포와 생존비율을 확인하기 위해, 5살 단위로 나눠서 시각화하였다.

Fare: 다른 수치형 변수인, Fare는 Pclass와 관련이 있을거라 판단해, Pclass별 Fare의 평균을 확인하였고, 히스토그램을 통해 등급 별 요금의 전반적인 분포를 확인하였다.

Name: 성을 이용해 몇몇 가족을 파악할 수 있었고, 이름 내에 호칭이 존재하는 것을 확인하였다.

Ticket: 동일한 티켓 번호를 통해 몇몇의 가족을 파악할 수 있었다.

이처럼 단일 변수 파악 및 특성, 상황 별 Survived를 통해, 생존률이 높은 특성들을 파악할 수 있게 되었다.

2. 다중 변수 분석

그 후 조금 더 구체적으로 파악해보기 위해서 여러 변수들을 조합하여, 전반적인 분포와 생존률을 확인해 보았다.

Sex, Pclass,Survived 3가지의 변수를 통해, 각 등급별 남녀의 비율. 각 등급별 남녀의 생존률을 확인해 보았다. 

Age, Pclass, Survived 3가지 변수를 통해, 나이대별, 등급 비율과 히스토그램을 그려, 등급별 전반적인 나이분포와 생존 사망 여부를 확인해 보았다.

Embarked, Sex, Pclass, Survived 4가지 변수를 통해, 교차표를 그려 전반적인 분포를 확인해보았다. 그 후, 승선항별 티켓 등급 비율, 승선항별 남녀 비율을 'countplot'을 이용해 시각화 하였다.

SibSp, Pclass, Age 3가지 변수를 통해, SibSp 수별 티켓 등급 비율과, SibSp별 0~14세의 어린이 비율, 20대 비율을 확인하였다.

Parch, Pclass, Age 3가지 변수를 통해, Parch 수별 티켓 등급 비율과, Parch별 0~14세의 어린이 비율, 20대 비율을 확인하였다.

Parch, SibSp: 이 두 변수를 합쳐, Fsize라는 새로운 변수를 만들어, 전체 가족 수, 생존/사망 비율을 확인해보았다.


### 2-2. 머신러닝
1. 결측치 처리
 
Embarked: 최빈값을 이용해 대체

Age: Name에 포함된 호칭을 이용해, 같은 호칭을 가진 사람들의 평균 나이로 대체하였다.

Cabin: 절반 이상이 결측치이며, Cabin에 대해 다중값을 가진 데이터도 존재하기에, 제거하였다.

2. 상관관계 파악 및 변수 선택

Sex, Embarked, Initial을 수치형 변수로 변환시켜, Survived,Pclass, SibSp, Parch, Age, Fare, Fsize 변수와 함께 상관관계를 파악해보았다.

그 후 SibSp, Parch와 상관관계가 큰 Fsize 변수를 제거하였다.

생존률에 영향을 미치지 않는, name과 ticket 변수를 제거하였다.

또한, Age_group 대신 실제값인, Age 변수를 사용해보려 한다.

3. 정규화

입력된 숫자 특성들의 스케일을 맞추기 위해, Age변수와 Fare 변수에 대한 정규화를 진행하였다.

4. 모델 학습

-로지스틱 회귀, 의사결정나무, Knn, 나이브 베이즈 분류기, 랜덤 포레스트, Svm을 이용해 정확도를 측정해보았다.

5. 성능 측정

모델 학습 부분에서 성능을 측정하였으나, 일반화 성능을 보다 정확하게 판단하기 위해서, k-fold 교차 검증을 진행하였다.

6. 모델 튜닝

k-fold 교차검증에서 성능이 좋았던, 모델들을 그리드서치를 사용해 최적의 하이퍼파라미터 값을 구했다.

그 후, 다시 교차 검증을 통해 제일 정확도가 높았던 랜덤 포레스트 모델을 사용하였다.

7. test_set 예측

train_set에서 사용했던 변수들만 남기고, 나머지 변수들은 삭제해 주었다.

동일한 방식으로 결측치 처리 후 새로운 변수를 생성해주었다.

마지막으로, 동일하게 정규화와 문자형 변수를 수치형 변수로 변환시켜 주었다.

마지막으로, 랜덤 포레스트 모델을 이용해, 예측값을 데이터프레임 안에 생성해주었다.


## 3.개발 환경 명시:
-python: 3.12.4
-Jupyter notebook: 7.2.2

** 필수 라이브러리 **
1. 데이터 분석 및 처리:pandas, numpy
2. 데이터 시각화: matplotlib, seaborn
3. 1. 머신러닝 도구: scikit-learn
   2. 데이터 분리:train_test_split
   3. 정규화: MinMaxScaler
   4. 하이퍼 파라미터 탐색: GridSearchCV
   5. 머신러닝 모델: LogisticRegression, DecisionTreeClassifier, KNeighborsClassifier, GaussianNB, RandomForestClassifier, SVM
4. 모델 성능 평가
   1. 교차 검증: KFold, cross_val_score, cross_val_predict 
   2. 혼동 행렬: confusion_matrix
   3. 분류 보고서: classification_report
   4. 평가지표: metrics


## 4.터미널 명령어:
1. 프로젝트 폴더 생성: mkdir Projects
2. 프로젝트 폴더에 깃허브 레포지터리 연결: git clone https://github.com/jungbin927/Titanic_project.git
3. 프로젝트 폴더로 이동: cd Projects/Titanic_project
4. PowerShell에서 파이썬 가상환경 생성: python -m venv.venv
5. PowerShell에서 가상환경 활성: ./.venv/Scripts/Activate.ps1
6. Jupyter notebook 및 필수 라이브러리 설치: pip install jupyter notebook pandas numpy matplotlib seaborn scikit-learn
7. git 자동 줄바꿈 설정: git config core.autoclf true
8. 이메일 및 닉네임 등록: git config --global user.email "anjung135@naver.com" / git config --global user.name "jungbin927"
9. 로컬 저장소에 저장: git commit -m "modified notebook file"
10. 깃허브 업로드: git push origin main