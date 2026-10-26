# Yo'l xaritasi

Sanalar taxmin qilinmagan; keyingi bosqich kirish mezoniga bog'liq.

| Bosqich | Natija | Chiqish mezoni |
| --- | --- | --- |
| M0 — tashkil qilish | Hujjatlar, kontrakt loyihasi, tasklar, papkalar | Rejalashtirish paketi ko'rib chiqishga tayyor |
| M1 — vertikal tajriba | UI + snaryad + 2D/3D + slayder + grafik | G1 va referens snaryad tekshiruvi |
| M2 — domenlar | Mayatnik, sirt/to'lqin, molekulalar, orbital preset | Har domenning modeli, cheklovi, test dalili mavjud |
| M3 — ilmiy backend | Python hisoblash, birlik va xato kontrakti | G3, frontend integratsiya va regressiya |
| M4 — savoldan simulyatsiya | Tabiiy til → validatsiya → allowlist preset | Uch tilda korpus; unsupported/ambiguous holatlar |
| M5 — desktop release | Tauri + Python paketlash + Windows installer | Toza kompyuterda G5 tekshiruvi |

M1 avval deterministik preset bilan ishlaydi; LLM talab qilinmaydi.
Tauri/Python paketlash feasibility tekshiruvi M1da bajariladi, yakuniy tarqatish M5da.
M2 ichida mustaqil modullar kelishilgan kontraktdan keyin turli kod agentlariga berilishi mumkin; bu hujjat agentlarni avtomatik ishga tushirmaydi.
