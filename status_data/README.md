# Satus data
<div align="left">
    <img src="https://img.shields.io/badge/AmazonAWS-F01F7A?style=flat-square&logo=AmazonAWS&logoColor=white"/>
    <img src="https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=Terraform&logoColor=white"/>
    <img src="https://img.shields.io/badge/GitHub Actions-2088FF?style=flat-square&logo=GitHub Actions&logoColor=white"/>
    <img src="https://img.shields.io/badge/NodeJS-brightgreen?style=flat-square&logo=Node.js&logoColor=white"/>
<p>드라이버의 상태(출발 및 도착)정보를 받아 소비자에게 전달하는 서비스입니다.</p>
</div>

# 파일 설명

| Command | Description                                    |
| ---------- | ---------------------------------------------- |
| main |  전체 소스 코드의 네트워크 구현을 이해하기 위한 위한 tf 파일      |
| apigatway-status-lambda |  게이트웨이와 status-lambda 를 연결하기 위한 tf 파일           |
| dynamoDB |  dynamoDB 생성하기 위한 tf 파일           |
| status-lambda |  상태 메세지를 dynamoDB로 보내기 위한 tf 파일                  |
| status-lambda-iam | status-lambda 파일 사용을 위한 권한을 부여하는 tf 파일                  |
| hook-lambda | 디스코드로 상태 메세지를 보내기 위한 tf 파일        |
| hook-lambda-iam | hook-lambda 파일 사용을 위한 권한을 부여하는 tf 파일                 |




# 기술 설명

이 곳에서 설치에 관련된 이야기를 해주시면 좋습니다.

### aws-sdk

아래 사항들이 설치가 되어있어야합니다.

```
npm install aws-sdk
```

### axios

아래 사항들로 현 프로젝트에 관한 모듈들을 설치할 수 있습니다.

```
npm install axios
```


## Getting Started 
1. main.tf의 cloud - organization, name을 개인 terraform cloud 정보를 수정합니다.
2. terraform.yml를 .github\workflows로 위치를 변경합니다
3. secrets.TF_API_TOKEN 값을 발급받고 넣어줍니다. [참고1](https://learn.hashicorp.com/tutorials/terraform/cloud-login)
4. (Console) 콘솔상으로 실행을 할려면 다음 콘솔명령어를 실행합니다.
```
terraform login
terraform init
terraform apply
```
5. (GitActions)자동으로 배포가 가능합니다. 파일을 수정하여 GIT으로 push하면 GitActions가 실행됩니다.
![4](https://user-images.githubusercontent.com/67503900/171121876-54fb1f8a-677d-41ea-9c24-0c1ea5b06b34.JPG)

## 실행 내용
출발했을때의 예시 데이터 PUT {대기상태:0,출발:1,도착2:}

![3](https://user-images.githubusercontent.com/67503900/171121992-3e1cc170-65e6-479b-b53c-2673d84c3792.JPG)

데이터가 통과했을때의 WEBHOOK

![5](https://user-images.githubusercontent.com/67503900/171122306-07fd7b42-df30-432a-b1d0-b39e6e51a0df.JPG)

