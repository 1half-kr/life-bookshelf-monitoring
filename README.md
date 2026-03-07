# life-bookshelf-monitoring

Grafana Stack 모니터링 시스템 Ansible 배포

## 구성 요소

### 모니터링 서버 (talktobook-monitoring)
- **Grafana**: 대시보드 (포트 3000)
- **Loki**: 로그 수집 및 조회 (포트 3100)
- **Prometheus**: 메트릭 수집 및 조회 (포트 9090)

### 애플리케이션 서버
- **talktobook-server**: Spring Boot (Node Exporter + Alloy)
- **talktobook-ai**: FastAPI (Node Exporter + Alloy)
- **talktobook-stream**: RabbitMQ (Node Exporter + Alloy)

각 서버에 설치:
- **Alloy**: 로그를 Loki로 전송
- **Node Exporter**: 시스템 메트릭을 Prometheus로 전송

## 배포 방법

```bash
# 전체 배포
ansible-playbook playbook.yml

# 모니터링 서버만 배포
ansible-playbook playbook.yml --limit monitoring

# 애플리케이션 서버만 배포
ansible-playbook playbook.yml --limit app_servers
```

## GitHub Actions 배포

1. GitHub Secrets에 SSH 키 등록
2. main 브랜치에 push하면 자동 배포
인생책장 모니터링 시스템
