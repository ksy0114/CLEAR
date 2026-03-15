# 🛰️ CLEAR: 설명 가능한 지능형 AMR 군집 관제 시스템

> **VLA 기반 산업용 AMR 군집 제어 및 설명 가능한 지능형 FMS 개발**
> (VLA-based Industrial AMR Swarm Control & Explainable Intelligent FMS)

---

## 📌 Project Overview
본 프로젝트 **CLEAR**는 기존 규칙 기반 제어의 경직성과 AI의 블랙박스 현상을 해결하기 위한 하이브리드 자율주행 솔루션입니다.
* **VLA(Vision-Language-Action) 모델**: 카메라 영상과 자연어 명령을 복합 추론하여 로봇의 차기 목표 좌표(Target Pose)를 생성합니다.
* **하이브리드 제어 루프**: 서버(VLA)의 상위 판단과 엣지(Jetson Orin NX)의 저수준 제어(Pure Pursuit)를 결합하여 안정적인 주행을 실현합니다.
* **설명 가능한 FMS**: 로봇의 판단 근거와 신뢰도를 2D 웹 인터페이스로 시각화하여 운영자와의 소통을 강화합니다.

---

## 🛠️ Tech Stack (2026 Ver.)
- **AI/VLA (Training)**: Google Colab Pro (A100 GPU), OpenVLA, Phi-3.5-VLA, LoRA 파인튜닝
- **AI/VLA (Inference)**: FastAPI 서버, PyTorch, Quantization (4-bit)
- **OS/Middleware**: Ubuntu 24.04 LTS, ROS 2 Jazzy Jalisco
- **Robot Control**: Jetson Orin NX, Pure Pursuit Algorithm, Python/C++
- **Communication**: MQTT / WebSocket (Server-to-Robot real-time sync)
- **FMS/Monitoring**: React, TypeScript, HTML5 Canvas, PostgreSQL, Redis

---

## 👥 Team Roles (4인 동등 분담)
| 이름 | 역할 | 주요 담당 업무 |
| :--- | :--- | :--- |
| **김서영** | **인원 A: AI 추론/모델** | VLA 모델 구축 및 LoRA 학습, Target 좌표 생성 엔진, 신뢰도 산출 |
| **김범열** | **인원 B: 로봇 제어/통신** | Jetson Orin NX 환경 구축, Pure Pursuit 제어기 구현, 서버-로봇 통신 모듈 |
| **강대현** | **인원 C: 통합/시스템** | ROS 2 Jazzy 기반 시스템 통합, 다중 로봇 간 충돌 방지 로직, 전체 파이프라인 최적화 |
| **조현아** | **인원 D: FMS/데이터** | 2D 웹 관제 대시보드 개발, AI 판단 근거(XAI) 시각화, 주행 로그 DB 관리 |

---

## 📂 Directory Structure
```text
CLEAR/
├── src/
│   ├── ai_server/          # VLA Inference & Learning (FastAPI)
│   │   ├── training/       # Colab용 LoRA 학습 스크립트
│   │   └── inference/      # Target Pose 생성 및 XAI 엔진
│   ├── robot_control/      # ROS 2 Jazzy Workspace
│   │   ├── perception/     # Camera/LiDAR 데이터 처리
│   │   └── controller/     # Pure Pursuit 기반 저수준 제어
│   └── fms_web/            # 2D Web Dashboard (React)
├── docs/                   # 수행계획서 및 HCI Korea 논문 초안
└── docker-compose.yml      # 통합 배포 환경 설정
