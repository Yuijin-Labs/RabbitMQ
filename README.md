# RabbitMQ

[RabbitMQ는 클라우드 환경 및 로컬 환경에서 쉽게 배포할 수 있는 메시지 브로커입니다.](https://www.rabbitmq.com/)

<br/><br/>

# Installation

원활한 관리를 위해 rabbitMQ docker image로 관리합니다. 또한 포트 등 설정을 간편하게 관리하기 위해 docker-compose.yml으로 관리하고 아래 형식과 같습니다.

```yaml
version: '3'
services:
  rabbitmq:
    image: rabbitmq:3-management    # 관리 UI가 포함된 이미지
    container_name: rabbitmq
    ports:
      - "5672:5672"                 # RabbitMQ 기본 AMQP 포트
      - "15672:15672"               # RabbitMQ 관리 UI 포트
    environment:
      RABBITMQ_DEFAULT_USER: guest  # 기본 사용자명
      RABBITMQ_DEFAULT_PASS: guest  # 기본 비밀번호
    volumes:
      - rabbitmq_data:/var/lib/rabbitmq  # 데이터를 저장할 볼륨

volumes:
  rabbitmq_data:
```

<br/><br/>

# Run

```shell
docker compose up -d
```

<br/><br/>

# Remove

```shell
docker-compose down --volumes
```

