> **⚠️ Temporary dump repository — this is not the main project.**
>
> I am the owner of **[anujj87/AIVoiceStudio](https://github.com/anujj87/AIVoiceStudio)**.
> This repository is a **dump (mirror) of that project**. It provides the
> **latest version, V2027** (AI Voice Studio `2027.1.0`), while the main
> repository still carries the **older V2026** build.
>
> - **Main repository:** [anujj87/AIVoiceStudio](https://github.com/anujj87/AIVoiceStudio) — contains the old **V2026**.
> - **This repository:** a dump that provides the **latest V2027** for now.
> - The main repo is currently **pending approval on WINGET**.
> - **This dump repo will be deleted** once the app is available on WINGET.
> - **Every update — including this version — will be available from the main repo.**
> - So this repository only exists while the main repo's WINGET submission is
>   still pending approval.
>
> For the current release and all future updates, always use
> **[anujj87/AIVoiceStudio](https://github.com/anujj87/AIVoiceStudio)**.

---

## Why the main repo stays on V2026

The main repository **[anujj87/AIVoiceStudio](https://github.com/anujj87/AIVoiceStudio)**
is currently **under review for WINGET**, and that review is pinned to a specific
release artifact:

- A winget package is tied to a fixed **installer URL** and its exact **SHA256
  hash**, recorded in the package manifests.
- Winget validation downloads the installer from that URL, checks it against the
  recorded SHA256 and installs it before the package can be approved.
- Replacing or re-tagging the file behind that URL (for example, publishing V2027
  over the V2026 release) changes its bytes, so the hash no longer matches —
  validation fails and the pending review has to start over.
- A new version therefore needs a **new** package submission for that new
  version, which cannot be merged until the current one is approved.

So the main repo must **stay frozen on V2026** while its submission is pending.
This dump repo exists only to carry the **latest V2027** build in the meantime,
without disturbing that review. It has no such constraint, and it **will be
deleted** once the main repo is approved and live on WINGET.

---

# AI Voice Studio

Convert documents (PDF, TXT, DOC/DOCX, HTML, Markdown, clipboard text) into
spoken **WAV / MP3 / FLAC** audio files using free, **offline neural TTS** models
that run locally through **ONNX Runtime** — no cloud, no account, full privacy.

Built with **Python + wxPython** and designed to be **fully accessible with
screen readers** (NVDA, JAWS, Narrator).

Version **2027.1.0** — ![License](https://img.shields.io/badge/license-GPL--3.0-blue)

---

## Free, with no hidden cost

AI Voice Studio is **completely free**. There is no price, no subscription, no
"Pro" edition, no trial, no feature locked behind a payment, **no advertising**
and no in-app purchase. There is no account to create and no telemetry — the
program does not phone home, and every voice, every engine and every
transcription runs on your own computer, offline. The only optional download it
offers (the ONNX GPU runtime, about 1.8 GB) is free as well.

The **application** is free software under the **GPL-3.0**: you may use it,
study it, share it and modify it at no cost. That licence covers *the program
itself*. It does **not** cover the voice engines and the speech models you
download — they are separate works with **their own licences**, and many of
them are free to use while a few are **not** free for commercial work:

| Voice / model | Its own licence | Free to use? |
|---|---|---|
| Piper, Kokoro, Kitten, Matcha-TTS, VITS zh-AISHELL3 code, OmniVoice, OmniVoice Server, Pocket TTS code, KokoClone, Chatterbox, Qwen3-TTS, VibeVoice | MIT or Apache-2.0 | Yes, including commercially |
| MMS TTS, F5-TTS weights | CC-BY-NC-4.0 | Free for personal use — **not** for commercial use |
| F5-TTS code, GPT-SoVITS, MOSS-TTS | MIT / Apache-2.0 | Yes for the code; the weights keep their own terms |
| SAPI5 / Windows Core voices | Windows and vendor EULAs | As your Windows licence allows |

So the honest summary is: **the software is free with no hidden cost, and most
voices are free too — but the voice is a separate product with a separate
licence, and a few voices are for personal, non-commercial use only.** If you
plan to use a recording commercially, check that voice's licence first;
`docs/THIRD-PARTY-LICENSES.html` (Help → Third-Party Licences) lists every one
of them with its full text where permitted.

---

## What you can use it for

Because everything runs offline and nothing is uploaded, AI Voice Studio is
used for work that must stay private as much as for convenience:

- **Podcasts and audio essays** — turn a script (PDF, DOCX, Markdown, HTML or
  the clipboard) straight into spoken audio, one file per section, with an
  `.m3u8` / `.pls` / `.wpl` playlist for the episode.
- **Game voice-over and character voices** — clone a voice from a five-second
  sample, speak the lines yourself, and generate every dialogue file with the
  same character voice. Eight open-source clone engines are built in, on CPU
  and on NVIDIA GPU.
- **Study notes and revision audio** — record your own notes and hear them
  while you walk, drive or rest your eyes, instead of re-reading them.
- **Audiobooks, lessons and accessible reading** — DAISY 2.02 and DAISY 3 books
  (audio + text + images) with playlists, built for screen-reader users first.
- **Turning audio or video into text** — transcribe recordings, voice memos,
  interviews, meetings, and **video or audio lectures** (`.mp4`, `.mkv`,
  `.m4a`, `.mp3`…) into TXT, Markdown, SRT, VTT, HTML, JSON or CSV. SRT/VTT are
  ready-made subtitles; a two-hour lecture can be split into chunks of
  *n* minutes per document.
- **Subtitles and captions** — the same transcription writes SRT and VTT with
  real timings, for a video, a lecture recording or an accessibility pass.
- **Readers and volunteers** — produce an audio version of a document people
  cannot read, on a machine with no internet connection.

---

## Features

- **Addon system** — install third-party TTS engines and voices as addons,
  inspired by NVDA's addon architecture. Addons can add new engines, voices,
  and capabilities. The addon development guide is available in Help menu.
- **Developer Mode** — enables heavy logging (diagnostic files for every
  subsystem), addon management, pip environment control, and diagnostic
  tools. Toggle in Settings → General.
- **Embedded Python runtime** — a managed Python virtual environment for
  addon dependencies, with pip support for installing any PyPI package.
- **Local neural TTS**: [Piper](https://github.com/rhasspy/piper) (MIT, 30+
  languages), [Kokoro-82M](https://huggingface.com/hexgrad/Kokoro-82M)
  (Apache-2.0, incl. the **multi-lang v1.0** (53 speakers) and **v1.1**
  (103 speakers) English+Chinese models, each with a smaller int8-quantized
  variant),
  [Matcha-TTS](https://github.com/shivammehta25/Matcha-TTS) (flow-matching,
  with its shared `vocos-22khz` vocoder downloaded automatically),
  [MMS TTS](https://huggingface.com/facebook/mms-tts) (VITS, 8 languages,
  non-commercial), and VITS **zh-AISHELL3** (174 speakers) — all downloaded
  from official open-source releases.
- **Download / Remove model manager** with TTS → language → variant → voice
  cascading combo boxes and per-file progress.
- **Voice cloning** — a voice is cloned from a 5–15 second sample of the person
  speaking: choose a name, pick the sample, optionally type its transcript, and the
  voice becomes selectable everywhere. Cloning is provided by the **Voice Lab**
  engines below and by **OmniVoice** (voice clone and voice design). The cloning engine
  of earlier releases has been retired in favour of them (its name is not used here
  because the component is gone).
- **Voice Clone category (the Voice Lab)** — open-source voice-cloning engines
  that run on a normal **CPU** and additionally on the **GPU** when an NVIDIA
  card is detected: [Pocket TTS by
  Kyutai](https://github.com/kyutai-labs/pocket-tts),
  [F5-TTS](https://github.com/SWivid/F5-TTS),
  [KokoClone](https://github.com/Ashish-Patnaik/kokoclone) (Kokoro-ONNX + Kanade
  voice conversion), [Chatterbox](https://github.com/resemble-ai/chatterbox),
  [Qwen3-TTS](https://github.com/QwenLM/Qwen3-TTS),
  [VibeVoice](https://github.com/vibevoice-community/VibeVoice),
  [MOSS-TTS by OpenMOSS](https://github.com/OpenMOSS/MOSS-TTS) and
  [GPT-SoVITS](https://github.com/RVC-Boss/GPT-SoVITS). Each engine is
  installed with one button into the app's managed Python environment **of its
  own** (`tts_envs\<engine>`), its **pre-made
  voices** (26 Pocket TTS voices, the bundled
  F5-TTS references, one Kokoro voice per language for KokoClone, nine Qwen3-TTS
  speakers, seven VibeVoice presets, a default voice per language for each
  MOSS-TTS variant) appear in
  **Available TTS**, in the Preview lists and in
  the Recording window, and you can clone your own voice from a 3–15 second
  recording. **GPT-SoVITS has no voices of its own** — it is clone-only, so its
  voices appear once you create or clone one on the Voice Clone page. It speaks
  English, Chinese, Korean and Cantonese; Japanese is not offered, because the
  Japanese front-end needs `pyopenjtalk`, which has no installable build for
  the Python this app runs on. Every
  engine's variants are held to **under 12 GB of video memory**; MOSS-TTS's
  Local Transformer checkpoints (4B latest and 1.7B) are offered, while the 8B
  v1.5 checkpoint that needs ~19 GB is not.
- **Speech to text (transcription)** — transcribe recordings and videos into
  documents (TXT, SRT, VTT, HTML, JSON, CSV). Every model is installed on its
  own into `stt_envs\<model id>` and runs in the CPU/GPU the model is meant
  for — see [Speech to text](#speech-to-text-stt) below.
- **Audio description (video)** — a vision-language model watches a video and
  narrates what is happening for a blind or low-vision viewer. One run writes
  **three files per video**: the description document (script, HTML, SRT, VTT
  or JSON), the **spoken narration** read by one of your offline voices, and a
  **described video** — the original picture and sound with the description
  heard over the pauses (or, in extended audio description, the film stopped for
  every description). The source video is never modified. Each model gets its
  own environment under `describe_envs\<model id>` — see
  [Audio description](#audio-description-video) below.
- **Compute back-ends**: CPU always; **GPU (CUDA)** is offered when an NVIDIA
  GPU is detected; an **Auto** option is offered when more than one back-end
  exists. (DirectML/NPU is deliberately not offered — sherpa-onnx has no
  DirectML runtime to load.) The Voice Lab engines add their own device
  choice — CPU always, plus GPU and Auto when an NVIDIA GPU is present — both
  in Settings and per project in the Recording window.
- **A Compute combo next to every Preview button**: in **Available TTS**,
  **Recording settings**, **Punctuation** and **OmniVoice engines** you choose
  CPU / GPU / Auto right where you press Preview. The choice is remembered per
  category in Settings. **GPU** uses the whole available NVIDIA card (whatever
  card the driver exposes, no model or VRAM requirement); **CPU** uses between
  80% and 95% of the machine's logical CPUs, leaving the desktop responsive.
- **Input**: PDF, TXT, Markdown, HTML, DOCX (and DOC via Word automation),
  clipboard text. Output: WAV natively; MP3/FLAC via FFmpeg, which the app
  downloads for you into `%APPDATA%\AIVoiceStudio\ffmpeg` on first use.
- **Audio file creation modes** with the naming rules from the spec:

  | Mode | Files |
  |---|---|
  | Page by page with heading style 1 | `01 page 1`, `02 <heading>`, `03 page 2`, … |
  | Page by page only | `01 page 1`, `02 page 2`, … |
  | Heading style 1 only | `01 <heading>`, `02 <heading>`, … |
  | Break on every heading | one file per heading level 1–6, each with its content up to the next heading |
- **Recording window** (`Ctrl+Shift+R`): shows the text to record first, then
  per-project TTS, language, variant, voice, rate, pitch, volume and output
  format. Every segment is **saved to disk immediately**; if the app stops,
  reopening the project **resumes** from the first unsaved segment. The exact
  text sent to the TTS is logged to `processed_text.json` next to the audio
  files.
- **New Project wizard** (`Ctrl+Shift+N`): project name → open document →
  choose punctuation (spoken-word expansion) → choose audio mode → Finish
  opens the Recording window. Punctuation for a project is fixed here, so the
  Recording window no longer shows it.
- **Punctuation** (Settings → Punctuation tab): the default mode for new
  projects — Default (TTS decides), None (strip), Math (keep symbols) or **All**
  (speak every mark as a word: `quote`, `dot`, `left paren`, `tic`, …), with a
  live example that shows exactly how your text will be spoken.
- **Screen-reader friendly**: every control is labelled and has a proper
  accessible name; menu bar with mnemonics; OK/Cancel/Apply dialogs;
  check boxes for single choices, combo boxes for multi choices, radio buttons
  for small single-choice sets.
- **Themes**: System default, the original **Light** and **Dark**, plus **ten
  predefined dark themes** (Midnight Graphite, Obsidian Gold, Deep Navy, Forest
  Pine, Plum Royale, Crimson Slate, Ocean Teal, Amber Dusk, Carbon Lime, Blue
  Steel), each with its own palette and painted look. A **custom theme studio**
  (Settings → General → *Create custom theme…*) lets you pick your own colours
  and style and save as many themes as you like.
- **Wallpapers**: any theme — built-in, predefined or custom — can show a
  wallpaper on the welcome screen: your own picture, or the theme's painted
  pattern. The welcome screen is a full-width **action bar** of the four main
  buttons, a left **projects sidebar** with the recent-projects list, and the
  large empty area that remains — and the wallpaper fills only that empty area,
  so it never paints behind a button or the project list.
- **Updates** — **Help → Check for updates** (`Alt+D`) asks GitHub for the
  newest release and, when there is one, shows the release notes and
  downloads the installer for this Windows version; the download is
  resumable and can be cancelled. A check also runs once a day at start-up
  and can be switched off in **Settings → General → Updates**.
- **winget** — the release ships the package manifests the Windows Package
  Manager needs (`winget/`), so `winget install AnujSharma.AIVoiceStudio`
  and `winget upgrade AnujSharma.AIVoiceStudio` use exactly the same
  installer, with the same silent switches
  (`/VERYSILENT /SUPPRESSMSGBOXES /NORESTART`).
- Installer (32-bit and 64-bit): a **per-user install by default** (no
  administrator rights needed), with the usual Inno *install for all users /
  for me only* choice kept; install location, Start Menu folder choice,
  optional desktop icon, readme, launch-after-setup. Scripted and unattended
  installs never wait for a click.

## Quick start (from source)

Requires Python 3.11+ on Windows.

```bash
python -m venv .venv
.venv\Scripts\pip install -r requirements.txt
.venv\Scripts\python main.py
```

Then:

0. On first launch, tick the agreement check box in the terms-of-use dialog and
   press **I Agree** (the application does not start otherwise).
1. **Settings** (`Ctrl+,`) → **Download and remove** → pick
   `Piper` / `English (United States)` / `Medium quality` → **Download**.
2. **File → New Project** (`Ctrl+Shift+N`) → name it, open a document, choose
   an audio mode, press Finish.
3. In the Recording window press **Start recording**. Audio files land in the
   project folder.

## Data locations

| What | Where |
|---|---|
| Settings | `%APPDATA%\AIVoiceStudio\settings.json` |
| Downloaded voices | `%APPDATA%\AIVoiceStudio\models` |
| Cloned voices (Voice Clone) | `%APPDATA%\AIVoiceStudio\models\custom\<voice name>` |
| Voice Lab engine models (Hugging Face cache) | `%USERPROFILE%\.cache\huggingface` |
| ONNX GPU runtime / optional runtimes | `%APPDATA%\AIVoiceStudio\runtime` |
| One virtualenv per pip-installed TTS engine | `%APPDATA%\AIVoiceStudio\tts_envs\<engine>` |
| One virtualenv per speech-to-text model | `%APPDATA%\AIVoiceStudio\stt_envs\<model id>` |
| One virtualenv per video-description model | `%APPDATA%\AIVoiceStudio\describe_envs\<model id>` |
| Managed environment for addons | `%APPDATA%\AIVoiceStudio\addon_env` |
| Python runtime the environments are built from | `%APPDATA%\AIVoiceStudio\python_runtime` |
| Projects & audio | `%APPDATA%\AIVoiceStudio\projects\<project name>` |
| FFmpeg | `%APPDATA%\AIVoiceStudio\ffmpeg` |
| Logs | `%APPDATA%\AIVoiceStudio\logs\app.log` |

## GPU

- **GPU for the built-in ONNX engines**: install `onnxruntime-gpu` (see
  `requirements-gpu.txt`) and have NVIDIA CUDA drivers; the app then shows
  "GPU (CUDA)". The packaged application offers this as a download in
  Settings → Compute. A GPU run uses the **whole available NVIDIA card** — any
  CUDA-capable card the driver exposes, with no model or VRAM requirement —
  while a CPU run uses **80–95 % of the logical CPUs**.
- **GPU for the Voice Lab engines**: no extra runtime is needed beyond the
  NVIDIA driver; each engine gets the CUDA build of PyTorch in its own
  environment (see below).
- **GPU for speech to text**: the same rule — an NVIDIA driver is the whole
  requirement. Every speech-to-text model runs in an environment of its own
  with its own PyTorch, so a transcription never depends on the optional
  sherpa-onnx GPU runtime being downloaded.
- **NPU (DirectML)**: not offered. sherpa-onnx ships no DirectML execution
  provider, so there is nothing to load.

## Voice Clone engines (CPU, plus GPU when available)

Settings → **Voice Clone** installs open-source voice-cloning engines, each
into **its own Python virtualenv** under
`%APPDATA%\AIVoiceStudio\tts_envs\<engine>`. None of them *needs* a GPU: they
all speak on the CPU, and the moment an NVIDIA GPU is detected the **Device**
selector offers **GPU (CUDA)** and **Auto** next to the CPU — the CPU option
never disappears. The Recording window offers the same device choice per
project.

### Python environments (one per TTS engine)

Every TTS engine that is installed with pip gets its **own** Python
virtualenv, so one engine's dependency pins (torch, torchaudio, transformers,
triton) can never break another's:

| Environment | Holds |
|---|---|
| `tts_envs\pocket_tts` | Pocket TTS (Kyutai) |
| `tts_envs\f5tts` | F5-TTS |
| `tts_envs\kokoclone` | KokoClone (Kokoro-ONNX + Kanade) |
| `tts_envs\chatterbox` | Chatterbox (its own pinned PyTorch) |
| `tts_envs\qwen3tts` | Qwen3-TTS (its own pinned `transformers`) |
| `tts_envs\vibevoice` | VibeVoice (its own pinned `transformers`) |
| `tts_envs\moss_tts` | MOSS-TTS (its own pinned `transformers` 5.x) |
| `tts_envs\gptsovits` | GPT-SoVITS (its fetched source tree and weights) |
| `stt_envs\<model id>` | one speech-to-text model (see below) |
| `tts_envs\omnivoice` | **both** OmniVoice engines |
| `addon_env` | addons, the Developer tab and the sherpa-onnx GPU runtime |

The two OmniVoice engines (the direct Triton runner and the HTTP server) are
the *same model* behind two front-ends; they want the same base package and
the same CUDA PyTorch, so they deliberately share one environment instead of
duplicating several gigabytes of wheels. Engines you installed before these
per-engine environments existed keep working: the app falls back to the shared
`addon_env` until you reinstall them from their category.

**KokoClone is the exception that never falls back.** It wants a newer PyTorch
and a newer ONNX runtime than the other engines, and the only packages it may
ever import are the ones it installed itself — so it is marked
"own environment only": it runs in `tts_envs\kokoclone` and nowhere else, it is
never reported as installed because another engine's package is present in
`addon_env`, and *Remove engine* deletes its environment instead of picking
packages out of the shared one.

### Where the environments get their Python

A virtualenv is not self-contained: it holds its own `site-packages` but *runs
on top of* the interpreter it was built from, whose absolute path it records in
its `pyvenv.cfg`. The environments live in `%APPDATA%` so that uninstalling
never throws away gigabytes of packages - which means they also outlive the
installation, and a base interpreter inside the program folder would turn every
one of them into a broken environment the moment somebody reinstalled the
application: its `Scripts\python.exe` prints
`did not find executable at '...': The system cannot find the path specified.`
and exits with code **103**, which reaches the user as a model that crashed
before it produced anything.

The application therefore builds its environments on **a per-user copy of the
bundled Python runtime** (`%APPDATA%\AIVoiceStudio\python_runtime`, made once on
first use). That path cannot move, so reinstalling, upgrading or moving the
application changes nothing for the models already installed. An environment
built by an earlier installation anyway - it names a Python that has gone - is
**re-pointed** at the current one rather than rebuilt
(`python -m venv --upgrade`, through `python_runtime.PythonRuntime.repair_env`),
which keeps the packages inside it; only when even that cannot be done is a
fresh environment created. Every worker launch goes through
`PythonRuntime.usable_python_exe`, so a description, transcription or voice
engine that is still installed starts again after the application moved.

### GPU support for every engine

Every Voice Clone engine supports CUDA, so each one gets the **CUDA build of
PyTorch** installed into its own environment whenever an NVIDIA GPU with a
working driver is detected (`download.pytorch.org/whl/cu128`; on Windows the
plain PyPI wheel is CPU-only). `cu128` is deliberate: the older `cu121` index
stops at Python 3.12 and has **no wheels for the Python 3.13** the app runs
on, which made pip fail with "No matching distribution found for torch". The
OmniVoice engines are GPU-only and use the same index. Engines without a GPU
keep the ordinary CPU wheels, and if a CUDA wheel is unavailable for the
installed Python the app falls back to the CPU build and tells you so — the
engine is always installable.

| Engine | Package | Pre-made voices | Rough download |
|---|---|---|---|
| Pocket TTS (Kyutai) | `pocket-tts` | 26 voices in 6 languages | ~450 MB + PyTorch |
| F5-TTS (transformer) | `f5-tts` | 2 bundled reference voices | ~1.4 GB |
| KokoClone (Kokoro + Kanade) | `kokoclone` (source) | 7 Kokoro voices (one per language) | ~1.5 GB + PyTorch |
| Chatterbox (Resemble AI) | `chatterbox-tts` | one default voice per model | ~2.5 GB + PyTorch |
| Qwen3-TTS (Alibaba Qwen) | `qwen-tts` | 9 named speakers per CustomVoice model | ~2–9 GB on first use + PyTorch |
| VibeVoice (Microsoft, fork) | `vibevoice` (source) | 7 preset voices | ~4 GB (1.5B) or ~18 GB (7B) + PyTorch |
| MOSS-TTS (OpenMOSS) | `moss-tts` (source) | one built-in voice per language (synthesised from the text alone) | ~6.5 GB (1.7B) or ~9.5 GB (4B) + PyTorch |
| GPT-SoVITS (RVC-Boss) | source tree (fetched) | none — clone-only | ~1.5–2 GB of weights + PyTorch |

On a machine with an NVIDIA GPU the Voice Lab installs the **CUDA build of the
ONNX runtime** for KokoClone as well (`onnxruntime-gpu`), so the card drives both
of its stages — the Kokoro ONNX synthesis *and* the Kanade voice conversion. It
falls back to the CPU providers on its own when the GPU cannot be used.

Each engine's model is downloaded from Hugging Face the first time you
synthesize with it, and stays in the Hugging Face cache afterwards.

### Voxtral 4B TTS is deliberately not offered

Mistral AI's **[Voxtral 4B TTS](https://huggingface.co/mistralai/Voxtral-4B-TTS-2603)**
(the 4B text-to-speech model — not the Voxtral speech-to-text models that
**Settings → Manage the STT** installs) is *not* in the TTS catalog, and this was
a decision rather than an omission. It is loadable **only by vLLM-Omni**:
`transformers` refuses the checkpoint ("model type `voxtral_tts` but
Transformers does not recognize this architecture") and there is no ONNX, GGUF
or pip distribution, while **vLLM publishes no Windows wheels at all** — every
`vllm`/`vllm-omni` wheel is Linux, and upstream points Windows users at WSL2 —
so it cannot be installed into an engine's environment on this application's
platform (and, having no CPU path, could not be offered as a CPU run either).
It also needs a **single NVIDIA GPU of 16 GB or more** (published runs used
20.5 GiB of a 24 GB card and 27.3 GiB of a 32 GB one), which is above the 12 GB
ceiling every Voice Lab engine here is held to. Two further limits would have
had to be explained in the UI rather than delivered: the open-weights
checkpoint **omits the codec's encoder**, so cloning a voice from a recording
fails (`encode_waveforms requires encoder weights which are not available in
the open-source checkpoint`), and the model **takes no emotion tags or text
instructions** — emotion is chosen only by picking one of its preset voices, of
which just three carry one (`neutral`, `casual`, `cheerful`). Offering it would
have promised an install, a card and a clone that cannot be made. The Voxtral
**speech-to-text** model stays offered, because it does run locally.

### Which environment an engine speaks in

Each engine's worker is started with the interpreter of the engine's **own**
environment. That decision is read straight from the environment's
`site-packages` on disk (`venv_packages.package_present`) rather than from the
cached package probe the Settings pages use: the probe answers "not
installed" until its background check has finished, and a worker started in
the wrong environment fails with a baffling `ModuleNotFoundError` (an engine
reporting "No module named 'torch'" even though its own environment has
PyTorch). An engine found only in the shared
`addon_env` still runs there; an engine in neither environment says so in its
own words instead.

After a successful install the app **imports the engine once** in its own
environment (`voicelab.verify_engine_import`) and reports it when that fails,
so a dependency combination the engine cannot load shows up in the install
dialog instead of on your first preview.

### Audio decoding without FFmpeg

From TorchAudio 2.9 on, `torchaudio.load`/`save` decode through **TorchCodec**
(its `backend` argument is accepted and ignored), and TorchCodec on Windows
needs FFmpeg's *shared* libraries — which the app does not install. F5-TTS
reads its reference clip that way, so previewing any F5-TTS voice failed with
"Could not load libtorchcodec". The engine worker now probes TorchCodec on a
real file first and, **only when it is genuinely broken**, backs
`torchaudio.load`/`save` with `soundfile` (whose wheel contains libsndfile, so
nothing has to be installed on the computer). WAV, FLAC, OGG and MP3 work that
way; a machine that has FFmpeg keeps TorchCodec and its wider format support.
F5-TTS also cleans the reference clip with pydub, which shells out to FFmpeg
for anything that is not a WAV, so a non-WAV reference (MP3/FLAC/OGG — the
formats the Voice Clone page offers) is converted to a WAV once with
soundfile before the engine sees it.

Cloning works from a short recording of the voice you want (5–15 seconds of
clean speech) plus, optionally, a transcript of it; the reference is copied
into the voice folder, so the clone keeps working after you move the original
file. F5-TTS also wants a transcript of the reference clip; without one the
engine conditions on the audio alone.

Every Voice Lab engine runs in a separate worker process, so PyTorch
never loads inside the application itself.

### Per-engine tuning

Every engine has its own generation knobs, reachable from two places:

* **Settings → Voice Clone → Engine tuning...** saves the *defaults* of the
  selected engine (used by every project that has not changed them),
* **Recording window → Engine tuning...** saves *per-project overrides*; the
  line next to the button shows which values the project will use, and where
  they come from.

| Engine | Tuning options |
|---|---|
| Pocket TTS | int8 quantization (CPU speed-up), seed |
| F5-TTS | diffusion steps (NFE), CFG strength, sway sampling, cross-fade, target RMS, fixed duration, trim silence, seed |
| KokoClone | seed (its Kokoro stage is deterministic and the Kanade conversion has no sampler) |
| Chatterbox | exaggeration, CFG weight, temperature, repetition penalty, min-p, top-p, seed |
| Qwen3-TTS | style instruction, temperature, top-p, top-k, repetition penalty, max new tokens, x-vector-only mode, seed |
| VibeVoice | CFG scale, diffusion (DDPM) steps, seed |
| MOSS-TTS | max new tokens, fixed duration (tokens), seed |
| GPT-SoVITS | text split method, temperature, top-k, top-p, repetition penalty, speaking speed, pause between sentences, diffusion steps (v3/v4), super-sampling (v3/v4), parallel inference, seed |

A control always starts at the engine's own default and **only values that
differ from it are stored and sent**, so a project you never tune behaves
exactly like a freshly installed engine, and *Reset to engine defaults* is the
same as "let the engine decide". Parameters the installed version of an engine
does not support (the engines rename them between releases) are skipped, logged
and never fail a recording.

> Kyutai's *voice-cloning* Pocket TTS weights live behind a Hugging Face
> repository that may require accepting its terms and logging in
> (`huggingface-cli login`) before the first synthesis.

## Speech to text (STT)

Settings → **Manage the STT** installs speech-recognition models, and the
**Transcribe** dialog of a transcription project (or **Open** on a recent one)
runs one of them over the project's recordings and videos, writing TXT, SRT,
VTT, HTML, JSON or CSV documents. A modal progress window shows how far the
run has got and can cancel it; when it finishes, **Open project folder** opens
the folder the documents were written to.

Every model gets a Python environment **of its own**
(`stt_envs\<model id>`), because their stacks conflict constantly — NeMo
against `transformers`, two different PyTorch pins, `protobuf` at two versions.
Installing one model can therefore never break another, and *Remove model*
deletes that environment instead of picking packages out of a shared one. The
models are declared in `ai_voice_studio/stt/catalog.py`.

| Model | Back-end | Languages | For |
|---|---|---|---|
| Whisper Large V3 | faster-whisper (CTranslate2) | 99+ | GPU or CPU (GPU recommended) |
| Whisper Small/Base | faster-whisper (CTranslate2) | 99+ | CPU or GPU |
| Qwen3-ASR (1.7B / 0.6B) | transformers | 52 | GPU or CPU |
| NVIDIA Canary-Qwen (2.5B / 1B) | NeMo | 25 European | 2.5B: GPU only · 1B: CPU or GPU |
| NVIDIA Parakeet TDT 0.6B | NeMo | English | GPU or CPU |
| Moonshine (base / tiny) | transformers | English | CPU or GPU |
| SpeechBrain (LibriSpeech / Hindi) | SpeechBrain | multi | CPU or GPU |
| Voxtral Mini 3B | transformers | 13 | GPU or CPU |
| IBM Granite Speech (1B / 2B / 8B) | transformers | English + 7 | 1B/2B: CPU or GPU · 8B: GPU only |

**No model needs an account, a token or a licence click-through.** A model whose
repository is *gated* on Hugging Face — Cohere Transcribe was one — cannot be
downloaded by a user who has no Hugging Face account, so it is deliberately not
in the catalog.

**Only a model that cannot run without a GPU is shown a GPU alone.** Almost
every model here runs on both devices, so the *Compute* combo offers both the
CPU and the GPU whenever an NVIDIA card is present (the recommended device
first: the GPU for Whisper Large V3, Voxtral, Parakeet TDT and Qwen3-ASR, the
CPU for Moonshine, SpeechBrain and Whisper Small/Base), and the CPU alone on a
machine with no card — many users have none, and must still be able to
transcribe. The two checkpoints that genuinely cannot run on a CPU say so:
Canary-Qwen **2.5B** is a speech-language model and Granite Speech **8B** is
~17 GB of weights, so each offers the GPU alone and names the reason. Because
the device can differ between variants, the combo is rebuilt when the variant
changes (Canary-Qwen 2.5B → GPU only, its 1B → CPU or GPU). An *Auto* choice is
never offered, because it would quietly pick the device instead of the user.

A **GPU run** needs its CUDA runtime in that model's own environment. Whisper's
CTranslate2 back-end needs cuBLAS, which is not part of `faster-whisper`; the
catalog lists it as a CUDA-only package and the installer adds it on a GPU
machine. If a model's environment predates that wheel, a GPU run would quietly
fall back to the CPU — so the *Manage the STT* category names the missing wheel
and turns **Install selected model** into a repair.

**Timings are requested only where they exist.** Whisper and the CTC/NeMo models
report when each phrase was spoken; the audio language models (Qwen3-ASR,
Voxtral, Granite Speech, Moonshine) do not, and `transformers` raises rather
than returning them. The catalog declares the capability per model, and the
worker never asks for timings a model cannot give; a model without timings
yields one untimed segment.

Voxtral is offered at **3B only**: the 24B checkpoint is roughly 48 GB of
bfloat16 weights, which cannot load on an ordinary 12 GB card (or in 16 GB of
system RAM), so offering it would promise a run that cannot finish.

### What you can transcribe

A transcription project accepts **audio and video** alike: WAV, MP3, FLAC, M4A,
AAC, OGG/Opus, WMA and AIFF recordings, and the video containers MP4, MKV, MOV,
WebM, AVI, M4V, MPG, MPEG, WMV, TS and M2TS. FFmpeg — which the application
already downloads for MP3/FLAC output — decodes the video formats too, so a
lecture recorded as `.mp4` needs no separate step; point the project at a folder
and it walks it recursively. This is what makes the usual jobs possible: a
recorded **lecture or class** becomes searchable text, a **voice memo or
meeting** becomes notes, and a **video** gets an SRT or VTT subtitle file that
any player understands. TXT and Markdown with an optional timestamp, HTML, JSON
and CSV are there for study and for feeding the text to something else. Because
nothing is uploaded, a confidential interview or a private medical note can be
transcribed on a machine with no internet connection at all.

## Audio description (video)

Settings → **Manage the video describer** installs the vision-language models
that describe video, and an **audio description** project runs one of them over
its videos. A run writes **three files per video into the project folder**:

| Output | What it is |
|---|---|
| `<video>.txt` (or `.html`, `.srt`, `.vtt`, `.json`) | The description document in the format the project chose. The reviewable plain-text script is always written beside any other format. |
| `<video> - narration.wav` | The descriptions read aloud by an installed offline voice, laid at the times they belong to. WAV, or MP3/FLAC if that is the recording format. |
| `<video> - described.mp4` | **The watchable film.** The original picture stream is copied untouched and the original soundtrack is mixed with the narration, so the film and the description are heard together. In extended audio description the picture carries the pauses instead. |

The **source video is read only** — it is never edited, renamed or overwritten;
the described film is a new file next to it. **Edit → Restart All Descriptions**
deletes the three outputs and starts again; **Edit → Start Selected
Descriptions** describes only the videos you pick.

Every model runs in a Python environment **of its own**
(`describe_envs\<model id>`) with its own PyTorch and `transformers`, so a
describing model can never break a TTS engine or a speech-to-text model, and
*Remove model environment* deletes exactly that. The models are declared in
`ai_voice_studio/describe/catalog.py`.

| Model | Sizes offered | For |
|---|---|---|
| Qwen3-VL | 2B · 4B · 8B · 30B-A3B | 4B is the best fit for a 12 GB card; 8B is the best quality that fits one |
| Qwen2.5-VL | 3B · 7B | Lighter alternative |
| Qwen2.5-Omni | 3B · 7B | Small GPU or CPU |
| Qwen3-Omni 30B-A3B | 30B | Best descriptions of any open model here |
| Gemma 3 | 4B · 12B · 27B | 12B loads in 4-bit on a 12 GB card |
| Gemma 4 | E2B · E4B · 12B | Small and fast up to a unified audio/video 12B |
| MiniCPM-o 2.6 | 8B | Needs its own modelling code |
| SmolVLM2 | 2.2B · 500M · 256M | Fastest; runs with no card |
| Moondream 2 | 1.9B | Small, CPU-friendly |

**Descriptions are made one window at a time.** A *chunk* (1–10 minutes, chosen
in the wizard) bounds memory, drives the progress bar and is what can be resumed;
a *window* is what one description covers, and it is twenty seconds — the
cadence broadcast audio description uses. Describing a two-minute chunk in one
call was measured to reduce a whole lecture to “a man sits in a chair beside a
whiteboard”, with the line of code that had appeared never mentioned; one
description per twenty seconds reports the change. Each window is told what the
previous description said, so the model says what has changed — text, code, a
gesture, a new person — instead of describing the same scene again, and a window
whose picture has not changed at all is skipped (and reported as skipped)
rather than repeated.

**Placement** decides how a description reaches the viewer:

- **Standard** — speak into the pauses of the soundtrack. The film is not
  changed at all: the picture is copied and the description is mixed into a
  silence. *Fit descriptions into the pauses* uses the speech-to-text model to
  find those silences and put each description into the pause that follows the
  moment it describes; a description no pause can hold is left out of the timed
  track rather than spoken over dialogue, and the run says how many.
- **Extended** — pause the video for each description. The picture holds on the
  frame it had reached while the description is spoken, then goes on: nothing is
  ever talked over, at the price of a longer film (about eleven seconds per
  description). This is the option for a film whose dialogue never leaves a
  pause, and the one that lets the viewer read the on-screen text before the
  description explains it.

The **guideline prompt** every request carries is a first-class part of the
feature rather than a preference: present tense, one or two short sentences, say
what matters first, be objective, never invent, name a person only when the
video itself does. It distils the professional audio-description guidelines the
VideoA11y study collected from 154 industry standards.

**FFmpeg is required** (it decodes the frames, reads the video's length and
writes the described video). When it is missing, **Start audio description**
offers to download it into `%APPDATA%\AIVoiceStudio\ffmpeg` instead of failing.
On a Windows account without Developer Mode the Hugging Face cache stores model
files as copies rather than symlinks; the app switches that on by itself and
says so.

## Keyboard gestures

Settings → **Keyboard gestures** is modelled on NVDA's Input Gestures dialog. The
application's commands are grouped by category in a tree (Projects, Recording,
Help, Application); selecting one lists the keyboard keys that trigger it, and
**Add gesture…**, **Remove gesture** and **Restore defaults** edit them. The
command catalog and the binding model live in `ai_voice_studio/gestures.py`; a
gesture is a normalized `kb:<modifiers+key>` string, and the user's overrides
are stored in `settings['gestures.bindings']`.

A gesture needs Ctrl, Alt or Windows (or a function key), so a bare letter can
never take over ordinary typing. A key that another command already uses is
named before it is reassigned, and a genuine clash is reported in the status
line rather than resolved silently. The main window offers every key press to
the configured gestures before its built-in shortcuts, and reloads them when
the Settings window closes — no restart.

## Documentation

All of these ship with the installer (`docs\`) and are in the **Help** menu:

| Document | Contents |
|---|---|
| `README.html` | Features, shortcuts, project types, first launch, licences |
| `UserGuide.html` | Every window and Settings category, voice cloning, troubleshooting |
| `AddonDevelopmentGuide.html` | Writing addons and TTS engines |
| `AccessibilityGuide.html` | The accessibility rules the UI follows |
| `THIRD-PARTY-LICENSES.html` | Every bundled component with its licence and full text |
| `WHATS-NEW.html` | What changed from the 2026 series to 2027 |
| `book/index.html` (F1) | The bundled book: 94 chapters and 3 appendices from basic Python to rebuilding this application, including speech to text, audio description, the Voice Lab, per-engine environments, compute choice, the theme studio, the update checker and the terms dialog |
| `winget/README.md` | The winget package: what the manifests mean and how a release is published to the Windows Package Manager |

`PROJECT_SPEC.md` is the specification behind the implementation and
`DEV_PLAN.md` tracks the phases.

## Updates and winget

Release 2026.3.7 adds an update checker and the winget packaging standard.

- `ai_voice_studio/updates.py` reads the latest release from
  `api.github.com/repos/anujj87/AIVoiceStudio/releases/latest`, compares it
  with `constants.APP_VERSION` and picks the installer for this
  architecture. Nothing is downloaded or installed without the user asking.
- `ai_voice_studio/gui/update_dialog.py` owns the dialogs: the quiet daily
  check, the *Check for updates* answer, and the download-and-install flow.
- `winget/manifests/a/AnujSharma/AIVoiceStudio/<version>/` holds the three
  generated winget manifests; `tools/make_winget.py` writes them (with the
  SHA256 of the built installer) and `tools/winget_validate.py` checks them
  against winget's rules. `tests/test_winget.py` runs that checker in the
  suite.

## Packaging

See `packaging/` — `build.ps1` drives PyInstaller (per-arch) and Inno Setup to
produce `AI-Voice-Studio-v-<version>-Setup-x64.exe` / `-x86.exe`. The installer
is **per-user by default**: `PrivilegesRequired=lowest` means {autopf} is
`%LOCALAPPDATA%\Programs` and **no administrator rights** are needed, while
`PrivilegesRequiredOverridesAllowed=dialog` keeps Inno's *Select Setup Install
Mode* dialog, so a person can still install for all users (`C:\Program Files`,
elevated) or just for themselves; an earlier install of the same `AppId` is
found and updated in place, with its mode preselected.
An unattended install never waits on that dialog: the winget manifest passes
`/SUPPRESSMSGBOXES`, and Inno then takes the recommended choice, which without
elevation is the per-user one - the same flags `ai_voice_studio/updates.py`
uses for the in-app update. `DisableStartupPrompt=yes` removes Setup's own
choiceless "This will install ... Do you wish to continue?" prompt for the same
reason. The remaining wizard widgets are a Start Menu folder choice, optional
desktop icon, license page, and launch/readme options.
`packaging\silent_install.ps1` runs the built setup — or its uninstaller
(`-Uninstall`) — with every switch above: `-Dir`, `-Log` and `-AllUsers` set the
install location, Inno's log and an all-users install, and the exit code is 0
only when the work really succeeded. It exists because those switches are easy
to lose: a POSIX shell rewrites them, so in Git Bash/MSYS2
`Setup.exe /VERYSILENT /SUPPRESSMSGBOXES /NORESTART` reaches Setup as
`"C:/Program Files/Git/VERYSILENT" "C:/Program Files/Git/SUPPRESSMSGBOXES"
"C:/Program Files/Git/NORESTART"`, Setup ignores the arguments it does not
recognise and opens its wizard, and the "unattended" install then waits on a
dialog nobody is there to answer. The driver hands the switches over untouched,
and it waits for the uninstaller, which copies itself to a temporary file,
exits 0 and only then deletes the files.
A folder can still hold something after a *successful* uninstall: the bundled
runtime writes `__pycache__` files next to its own modules the first time it
runs, and Inno removes only the files Setup installed - so an uninstall driven
by a check for "nothing left" waits for files that will never go. The driver
knows those bytecode caches are the runtime's and clears them, which is what
makes an uninstall finish instead of timing out after ten minutes.
Models are never bundled; they are downloaded by the user in-app.

## License

GPL-3.0-or-later (see `LICENSE`). Components keep their own licences:
Piper = MIT, Kokoro-82M = Apache-2.0, Kitten TTS = Apache-2.0, Matcha-TTS =
Apache-2.0, OmniVoice and OmniVoice Server = Apache-2.0, Pocket TTS =
Apache-2.0, F5-TTS = MIT code with **CC-BY-NC-4.0 weights
(non-commercial)**, KokoClone = Apache-2.0 (its Kanade voice-conversion model
is Apache-2.0 as well), Chatterbox = MIT, Qwen3-TTS = Apache-2.0, VibeVoice =
MIT, MMS = CC-BY-NC (non-commercial), and the SAPI5 / Windows
Core voices fall under Windows and vendor EULAs. The application bundles
`sherpa-onnx` (Apache-2.0), `onnxruntime` (MIT), `wxPython` (wxWindows
Licence), `numpy` (BSD-3-Clause), `requests` (Apache-2.0), `pypdf`
(BSD-3-Clause) and `python-docx` (MIT). The complete list, with the licence
texts, is `docs/THIRD-PARTY-LICENSES.html` (Help → Third-Party Licences).

On first launch the application asks you to accept terms of use covering
voice-cloning rights, illegal use, commercial licensing and system voices;
it does not start unless you agree.

## Author

Developed by **Anuj Sharma**.

## Acknowledgements

Inspired by accessible reading software such as
[Bookworm](https://github.com/blindpandas/bookworm), and built on
[sherpa-onnx](https://github.com/k2-fsa/sherpa-onnx), [Piper](https://github.com/rhasspy/piper),
and [Kokoro](https://huggingface.co/hexgrad/Kokoro-82M).

## Hashtags

#TextToSpeech #TTS #SpeechToText #STT #Transcription #VoiceCloning #OfflineAI
#LocalAI #NoCloud #PrivateByDesign #OpenSource #FreeSoftware #GPLv3
#Windows #wxPython #Python #Accessibility #A11y #ScreenReader #NVDA #JAWS
#Narrator #Audiobook #DAISY #Podcast #VoiceOver #GameAudio #Subtitles #SRT
#StudyNotes #LectureNotes #TextFromVideo #AudioToText #CPU #CUDA #GPU
