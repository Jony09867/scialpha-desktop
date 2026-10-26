# Maqsadlar va natija mezonlari

Holatlar: planned → ready → in_progress → review → done; to'siq bo'lsa blocked.
Hozir faqat G0 hujjatlari tayyorlangan; dastur maqsadlari bajarilmagan.

| ID | Maqsad | Qabul dalili |
| --- | --- | --- |
| G0 | Agentlarga aniq loyiha asosi | Hujjatlar, vazifa IDlari, modul egasi va handoff tartibi mavjud |
| G1 | Snaryad uchun yaxlit tajriba | Parametr → hisob → Pods → 2D/3D → grafik; vaqt va parametrlar saqlanadi |
| G2 | To'rtta fan yo'nalishi | Fizika, matematika, kimyo, astronomiya sahnalari domen testlaridan o'tadi |
| G3 | Lokal ilmiy backend | Kontrakt validatsiyasi, birlik tekshiruvi, xatolar va regressiya tekshiriladi |
| G4 | Tabiiy tildan boshqariladigan preset | O'zbek/ingliz/rus misollari tasdiqlangan presetga o'tadi; noaniq savol aniqlashtiriladi |
| G5 | Windows tarqatish | Toza Windows muhitida o'rnatish, ishga tushish, offline preset, yopilish va uninstall tekshiriladi |

## O'lchanadigan talablar

- Referens snaryad: v0=25 m/s, burchak=45°, g=9.81 m/s², drag=0, y0=0; H≈15.927625 m, R≈63.710499 m, T≈3.604010 s. Analitik qiymatlarga mutlaq xatolik ≤0.00001 tegishli SI birligi.
- 2D/3D almashtirish hisoblash vaqti, parametrlar va play/pause holatini o'zgartirmaydi.
- Render maqsadi: oddiy presetda 60 FPS; benchmark qurilma/GPU/oyna o'lchami yoziladi. Qurilma hali tanlanmagan, maqsad bajarildi deb hisoblanmaydi.
- Parametr tahriridan vizual javobgacha p95 ≤100 ms — kelishiladigan referens qurilmada; og'ir backend hisoblari alohida loading va bekor qilish holatiga ega.
- Takroriy bir xil kirish bir xil model natijasini beradi; birliklar ko'rinadi.
- Noto'g'ri parametr, qo'llanmaydigan savol va backend uzilishi ilovani yiqitmaydi.

Yakuniy qabul: docs/QUALITY_PLAN.md dalillari va foydalanuvchi ko'rib chiqishi.
