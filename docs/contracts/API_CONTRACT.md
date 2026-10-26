# Lokal API — reja

Holat: P02/P12 uchun tavsif; server hali mavjud emas.

| Operatsiya | Reja | Javob |
| --- | --- | --- |
| Health | GET /health | Yadro va kontrakt versiyasi, tayyorlik |
| Solve | POST /solve | Validatsiyalangan SimulationResponse |
| Simulate | POST /simulate | Model, parametr revisioni va vaqt oralig'iga mos namunalar |
| Chemistry | POST /chemistry | Tasdiqlangan molekula, atom/bog' va koordinata ma'lumotlari |

Savol yuborish va parametr yangilash request_id bilan korrelyatsiya qilinadi.
Frontend oxirgi revisionga mos javobni qabul qiladi; bekor qilingan so'rov kechiksa eski natija tashlanadi.
HTTP xatolarida ham bir xil error envelope ishlatiladi; invalid_input, unsupported_model, computation_timeout, backend_unavailable va internal_error ajratiladi.
Aniq body maydonlari, timeout qiymatlari va versiya prefiksi P02da muzlatiladi.
Autentifikatsiya faqat lokal sessiyaga tegishli; tashqi tarmoqqa server ochilmaydi.
