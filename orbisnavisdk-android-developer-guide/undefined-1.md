# 준비하기

### 사전 준비  <a href="#preparation" id="preparation"></a>

‌아이나비 내비게이션 SDK를 사용하기 위해서는 인증을 위한 **APP KEY**가 필요합니다.‌

#### 서비스 활성화 및 APP KEY 발급

* **APP KEY** 발급을 위해서는 [**iMPS**](https://mapsapi.inavisys.com/) 계정이 필요합니다. 계정이 없다면 먼저 계정을 생성해주세요.
* [**iMPS Console**](https://mapsapi.inavisys.com/dash-board/) 에서 APP을 생성합니다.
* 생성된 APP에서 상품을 신청을 신청하시면, **APP KEY**를 확인할 수 있습니다.

### Android Studio 프로젝트 환경 구성 <a href="#project-settings" id="project-settings"></a>

아이나비 지도 SDK는 별도 저장소를 통해 배포되므로, 다음과 같이 프로젝트 및 앱 모듈 레벨의 **build.gradle** 파일에 저장소 설정과 아이나비 지도 SDK에 대한 의존성을 추가합니다.

```groovy
/* Root Project build.gradle.kts */
dependencyResolutionManagement {
    repositories {
        google()
        mavenCentral()
        maven { url = uri("https://repo.inavi.com/artifactory/navigation") }
    }
}
```

```groovy
/* App Module build.gradle */
dependencies {
    implementation 'com.inavisys.navisdk.ui:ui-android:0.0.1'
}
```

### APP KEY 설정 <a href="#app-key-settings" id="app-key-settings"></a>

발급받은 **APP KEY**를 설정할 수 있도록 아래의 두 가지 방법을 제공합니다.

{% hint style="danger" %}
**APP KEY**가 설정되지 않으면 초기화 단계에서 인증 오류가 발생합니다.
{% endhint %}

#### AndroidManifest.xml에서 설정

**AndroidManifest.xml**에 다음과 같이 `<meta-data>`를 추가하여 **APP KEY**를 설정할 수 있습니다.

```markup
<!-- AndroidManifext.xml -->
<manifest>
    <application>
        <meta-data
            android:name="com.inavi.navisdk.appkey"
            android:value="YOUR_APP_KEY" />
    </application>
</manifest>
```

