# SciAlpha 2D/3D — Ilmiy Hisoblash va Interaktiv Simulyatsiya Dasturi (Master Blueprint & AI Prompts)

Ushbu hujjat **Wolfram Alpha** dizayni va aniqligiga ega bo'lgan, ammo barcha tabiiy va aniq fanlar (Matematika, Fizika, Kimyo, Biologiya, Astronomiya) bo'yicha javoblarni **jonli 2D va 3D parametrik simulyatsiyalar** bilan ko'rsatib beradigan `.exe` Desktop ilovasining yagona texnik loyihasi (Master Blueprint) va AI yordamchilar (**Antigravity, GitHub Copilot, GPT, Gemini**) uchun tayyor ko'rsatmalar to'plamidir.

> **Foydalanish bo'yicha maslahat:** Ushbu faylni GitHub repozitoriyangizning asosiy papkasiga `MASTER_BLUEPRINT.md` yoki `CLAUDE.md` / `.github/copilot-instructions.md` nomi bilan joylashtiring. Shunda Antigravity va GitHub Copilot loyihani ochishi bilan nima qurayotganimizni 100% tushunadi.

## 1. Loyiha Konsepsiyasi va Wolfram Alpha'dan Ustunligi

Oddiy chat-botlar (LLM) ilmiy savollarga faqat matn bilan javob beradi va murakkab hisob-kitoblarda adashadi. Wolfram Alpha esa aniq hisoblaydi, lekin ko'p savollarni tushunmaydi va faqat qotib qolgan (statik) rasmlar chiqaradi.

**SciAlpha 2D/3D** quyidagi 4 ta muammoni hal qiladi:
1. **Har qanday savolni tushunish (Neuro-Symbolic Engine):** Foydalanuvchi oddiy tilda yozgan har qanday ilmiy savolni LLM tahlil qiladi, ammo hisob-kitobni Python'ning aniq ilmiy kutubxonalari (`SymPy`, `SciPy`, `RDKit`, `Astropy`, `Pint`) bajaradi.
2. **Wolfram Alpha uslubidagi "Pod" (Kartochkali) Dizayn:** Natijalar tartibsiz chat xabarlari kabi emas, balki Wolfram Alpha kabi mantiqiy bloklarga (**Pods**) bo'lingan holda chiqadi: *Kiritilgan savol talqini*, *Aniq natija*, *2D/3D Interaktiv Laboratoriya*, *Qadamma-qadam yechim*, *Jonli grafiklar*.
3. **2D va 3D Interaktiv Simulyatsiya:** Har bir ilmiy jarayonni foydalanuvchi 1 ta tugma orqali **2D (tekislik / sxema / vektorlar)** yoki **3D (fazoviy model / WebGL)** rejimiga o'tkaza oladi.
4. **Jonli Parametrlar (Slayderlar):** Foydalanuvchi massa, tezlik, burchak, tortishish kuchi ($g$), harorat, konsentratsiya yoki funksiya koeffitsiyentlarini slayder orqali o'zgartirganda, 2D/3D simulyatsiya va grafiklar 60 FPS tezlikda real vaqtda o'zgaradi.

## 2. Wolfram Alpha Uslubidagi Dizayn Tizimi (UI/UX Specification)

Ilova interfeysi xuddi **Wolfram Alpha** kabi toza, akademik, yuqori kontrastli va strukturalangan bo'lishi shart.

### 2.1. Ranglar Palitrasi va Tipografiya

| Element | Rang kodi (Hex) | Vazifasi va Wolfram Alpha uslubi |
| :--- | :--- | :--- |
| **Asosiy Brend Rangi (Wolfram Orange)** | `#F65314` / `#FF6B00` | Qidiruv tugmasi (`=`), faol slayderlar, 2D/3D o'tkazgich va asosiy urg'ular. |
| **Ikkinchi urg'u (Scientific Blue)** | `#0070C0` | Matematik grafik chiziqlari, vektor o'qlari va "Step-by-step solution" tugmasi. |
| **Asosiy Fon (Workspace Background)** | `#F7F8FA` (Yorug') / `#121418` (Tungi) | Ko'zni charchatmaydigan toza laboratoriya foni. |
| **Pod (Kartochka) Foni va Chegarasi** | `#FFFFFF` (Chegara: `#E2E5EC`) | Har bir natija bloki (Pod) alohida oq kartochka ichida joylashadi. |
| **Pod Sarlavhasi (Pod Header Bar)** | `#F0F2F5` (Matn: `#333740`) | Har bir kartochkaning tepasida ingichka kulrang sarlavha chizig'i (masalan, `Input interpretation`, `Interactive 2D/3D Simulation`, `Step-by-step solution`). |
| **Matn va Formulalar Shrifti** | `Inter` (UI), `KaTeX_Main` (Matematika), `JetBrains Mono` (Kod/Qiymatlar) | Barcha matematik va kimyoviy formulalar `KaTeX` orqali bosma kitob darajasida chiziladi. |

### 2.2. Ekran Joylashuvi (Desktop Layout)

1. **Yuqori Qidiruv Paneli (Wolfram Header & Input Bar):**
   * Markazda katta, to'q sariq ramkali qidiruv maydoni: `[ Savol yoki formulani kiriting... ] [=]`.
   * Pastida tezkor matematik/ilmiy belgilar paneli ($\int, \sum, \sqrt{x}, \pi, \infty, \Delta, \rightarrow$) va fanlar bo'yicha filtr (`Barchasi`, `Matematika`, `Fizika`, `Kimyo`, `Biologiya`, `Astronomiya`).
2. **Asosiy Natijalar Maydoni (2 Ustunli "Wolfram Pods" Tizimi):**
   * **Chap Ustun (Matematik va Nazariy Podlar — ekranning 45% qismi):**
     * **Pod 1: Input Interpretation** — AI savolni qanday formula yoki tizim sifatida tushunganini ko'rsatadi.
     * **Pod 2: Exact Result / Numerical Value** — Aniq javob va o'lchov birliklari.
     * **Pod 3: Step-by-Step Solution** — *"Show steps"* tugmasi bosilganda ochiladigan qadamma-qadam yechim va qoidalar.
     * **Pod 4: Related Formulas & Constants** — Shu mavzuga oid fizik/kimyoviy qonunlar.
   * **O'ng Ustun (Vizual Simulyatsiya va Parametrlar Podlari — ekranning 55% qismi, ekran bilan birga siljimaydigan sticky holatda):**
     * **Pod 5: Interactive 2D/3D Simulation Viewport** — Yuqori o'ng burchagida `[ 2D | 3D ]` o'tkazgichi, `[ Play / Pause ]`, `[ Reset ]`, `[ Slow-Mo 0.25x ]` va `[ Vektorlarni ko'rsatish ]` tugmalari joylashgan interaktiv laboratoriya oynasi.
     * **Pod 6: Parameter Controls (Sliders)** — Foydalanuvchi o'zgartiradigan barcha kiruvchi o'zgaruvchilar (har bir slayder yonida aniq son qiymati va o'lchov birligi yoziladi).
     * **Pod 7: Real-Time Dynamic Plots** — Simulyatsiya ishlagan sari jonli chiziladigan 2D grafik (masalan, Energiya-Vaqt yoki Tezlik-Masofa grafigi).

## 3. Texnologik Stek va Modulli Arxitektura (`.exe` Desktop App)

Loyiha kichik, bir-biridan mustaqil modullardan iborat bo'lib, `.exe` formatiga **Tauri (yoki Electron)** orqali yig'iladi.

| Qatlam | Texnologiya / Kutubxona | Nima uchun aynan shu tanlandi? |
| :--- | :--- | :--- |
| **Desktop Qobiq (.exe)** | `Tauri v2` (yoki `Electron`) + `Vite` | Kompyuter GPU kuchidan to'liq foydalanadi, xavfsiz va `.exe` faylga oson yig'iladi. |
| **Frontend UI & Matematik Yozuv** | `React 18` + `TypeScript` + `TailwindCSS` + `KaTeX` | Wolfram Alpha uslubidagi Pod kartochkalarini va LaTeX formulalarini tez va toza chizadi. |
| **3D Simulyatsiya Dvigateli** | `Three.js` + `@react-three/fiber` + `@react-three/drei` + `@react-three/rapier` | AI'lar (GPT, Claude, Gemini, Copilot) `Three.js` kodini eng yuqori aniqlikda yozadi; `Rapier` esa 3D fizikani 60 FPS da hisoblaydi. |
| **2D Simulyatsiya va Grafiklar** | `HTML5 Canvas` + `Matter.js` (2D fizika) + `Plotly.js` (Ilmiy grafiklar) | 2D sxemalar, kuch vektorlari, optika va jonli funksiyalar uchun. |
| **Kimyo va Molekulalar 3D** | `3Dmol.js` + `RDKit` (Python) | SMILES yoki formula bo'yicha istalgan molekulani 3D atom-bog' ko'rinishida chizish. |
| **Python Ilmiy Yadro (Backend)** | `FastAPI` + `SymPy` + `SciPy` + `NumPy` + `Pint` + `Astropy` | LLM hisob-kitobda adashmasligi uchun barcha tenglamalar, integrallar va fizik kattaliklar Python'da 100% aniq hisoblanadi. |

### 3.1. Loyiha Papkalar Tuzilishi (Folder Structure)

```text
scialpha-desktop/
├── MASTER_BLUEPRINT.md              # Ushbu asosiy arxitektura va AI promptlar fayli
├── package.json
├── src-tauri/                       # Desktop .exe yig'uvchi qism (Rust/Tauri)
├── backend/                         # Python Ilmiy va Matematik Yadro (FastAPI)
│   ├── main.py                      # API endpointlar (/solve, /simulate, /chemistry)
│   ├── requirements.txt             # sympy, scipy, numpy, pint, rdkit, astropy, fastapi
│   ├── engines/
│   │   ├── math_engine.py           # SymPy: tenglamalar, integrallar, step-by-step
│   │   ├── physics_engine.py        # SciPy/Pint: mexanika, elektr, optika, birliklar
│   │   ├── chem_bio_engine.py       # RDKit/Biopython: molekulalar 3D koordinatasi, reaksiyalar
│   │   └── llm_orchestrator.py      # Savolni JSON Simulation Schema'ga aylantiruvchi AI agent
│   └── knowledge_base/
│       ├── constants.json           # Fizik va astronomik o'zgarmaslar bazasi
│       └── elements_periodic.json   # Mendeleyev jadvali va atom xossalari
└── src/                             # Frontend (Wolfram UI + 2D/3D Engine)
    ├── App.tsx                      # Asosiy Wolfram Alpha interfeysi
    ├── types/
    │   └── simulation.ts            # Universal Simulation JSON Schema tiplari
    ├── components/
    │   ├── WolframHeader.tsx        # To'q sariq qidiruv paneli va matematik klaviatura
    │   ├── PodCard.tsx              # Wolfram uslubidagi standart oq kartochka (Pod)
    │   ├── StepByStepPod.tsx        # Qadamma-qadam yechim bloki (KaTeX bilan)
    │   ├── ParameterSlidersPod.tsx  # Dinamik slayderlar bloki
    │   └── LiveChartPod.tsx         # Jonli o'zgaruvchi grafiklar (Plotly/Canvas)
    └── simulation/
        ├── SimulationViewport.tsx   # 2D va 3D rejimni almashtiruvchi asosiy oyna
        ├── Canvas2DEngine.tsx       # 2D chizma, vektorlar va fizika dvigateli
        ├── Three3DEngine.tsx        # 3D WebGL/Three.js sahna dvigateli
        └── presets/                 # Tayyor ilmiy konstruktor modullari (Primitives)
            ├── MechanicsScene.tsx   # Mayatnik, snaryad, prujina, to'qnashuvlar
            ├── MathSurfaceScene.tsx # 2D/3D funksiyalar va integrallar yuzasi
            ├── Molecule3DScene.tsx  # 3D atomlar, orbitallar va kimyoviy bog'lar
            └── SolarOrbitScene.tsx  # Gravitatsiya va kosmik jismlar harakati
```

## 4. Universal Simulyatsiya JSON Sxemasi (Data Contract)

Backend (Python + AI) va Frontend (React 2D/3D) bir-birini xatosiz tushunishi uchun har qanday ilmiy savol quyidagi **qat'iy JSON kontrakt**ga aylantiriladi:

```json
{
  "query": "45 gradus burchak ostida 25 m/s tezlik bilan otilgan jism harakati",
  "domain": "physics",
  "simulation_type": "projectile_motion",
  "input_interpretation_latex": "v_0 = 25\\text{ m/s}, \\quad \\alpha = 45^\\circ, \\quad g = 9.81\\text{ m/s}^2",
  "exact_results": [
    { "label": "Maksimal balandlik (H_max)", "latex": "H_{\\max} = \\frac{v_0^2 \\sin^2\\alpha}{2g} \\approx 15.93\\text{ m}" },
    { "label": "Uchish uzoqligi (L_max)", "latex": "L_{\\max} = \\frac{v_0^2 \\sin(2\\alpha)}{g} \\approx 63.71\\text{ m}" },
    { "label": "Uchish vaqti (T)", "latex": "T = \\frac{2 v_0 \\sin\\alpha}{g} \\approx 3.60\\text{ s}" }
  ],
  "steps": [
    { "title": "1-qadam: Tezlikni X va Y o'qlariga proyeksiyalash", "latex": "v_{0x} = v_0 \\cos\\alpha, \\quad v_{0y} = v_0 \\sin\\alpha" },
    { "title": "2-qadam: Harakat tenglamalarini tuzish", "latex": "x(t) = v_{0x} t, \\quad y(t) = v_{0y} t - \\frac{1}{2}gt^2" }
  ],
  "parameters": [
    { "id": "v0", "label": "Boshlang'ich tezlik (v₀)", "min": 1, "max": 100, "step": 1, "default": 25, "unit": "m/s" },
    { "id": "angle", "label": "Otilish burchagi (α)", "min": 5, "max": 85, "step": 1, "default": 45, "unit": "°" },
    { "id": "gravity", "label": "Erkin tushish tezlanishi (g)", "min": 1.6, "max": 24.8, "step": 0.1, "default": 9.81, "unit": "m/s²" },
    { "id": "drag", "label": "Havo qarshiligi (k)", "min": 0, "max": 0.5, "step": 0.01, "default": 0, "unit": "" }
  ],
  "visual_config": {
    "default_mode": "3D",
    "show_vectors": true,
    "show_grid": true,
    "camera_position": [30, 20, 50]
  }
}
```

## 5. AI Yordamchilar Uchun Tayyor Promptlar (Copy-Paste Prompts)

Loyiha ustida ishlayotganingizda **Antigravity**, **GitHub Copilot** va **GPT / Claude / Gemini** ga quyidagi maxsus promptlarni nusxalab berasiz.

### 5.1. MASTER SYSTEM PROMPT (Barcha AI'lar loyihani tushunishi uchun)

> *Ushbu promptni yangi chat ochganda yoki Antigravity / Cursor / Copilot'ning System Rules qismiga joylashtiring:*

```text
ROLE & OBJECTIVE:
You are the Lead Principal Architect and Scientific Simulation Engineer building "SciAlpha 2D/3D" — a desktop (.exe) Computational Knowledge & Interactive 2D/3D Simulation Engine inspired by Wolfram Alpha.

CORE PRODUCT VISION:
1. WOLFRAM ALPHA UI DESIGN: All outputs MUST be rendered inside structured, high-contrast "Pods" (clean white cards `#FFFFFF` with subtle gray header bars `#F0F2F5`, `#E2E5EC` borders, and Wolfram Orange `#F65314` accents). Never build a generic chat-bubble interface.
2. NEURO-SYMBOLIC ACCURACY: Never let an LLM guess mathematical or physical calculations. Use Python (`SymPy`, `SciPy`, `NumPy`, `Pint`, `RDKit`) in the backend or deterministic physics formulas in the frontend to compute exact analytical and numerical values.
3. DUAL 2D & 3D INTERACTIVE SIMULATION: Every scientific query must render an interactive simulation viewport with a seamless `[ 2D | 3D ]` toggle, `[ Play / Pause / Reset ]` controls, vector arrows, and real-time parameter sliders.
4. REAL-TIME PARAMETER REACTIVITY: When the user drags any parameter slider (e.g., mass, velocity, angle, gravity, temperature, frequency, equation coefficients), the 2D/3D scene, exact numerical readouts, and dynamic graphs must update immediately at 60 FPS without reloading the page.
5. MODULAR ARCHITECTURE: Keep every simulation scene, UI Pod, and backend solver strictly modular and self-contained so adding new scientific domains never breaks existing code.
```

### 5.2. ANTIGRAVITY UCHUN PROMPT (1-Bosqich: Loyiha Karkasi va MVP Yaratish)

> *Antigravity agentiga loyihani noldan yig'ishni buyurish uchun ushbu promptni bering:*

```text
Read MASTER_BLUEPRINT.md carefully. Your task is to scaffold and implement Phase 1 (Working MVP) of the SciAlpha 2D/3D Desktop App.

Please execute the following steps autonomously:
1. Initialize a React + TypeScript + Vite + TailwindCSS frontend project configured for desktop packaging (Tauri/Electron ready), and install `three`, `@types/three`, `katex`, and `lucide-react`.
2. Build the authentic Wolfram Alpha-inspired UI layout (`WolframHeader.tsx`, `PodCard.tsx`, `StepByStepPod.tsx`, `ParameterSlidersPod.tsx`, `LiveChartPod.tsx`) using the exact color palette (`#F65314` Wolfram Orange, `#F7F8FA` background, clean Pod headers).
3. Implement the `SimulationViewport.tsx` engine supporting a live `[ 2D | 3D ]` mode switch, `[ Play / Pause / Reset ]`, time-scale control (`0.25x`, `1x`, `2x`), and vector overlays.
4. Implement 4 complete, interactive scientific simulation modules out-of-the-box so the app works immediately:
   - Physics (Mechanics): Projectile Motion & Pendulum Dynamics in 2D and 3D with velocity/force vectors and live energy plots.
   - Mathematics (Calculus/3D): 3D Parametric Surface & Wave Interference (`z = f(x, y, t)`) with slice planes in 2D and rotatable mesh in 3D.
   - Chemistry (Molecular): Interactive 2D Structural Formula & 3D CPK Ball-and-Stick Molecule Viewer (Water, Methane, Benzene, Caffeine, DNA base pair) with bond angles and thermal vibration slider.
   - Astronomy (Astrophysics): 2D/3D Orbital Mechanics & Gravity Well simulator with adjustable star/planet masses and orbital eccentricity.
5. Verify that all TypeScript types compile cleanly and run the dev server to confirm zero runtime errors.
```

### 5.3. GITHUB COPILOT UCHUN PROMPT (`.github/copilot-instructions.md`)

> *Loyiha ichida `.github/copilot-instructions.md` faylini ochib, ichiga buni tashlab qo'ysangiz, Copilot har safar kod yozayotganda shu qoidalarga amal qiladi:*

```text
# GitHub Copilot Instructions for SciAlpha 2D/3D

- **UI Style**: Always use Wolfram Alpha "Pod" components (`<PodCard title="...">`). Use `KaTeX` for all math/physics formulas. Never render plain-text equations like `v0^2 / 2g`.
- **2D/3D Synchronization**: Any simulation state (time `t`, position vectors, slider parameters) must be shared between the 2D Canvas renderer and the 3D Three.js renderer so switching between 2D and 3D preserves the exact state and slider values.
- **Physics & Math Precision**: Always include explicit SI units (`m/s`, `N`, `J`, `K`, `mol/L`) in slider labels and result pods. Use Runge-Kutta (RK4) or exact analytical equations for physics integration rather than naive Euler steps when accuracy matters.
- **Error Handling**: Wrap dynamic 3D/2D simulation renderers in an ErrorBoundary so a malformed user formula shows a clean mathematical error notice inside the Pod instead of crashing the app.
```

### 5.4. ILMIY AI GENERATOR PROMPTI (Ilova ichidagi LLM yangi savoldan 2D/3D simulyatsiya yaratishi uchun)

> *Bu prompt dasturning o'zida (`backend/engines/llm_orchestrator.py` ichida) ishlaydi. Foydalanuvchi dasturda tayyor bo'lmagan yangi savol berganda, ichki AI shu prompt yordamida yangi 2D/3D sahna yaratadi:*

```text
You are the SciAlpha Simulation Compiler. Given a user's scientific question in any language (including Uzbek, English, or Russian):
1. Identify the scientific domain (`math`, `physics`, `chemistry`, `biology`, `astronomy`).
2. Formulate the exact mathematical equations and step-by-step analytical derivation in valid LaTeX.
3. Extract 3 to 6 key interactive parameters with realistic physical bounds (`min`, `max`, `step`, `default`, `unit`) so the user can manipulate the phenomenon via sliders.
4. Output ONLY a valid JSON object matching the `SimulationResponseSchema`, including the declarative scene graph (`objects`, `forces`, `fields`, `update_equations`, `plot_series`) required by the 2D Canvas and 3D Three.js engines.
```

## 6. Bosqichma-Bosqich Amalga Oshirish Rejasi (Roadmap)

1. **1-Bosqich (Asosiy UI va 2D/3D Yadro):** Wolfram Alpha dizaynidagi Pod'lar tizimi, 2D/3D almashtirgich, Slayderlar va 4 ta asosiy fan (Matematika, Fizika, Kimyo, Astronomiya) bo'yicha jonli simulyatsiya yadrosini ishga tushirish.
2. **2-Bosqich (Python Ilmiy Backend):** Lokal `FastAPI` + `SymPy` + `SciPy` + `RDKit` serverini ulash — har qanday tenglama va kimyoviy formulani cheksiz aniqlikda yechish.
3. **3-Bosqich (AI Text-to-Simulation Konveyeri):** LLM API (Gemini / GPT / lokal Ollama) ulab, foydalanuvchi o'zbek tilida yozgan ixtiyoriy savolni avtomatik ravishda 2D/3D simulyatsiyaga aylantirish.
4. **4-Bosqich (`.exe` Kompilatsiya):** Tauri yoki Electron yordamida Python yadrosi va Frontendni bitta mustaqil `.exe` o'rnatish fayliga (`SciAlpha_Setup.exe`) yig'ish.

