# Fayllar tashkiloti

Hozirgi barcha modul papkalari README bilan belgilangan; source va dependency manifestlar hali yaratilmagan.

| Yo'l | Mas'ul | Kelajakdagi tarkib |
| --- | --- | --- |
| src/components/ | UI | Header, PodCard, steps, controls va chart Pods |
| src/types/ | Contract | Frontend kontrakt tiplari |
| src/simulation/ | Simulation | Umumiy holat, viewport va render adapterlari |
| src/simulation/presets/ | Domain agents | Mexanika, sirt, molekula va orbit sahnalari |
| backend/engines/ | Backend/Science | Matematik, fizik, kimyoviy solver va LLM router |
| backend/knowledge_base/ | Science | Manbasi, versiyasi va birliklari ko'rsatilgan konstantalar |
| src-tauri/ | Desktop | Desktop config, sidecar lifecycle va installer |
| tests/ | QA | Unit, contract, integration, ilmiy regression, desktop smoke |
| docs/contracts/ | Contract | API va simulyatsiya kontrakti tavsifi |
| docs/agents/ | Organizer | Rollar, birinchi task va handoff |
| docs/decisions/ | Architecture | ADR hujjatlari |
| .github/ | Organizer | Agent ko'rsatmasi, issue va PR shablonlari |

Blueprintdagi main.py, App.tsx, package.json, requirements.txt va simulation.ts — kelajak fayllari; ularning bo'sh yoki soxta implementatsiyasi yaratilmaydi.
Kod agenti kerakli faylni o'z taski doirasida yaratadi. Bir moduldagi o'zgarish boshqa modul egasi bilan kontrakt orqali kelishiladi.
