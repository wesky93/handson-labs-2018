# 개발환경 구축

## 진행 순서

1. AWS IAM user 생성

[IAM 생성하기](https://console.aws.amazon.com/iam/home?region=ap-northeast-2#/users$new?step=details)

- datalake_2018로 생성
![alt 사용자 추가](1-1.jpg)

- 전체권한 주기
![alt 권한 추가](1-2.jpg)

사용자 생성후 액세스,시크릿키 파일을 다운 받아 주세요



2. AWS CLI 설치 및 설정
[설치 방법](https://docs.aws.amazon.com/ko_kr/streams/latest/dev/kinesis-tutorial-cli-installation.html)

```
aws configure --profile datalake
AWS Access Key ID [None]: <액세스키>
AWS Secret Access Key [None]: <시크릿키>
Default region name [None]: ap-northeast-2
Default output format [None]: json
``

3. cloud9 생성
`aws cloudformation create-stack --stack-name sls-datalake-init --template-body https://gist.githubusercontent.com/wesky93/7bab93cf680235e197391f0dc4bdec03/raw/690430e1aaf1ca9445a5b5c93844f7b87d7b2ed6/Cloud9.yml --region ap-southeast-1 --profile datalake`

[생성된 cloud9](https://ap-southeast-1.console.aws.amazon.com/cloud9/home/account)
로그인은 앞전에 생성한 datalake_2018로 로그인 해주세요

- 실습 완료후 cloud9 삭제시
`aws cloudformation delete-stack --stack-name sls-datalake-init --region ap-southeast-1 --profile datalake`

4. Cloud9 설정

- python3.6 설정 : 설정 > Project Settings > Python Suppoert > Python Version -> python3.6으로 변경
- 서울 리전 설정 : 설정 > AWS Settings > AWS > Region -> Asia Pacific(Seoul)로 변경
- git clone : `git clone https://github.com/wesky93/handson-labs-2018.git && cd handson-labs-2018/serverless_datalake`

5. 개발환경 구축
- `python3 -m venv .venv`
- `.venv/bin/activate`
- `pip install -r requierments.txt`
- `npm install -g serverless`

- [ ] kibana에서 사용할 브이월드 라이센스 키 발급 문서화 필요
- [ ] 전체 구축완료후 sls pulgin 설치과정 추가 필요