# <img src="https://github.com/user-attachments/assets/34f114bb-c04a-424a-8ccf-de89b5b6dcc6" width="50" alt="лунамояGIF"> Innerverse
> **시간성과 감정을 주제로 한 XR 명상 프로토타입**


<br/>

## Project Info
* **Development Period:** 2025.06.24 ~ 2025.07.01 (1 Week)
* **Team Composition:** **1인 개발**
* **Role:** 기획, 시스템 설계, 콘텐츠 구현, 최적화 전담
* **Target Device:** Meta Quest (Standalone)

<br/>

## Overview
**Innerverse**는 시간의 흐름과 감정의 변화를 주제로 한 **XR 기반 명상 프로토타입**입니다.

단 1주일의 개발 기간 동안, XR SDK의 핵심 기능을 활용하여 현실 공간(MR)에서 가상의 황혼(VR)으로 이어지는 연출을 구현하는 데 집중했습니다.

<br/>

##  Demo Video
이미지를 클릭하면 유튜브 영상으로 이동합니다.

[![Innerverse Demo](https://img.youtube.com/vi/j6A2rMOCzRQ/maxresdefault.jpg)](https://www.youtube.com/watch?v=j6A2rMOCzRQ)

<br/>

## Key Features & Sequence

### 1. MR Environment & Hand Interaction
* **Gesture-Based Spawn**: 패스스루(Passthrough) 환경에서 **왼손바닥**을 펼치는 제스처를 인식하여 'Innerverse' 구체를 소환합니다.
* **Socket Interaction**: **오른손**으로 구체를 터치하면 상호작용 소켓이 생성되며, 구체를 소켓에 끼워 넣는 직관적인 행동을 통해 다음 시퀀스로 진입합니다.
* **Seamless Transition**: 단순한 씬 로딩(Cut)이 아닌, Skybox의 색상 그라디언트 변화와 Passthrough 투명도(Opacity)를 실시간으로 조절하여 **현실과 가상의 경계를 부드럽게 허무는 연출**을 구현했습니다.

### 2. Immersive VR Twilight
* **Dynamic Lighting**: 약 **1분 40초** 동안 진행되는 명상 시퀀스에 맞춰, 해가 지고 밤이 찾아오는 조도 변화를 시각적으로 표현했습니다.
* **Synesthetic Feedback (공감각적 경험)**: 시각적 변화뿐만 아니라, 손을 물 오브젝트에 가까이 대면 물 흐르는 소리가 커지는 **거리 기반 인터랙티브 사운드**를 적용하여 몰입감을 극대화했습니다.
* **Atmosphere**: 주변을 부유하는 나비와 파티클 효과를 통해 평온하고 몽환적인 명상 분위기를 조성했습니다.

<br/>

## Tech Stack

| Category | Details |
| :--- | :--- |
| **Engine** | Unity 2022.3 LTS (URP) |
| **XR Framework** | Meta XR SDK (Core, Interaction, Building Blocks)<br>OpenXR, XR Interaction Toolkit |
| **Language** | C# |
| **Async** | **Cysharp.UniTask** |
| **Platform** | Android (Meta Quest Series) |

<br/>

## Optimization Strategy
모바일 XR 환경(Standalone)에서 **72fps 방어**와 발열 최소화를 위해 다각도의 최적화를 수행했습니다.

### 1. Async Logic (비동기 시스템)
* **UniTask**: 기존 Coroutine 대비 GC(가비지 컬렉션) 할당이 적고 가독성이 좋은 **UniTask**를 사용하여 비동기 로직을 경량화했습니다.
* **Non-Blocking Loading**: `0.AsyncLoadingScene`을 별도로 구축하여 씬 전환 시 화면 멈춤(Freezing) 현상을 방지하고 사용자 경험을 개선했습니다.

### 2. Rendering & GPU
* **URP Lightweight Setup**: Depth Texture 및 Opaque Texture 비활성화, Main Light Shadow 해상도, Shadow Distance 10m 제한 등을 통해 렌더링 파이프라인 부하를 최소화했습니다.
* **Draw Call Reduction**:
    * **GPU Instancing**: 동일한 머티리얼을 사용하는 환경 오브젝트의 배칭 처리.
    * **LOD (Level of Detail)**: 나무 등 자연물에 3단계 LOD를 적용하여 거리에 따른 폴리곤 연산 최적화.

### 3. Lighting & Device Setting
* **Baked Lighting**: 모든 정적(Static) 조명을 **Baked** 모드로 설정하여 런타임 라이트 연산 비용을 0에 가깝게 제거했습니다.
* **OVR Optimization**: 앱 구동 시 `Foveated Rendering(FFR)`, `Display Frequency` 등 오큘러스 전용 하드웨어 최적화 옵션이 자동으로 적용되도록 스크립팅했습니다.

<br/>

## Resources
* 본 프로젝트는 **Unity Asset Store**의 무료 라이선스 에셋을 활용하여 제작되었습니다.

---

<div align="left">
  <strong>나우진 (Woojin Na)</strong>
  <br>
  Unity Client Developer
  <br><br>
  <a href="mailto:uujin314@icloud.com">
    <img src="https://img.shields.io/badge/Email-uujin314@icloud.com-bed?style=flat-square&logo=icloud&logoColor=white"/>
  </a>
</div>
