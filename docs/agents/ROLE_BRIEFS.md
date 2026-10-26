# Kod agentlari uchun rollar

Haqiqiy agentlar hali ishga tushirilmagan yoki biriktirilmagan.

| Rol | Vazifa | Fayl doirasi | Topshirish dalili |
| --- | --- | --- | --- |
| Organizer | G'oya, goals, plan, backlog, handoff | docs, README, agent hujjatlari | Izchil task va qabul mezonlari; dastur kodi yo'q |
| Contract | UI/backend kelishuvi | docs/contracts, keyin src/types | Versiyalangan maydonlar va validatsiya holatlari |
| UI | Pods, inputs, accessible layout | src/components | Barcha UI holatlari va klaviatura tekshiruvi |
| Simulation | Umumiy state, 2D/3D adapter | src/simulation | State continuity va performance dalili |
| Science/Backend | Model va solver | backend/engines | Manba, faraz, birlik, tolerans va regression |
| Domain | Math/chemistry/astronomy preset | presets va tegishli engine | Domen testi va 2D/3D xaritasi |
| Desktop | Tauri, Python sidecar, installer | src-tauri | Toza Windows tekshiruvi |
| QA/Integration | Yaxlit qabul | tests va quality dalillari | Mezonga bog'langan hisobot |

Har agentga task ID, scope, dependencies va acceptance beriladi.
Bir vaqtning o'zida umumiy state yoki kontraktni bir nechta agent o'zgartirmaydi; integratsiya egasi kelishiladi.
Topshiriq shabloni: [HANDOFF_TEMPLATE.md](HANDOFF_TEMPLATE.md).
