# Real-Time-Furniture-Classification-System-Computer-Vision
Bu layihədə müxtəlif bucaqlardan çəkilmiş mebel şəkillərini 6 kateqoriya üzrə (yataq, stul, jurnal masası, yemək masası, komod və divan) tanıyan dərin öyrənmə (Deep Learning) modeli qurulub.

İstifadə olunan Data haqqında
Ümumi həcm: 6 sinif üzrə cəmi 10,364 şəkil.

Siniflərin paylanması:

Divan (Sofa): 2,904 şəkil

Stul (Chair): 2,718 şəkil

Yemək masası (Dining Table): 1,861 şəkil

Yataq (Bed): 1,244 şəkil

Komod (Dresser): 1,109 şəkil

Jurnal masası (Coffee Table): 528 şəkil

Bölgü qaydası (Data Leakage-in qarşısının alınması): Datada eyni mebelin müxtəlif bucaqlardan çəkilmiş bir neçə şəkli olduğu üçün məlumatlar təsadüfi deyil, qovluq (obyekt) əsaslı bölünüb (70% Train - 6,973 şəkil, 15% Validation - 1,617 şəkil, 15% Test - 1,774 şəkil). Bu üsul eyni mebelin həm öyrənmə, həm də test dəstində yer almasının qarşısını alır.

Nələr edilib?
Data Hazırlığı: Şəkillər 224x224 ölçüsünə gətirilib, ImageNet standartlarına uyğun normallaşdırılıb. Öyrənmə dəstinə üfüqi çevirmə (Horizontal Flip), fırlanma (Rotation) və rəng tənzimləmələri (Color Jitter) tətbiq olunub.

Model Arxitekturası: Transfer Learning yanaşması ilə öncədən öyrədilmiş ConvNeXt-Base modelindən istifadə edilib və son çıxış təbəqəsi 6 sinfə uyğunlaşdırılıb.

İki mərhələli təlim (Two-Stage Fine-Tuning):

1-ci mərhələ: Modelin əsas hissəsi dondurulub və yalnız yeni əlavə olunan təsnifat təbəqəsi 1e-3 öyrənmə sürəti (learning rate) ilə 4 epox öyrədilib.

2-ci mərhələ: Modelin son iki bloku (features[-2:]) açılıb və bütün sistem 1e-5 öyrənmə sürəti ilə daha 4 epox incə tənzimlənib (fine-tuning). Ən yaxşı validation nəticəsi verən çəkilər yadda saxlanılıb.

Əldə olunan nəticələr
1-ci mərhələ Validation Accuracy: 87.45%

2-ci mərhələ Validation Accuracy: 88.37%

Yekun Test Accuracy: 89.46%

Macro F1-Score: 0.846

Siniflər üzrə F1-Score göstəriciləri:

Komod (Dresser): 0.985

Yataq (Bed): 0.979

Divan (Sofa): 0.946

Stul (Chair): 0.903

Yemək masası (Dining Table): 0.851

Jurnal masası (Coffee Table): 0.412 (Bu sinifdə şəkil sayının az olması və jurnal masalarının vizual olaraq yemək masaları ilə qarışdırılması nəticəni aşağı salıb).
