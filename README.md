# 🎤 MJ Meme Challenge

Imitate Michael Jackson's iconic sounds and see how close you get!

---

## Demo

> Just open `mj_meme_challenge.html` in any modern browser. No server required.

---

## Features

- 🕺 **"Hee Hee"** — MJ's legendary laugh
- 💥 **"Aow!"** — The iconic vocal exclamation
- ▶ Play the original audio (embedded in file)
- 🎙️ Record yourself trying to imitate it
- 📊 Similarity score with grade

---

## How to Use

1. Open `mj_meme_challenge.html` in Chrome, Safari, Firefox, or any modern browser
2. Select a meme ("Hee Hee" or "Aow!")
3. Hit **Play Original** to hear the reference sound
4. Press the 🎙️ button to start recording
5. Do your best imitation, then press stop
6. Check your score!

> You'll need to **allow microphone access** when prompted by the browser.

---

## Scoring Breakdown

### Hee Hee
| Criteria | Condition | Points |
|----------|-----------|--------|
| Syllable count | 2 syllables (2 energy peaks) | 35 |
| Duration | 0.3s – 1.8s | 25 |
| High-frequency content | ZCR > 0.07 | 25 |
| Volume | RMS 0.05 – 0.4 | 15 |

### Aow!
| Criteria | Condition | Points |
|----------|-----------|--------|
| Syllable count | 1 short sharp burst | 35 |
| Duration | 0.15s – 1.0s | 25 |
| Volume | RMS > 0.08 (loud) | 25 |
| Frequency | ZCR 0.03 – 0.12 | 15 |

---

## How It Works

No server, no AI model — just the **Web Audio API** running entirely in the browser.

```
Microphone input
    ↓
Waveform analysis via Web Audio API
    ↓
Measure: RMS energy · ZCR · syllable count · duration
    ↓
Compare against meme-specific targets → output score
```

Audio files are **Base64-encoded** and embedded directly in the HTML, so no external files are needed for playback.

---

## Tech Stack

- Vanilla JS (zero dependencies)
- [Web Audio API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API) — microphone input & waveform analysis
- [MediaRecorder API](https://developer.mozilla.org/en-US/docs/Web/API/MediaRecorder) — recording
- Base64 encoding — audio file embedding

---

## Adding New Memes

Add a new entry to the `AUDIO_B64` object and write its scoring logic inside `computeScore()`.

```javascript
// 1. Add the audio
const AUDIO_B64 = {
  heehee: '...base64...',
  dow:    '...base64...',
  shamone: '...base64...',  // new meme
};

// 2. Add scoring logic
if (selectedMeme === 'shamone') {
  // define your own criteria and point breakdown
}
```

To convert an audio file to Base64:
```bash
base64 -i your_audio.mp3 | tr -d '\n' > output.txt
```

---

## Browser Compatibility

| Browser | Supported |
|---------|-----------|
| Chrome 74+ | ✅ |
| Firefox 76+ | ✅ |
| Safari 14.1+ | ✅ |
| Edge 79+ | ✅ |

---

## License

MIT

---

Korean.ver

# 🎤 MJ 밈 챌린지

마이클 잭슨의 명대사를 따라하고, 얼마나 비슷한지 점수로 확인해 보세요!

![MJ 밈 챌린지 스크린샷](screenshot.png)

---

## 데모

> `mj_meme_challenge.html` 파일을 브라우저로 열기만 하면 바로 실행됩니다. 서버 불필요.

---

## 기능

- 🕺 **"히히"** — 마이클 잭슨의 그 유명한 웃음소리
- 💥 **"아오!"** — 전설의 추임새
- ▶ 원본 오디오 재생 (파일 내장)
- 🎙️ 마이크로 따라하기
- 📊 유사도 점수 및 등급 판정

---

## 사용 방법

1. `mj_meme_challenge.html`을 크롬/사파리/파이어폭스 등 최신 브라우저로 열기
2. 따라할 밈 선택 ("히히" 또는 "아오!")
3. **원본 듣기** 버튼으로 먼저 소리 확인
4. 🎙️ 버튼을 눌러 녹음 시작
5. 따라한 뒤 버튼을 다시 눌러 중지
6. 점수 확인!

> 브라우저에서 **마이크 권한 허용**을 해주셔야 녹음이 가능합니다.

---

## 점수 기준

### 히히
| 항목 | 조건 | 배점 |
|------|------|------|
| 음절 수 | 2음절 (피크 2개) | 35점 |
| 길이 | 0.3초 ~ 1.8초 | 25점 |
| 고음 성분 | ZCR > 0.07 | 25점 |
| 음량 | RMS 0.05 ~ 0.4 | 15점 |

### 아오!
| 항목 | 조건 | 배점 |
|------|------|------|
| 음절 수 | 1음절 (짧고 강하게) | 35점 |
| 길이 | 0.15초 ~ 1.0초 | 25점 |
| 음량 | RMS > 0.08 (강하게) | 25점 |
| 주파수 | ZCR 0.03 ~ 0.12 | 15점 |

---

## 동작 원리

별도 서버나 AI 모델 없이 **브라우저 Web Audio API**만으로 동작합니다.

```
마이크 입력
    ↓
Web Audio API로 파형 분석
    ↓
RMS(음량) · ZCR(음성 특징) · 음절 수 · 길이 측정
    ↓
밈별 기준값과 비교 → 점수 산출
```

오디오 파일은 **Base64로 인코딩**되어 HTML 안에 내장되어 있어 외부 파일 로드 없이 재생됩니다.

---

## 기술 스택

- Vanilla JS (프레임워크 없음)
- [Web Audio API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API) — 마이크 입력 및 파형 분석
- [MediaRecorder API](https://developer.mozilla.org/en-US/docs/Web/API/MediaRecorder) — 녹음
- Base64 인코딩 — 오디오 파일 내장

---

## 밈 추가하는 법

`AUDIO_B64` 객체에 새 항목을 추가하고, `computeScore()` 함수 안에 해당 밈의 판정 로직을 작성하면 됩니다.

```javascript
// 1. 오디오 추가
const AUDIO_B64 = {
  heehee: '...base64...',
  dow:    '...base64...',
  cha:    '...base64...',  // 새 밈 추가
};

// 2. 판정 로직 추가
if (selectedMeme === 'cha') {
  // 원하는 기준으로 점수 계산
}
```

오디오 파일을 Base64로 변환하는 방법:
```bash
base64 -i your_audio.mp3 | tr -d '\n' > output.txt
```

---

## 브라우저 호환성

| 브라우저 | 지원 여부 |
|----------|-----------|
| Chrome 74+ | ✅ |
| Firefox 76+ | ✅ |
| Safari 14.1+ | ✅ |
| Edge 79+ | ✅ |

---

## 라이선스

MIT

