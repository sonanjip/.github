# Sonanjip / 손안집

**English** | [한국어](README.ko.md)

*A house in your hand.* **S**earch, **O**rganize, **N**ote, **A**sk — **N**atively, **J**ointly, **I**n **P**rivate.

Five Android apps that keep your AI on your phone and paired watch. No account or cloud inference: models run locally on the phone, your files, notes and recordings stay on your devices, and the apps work together under one roof. Each app has a Korean name that is easy to say in English.

| App | What it does |
|---|---|
| [**OndolSaem / 온돌샘**](https://github.com/sonanjip/ondolsaem) | The model host. Downloads each AI model once, keeps it in memory and shares it with the other apps (embeddings, chat, image generation, OCR, speech, faces, yes/no decisions; NPU on supported chips). *Ondol* warms the whole house, a *saem* (spring) serves everyone. |
| [**Nunsori / 눈소리**](https://github.com/sonanjip/nunsori) | Search the photos, documents, audio and video on your phone by meaning. *Eye and sound*: it sees and hears your files. |
| [**Jogakbo / 조각보**](https://github.com/sonanjip/jogakbo) | Notes from memos, web pages, YouTube and recordings, each with an on-device summary, tags and search. A *jogakbo* is a patchwork wrapping cloth. |
| [**Malbotdari / 말벗다리**](https://github.com/sonanjip/malbotdari) | A chat assistant that answers from your files (through Nunsori) and notes (through Jogakbo). A *malbot* is someone to talk to, a *dari* a bridge. |
| [**Dorangori / 도란고리**](https://github.com/sonanjip/dorangori) | A phone + Wear OS companion: capture voice on the watch, queue it until connected, then transcribe locally on the phone through OndolSaem. Copy the text, prefill a Malbotdari question, or save one Jogakbo note with both audio and transcript. Built to extend beyond recording into phone–watch on-device AI. |

<p>
<img src="https://raw.githubusercontent.com/sonanjip/ondolsaem/main/docs/images/demo.gif" width="180" alt="OndolSaem">
<img src="https://raw.githubusercontent.com/sonanjip/nunsori/main/docs/images/demo-search.gif" width="180" alt="Nunsori">
<img src="https://raw.githubusercontent.com/sonanjip/jogakbo/main/docs/images/demo.gif" width="180" alt="Jogakbo">
<img src="https://raw.githubusercontent.com/sonanjip/malbotdari/main/docs/images/demo.gif" width="180" alt="Malbotdari">
<img src="https://raw.githubusercontent.com/sonanjip/malbotdari/main/docs/images/demo-imagegen.gif" width="180" alt="Malbotdari (Image Generation)">
</p>

## Dorangori: watch to phone

<img src="https://raw.githubusercontent.com/sonanjip/dorangori/main/docs/images/demo.gif" width="560" alt="Dorangori watch and phone demo, side by side">

Real emulator UI, with a prerecorded speech sample supplied to the emulator microphone; inference runs locally with no cloud inference.

## How they fit together

```mermaid
flowchart RL
    W["⌚ Paired watch<br/>Dorangori voice capture"]
    subgraph phone["📱 Your phone (local inference)"]
        D["🔗 Dorangori<br/>watch companion"]
        M["💬 Malbotdari<br/>chat assistant"]
        N["👁️ Nunsori<br/>file search"]
        J["🧩 Jogakbo<br/>notes"]
        O["♨️ OndolSaem<br/>model host"]
    end
    W -- "queued audio delivery when connected" --> D
    D -- "local speech recognition" --> O
    D -- "prefill a question (optional)" --> M
    D -- "one audio + transcript note" --> J
    M -- "search and read files" --> N
    M -- "search and read notes" --> J
    N -. "index changed" .-> M
    M -- "chat, image generation, decisions" --> O
    N -- "embeddings, OCR, speech, faces" --> O
    J -- "summaries, speech, embeddings, tags" --> O
```

OndolSaem needs none of the others and all of them build on it, so install it first. Nunsori and Jogakbo need only OndolSaem; Malbotdari uses OndolSaem plus Nunsori and Jogakbo when they are installed. Dorangori needs OndolSaem **0.9.0+** for an explicit recognition language; saving audio and text together needs Jogakbo **0.7.0+**. Malbotdari is optional.

## About the names

The names draw on everyday Korean words and are easy to say in English. Some also have backronyms describing what they do; Dorangori takes its meaning from Korean words.

- **손안집 (Sonanjip)**: **손** (hand) + **안** (inside) + **집** (house), *a house in the palm of your hand*. The apps live on your phone and paired watch, and what is yours stays on your devices. *Ondol* and *jogakbo* already come from a Korean home, so the organization is the house they share. Backronym: **S**earch, **O**rganize, **N**ote, **A**sk (what the apps do) — **N**atively, **J**ointly, **I**n **P**rivate (how they do it).
- **온돌샘 (OndolSaem)**: **온돌**, the floor heating that warms a whole house from underneath, + **샘**, a spring everyone draws from. It sits below the other apps, keeps the models warm and lets every app draw from the same source. ONDOL + SAEM. [More](https://github.com/sonanjip/ondolsaem#about-the-name)
- **눈소리 (Nunsori)**: **눈** (eye) + **소리** (sound). It indexes what can be seen and what can be heard. NUNSORI. [More](https://github.com/sonanjip/nunsori#about-the-name)
- **조각보 (Jogakbo)**: **조각** (scrap) + **보** (wrapping cloth), a patchwork cloth sewn from scraps, as notes are stitched from web pages, videos, recordings and memos. JOGAKBO. [More](https://github.com/sonanjip/jogakbo#about-the-name)
- **말벗다리 (Malbotdari)**: **말벗** (someone to talk to) + **다리** (bridge). An assistant to talk with that bridges your other apps. MALBOT + DARI. [More](https://github.com/sonanjip/malbotdari#about-the-name)
- **도란고리 (Dorangori)**: **도란도란**, quiet, friendly conversation, + **고리**, a link or ring. Its teal and apricot interwoven rings icon represents watch and phone working together. [More](https://github.com/sonanjip/dorangori#about-the-name)

**Install**: start with OndolSaem, then add the apps you want. APKs are on each repository's Releases page (phone: Android 10+, arm64; watch: Wear OS 3+). The apps share a signing key for direct connections. For Dorangori, install both the phone and Wear APKs with matching signing certificates. On Samsung hardware, use the existing Galaxy Wearable app for pairing; the Pixel Watch app is only for the emulator setup. See the [Dorangori repository](https://github.com/sonanjip/dorangori) for watch sideloading over Wi-Fi ADB.
