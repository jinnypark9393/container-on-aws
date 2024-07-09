---
description: 컨테이너 이미지의 빌드 및 저장 방법과 그 모범 사례를 알아봅니다.
---

# 컨테이너 이미지 빌드 시 모범 사례

## 컨테이너 이미지 빌드 및 배포 과정

<figure><img src="../.gitbook/assets/container-build-1.png" alt=""><figcaption></figcaption></figure>

개발자가 애플리케이션을 컨테이너로 배포하기 위해서는 컨테이너 이미지를 빌드하고 배포하는 과정이 필요합니다. 일반적으로, 컨테이너 이미지를 빌드하기 위해서는 일반적으로 [도커](https://www.docker.com/)를 사용하게 되며, Dockerfile이라는 파일에서 해당 컨테이너 이미지를 어떻게 빌드할 것인지 명세를 작성해서 컨테이너 이미지를 빌드합니다. 해당 이미지를 컨테이너 실행 환경에 배포하기 위해서 리모트 컨테이너 이미지 저장소(Container Image Registry) 이미지를 저장(push)하고, 실제 실행환경에서 애플리케이션을 구동하기 위해 저장한 이미지를 받아(pull)와 컨테이너를 실행하게 됩니다.

<figure><img src="../.gitbook/assets/container-build-2.png" alt=""><figcaption></figcaption></figure>

AWS 서비스를 활용해 애플리케이션을 컨테이너로 배포하기 위해서는 어떻게 해야 할까요? 위와 동일하게 개발자가 Dockerfile을 작성하여 컨테이너 이미지를 빌드합니다. 그 다음, 빌드된 이미지를 AWS의 관리형 이미지 저장소인 Amazon ECR에 저장(push)하고, ECR에서 이미지를 받아(pull)와 Amazon EKS 또는 Amazon ECS에서 컨테이너를 실행하게 됩니다.

<figure><img src="../.gitbook/assets/dockerfile.png" alt=""><figcaption></figcaption></figure>

Dockerfile은 위에서 설명했듯, 애플리케이션의 컨테이너 이미지를 빌드하는 데 필요한 명령어를 정의한 파일입니다. 위 이미지의 왼쪽 파일처럼, Dockerfile을 정의하여 컨테이너 이미지를 빌드할 수 있고, 하나의 명령어 라인이 하나의 컨테이너 레이어로 매핑됩니다. Dockerfile을 통해 애플리케이션의 설정과 실행 방법을 명확하게 정의할 수 있기 때문에 일관된 환경에서 애플리케이션을 배포할 수 있게 됩니다.

{% hint style="info" %}
Dockerfile에서 활용할 수 있는 명령어 리스트는 [다음 링크](https://docs.docker.com/reference/dockerfile/)에서 확인할 수 있습니다.
{% endhint %}



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
