# 손안집 / Sonanjip

[English](README.md) | **한국어**

*손안의 집.* **S**earch, **O**rganize, **N**ote, **A**sk — **N**atively, **J**ointly, **I**n **P**rivate.

AI를 폰 안에 두는 Android 앱 네 개입니다. 계정도 클라우드도 없습니다. 모델은 기기에서 돌고, 파일과 노트는 폰을 떠나지 않으며, 앱들은 한 지붕 아래에서 서로 돕습니다. 앱 이름은 모두 영어로도 부르기 쉬운 한국어입니다.

| 앱 | 하는 일 |
|---|---|
| [**온돌샘 / OndolSaem**](https://github.com/sonanjip/ondolsaem) | 모델 호스트. AI 모델을 한 번만 받아 메모리에 올려 두고 다른 앱과 함께 씁니다(임베딩, 채팅, OCR, 음성 인식, 얼굴, 예·아니오 판단, 지원 칩에서는 NPU). 집 전체를 데우는 *온돌*과 누구나 물을 긷는 *샘*. |
| [**눈소리 / Nunsori**](https://github.com/sonanjip/nunsori) | 폰 안의 사진·문서·음성·영상을 의미로 검색합니다. *눈*으로 보고 *소리*로 듣습니다. |
| [**조각보 / Jogakbo**](https://github.com/sonanjip/jogakbo) | 메모, 웹페이지, 유튜브, 녹음을 노트로 모으고, 폰에서 요약·태그·검색을 합니다. 자투리 천을 이어 만든 *조각보*처럼. |
| [**말벗다리 / Malbotdari**](https://github.com/sonanjip/malbotdari) | 내 파일(눈소리)과 노트(조각보)를 찾아 답하는 채팅 비서. 이야기 상대 *말벗*, 앱을 잇는 *다리*. |

<p>
<img src="https://raw.githubusercontent.com/sonanjip/ondolsaem/main/docs/images/demo.gif" width="180" alt="온돌샘">
<img src="https://raw.githubusercontent.com/sonanjip/nunsori/main/docs/images/demo-search.gif" width="180" alt="눈소리">
<img src="https://raw.githubusercontent.com/sonanjip/jogakbo/main/docs/images/demo.gif" width="180" alt="조각보">
<img src="https://raw.githubusercontent.com/sonanjip/malbotdari/main/docs/images/demo.gif" width="180" alt="말벗다리">
</p>

## 앱 사이의 관계

```mermaid
flowchart RL
    subgraph phone["📱 내 폰 (밖으로 나가는 것 없음)"]
        M["💬 말벗다리<br/>채팅 비서"]
        N["👁️ 눈소리<br/>파일 검색"]
        J["🧩 조각보<br/>노트"]
        O["♨️ 온돌샘<br/>모델 호스트"]
    end
    M -- "파일 검색·읽기" --> N
    M -- "노트 검색·읽기" --> J
    N -. "인덱스 변경 알림" .-> M
    M -- "채팅, 판단" --> O
    N -- "임베딩, OCR, 음성 인식, 얼굴" --> O
    J -- "요약, 음성 인식, 임베딩, 태그" --> O
```

온돌샘은 다른 앱 없이도 설치할 수 있고, 나머지 앱들이 모두 기대는 바탕이라 먼저 설치합니다. 눈소리와 조각보는 온돌샘만 있으면 되고, 말벗다리는 온돌샘에 더해 설치된 눈소리와 조각보도 씁니다.

## 이름의 뜻

여기의 이름은 모두 영어로도 발음하기 쉬운 일상적인 한국어 단어의 조합이고, 하는 일을 풀어 쓴 역두문자가 붙어 있습니다.

- **손안집 (Sonanjip)**: **손** + **안** + **집**, *손안의 집*입니다. 앱들은 손에 쥔 폰 안에 살고, 내 것은 그 집 밖으로 나가지 않습니다. *온돌*과 *조각보*가 이미 한옥 살림에서 온 이름이라, 조직은 그 앱들이 함께 사는 집이 됩니다. 역두문자: **S**earch, **O**rganize, **N**ote, **A**sk(앱들이 하는 일) — **N**atively, **J**ointly, **I**n **P**rivate(하는 방식).
- **온돌샘 (OndolSaem)**: 집 전체를 밑에서 데우는 **온돌** + 누구나 물을 길어 가는 **샘**. 다른 앱들 아래에서 모델을 데워 두고, 모든 앱이 같은 샘에서 길어 갑니다. ONDOL + SAEM. [자세히](https://github.com/sonanjip/ondolsaem/blob/main/README.ko.md#이름의-뜻)
- **눈소리 (Nunsori)**: **눈** + **소리**. 눈으로 보는 것과 귀로 듣는 것을 함께 인덱싱합니다. NUNSORI. [자세히](https://github.com/sonanjip/nunsori/blob/main/README.ko.md#이름의-뜻)
- **조각보 (Jogakbo)**: **조각** + **보**. 자투리 천을 이어 만든 보자기처럼, 웹페이지·영상·녹음·메모 조각을 이어 노트로 모읍니다. JOGAKBO. [자세히](https://github.com/sonanjip/jogakbo/blob/main/README.ko.md#이름의-뜻)
- **말벗다리 (Malbotdari)**: 이야기 상대 **말벗** + 앱을 잇는 **다리**. 대화하는 비서이면서 다른 앱으로 건너가 답을 찾아옵니다. MALBOT + DARI. [자세히](https://github.com/sonanjip/malbotdari/blob/main/README.ko.md#이름의-뜻)

**설치**: 온돌샘을 먼저 설치하고, 원하는 앱을 추가하세요. APK는 각 레포의 Releases에 있습니다(Android 10 이상, arm64). 네 앱은 같은 키로 서명되어 서로 승인 없이 바로 연결됩니다.
