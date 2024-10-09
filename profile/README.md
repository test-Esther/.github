# 1st Project_ETL

## Topic
- 영화 박스오피스 API를 이용하여 ETL 수행 

## Object
- 영화 박스오피스 데이터 수집/처리/보관 및 활용
- 각각 단계에 대하여 파이썬 프로그램을 package(PIP설치) 단위로 개발
- 개발 package 를 airflow 적용 및 운영

## Structure
![image](https://github.com/user-attachments/assets/6d8a831a-4b24-43ab-8bdf-abd16203b1a5)
### Extract
- 한국영화진흥위원회 open API 사용, ETL 과정 중 추출 단계
### Load
- 2016년도에 개봉한 영화 중 매출액 기준 상위 10개의 영화를 집계하는 단계
### Transform
- Load 단계에서 집계된 자료 중 한국 영화만 필터링하는 단계
### Airflow
- ETL 과정의 결과를 airflow로 가시화

## Branch strategy
![image](https://github.com/user-attachments/assets/e1cc7dd3-90e8-44a9-b408-96142738ffaf)

## Usage
- 공통 작업 (Option)
```bash
# 개발 및 수정
$ pdm init
$ source .venv/bin/activate
$ pdm install

# Option
$ pdm venv create
```
### Extract
```bash
$ git clone git@github.com:test-Esther/extract.git
$ cd team_jkl/extract
```
### Load
```bash
$ pip install git+https://github.com/test-Esther/load.git
$ cd team_jkl/load

# plus top10.parquet 파일 필요
```
### Transform
```bash
$ git clone git@github.com:test-Esther/tranform.git
$ cd team_jkl/transform
```
### Airflow
```bash
$ pip install git+https://github.com/test-Esther/airflow_jkl.git

# 환경 설정
# 해당 프로그램 사용 시 airflow 설치 필수

$ pyenv virtualenv <virtual environment> <environment name>
$ pyenv shell <environment name>
$ pip install apache-airflow

# 이후,
$ vi ~/.zshrc

[Airflow]
$ export AIRFLOW_HOME=~/airflow_<YOURS>
$ export AIRFLOW__CORE__DAGS_FOLDER=<YOURS>/airflow/dags
$ export AIRLFOW__CORE__LOAD_EXAMPLES=False

# 실행
$ airflow standalone
```
#### 유의사항
- 해당 프로그램에 접속하려면 한국영화진흥위원회(kobis)에서 발급한 key 및 ~/.zshrc에 환경 변수로 저장 필요
```bash
$ export MOVIE_API_KEY=<YOUR KEY>
```

## Result
### Pipeline
#### Extract
![pipe_line_E](https://github.com/user-attachments/assets/3f2c9214-4ec0-478b-b1f5-96134de7d17a)
#### Load and Transform
![pipe_line_T](https://github.com/user-attachments/assets/2bb275aa-5958-4a7c-8066-c1acd2bf4610)

### Top 10
![result1](https://github.com/user-attachments/assets/5dba3a20-5a18-4f96-a8c2-726786c83d5a)


