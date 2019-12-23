### 1. 개요
이 페이지에서는 개발자용 Vehicle Plus SDK (비이클 플러스 SDK)의 사용법에 대해서 설명합니다.
비이클플러스 SDK는 비이클 플러스 앱을 사용하여 자동차데이터를 손쉽게 사용할 수 있는 개발환경입니다. 1.3.0 최신버전 기준 현재 안드로이드 환경에서 사용이 가능하며, 개발자용 SDK(Software Development Kit)와 에이전트앱을 제공합니다.

### 2. Vehicle Plus Agent App 설치하기
비이클 플러스  SDK는 첫번째로 Google Play에서 비이클 플러스앱을 설치해야 사용이 가능합니다.

Google Play를 통해 제공되는 비이클 플러스는 일반 사용자에게 공개된 어플리케이션으로 차량과의 통신을 위해 필수적으로 설치되어야하며, 개발자는 이 문서와 함께 제공되는 SDK로 에이전트앱에 접근할 수 있습니다.

비이클 플러스 앱 구글플레이 주소 : <br>
https://play.google.com/store/apps/details?id=com.awesomeit.vehicleplus

비이클 플러스 앱의 설치방법은 Google Play에서 일반적인 앱을 설치하는 방법과 동일합니다. 위의 URL에서 설치를 선택해서 진행하면 간단하게 완료할 수 있습니다.

> NOTE: 비이클 플러스 앱은 안드로이드 5.0 이상, 인터넷이 연결되어 있는 모바일에서만 지원합니다. 오프라인 환경에서만 사용가능한 프라이빗 버전은 관리자에게 별도로 문의해주시길 바랍니다.

### 3. SDK 설치하기
비이클 플러스앱을 설치하였으면, 비이클 플러스와 통신하기 위해 SDK를 설치해야합니다. SDK는 Java로 구현되어 있으며, 안드로이드 컴포넌트가 포함된 라이브러리로 구성되어 있습니다. SDK는 VehiclePlus 블로그에 공개되어 있으며, aar파일의 형태로 손쉽게 다운로드 받을 수 있습니다.

비이클 플러스 SDK 다운로드 주소 : <br>
https://github.com/vehicleplus/hello-vehicleplus

### 4. 요구사항 확인하기
비이클 플러스 SDK는 다음과 같은 사양에서 작동이 가능합니다. 안드로이드를 사용하는 모든 디바이스에서 사용이 가능하지만, 공식적으로 사용이 가능한 환경은 아래와 같습니다.

요구 환경
* Android를 지원하는 모바일(휴대폰) 디바이스
* 인터넷이 상시로 연결되어 있어야 함.
* Android 5.0 이상부터(API 21, Lollipop) Android 9.0 (API 28, Pie) 이하

사용 라이브러리
* Google / gson : https://github.com/google/gson

app.gradle에 dependencies 추가하기.
<pre><code>
dependencies {
 implementation 'com.google.code.gson:gson:2.8.5'
}
</code></pre>

> NOTE : 위에 명시된 다른 환경에서 설치 및 사용이 가능하지만, 공식적이지 않은 환경에서의 오작동은 어썸잇(주)에서 보장하지 않습니다.

### 5. 차량 연결 어댑터
비이클 플러스는 모든 사용자가 손쉽게 사용할 수 있도록 범용적으로 개발된 ELM327 인터페이스를 사용할 수 있게 구현되어 있습니다. ELM327 인터페이스를 지원하는 어댑터를 모두 지원하지만, 표준 통신만 지원하는 일부 중국산 제품은 권장하지 않습니다. <br>
ELM327 인터페이스는 현재 블루투스 어댑터만 지원합니다.

> NOTE : 이후 버전부터는 ELM327 인터페이스 및 다른 디바이스도 지원할 예정입니다. ELM327 1.5V를 권장합니다.

### 6. 비이클 플러스 SDK 설치하기
비이클 플러스 SDK는 Java로 구현되어 있는 안드로이드 라이브러리 서비스로 제공됩니다.
SDK는 Vehicle Plus 블로그에 공개되어 있으며, aar파일의 형태로 손쉽게 다운로드 받을 수 있습니다.

> NOTE : SDK를 사용하는 예제 소스는 [Github](https://github.com/vehicleplus/vehicleplus.github.io)에 오픈소스로 공개되어 있습니다. 빠르게 사용하기 위해서는 Github에 방문하여 Hello Vehicleplus를 다운받아 사용하시길 바랍니다.  
[https://github.com/vehicleplus/hello-vehicleplus](https://github.com/vehicleplus/hello-vehicleplus)

<h4> 6.1 설치방법
일반적인 aar 라이브러리의 추가 방법과 동일합니다. 이 문서에서는 초기 버전인 0.0.1 버전기준으로 설명하고, 안드로이드 3.3.2 버전 기준으로 설명합니다.

블로그에서 vehicleplus-sdk-android-0.0.1.aar를 다운로드 받습니다. <br>

안드로이드 스튜디오에서 Project 탭에서 app\libs 폴더에 다운로드된 aar파일을 추가합니다. <br>

![](/resources/images/library_manual_image_01.png)
