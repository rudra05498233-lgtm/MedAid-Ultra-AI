# MedAid Ultra — AI-Powered First Aid Assistant

**Live demo:** https://rudra05498233-lgtm.github.io/MedAid-Ultra-AI/

Every year, people in India are harmed not because treatment wasn't available, but because nobody knew what to do in the first few minutes. MedAid Ultra is a free, no-login web app that gives anyone quick first-aid guidance, symptom triage, and emergency contacts, right in the browser.

> No app download. No login. No cost. Open the link and get guidance.

> **Medical disclaimer:** MedAid Ultra is for educational use and general guidance only. It is not a medical diagnosis and does not replace a doctor. In any emergency, call **112** (India) immediately.

---

## Features

- **First Aid Library:** step-by-step guides for about 60 conditions, including CPR (30:2), burns, stroke (FAST), and snakebite (India-specific), with severity labels (critical / moderate / mild).
- **AI Symptom Checker:** tap a body region or describe your symptoms and get triage guidance, with chat memory during the session.
- **Skin AI Detector:** upload or capture a skin photo. A MobileNetV2 model trained on the HAM10000 dataset runs in the browser and gives class confidences (7 classes), plus an ABCDE melanoma self-check.
- **AI Medicine Recommendations:** suggested medicines based on your symptoms, with a link to order from 1mg.
- **Health Reports:** enter basic details, chat with the AI, and download a PDF health report.
- **Health Calculators:** BMI (WHO categories) and TDEE (daily calorie needs).
- **Fitness Programs & Injury Prevention:** workout plans for weight loss, muscle gain, recovery, strength, and yoga.
- **India Emergency Numbers:** 112, 102, 100, 101, ready to copy.
- **Bilingual:** English and Hindi (हिं).

## Tech Stack

- HTML, CSS, JavaScript (single-page web app)
- TensorFlow.js (in-browser inference with MobileNetV2)
- LLM API for the symptom checker and report generation
- Hosted on GitHub Pages

## How to Run Locally

```bash
git clone https://github.com/rudra05498233-lgtm/MedAid-Ultra-AI.git
cd MedAid-Ultra-AI
# open index.html in your browser, or serve it:
python -m http.server 8000
```

Then open `http://localhost:8000`.

AI features need an API key. **Do not put keys in the front-end code.** See the Security section below.

## Skin Model

- Architecture: MobileNetV2
- Dataset: HAM10000 (7 skin-lesion classes)
- Input: 224×224 images with MobileNetV2 normalization
- Output: softmax probabilities over the 7 classes
- Convert a Keras model to TF.js with:

```bash
pip install tensorflowjs
tensorflowjs_converter --input_format=keras skin_model.h5 ./tfjs_model/
```

This model is a learning project. It is **not** a clinical tool and may be wrong.

## Security

- API keys must never be committed to a public repo or shipped in client-side JavaScript. Anyone can read them in the browser.
- AI calls should go through a small backend or serverless proxy that holds the key and applies rate limits.

## Screenshots

_Add screenshots or a short demo video link here._

## Roadmap

- Move AI calls to a server-side proxy
- Add more languages
- Offline mode for core first-aid guides
- Improve the skin model and report its limitations clearly

## Author

**Rudra** — Roblox (Luau) & web developer
GitHub: [rudra05498233-lgtm](https://github.com/rudra05498233-lgtm)

## License

Add a license (for example MIT) before others reuse the code.
