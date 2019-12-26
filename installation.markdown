---
layout: page
title: 설치하기
permalink: /installation/
---
<h1>목차</h1>
 <ul>
	<ol type="1" start="1">
 		<li><a href="#title_1">비이클 플러스 에이전트 앱 설치하기</a></li>
		<li><a href="#title_2">SDK 설치하기</a></li>
			<ol type="a" start="a">
				<li><a href="#title_2_a">설치방법</a></li>
				<li><a href="#title_2_b">Project의 build.gradle에 libs 폴더 추가하기</a></li>
				<li><a href="#title_2_c">Module:app의 build.gradle에 aar library 추가하기</a></li>
			</ol>
		<li><a href="#title_3">라이브러리 추가하기</a></li>
			<ol type="a" start="a">
				<li><a href="#title_3_a">사용 라이브러리</a></li>
				<li><a href="#title_3_b">app.gradle에 dependencies 추가하기</a></li>
			</ol>
	</ol>
 </ul>
<br>

<h3><div id="title_1">1. 비이클 플러스 에이전트 앱 설치하기</div></h3>
비이클 플러스 SDK는 첫번째로 Google Play에서 비이클 플러스앱을 설치해야 사용이 가능합니다.

Google Play를 통해 제공되는 비이클 플러스는 일반 사용자에게 공개된 어플리케이션으로 차량과의 통신을 위해 필수적으로 설치되어야합니다.<br> 개발자는 이곳에서 제공되는 비이클플러스 SDK로 비이클플러스 앱에 접근할 수 있습니다.
<br>
<br>
비이클 플러스 앱 구글플레이 주소 : <br>
[https://play.google.com/store/apps/details?id=com.awesomeit.vehicleplus](https://play.google.com/store/apps/details?id=com.awesomeit.vehicleplus)
<br>
<br>
<br>
비이클 플러스 앱의 설치방법은 Google Play에서 일반적인 앱을 설치하는 방법과 동일합니다. 위의 URL에서 설치를 선택해서 진행하면 간단하게 완료할 수 있습니다. 
<br>
<br>
> NOTE: <br>
비이클 플러스 앱은 안드로이드 5.0 이상, 인터넷이 연결되어 있는 모바일에서만 지원합니다. <br>
오프라인 환경에서만 사용가능한 프라이빗 버전은 관리자에게 별도로 문의해주시길 바랍니다.
<br>
<br>
<h3><div id="title_2">2. SDK 설치하기</div></h3>
비이클 플러스앱을 설치하였으면, 비이클 플러스와 통신하기 위해 SDK를 설치해야합니다. SDK는 Java로 구현되어 있으며, 안드로이드 컴포넌트가 포함된 라이브러리로 구성되어 있습니다. SDK는 VehiclePlus 블로그에 공개되어 있으며, aar파일의 형태로 손쉽게 다운로드 받을 수 있습니다.

비이클 플러스 SDK 다운로드 주소 : <br>
[https://github.com/vehicleplus/hello-vehicleplus](https://github.com/vehicleplus/hello-vehicleplus)

> NOTE : SDK를 사용하는 예제 소스는 [Github](https://github.com/vehicleplus/vehicleplus.github.io)에 오픈소스로 공개되어 있습니다. 빠르게 사용하기 위해서는 Github에 방문하여 Hello Vehicleplus를 다운받아 사용하시길 바랍니다.  

<h4><div id="title_2_a">a. 설치방법</div></h4>
일반적인 aar 라이브러리의 추가 방법과 동일합니다. 이 문서에서는 초기 버전인 0.0.1 버전기준으로 설명하고, 안드로이드 3.3.2 버전 기준으로 설명합니다.

블로그에서 vehicleplus-sdk-android-0.0.1.aar를 다운로드 받습니다. <br>

안드로이드 스튜디오에서 Project 탭에서 app\libs 폴더에 다운로드된 aar파일을 추가합니다. <br>

![](/resources/images/library_manual_image_01.png)

>NOTE : aar 파일을 정상적으로 반영하기 위해 Sync Project with Gradle Files를 확인해주십시오. 그렇지 않으면 SDK를 정상적으로 사용할 수 없습니다.

<h4><div id="title_2_b">b. Project의 build.gradle에 libs 폴더 추가하기</div></h4>
aar 파일을 사용하기 위해 app/build.gradle에 추가해줘야 합니다. aar 파일을 추가하는 방법은 다음과 같습니다. 버전명은 예제와 다를 수 있으므로 다운받은 버전과 확인하여 변경해주세요.

<pre><code>
allprojects {
  repositories {
  	google()
	jcenter()
	flatDir {
           dirs 'libs'
	}
  }
}
</code></pre>

<h4><div id="title_2_c">c. Module:app의 build.gradle에 aar library 추가하기</div></h4>

<pre><code>
dependencies {
    implementation 'com.awesomeit.vehicleplus.library:vehicleplus-sdk-android-0.0.1@aar'
}
</code></pre>

<br>

<h3><div id="title_3">3. 라이브러리 추가하기</div></h3>
비이클 플러스 SDK를 사용하기 위해서는 지정된 오픈소스를 추가해야합니다.

<h4><div id="title_3_a">a. 사용 라이브러리</div></h4>
* Google / gson : https://github.com/google/gson

<h4><div id="title_3_b">b. app.gradle에 dependencies 추가하기.</div></h4>
<pre><code>
dependencies {
    implementation 'com.google.code.gson:gson:2.8.5'
}
</code></pre>

> NOTE : 위에 명시된 다른 환경에서 설치 및 사용이 가능하지만, 공식적이지 않은 환경에서의 오작동은 어썸잇(주)에서 보장하지 않습니다.