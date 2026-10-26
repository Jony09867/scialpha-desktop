# Ishlar ro'yxati

Mas'ullar hozir rol sifatida berilgan; real agent biriktirilganda nomi yoziladi.
M0 dokumentatsiya natijasidir; barcha implementatsiya tasklari ochiq.

| ID | Ish | Rol | Bog'liqlik | Holat | Qabul mezoni |
| --- | --- | --- | --- | --- | --- |
| P00 | Rejalashtirish paketini tayyorlash | Organizer | — | done | README, plan, goals, kontrakt va handoff mavjud |
| P01 | Stek mosligi va desktop feasibility | Desktop | P00 | ready | Versiyalar, Python bundling tajribasi va ADR |
| P02 | Kontrakt v1ni yakunlash | Contract | P00 | ready | Maydonlar, birliklar, errors, valid/invalid misollar |
| P03 | Frontend karkasi va Pods | UI | P01,P02 | planned | UI holatlari va klaviatura boshqaruvi |
| P04 | Snaryad deterministik modeli | Science | P02 | planned | Referens qiymatlar va chekka holatlar |
| P05 | Umumiy state va 2D/3D render | Simulation | P03,P04 | planned | Toggle state saqlaydi; pause/reset ishlaydi |
| P06 | Slayder va grafik integratsiyasi | UI + Simulation | P05 | planned | Natija, grafik va sahna bitta versiyada |
| P07 | M1 qabul tekshiruvi | QA | P06 | planned | G1 dalillari va performance yozuvi |
| P08 | Mayatnik modeli | Science + Simulation | P07 | planned | Kichik/katta burchak farazi va energiya testi |
| P09 | Sirt va to'lqin modeli | Math + Simulation | P07 | planned | 2D kesim 3D sirtga mos |
| P10 | Molekula ko'rish | Chemistry | P07 | planned | Atom/bog' identifikatorlari va manba ko'rsatilgan |
| P11 | Orbital model | Astronomy | P07 | planned | Birliklar, orbit va invariant tekshiruvlari |
| P12 | FastAPI va solverlar | Backend | P01,P02,P07 | planned | Validatsiya, timeout va hisob regressiyasi |
| P13 | UI/backend integratsiyasi | Integration | P08,P09,P10,P11,P12 | planned | Xatolar va stale javoblar boshqariladi |
| P14 | LLM preset router | AI integration | P13 | planned | Uch til korpusi, allowlist, no-code execution |
| P15 | Python sidecar va installer | Desktop | P01,P13 | planned | Toza Windows, offline preset, lifecycle |
| P16 | Release qabul | QA | P14,P15 | planned | G2–G5 dalillari va release checklist |

P00dan keyingi birinchi topshiriq: docs/agents/FIRST_TASK.md.
Task holatini faqat dalil bilan yangilang; branch, PR va test havolalarini task ostiga qo'shing.
