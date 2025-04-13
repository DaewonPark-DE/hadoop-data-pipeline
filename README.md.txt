# Hadoop 기반 데이터 파이프라인 프로젝트

## 📌 프로젝트 개요
Kafka → Spark → Hadoop(HDFS) → Hive로 이어지는 데이터 파이프라인을 구축한 프로젝트입니다.  
실시간 로그 수집부터 정제, 저장, 분석이 가능한 전체 흐름을 직접 구성하여,  
데이터 엔지니어로 전환하기 위한 실전 경험을 쌓았습니다.

## 🧱 아키텍처 구성
![architecture](./docs/architecture.png)

## ⚙️ 사용 기술 스택
- **Apache Kafka** – 실시간 로그 스트리밍
- **Apache Spark (Structured Streaming)** – 실시간 처리 및 변환
- **Hadoop HDFS** – 분산 저장소
- **Apache Hive** – 분석용 SQL 쿼리 지원
- **Docker Compose** – 로컬 클러스터 환경 구축

## 🔄 데이터 흐름 설명
1. Kafka로 JSON 로그 송신 (Producer)
2. Spark Streaming이 Kafka 메시지를 수신 → Parquet 포맷으로 저장
3. HDFS에 저장된 데이터를 Hive 외부 테이블로 연결
4. Hive에서 SQL 기반 분석 수행

## 🛠️ 실행 환경
- `docker-compose.yml`로 구성된 Hadoop, Hive, Spark, Kafka 컨테이너 환경
- Hive는 metastore 연동, HDFS는 `namenode:9000` 경로 사용

## 🧪 예시 쿼리
```sql
SELECT device_id, COUNT(*) FROM logs WHERE action = 'purchase' GROUP BY device_id;
