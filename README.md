# aws-switch-accesskey

## DEPRECATE
- a 스크립트는 치명적인 문제로 인해 더이상 지원하지 않으며 삭제합니다. v0.0.1 버전에 백업했습니다.

## Description

Script for managing multiple aws sso account

~~awscli 는 AWS_PROFILE 환경변수를 통해 multi accesskey 를 관리할수 있도록 지원하고 있지만,~~

fzf 기능을 활용하여 switch 하기 위해 따로 제작한 스크립트 입니다.

## Usage

### aao

clone 해서 받은 aao 는 python3 script 입니다.

* aao 파일을 적절한 위치에 옮겨놓고 바로 사용할 수 있도록 설정합니다.

* sso-ruls.json 파일을 참고하여 파일을 생성합니다.
    * 파일 위치는 다음과 같이 합니다.
```txt
  SSO_URL_LIST_FILE = f"{Path.home()}/.aws/accounts/sso-urls.json"
```

* 사용해 봅시다.
```bash
# init
$ aao -i
aws sso login --profile 11st-dev-sso-master
aws sso login --profile 11st-prod-sso-master

# real login
$ aws sso login --profile 11st-dev-sso-master
$ aws sso login --profile 11st-prod-sso-master

# credential file setting
$ aao -s
{'sso_start_url': 'https://d-123412341234.awsapps.com/start', 'sso_region': 'ap-southeast-1'}
{'sso_start_url': 'https://d-123412341234.awsapps.com/start', 'sso_region': 'ap-southeast-1', 'sso_role_name': 'AdministratorAccess', 'sso_account_id': '12341234'}
{'sso_start_url': 'https://d-123412341234.awsapps.com/start', 'sso_region': 'ap-southeast-1', 'sso_role_name': 'Billing', 'sso_account_id': '12341234'}
{'sso_start_url': 'https://d-123412341234.awsapps.com/start', 'sso_region': 'ap-southeast-1', 'sso_role_name': 'AdministratorAccess', 'sso_account_id': '6548987'}
{'sso_start_url': 'https://d-456745674567.awsapps.com/start', 'sso_region': 'ap-southeast-1'}
{'sso_start_url': 'https://d-456745674567.awsapps.com/start', 'sso_region': 'ap-southeast-1', 'sso_role_name': 'AdministratorAccess', 'sso_account_id': '12341234'}
{'sso_start_url': 'https://d-456745674567.awsapps.com/start', 'sso_region': 'ap-southeast-1', 'sso_role_name': 'AdministratorAccess', 'sso_account_id': '1345621346'}
{'sso_start_url': 'https://d-456745674567.awsapps.com/start', 'sso_region': 'ap-southeast-1', 'sso_role_name': 'AdministratorAccess', 'sso_account_id': '425763456'}
{'sso_start_url': 'https://d-456745674567.awsapps.com/start', 'sso_region': 'ap-southeast-1', 'sso_role_name': 'AdministratorAccess', 'sso_account_id': '24572456'}

$ aao
5/5
Select credential
sso-dev-1
sso-dev-2
sso-dev-3
sso-dev-4
sso-dev-5

$ aws s3 ls
```


