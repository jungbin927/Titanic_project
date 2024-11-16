# Titanic_project

## 분석 목적:
본 프로젝트는 Titanic 승객 데이터를 바탕으로, 변수들의 특성을 파악하여 숨겨진 의미를 파악하는 프로젝트이다.
또한 의미있는 특성을 활용하여 모델을 학습시키고, 탑승객의 생존 여부를 예측하는 머신 러닝 프로젝트이다.

## 구체적 구현 내용:
### 1.EDA
우선 단일 변수를 분석하였다. 
Survived, Pclass, Sex, SibSp, Parch, Embarked: 범주형 변수들을 원 그래프와 히스토그램을 이용해, 전반적인 분포와 비율을 확인하였다.
그리고, Survived 변수의 사망/생존 비율을 기준으로, 어떠한 특성,상황에서 생존률이 높고 낮은지 'barplot','countplot'을 이용해 파악하였다.

Age: 수치형 변수인, Age를 나이의 분포와 생존비율을 확인하기 위해, 5살 단위로 나눠서 시각화하였다.
Fare: 다른 수치형 변수인, Fare는 Pclass와 관련이 있을거라 판단해, Pclass별 Fare의 평균을 확인하였고, 히스토그램을 통해 등급 별 요금의 전반적인 분포를 확인하였다.
Name: 성을 이용해 몇몇 가족을 파악할 수 있었고, 이름 내에 칭호가 존재하는 것을 확인하였다.
Ticket: 동일한 티켓 번호를 통해 몇몇의 가족을 파악할 수 있었다.
이처럼 단일 변수 파악 및 특성, 상황 별 Survived를 통해, 생존률이 높은 특성들을 파악할 수 있게 되었다.

그 후 조금 더 구체적으로 파악해보기 위해서 여러 변수들을 조합하여, 전반적인 분포와 생존률을 확인해 보았다.
Sex, Pclass,Survived 3가지의 변수를 통해, 각 등급별 남녀의 비율. 각 등급별 남녀의 생존률을 확인해 보았다. 
Age, Pclass, Survived 3가지 변수를 통해, 나이대별, 등급 비율과 히스토그램을 그려, 등급별 전반적인 나이분포와 생존 사망 여부를 확인해 보았다.
Embarked, Sex, Pclass, Survived 4가지 변수를 통해, 교차표를 그려 전반적인 분포를 확인해보았다. 그 후, 승선항별 티켓 등급 비율, 승선항별 남녀 비율을 'countplot'을 이용해 시각화 하였다.
SibSp, Pclass, Age 3가지 변수를 통해, SibSp 수별 티켓 등급 비율과, SibSp별 0~14세의 어린이 비율, 20대 비율을 확인하였다.
Parch, Pclass, Age 3가지 변수를 통해, Parch 수별 티켓 등급 비율과, Parch별 0~14세의 어린이 비율, 20대 비율을 확인하였다.
Parch, SibSp: 이 두 변수를 합쳐, Fsize라는 새로운 변수를 만들어, 전체 가족 수, 생존/사망 비율을 확인해보았다.

## 개발 환경 명시:
python: 3.12.4
Jupyter notebook: 7.2.2
** 필수 라이브러리 **
-pandas
-numpy
-시각화: matplotlib, seaborn
-sklearn-learn
-train_test_split
-머신러닝 모델: LogisticRegression, DecisionTreeClassifier, KNeighborsClassifier, GaussianNB, RandomForestClassifier
-앙상블 분석: AdaBoostClassifier
-모델 성능 평가:cross_val_score, confusion_matrix, classification_report, metrics

## 터미널 명령어:
1. 프로젝트 폴더 생성: mkdir Projects
2. 프로젝트 폴더에 깃허브 레포지터리 연결: git clone https://github.com/jungbin927/Titanic_project.git
3. 프로젝트 폴더로 이동: cd Projects/Titanic_project
4. PowerShell에서 파이썬 가상환경 생성: python -m venv.venv
5. PowerShell에서 가상환경 활성: ./.venv/Scripts/Activate.ps1
6. Jupyter notebook 및 필수 라이브러리 설치: pip install jupyter notebook pandas numpy matplotlib seaborn scikit-learn
7. git 자동 줄바꿈 설정: git config core.autoclf true
8. 이메일 및 닉네임 등록: git config --global user.email "anjung135@naver.com"
git config --global user.name "jungbin927"
9. 로컬 저장소에 저장: git commit -m "modified notebook file"
10. 깃허브 업로드: git push origin main
VS 코드에서 프로젝트 폴더 연결 후, pypproject.toml, .gitignore 생성
.gitignore에 .venv, ipynb_.checkpoints 적어 비활성화
