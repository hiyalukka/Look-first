# 🌿 Look First

**An AI naturalist that makes you look up before it answers.**

Most plant and bird identifiers keep you staring at a screen. Look First does the opposite: it refuses to name anything until you've actually *looked*, then reveals what you found. It runs entirely in your browser using an open-weight model (Gemma), with no server and no API key.

Built for the **DEV Hacktoberfest Open-Source AI Challenge, Week 1: Touch Grass**.

**[▶ Try the live app](https://hiyalukka.github.io/Look-first/)**

<!-- Add a screenshot or GIF here, e.g.: ![Look First screenshot](screenshot.png) -->

---

## The idea

Every AI product measures success by how long you stay. Look First measures success by how little you use it.

1. **📍 Say where you are.** One sentence about what's around you.
2. **👀 Get three tiny tasks.** Look at the leaf edge, touch the bark, listen for the call. The AI will not identify anything yet.
3. **⏱ The screen goes dark.** A two-minute "Eyes up" timer takes over the page while you go and look.
4. **🌿 Get the reveal.** A best guess, a confidence level (low / medium / high), one honest caveat, and one tiny next quest nearby.
5. **📓 Keep a field journal.** Every session is saved, including how long you spent outside, and can be downloaded as markdown.

## Why open-weight AI?

| What you get | Why it matters |
|---|---|
| 🧠 Runs in the browser | No backend to host or pay for |
| 📴 Works offline after first load | Useful where trail signal is poor |
| 🔒 Notes stay on your device | What you type reveals where you are |
| 💸 No API key, no usage meter | Free to share with a whole class or club |
| 🔁 Swappable models | Pick a lighter model for a weaker laptop |

## Tech stack

- **[Gemma](https://ai.google.dev/gemma)**: open-weight model (`gemma-2-2b-it`, 4-bit quantized)
- **[WebLLM](https://github.com/mlc-ai/web-llm)**: open-source in-browser LLM inference via WebGPU
- Plain **HTML, CSS and JavaScript**: a single `index.html`, no build step

The core of the project is the system prompt: a strict two-turn script that forbids identification on turn one and requires a confidence level and caveat on turn two. See the `SYSTEM` constant in `index.html`.

## Run it

**Option 1: Use the live link** (above). The first visit downloads the model once, which can take a few minutes. After that it's cached.

**Option 2: Run locally**
```bash
git clone https://github.com/YOUR-USERNAME/look-first.git
cd look-first
python -m http.server 8000
# open http://localhost:8000 in Chrome or Edge
```

**Option 3: Host it yourself**: upload `index.html` to any static host. GitHub Pages works: *Settings → Pages → Deploy from branch → main / root*.

### Requirements
- A browser with **WebGPU** (recent Chrome or Edge)
- Enough free memory for a ~2B parameter model
- A one-time model download (several hundred MB to over a gigabyte)

## Known limitations

Honest list, because small models have real limits:

- **Text-only.** You describe what you see; it doesn't look at photos yet.
- **A 2B model can be wrong.** That's why every answer includes a confidence level and a caveat. Please check a local field guide.
- **Slow first load** on slow connections.
- **WebGPU required**, so some phones and older browsers won't work.

## Roadmap

- [ ] Photo input with a multimodal Gemma model
- [ ] Regional field-guide context for better local answers
- [ ] A printable one-page "pocket card" so the phone can stay home
- [ ] Group quests for clubs and classes

## Contributing

Ideas and PRs are welcome, especially better prompts for specific regions, plants and birds. Open an issue to discuss first.

## License

MIT. See `LICENSE`.

