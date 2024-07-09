---
description: 컨테이너 이미지의 빌드 및 저장 방법과 그 모범 사례를 알아봅니다.
---

# 컨테이너 이미지 빌드 시 모범 사례

## 컨테이너 이미지 빌드 및 배포 과정

<figure><img src="../.gitbook/assets/container-build-1.png" alt=""><figcaption></figcaption></figure>

컨테이너 이미지를 빌드하기 위해서 일반적으로 [도커](https://www.docker.com/)를&#x20;



<figure><img src="../.gitbook/assets/container-build-2.png" alt=""><figcaption></figcaption></figure>



<figure><img src="../.gitbook/assets/dockerfile.png" alt=""><figcaption></figcaption></figure>



## 컨테이너 이미지 빌드 시 모범 사례

1.  이미지 레이어를 최소화 하기 위해 다수의 명령어를 묶어서 실행합니다.

    <figure><img src="../.gitbook/assets/container-image-build-bp-1 (1).png" alt=""><figcaption></figcaption></figure>
2.  멀티 스테이지 빌드를 활용하여 이미지 레이어를 최소화합니다.

    <figure><img src="../.gitbook/assets/container-image-build-bp-2.png" alt=""><figcaption></figcaption></figure>
3.  컨테이너 이미지 레이어 캐싱을 극대화 하기 위해 자주 변경되지 않는 Framework, Library 및 애플리케이션 레이어를 분리합니다.

    <figure><img src="../.gitbook/assets/container-image-build-bp-3.png" alt=""><figcaption></figcaption></figure>
4.  좀비 프로세스의 방지를 위해 tini, dumb-init과 같은 도구를 활용합니다.

    <figure><img src="../.gitbook/assets/container-image-build-bp-4.png" alt=""><figcaption></figcaption></figure>
5.  멀티 아키텍처 이미지를 빌드하여 다양한 플랫폼의 인스턴스를 활용할 수 있도록 합니다.

    <figure><img src="../.gitbook/assets/container-image-build-bp-5.png" alt=""><figcaption></figcaption></figure>
