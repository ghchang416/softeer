# W3 팀 위키

## **팀 활동 요구사항**

4개의 xml files들을 살펴 보고 각 화일의 셋팅 중에 중요하거나 유용하다고 생각되는 것들을 각자 골라서 용법을 파악해 보세요. 그런 다음 팀과 함께 토의한 다음, 위키에 정리하시오.

### 주요 설정 요소 및 설명

| 설정 항목 | 설명 | 비고 |
| --- | --- | --- |
| `<memoryMb>` | 각 Task(MAP/REDUCE)에 할당되는 메모리 용량 | 리소스 부족 시 OOM 발생 가능 |
| `<numReduceTasks>` | 실행될 Reduce Task 개수 설정 | 적절한 개수 설정이 성능에 중요 |
| `<compression>` | 출력 파일의 압축 여부 설정 | 저장 공간 및 네트워크 트래픽 최적화 |
| `<file>` | Mapper 또는 Reducer 실행 파일 경로 | 파이프라인 흐름 제어 핵심 |

### 각 XML 파일 분석 내용

- **job-config.xml**
    - 전체 MapReduce Job에 대한 설정 포함
    - ex: input/output path, job name 등
- **mapper-config.xml**
    - Mapper에서 필요한 설정
    - ex: Mapper class, input format 등
- **reducer-config.xml**
    - Reducer 설정
    - ex: Reducer class, output format 등
- **hadoop-site.xml**
    - 클러스터 전반에 적용되는 글로벌 설정
    - ex: replication, block size 등

---

## **팀 활동 요구사항**

'predefined keywords'가 아닌 다른 방법으로 나누고자 한다면 어떤 방법이 있을까요? 팀과 함께 논의해서 다른 방법을 시도해 보세요.

### 기존 방식: Predefined Keywords

- 사전에 정의한 긍정/부정 키워드를 기준으로 분류
- **장점**: 단순하고 빠름
- **단점**: 유연성 부족, 키워드 누락에 취약

### 대체 분류 방법 제안

| 방법 | 설명 | 장점 | 단점 |
| --- | --- | --- | --- |
| **TF-IDF + KMeans** | 단어 중요도를 수치화하고 클러스터링 | 자동 분류, 키워드 불필요 | 클러스터 해석 어려움 |
| **LDA 토픽 모델링** | 문서에서 추출된 주제 기반으로 그룹화 | 의미 기반 분류 가능 | 파라미터 튜닝 필요 |
| **Word2Vec/FastText** | 단어 임베딩으로 유사도 기반 분류 | 의미적 유사성 파악 | 임베딩 품질 의존적 |
| **Rule-based 방식** | 패턴 또는 정규식 기반 규칙 분류 | 해석 용이, 설명력 좋음 | 복잡한 패턴에서 어려움 |
| **머신러닝 분류기** | SVM, RandomForest, Naive Bayes 등 지도학습 | 높은 정확도 가능 | 라벨링 데이터 필요 |

### 결론 제안

- **TF-IDF + KMeans**
- 이유:
    - 키워드 사전에 의존하지 않고 자동 분류 가능
    - 새로운 데이터에서도 확장성 좋음
- 단점 보완:
    - 클러스터 해석을 돕기 위해 대표 단어 출력 추가
