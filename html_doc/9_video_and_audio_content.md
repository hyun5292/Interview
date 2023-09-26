※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- [Web 상의 비디오 및 오디오](#web-상의-비디오-및-오디오)<br/>
  - [`<video>` 요소](#video-요소)<br/>
  - [호환성 향상을 위한 여러 소스 형식 사용](#호환성-향상을-위해-여러-소스-형식-사용)<br/>
    - [미디어 파일의 내용](#미디어-파일의-내용)<br/>
    - [browser에서 미디어 파일 지원](#browser에서-미디어-파일-지원)<br/>
  - [기타 `<video>` 기능](#기타-video-기능)<br/>
  - [`<audio>` 요소](#audio-요소)<br/>
- [비디오 텍스트 트랙 표시](#비디오-텍스트-트랙-표시)<br/>

<br/>

# Video and Audio Content

> [목표] <b>이 글에서는 `<video>`와 `<audio>` 요소를 사용하는 방법을 알아보겠습니다. 그런 다음 동영상에 캡션/자막을 추가하는 방법을 살펴보는 것으로 마무리하겠습니다.</b>

## Web 상의 비디오 및 오디오

### `<video>` 요소

```html
<video src="rabbit320.webm" controls>
  <p>
    Your browser doesn't support HTML video. Here is a
    <a href="rabbit320.webm">link to the video</a> instead.
  </p>
</video>
```

결과

<img src="https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content/simple-video.png" alt="video 태그 결과">

- <b style="color: #F2B705;">src</b><br/>: `<img>` 요소와 마찬가지로 <b style="color: #F2B705;">src</b> 속성에는 삽입하려는 비디오 경로가 포함됩니다.

- <b style="color: #F2B705;">controls</b><br/>: 사용자는 비디오 및 오디오 재생을 제어할 수 있어야 합니다. <b style="color: #F2B705;">controls</b> 속성을 사용하여 browser의 자체 제어 interface를 포함하거나 적절한 JavaScript API를 사용하여 interface를 구축해야 합니다. interface에는 최소한 미디어를 시작 및 중지하고 볼륨을 조정하는 방법이 포함되어야 합니다.

- `<video>` 태그 내부의 단락<br/>: 이를 <b style="color: orange;">대체 content</b>라고 합니다. 이는 page에 액세스하는 browser가 해당 요소를 지원하지 않는 경우 표시되므로 `<video>` 이전 browser에 대한 대체 content를 제공할 수 있습니다. 이 경우 비디오 파일에 대한 link를 제공했기 때문에 사용자는 사용하는 browser에 관계없이 최소한 어떤 방식으로든 액세스할 수 있습니다.

<br/>

### 호환성 향상을 위해 여러 소스 형식 사용

위의 예제에는 문제가 있습니다. browser 마다 지원하는 비디오(및 오디오) 형식이 다르기 때문에 비디오가 재생되지 않을 수도 있습니다.

<br/>

#### 미디어 파일의 내용

MP3, MP4, WebM과 같은 형식을 <b style="color: orange;">컨테이너 형식</b>이라고 합니다. 이는 미디어를 설명하는 metadata, 해당 채널을 encoding하는 데 사용되는 코덱 등과 함께 미디어를 구성하는 오디오 또는 비디오 트랙이 저장되는 구조를 정의합니다.

컨테이너 내의 오디오 및 비디오 트랙은 항상 미디어를 encoding 하는 데 사용되는 코덱에 적합한 형식으로 데이터를 보유합니다. 각 오디오 트랙은 오디오 코덱을, 비디오 트랙을 사용하여 encoding 됩니다.

<br/>

#### browser에서 미디어 파일 지원

이전 section에서 설명한 코덱은 원시 오디오와 비디오가 모두 매우 크기 때문에 비디오와 오디오를 관리 가능한 파일로 압축하기 위해 존재합니다. 각 web browser는 압축된 오디오 및 비디오를 binary data로 변환하거나 그 반대로 변환하는 데 사용되는 다양한 코덱을 지원합니다.

각 browser가 서로 다른 컨테이너 파일 형식 세트를 지원할 뿐만 아니라 각각 서로 다른 코덱 선택을 지원하기 때문에 상황이 약간 복잡해집니다. 귀하의 website나 app이 사용자의 browser에서 작동할 가능성을 최대화하려면 사용하는 각 미디어 파일을 다양한 형식으로 제공해야 할 수도 있습니다.

요구 사항에 가장 적합한 컨테이너 파일 형식을 선택하는 데 도움이 필요하면 <a href="https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Containers#choosing_the_right_container">올바른 컨테이너 선택</a>을 참조하세요.

<br/>

- 명심해야 할 추가 사항<br/>
  mobile browser는 desktop 버전이 지원하는 것과 동일한 형식을 모두 지원하지 않는 것처럼 desktop browser에서 지원하지 않는 추가형식을 지원할 수 있습니다. 게다가 desktop과 mobile browser 모두 미디어 재생 처리를 오프로드하도록 설계될 수 있습니다. 즉, 미디어 지원은 사용자가 설치한 소프트웨어에 따라 부분적으로 달라집니다.

  ```html
  <video controls>
    <source src="rabbit320.mp4" type="video/mp4" />
    <source src="rabbit320.webm" type="video/webm" />
    <p>
      Your browser doesn't support this video. Here is a
      <a href="rabbit320.mp4">link to the video</a> instead.
    </p>
  </video>
  ```

  여기서 `<video>` 태그에서 <b style="color: #F2B705;">src</b> 속성을 제거하고 대신 자체 소스를 기리키는 별도의 요소 `<source>`를 포함했습니다. 이 경우 browser는 `<source>` 요소를 살펴보고 지원하는 코덱이 있는 첫 번째 요소를 재생합니다. WebM 및 MP4 소스를 포함하면 요즘 대부분의 플랫폼과 browser에서 비디오를 재생하기에 충분합니다.

  각 `<source>` 요소에는 <b style="color: #F2B705;">type</b> 속성도 있습니다. 선택 사항이지만 포함하는 것이 좋습니다. <b style="color: #F2B705;">type</b> 속성에는 지정한 파일의 MIME 유형이 포함되어 있으며 browser를 사용하여 이해하지 못하는 비디오를 즉시 건너뛸 수 있습니다. 포함되지 않는 경우 browser는 작동하는 파일을 찾을 때까지 각 파일을 로드하고 재생하려고 시도합니다. 이는 분명히 시간이 걸리고 resource를 불필요하게 사용하는 것입니다.

<br/>

### 기타 `<video>` 기능

```html
<video
  controls
  width="400"
  height="400"
  autoplay
  loop
  muted
  preload="auto"
  poster="poster.png"
>
  <source src="rabbit320.mp4" type="video/mp4" />
  <source src="rabbit320.webm" type="video/webm" />
  <p>
    Your browser doesn't support this video. Here is a
    <a href="rabbit320.mp4">link to the video</a> instead.
  </p>
</video>
```

결과

<img src="https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content/poster_screenshot_updated.png" alt="추가 비디오 속성 결과" />

- <b style="color: #F2B705;">width & height</b><br/>: 비디오 크기를 제어할 수 있습니다. 두 경우 모두 비디오는 가로-세로 비율이라고 하는 원래의 너비-높이 비율을 유지합니다. 설정한 크기만큼 화면 비율이 유지되지 않으면 영상이 가로 방향으로 공간을 채우도록 커지며, 채워지지 않은 공간은 기본적으로 단색 배경색으로 표시됩니다.

- <b style="color: #F2B705;">autoplay</b><br/>: page의 나머지 부분이 로드되는 동안 오디오나 비디오가 즉시 재생되기 시작합니다. site에서 자동 재생 비디오(또는 오디오)를 사용하지 않는 것이 좋습니다. 사용자가 매우 짜증스러울 수 있기 때문입니다.

- <b style="color: #F2B705;">loop</b><br/>: 비디오(또는 오디오)가 끝날 때마다 다시 재생을 시작하도록 합니다. 이것은 또한 성가실 수 있으므로 꼭 필요한 경우에만 사용하십시오.

- <b style="color: #F2B705;">muted</b><br/>: 기본적으로 사운드가 꺼진 상태로 미디어가 재생됩니다.

- <b style="color: #F2B705;">poster</b><br/>: 동영상이 재생되기 전에 표시될 이미지의 URL입니다. 스플래시 화면이나 광고 화면에 사용하기 위한 것입니다.

- <b style="color: #F2B705;">preload</b><br/>: 대용량 파일을 버퍼링하는 데 사용됩니다.
  - none<br/>: 파일을 버퍼링하지 않습니다.
  - auto<br/>: 미디어 파일을 버퍼링합니다.
  - metadata<br/>: 파일의 metadata만 버퍼링합니다.

<br/>

### `<audio>` 요소

```html
<audio controls>
  <source src="viper.mp3" type="audio/mp3" />
  <source src="viper.ogg" type="audio/ogg" />
  <p>
    Your browser doesn't supportthis audio file. Here is a
    <a href="viper.mp3">link to theaudio</a> instead.
  </p>
</audio>
```

결과

<img src="https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content/audio-player.png" alt="audio 요소 결과" />

시각적 구성 요소가 없기 때문에 비디오 플레이어보다 공간을 덜 차지합니다. 오디오를 재생하려면 <b style="color: #F2B705;">controls</b>만 표시하면 됩니다. HTML 비디오와의 차이점은 다음과 같습니다.

- `<audio>` 요소는 <b style="color: #F2B705;">width</b>, <b style="color: #F2B705;">height</b> 속성을 지원하지 않습니다.
- <b style="color: #F2B705;">poster</b> 속성을 지원하지 않습니다.

<br/>

## 비디오 텍스트 트랙 표시

많은 사람들은 적어도 특정 시간에는 web에서 찾은 오디오/비디오 content를 들을 수 없거나 듣고 싶어하지 않습니다.

- 청각 장애를 갖고 있는 경우 오디오를 명확하게 들을 수 없습니다.
- 시끄러운 환경에 있기 때문에 듣지 못할 수도 있습니다.
- 주의가 산만하게 방해되는 환경에서 캡션을 사용하는 것은 매우 유용할 수 있습니다.
- 비디오의 언어를 사용하지 않는 사람들은 미디어 content를 이해하는 데 도움이 되는 텍스트 대본이나 번역을 원할 수도 있습니다.

이러한 사람들에게 오디오/비디오에서 말하는 단어의 사본을 WebVTT 파일 형식과 `<track>` 요소를 사용하여 제공할 수 있습니다.

<b style="color: orange;">WebVTT</b>는 각 텍스트 문자열이 표시되어야 하는 비디오의 시간 및 제한된 스타일/위치 정보와 같은 metadata와 함께 여러 텍스트 문자열을 포함하는 텍스트 파일을 작성하기 위한 형식입니다. 이러한 텍스트 문자열을 <b style="color: orange;">큐</b>라고 하며 다양한 목적으로 사용되는 여러 종류의 큐가 있습니다.

- <b>자막</b><br/> 오디오에서 말하는 단어를 이해하지 못하는 사람들을 위한 외국 자료의 번역입니다.

- <b>캡션</b><br/> 오디오를 들을 수 없는 사람들이 무슨 일이 일어나고 있는지 이해할 수 있도록 대화 내용이나 중요한 소리에 대한 설명을 동기화했습니다.

- <b>시간 제한 설명</b><br/> 시각 장애가 있거나 시각 장애가 있는 사용자에게 중요한 영상을 설명하기 위해 미디어 플레이어에서 음성으로 읽어야 하는 텍스트입니다.

```html
<video controls>
  <source src="example.mp4" type="video/mp4" />
  <source src="example.webm" type="video/webm" />
  <track kind="subtitle" src="subtitle_es.vtt" srclang="es" label="Spanish" />
</video>
```

결과

<img src="https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Video_and_audio_content/video-player-with-captions.png" alt="video track 요소 결과">

<br/>

> [참고] 검색 엔진은 특히 텍스트를 통해 성공하기 때문에 텍스트 트랙도 SEO에 도움이 됩니다. 텍스트 트랙을 사용하면 검색 엔진이 비디오 도중에 특정 지점으로 직접 link할 수 있습니다.
