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

<h4> 6.1. 설치방법</h4>
일반적인 aar 라이브러리의 추가 방법과 동일합니다. 이 문서에서는 초기 버전인 0.0.1 버전기준으로 설명하고, 안드로이드 3.3.2 버전 기준으로 설명합니다.

블로그에서 vehicleplus-sdk-android-0.0.1.aar를 다운로드 받습니다. <br>

안드로이드 스튜디오에서 Project 탭에서 app\libs 폴더에 다운로드된 aar파일을 추가합니다. <br>

![](/resources/images/library_manual_image_01.png)

>NOTE : aar 파일을 정상적으로 반영하기 위해 Sync Project with Gradle Files를 확인해주십시오. 그렇지 않으면 SDK를 정상적으로 사용할 수 없습니다.

<h4>6.2. Project의 build.gradle에 libs 폴더 추가하기 </h4>
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

<h4>6.3. Module:app의 build.gradle에 aar library 추가하기</h4>

<pre><code>
dependencies {
	implementation 'com.awesomeit.vehicleplus.library:vehicleplus-sdk-android-0.0.1@aar'
}
</code></pre>

### 7. Hello Vehicle Plus
<h4> 7.1. 리스너 설치하기</h4>
비이클 플러스에서 데이터를 수신하기 위해서는 데이터 수신을 하기 위한 리스너를 연결해줘야 합니다. 크게 2가지의 리스너가 있으며, 인터페이스로 구현되어 있으므로 사용할 클래스에 implements 해주면 됩니다.

>NOTE : 예제에서는 사용법을 안내하기 위해 MainActivity에 Interface를 연결하였습니다.

<h4> 7.2 기본적인 SDK의 동작 설명</h4>

차량의 데이터를 수신하기전에 비이클 플러스 에이전트앱과 연결을 하기 위한 작업을 수행해야 합니다. <br>
기본적으로 SDK는 에이전트앱과 연결할 수 있는 API들의 모음이며, 실제 차량과 통신 및 기타 작업을 수행하는 역할은 에이전트앱입니다.<br>
SDK의 VehicleManager 클래스를 이용해서 에이전트앱과 상호작용을 할 수 있습니다. <br>
VehicleManager 클래스를 사용할 클래스에 멤버로 지정하여 사용하면 편리합니다.<br>
VehicleManager를 사용하기 위해 new 키워드로 Object 생성시 Context를 Parameter로 넘겨줘야합니다. <br>

<pre><code>
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;import com.awesomeit.vehicleplus.library.api.VehicleManager;

public class MainActivity extends AppCompatActivity {
	private VehicleManager mVehicleManager = null;  
  
	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);  
		setContentView(R.layout.activity_main);  
  
		mVehicleManager = new VehicleManager(getApplicationContext());
	}
}
</code></pre>

<h4>7.3. 에이전트앱과 연동하기</h4>
VehicleManager를 생성하였다면, 본격적으로 에이전트앱과 연결하기를 구현합니다. <br>
에이전트앱을 실행하기 위해서는 다음과 같은 단계를 거칩니다. <br>

* connect(String, String) : void 호출
* setOnConnectionListener(ConnectionListener) : boolean 호출
* onConnected(void) : void 콜백 수신
* subscribe(VehicleDataRequest, VehicleDataListener) : void 호출
* start() : boolean 호출
* onDataReceived(VPVehicleDataTable) : void 콜백 수신

> NOTE : onDataReceived는 실제 데이터를 수신하는 콜백메서드로, JSON으로 만들어진 VPVehicleDataTable 객체를 수신합니다. VPVehicleDataTable은 String, VPVehicleData로 이루어진 HashMap을 멤버로 가지고 있습니다.

<h4>7.4. 에이전트앱과 연결하기 (connect, setOnConnectionListener) </h4>
에이전트앱과 SDK를 연결하기 위해서는 connect 메서드를 이용합니다. <br>
connect 메서드를 사용하면 에이전트앱에서 허용된 RemoteService에 binding 할 수 있습니다.<br>
connect 메서드를 실행하고 에이전트앱과 연결되면 onConnected 메서드가 콜백됩니다. 이때 onConnected 메서드의 콜백을 받기 위해서는 ConnectionListener 인터페이스를 구현(implements)하고, 리스너를 등록해주어야 합니다. 예제 코드는 다음과 같습니다. <br>

<pre><code>
public class MainActivity extends AppCompatActivity implements ConnectionListener {
	private VehicleManager mVehicleManager = null;
	private String mLicenseKey = "hdlgr8iTH/EoBtqBYPEDNtnUrKj/";
	private String mDescription = "description for application";  

	@Override  
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);  
		setContentView(R.layout.activity_main);  
  
		mVehicleManager = new VehicleManager(this);  
		mVehicleManager.setOnConnectionListener(this);
	}
  
	@Override
	protected void onStart() {  
		super.onStart();
		mVehicleManager.connect(mLicenseKey, mDescription);
	}
  
	@Override  
	public void onConnected() {  
		// This callback method is called when the SDK and agent are connected.  
	}  
  
	@Override  
	public void onConnectionFailed(VPResultInfo vpResultInfo) {  

	}  
}
</code></pre>

<h4> 7.5. 인증시도하기 (Certifications)</h4>
connect 메서드를 이용하여 연결 시도를 수행할때, connect 메서드의 파라미터를 확인해야합니다.<br>
connect 메서드의 파라미터로는 2가지가 필요합니다. <br>
첫번째는 어썸잇에서 발급해야하는 암호화된 인증키이며, 두번째는 앱을 설명할 문구입니다.<br>
비이클 플러스와 SDK는 어썸잇에서 발급한 올바른 인증키가 있어야 정상적으로 작동됩니다.<br>
connect를 통해 연결과 인증을 정상적으로 완료하면, 설치한 onConnected로 정상적으로 연결되었다는 콜백을 수신하게 됩니다.<br>
연결을 수행하기가 실패되면, onConnectedFailed 메서드에 실패 사유와 함께 콜백이 수신됩니다.<br>

>NOTE : 어썸잇에서 발급되는 인증키는 AES256으로 암호화된 String의 형태로 구성되어 있습니다. 간단한 등록절차를 통해 사용자 정보를 등록한 후 발급하고 있습니다. onConnectFailed 메서드의 실패 사유는 별도의 문서에 정의되어 있습니다.<br> VPResultInfo의 getResult 메서드를 호출하여 원인을 찾아서 해결해야 합니다.

<h4> 7.6. 중단하기(disconnect)</h4>
에이전트앱과 SDK의 연결을 끊을 수 있습니다. 앱의 종료 프로세스에 반드시 추가되어야 합니다.<br>
disconnect 메서드 없이 종료는 할 수 있습니다만, 그렇게 되면 unbinding 및 exception이 발생할 수 있습니다. <br>

<pre><code>
private void stopVehicleData() {
	mVehicleManager.disconnect();
}</code></pre>

<h4> 7.7. VehicleDataListener 연결하기 </h4>
차량의 데이터를 수신하기 위해서는 SDK의 VehicleManager의 VehicleDataListener를 구현해야합니다. <br>
VehicleDataListener를 구현하면 onReceived 메서드를 Override 해줘야합니다.

<pre><code>
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import com.awesomeit.vehicleplus.library.api.VehicleDataListener;

public class MainActivity extends AppCompatActivity implements VehicleDataListener {
	@Override  
	protected void onCreate(Bundle savedInstanceState) {  
		super.onCreate(savedInstanceState);  
		setContentView(R.layout.activity_main);  
	} 
  
	@Override  
	public void onDataReceived(VPVehicleDataTable vpVehicleDataTable) {  
	// Here your application codes..  
	}
}
</code></pre>

비이클 플러스 에이전트앱에 연결 후 subscribe(VehicleDataRequest, VehicleDataListener)를 이용하여 데이터를 수신할 수 있습니다. subscribe 메서드를 호출하고 에이전트앱에 정상적으로 연결되어 있다면, onDataReceived(VPVehicleDataTable) 메서드가 콜백됩니다. 에이전트앱이 데이터 통신 성공을 하면 HashMap 형태의 Paramter에 데이터가 전달되며, 사용자는 이 객체를 원하는 형태로 사용하면 됩니다.

<h4>7.8. VehicleDataRequest 만들기</h4>
subscribe를 호출하기전에 비이클 플러스에게 요청할 데이터 리스트를 작성해야 합니다.<br>
SDK에서는 VehicleDataRequest 클래스를 제공하고 여기에 addDataElement를 통해 원하는 데이터를 지정하여 사용할 수 있습니다.<br>
VehicleDataRequest 사용법은 build 패턴을 이용하여 간단히 사용할 수 있으며 예제 코드는 다음과 같습니다.

<pre><code>
private void getVehicleData() {
	VehicleDataRequest request = new VehicleDataRequest.Builder()  
			.addDataElement(VehicleData.Diesel.soot) // testing not supported.  
			.addDataElement(VehicleData.Battery.battery_charge_current)  
			.addDataElement(VehicleData.Battery.battery_charge_remain)  
			.build();  
}
</code></pre>
>NOTE : addDataElement(VehicleData) 및 addDataElementGroup(int[])로 데이터 리스트를 추가할 수 있습니다.

<h4>7.9. 데이터 수신하기</h4>
VehicleDataRequest와 VehicleDataListener를 정상적으로 설치하였으면 subscribe와 start를 통해 데이터 수신을 시작할 수 있습니다. 중단은 반드시 disconnect 메서드를 이용해 중단해야 합니다.

<pre><code>
private  void  getVehicleData() {

	VehicleDataRequest request = new VehicleDataRequest.Builder()  
				.addDataElement(VehicleData.Diesel.soot)
				.addDataElement(VehicleData.Battery.battery_charge_current)  
				.addDataElement(VehicleData.Battery.battery_charge_remain)  
				.build();

	mVehicleManager.subscribe(request, this);
	mVehicleManager.start();
}
</code></pre>

>NOTE : 지정되지 않은 번호의 인덱스를 addDataElement에 추가할 수는 있지만, 적합하지 않으면 에이전트앱에서 해당 데이터는 발신하지 않습니다.

<h4>7.10. 블루투스 기능 콜백 수신하기</h4>
ConnectionListener에는 onConnected(), onConnectionFailed(VPResultInfo)외에 블루투스 연결 확인을 위한 콜백도 지원합니다. <br>
비이클 플러스앱의 블루투스 연결상태를 파악할 수 있으며, 상태 변경에 대한 콜백수신이 가능합니다. 예제 코드는 다음과 같습니다.

<pre><code>
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import com.awesomeit.vehicleplus.library.api.VehicleDataListener;

public class MainActivity extends AppCompatActivity implements VehicleDataListener {
	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);  
		setContentView(R.layout.activity_main);  
	}
  
	@Override  
	public void onBluetoothConnected(VPBluetoothDeviceInfo vpBluetoothDeviceInfo) {
		// Here your application codes..  
	}  

	@Override  
	public void onBluetoothChanged(VPResultInfo vpResultInfo) {
		// Here your application codes..
	}
}
</code></pre>
