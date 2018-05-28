![Memory](https://github.com/ivsteam/hamonia-mon/blob/master/imgs/mem.png)

# Hamonia monitoring
하모니아 서비스에 대한 모니터링이 필요한 사용자가 쉽게 사용할 수 있도록 시계열 데이터베이스와 대시보드를 포함하여 제공합니다

## 서비스 구성
Hamonia 데이터 수집 --> InfluxDB 저장 --> Grafana 대시보드

## InfluxDB
InfluxDB 는 시계열 데이터베이스 입니다.
시계열 데이터베이스란 시간을 기반으로 지표를 쌓을 수 있게 해주는 데이터베이스로서 time 컬럼이 기본으로 탑재되는 데이터베이스를 의미합니다.
InfluxDB 는 HTTP 기반의 REST API를 제공하기 때문에 쉽게 지표를 쌓을 수 있습니다.

## Grafana
Grafana 는 시각화 도구입니다. 
쌓여있는 데이터를 효과적으로 시각화 할 수 있도록 해주는 프로그램으로서 모니터링을 위한 대시보드를 만드는 데 많이 사용되고 있습니다.

## History
* 2018-05-28 v1.0 - Grafana with InfluxDB Using docker-compose for Hamonia


# Requirement
- Ubuntu 16.04 에서 테스트 되었습니다.
- 시스템에 docker 가 필요합니다. 없는 경우 [이 문서](https://docs.docker.com/install/linux/docker-ce/ubuntu/) 를 참고하세요.
- docker-compose 가 필요니다. 없는 경우 [이 문서](https://docs.docker.com/compose/install/#install-compose) 를 참고하세요.
- 서비스를 위해서 3000/tcp, 8086/tcp 포트를 사용할 수 있어야 합니다. 


# Demo
- Demo site : [http://demo.invesume.com:3000]
- Login Account : admin / admin


# Install and Run

## 소스코드 다운로드
```
$ git clone https://github.com/ivsteam/hamonia-mon.git
```

## 빌드
```
$ cd hamonia-mon
$ docker-compose build
```

## 서비스 구동
```
$ docker-compose up -d
```
구동 후 grafana 플러그인을 다운로드 받는 과정이 있어서 시간이 걸립니다.
바로 접속하지 말고 1~2분 정도 기다려야 정상적으로 구동 됩니다.

## 접속

[http://localhost:3000](http://localhost:3000) 으로 접속한 후 admin/admin 으로 로그인 합니다.

## 데이터 보관
docker 를 재구동해도 데이터가 로컬 서버에 남아 있도록 분석한 데이터는 서버에 보관됩니다.
데이터가 저장되는 경로는 서버에서 아래의 명령어를 실행하면 알 수 있습니다.
```
$ docker volume inspect hamoniamon_grafana_data | grep Mountpoint
$ docker volume inspect hamoniamon_influxdb_data  | grep Mountpoint
```


## 모니터링 화면 예

![Memory](https://github.com/ivsteam/hamonia-mon/blob/master/imgs/mem.png)
![Network](https://github.com/ivsteam/hamonia-mon/blob/master/imgs/network.png)
![Disk](https://github.com/ivsteam/hamonia-mon/blob/master/imgs/du.png)


