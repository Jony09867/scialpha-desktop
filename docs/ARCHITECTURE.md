# Arxitektura rejasi

## Qatlamlar

- Desktop: Tauri v2 — boshlang'ich tanlov; Electron faqat ADR bilan asoslangan fallback.
- UI: React, TypeScript, Vite, Tailwind va KaTeX; versiyalar P01da tekshiriladi. Blueprintdagi React 18 majburiy lock emas.
- Vizual: Canvas 2D, Three.js ekotizimi 3D; Plotly grafiklar uchun nomzod.
- Ilmiy yadro: FastAPI, SymPy, SciPy, NumPy, Pint; RDKit va Astropy domen talabi bo'yicha.
- LLM: providerga bog'lanmagan adapter; faqat tasdiqlangan preset va parametrlarni tanlash.

## Ma'lumot oqimi

Savol/preset → talqin → kontrakt validatsiyasi → ilmiy model → natija + simulyatsiya holati → Pods, 2D, 3D, grafik.
Renderlar bitta vaqt va parametrlardan foydalanadi. UI komponentlari mustaqil fizik olam yaratmaydi.
M1da deterministik model lokal bo'lishi mumkin; M3da backend bilan qiymat pariteti regressiya orqali tekshiriladi.

## Ilmiy cheklovlar

Rapier/Matter vizual yordamchi bo'lishi mumkin; ular avtomatik ravishda ilmiy natijaning haqiqat manbai emas.
Analitik yechim mavjud bo'lsa undan foydalaniladi; sonli modelda algoritm, qadam, tolerans va farazlar yoziladi.
Mayatnikning kichik burchak formulasi katta burchakda aniq deb ko'rsatilmaydi.
Havo qarshiligi M1dan chiqarilgan; keyinchalik drag modeli va koeffitsiyent birligi alohida belgilanadi.

## Desktop chegaralari

Lokal backend faqat loopback orqali, ilova sessiyasiga bog'langan autentifikatsiya bilan ishlashi rejalashtiriladi.
Ishga tushirish, port tanlash, yopish va orphan process tozalash desktop agentining vazifasi.
API kalitlari frontend bundle yoki repoda saqlanmaydi.
Installerga Python/RDKit yetkazish og'irligi P01 risk tekshiruvida baholanadi.
