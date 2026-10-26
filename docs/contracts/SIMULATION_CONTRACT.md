# SimulationResponse v1 — kontrakt loyihasi

Holat: tavsiya; P02da yakunlanadi. Bu executable JSON Schema emas.

| Maydon | Talab va ma'no |
| --- | --- |
| schema_version | Majburiy kontrakt versiyasi; noma'lum versiya rad etiladi |
| request_id / revision | So'rov va parametr versiyasi; stale javobni ajratadi |
| status | success, unsupported, clarification_required yoki error |
| query / domain | Asl savol va math/physics/chemistry/biology/astronomy |
| simulation_type | Ro'yxatdan o'tgan preset ID; arbitrary kod emas |
| interpretation | Talqin LaTeX, farazlar va model chegaralari |
| results | Label, machine-readable qiymat, birlik, LaTeX va exact/numerical turi |
| steps | Tekshirilgan qoida va izohlar; mavjud bo'lmasa ochiq ko'rsatiladi |
| parameters | ID, label, min/max/step/default/current, unit va validation |
| simulation | Boshlang'ich holat, vaqt birligi, o'qlar va model ID |
| visual_config | 2D/3D default, grid, vektor va camera; hisob modelidan mustaqil |
| plot_series | Barqaror ID, o'qlar/birliklar, manba va sample chegarasi |
| provenance | Solver/model versiyasi, ma'lumot manbasi, tolerans |
| error | Kod, xavfsiz xabar, field va qayta urinish mumkinligi |

## Qoidalar

SI ichki birliklar; display birliklari alohida. Burchak ichkarida radian, UI gradus bo'lishi mumkin; aylantirish aniq.
NaN/Infinity, noma'lum preset, noto'g'ri dimension va chegaradan tashqari kirish rad qilinadi.
Step defaultni majburan yaxlitlamaydi: g=9.81 qiymati saqlanishi uchun gravity step=0.01 taklif etiladi.
2D/3D bir xil world coordinates va state revisiondan foydalanadi; 2D projection xaritasi presetda yoziladi.
Renderlar uchun alohida physics state bo'lmaydi.
Array uzunligi, ifoda hajmi, hisob timeouti va sampling limiti P02da son bilan belgilanadi.

Blueprintdagi objects/forces/fields/update_equations kelajak DSL g'oyasi.
v1da faqat allowlist preset va parametrlar bor; erkin update_equations bajarilmaydi.
