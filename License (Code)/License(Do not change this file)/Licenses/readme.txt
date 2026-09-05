==============================================================================
  LİSANS TASLAKLARI  —  KULLANIM VE REFERANS KILAVUZU
==============================================================================

Bu klasör, 50 adet lisans metnini isimsiz ve tarihsiz TASLAK (şablon) hâlinde
içerir. Her dosya, ilgili lisansın resmî ve tam metnidir; yalnızca telif
bildirimi alanları köşeli parantezli yer tutucularla boş bırakılmıştır.

Bu dosya (readme.txt), listedeki HER lisans için ayrı ayrı hazırlanmış
referans örnek yazıları içerir: lisans dosyasına yazılacak telif satırı,
kaynak koda eklenecek başlık bildirimi ve projenizin tanıtım metnine konulacak
lisans notu.

------------------------------------------------------------------------------
  İÇİNDEKİLER
------------------------------------------------------------------------------

  1.  Bu klasördeki dosyalar
  2.  Yer tutucu (placeholder) sözlüğü
  3.  Nasıl kullanılır — 4 adım
  4.  Hızlı karşılaştırma tablosu
  5.  Lisans referans örnekleri (her lisans için ayrı ayrı)
  6.  Sık yapılan hatalar
  7.  Biçim ve kodlama bilgisi
  8.  Kaynaklar
  9.  Yasal uyarı


==============================================================================
  1.  BU KLASÖRDEKİ DOSYALAR
==============================================================================

Toplam 50 lisans taslağı + bu readme.txt dosyası bulunmaktadır. Dosya adları
SPDX kimlikleriyle birebir aynıdır; böylece otomatik araçlarla eşleştirme
yapılabilir.

    1. 0BSD.txt                BSD Zero Clause License
    2. AFL-3.0.txt             Academic Free License v3.0
    3. AGPL-3.0.txt            GNU Affero General Public License v3.0
    4. Apache-1.1.txt          Apache Software License 1.1
    5. Apache-2.0.txt          Apache License 2.0
    6. Artistic-2.0.txt        Artistic License 2.0
    7. Beerware.txt            Beerware License
    8. BlueOak-1.0.0.txt       Blue Oak Model License 1.0.0
    9. BSD-2-Clause.txt        BSD 2-Clause "Simplified" License
   10. BSD-3-Clause.txt        BSD 3-Clause "New" or "Revised" License
   11. BSD-4-Clause.txt        BSD 4-Clause "Original" License
   12. BSL-1.0.txt             Boost Software License 1.0
   13. CC-BY-4.0.txt           Creative Commons Attribution 4.0 International
   14. CC-BY-NC-4.0.txt        Creative Commons Attribution-NonCommercial...
   15. CC-BY-NC-ND-4.0.txt     Creative Commons Attribution-NonCommercial-...
   16. CC-BY-NC-SA-4.0.txt     Creative Commons Attribution-NonCommercial-...
   17. CC-BY-ND-4.0.txt        Creative Commons Attribution-NoDerivatives...
   18. CC-BY-SA-4.0.txt        Creative Commons Attribution-ShareAlike 4.0...
   19. CC0-1.0.txt             Creative Commons Zero v1.0 Universal
   20. CDDL-1.0.txt            Common Development and Distribution License 1.0
   21. CECILL-2.1.txt          CeCILL Free Software License Agreement v2.1
   22. ECL-2.0.txt             Educational Community License v2.0
   23. EPL-1.0.txt             Eclipse Public License 1.0
   24. EPL-2.0.txt             Eclipse Public License 2.0
   25. EUPL-1.2.txt            European Union Public Licence v1.2
   26. GPL-2.0.txt             GNU General Public License v2.0
   27. GPL-3.0.txt             GNU General Public License v3.0
   28. ISC.txt                 ISC License
   29. LGPL-2.1.txt            GNU Lesser General Public License v2.1
   30. LGPL-3.0.txt            GNU Lesser General Public License v3.0
   31. LPPL-1.3c.txt           LaTeX Project Public License v1.3c
   32. MIT-0.txt               MIT No Attribution License
   33. MIT.txt                 MIT License
   34. MPL-2.0.txt             Mozilla Public License 2.0
   35. MS-PL.txt               Microsoft Public License
   36. MS-RL.txt               Microsoft Reciprocal License
   37. MulanPSL-2.0.txt        Mulan Permissive Software License v2
   38. NCSA.txt                University of Illinois/NCSA Open Source License
   39. ODbL-1.0.txt            Open Data Commons Open Database License v1.0
   40. OFL-1.1.txt             SIL Open Font License 1.1
   41. OSL-3.0.txt             Open Software License 3.0
   42. PostgreSQL.txt          PostgreSQL License
   43. Proprietary.txt         Tescilli Yazılım Lisans Sözleşmesi (Tüm...
   44. Python-2.0.txt          Python Software Foundation License 2.0
   45. Ruby.txt                Ruby License
   46. Sleepycat.txt           Sleepycat License (Berkeley DB)
   47. Unlicense.txt           The Unlicense
   48. Vim.txt                 Vim License
   49. WTFPL.txt               Do What The F*ck You Want To Public License v2
   50. Zlib.txt                zlib License


==============================================================================
  2.  YER TUTUCU (PLACEHOLDER) SÖZLÜĞÜ
==============================================================================

Taslaklarda geçen köşeli parantezli alanlar doldurulmalıdır. Parantezler DE
silinir — yani [YEAR] yerine sadece 2025 yazılır.

   [YEAR]                 Eserin ilk yayımlandığı yıl (aralık da olur:
                          2023-2025)
   [COPYRIGHT HOLDER]     Telif hakkı sahibinin tam adı (kişi veya tüzel kişi)
   [ORGANIZATION]         Kurum / şirket / vakıf adı
   [SOFTWARE NAME]        Yazılımın veya paketin adı
   [EMAIL]                İletişim e-posta adresi
   [PROJECT URL]          Proje veya kurum web adresi
   [DEVELOPMENT GROUP]    Geliştirme ekibinin/laboratuvarın adı (NCSA)
   [INSTITUTION]          Üniversite veya araştırma kurumu adı (NCSA)
   [RESERVED FONT NAME]   Korunan yazı tipi adı (OFL-1.1)
   [JURISDICTION]         Yetkili hukuk ve mahkeme yeri (Proprietary)

Bazı lisanslarda (GPL, Apache-2.0, MPL, MulanPSL vb.) yer tutucular yalnızca
metnin sonundaki 'nasıl uygulanır' ekinde bulunur. Bu eklerdeki yer tutucular
lisansın resmî metninin parçasıdır ve OLDUĞU GİBİ bırakılmalıdır; siz onları
kopyalayıp kaynak dosyalarınızın başına doldurarak eklersiniz.

   ÖNEMLİ: Lisans metninin İÇİNDEKİ, lisansı yazan kuruma ait telif
   satırları (örn. GPL'deki 'Copyright (C) 2007 Free Software Foundation',
   WTFPL'deki 'Copyright (C) 2004 Sam Hocevar') ASLA değiştirilmez. Bunlar
   lisans belgesinin kendi telifidir, sizin eserinizin değil.

   YER TUTUCUSU OLMAYAN LİSANSLAR (50 taslaktan 34'ü): GPL, AGPL, LGPL,
   MPL, EPL, Apache-2.0, CC ailesi, Unlicense, CC0 ve benzerlerinin
   metninde doldurulacak HİÇBİR alan yoktur. Bu lisanslarda LICENSE dosyası
   hiçbir ekleme yapılmadan BİREBİR kopyalanır; başına telif satırı
   EKLENMEZ. Telifiniz kaynak dosya başlıklarına (Bölüm 5, ÖRNEK 2) ve
   README notuna (ÖRNEK 3) yazılır. Hangi lisansta yer tutucu olduğunu
   Bölüm 5'teki 'Yer tutucular' satırından görebilirsiniz.

   KÖŞELİ PARANTEZ HER ZAMAN YER TUTUCU DEĞİLDİR: Bazı resmî metinlerde
   köşeli parantez bağlantı veya atıf işareti olarak geçer — örneğin
   BlueOak-1.0.0 içindeki '[Notices](#notices)' bir Markdown bağlantısıdır,
   doldurulacak bir alan değil. Yalnızca yukarıdaki sözlükte adı geçen
   alanlar doldurulur.


==============================================================================
  3.  NASIL KULLANILIR — 4 ADIM
==============================================================================

   ADIM 1 — Lisansı seçin
   Bölüm 4'teki karşılaştırma tablosundan ve Bölüm 5'teki açıklamalardan
   yararlanın. Kararsızsanız: kütüphane/araç için MIT veya Apache-2.0,
   değişikliklerin geri dönmesini istiyorsanız GPL-3.0 veya MPL-2.0, sunucu
   yazılımı için AGPL-3.0, içerik/dokümantasyon için CC-BY-4.0.

   ADIM 2 — Dosyayı kopyalayın ve adlandırın
   İlgili .txt dosyasını projenizin kök dizinine kopyalayın ve adını LICENSE
   veya LICENSE.txt yapın. GNU lisanslarında geleneksel ad COPYING'dir. Birden
   fazla lisans kullanıyorsanız LICENSES/ klasörü açıp dosyaları SPDX
   adlarıyla saklayın.

   ADIM 3 — Yer tutucuları doldurun (VARSA)
   Bölüm 2'deki sözlüğe göre köşeli parantezli alanları değiştirin.
   Parantezleri de silin. Lisans metninin geri kalanına DOKUNMAYIN — tek bir
   kelimesini değiştirmek bile onu farklı bir lisans hâline getirir.

   Bu adımın iki istisnası vardır (Bölüm 2):
     • Lisansın sonundaki 'nasıl uygulanır' ekinde geçen yer tutucular
       DOLDURULMAZ, olduğu gibi bırakılır (Apache-2.0, GPL ailesi,
       MulanPSL vb.). Onları kopyalayıp ADIM 4'te kaynak dosyalarınıza
       doldurarak eklersiniz.
     • Metninde hiç yer tutucu bulunmayan 34 lisansta bu adım tamamen
       ATLANIR: LICENSE dosyası birebir kopyalanır, içine hiçbir satır
       eklenmez. Doğrudan ADIM 4'e geçin.

   ADIM 4 — Bildirimleri yerleştirin
   Bölüm 5'teki ilgili lisansın örneklerinden yararlanarak kaynak
   dosyalarınızın başına bildirim satırlarını, projenizin tanıtım metnine de
   lisans notunu ekleyin.


==============================================================================
  4.  HIZLI KARŞILAŞTIRMA TABLOSU
==============================================================================

   Copyleft sütunu: Yok = izin verici | Zayıf = dosya/kütüphane düzeyi
                    Güçlü = tüm türev eseri kapsar

   DOSYA                  COPYLEFT    PATENT  KATEGORİ
   -------------------------------------------------------------------------
   0BSD.txt               Yok         Yok     İzin verici
   AFL-3.0.txt            Yok         Var     İzin verici
   AGPL-3.0.txt           Güçlü       Var     Copyleft + ağ
   Apache-1.1.txt         Yok         Yok     İzin verici (eski)
   Apache-2.0.txt         Yok         Var     İzin verici
   Artistic-2.0.txt       Zayıf       Var     Zayıf copyleft
   Beerware.txt           Yok         Yok     İzin verici (mizahi)
   BlueOak-1.0.0.txt      Yok         Var     İzin verici
   BSD-2-Clause.txt       Yok         Yok     İzin verici
   BSD-3-Clause.txt       Yok         Yok     İzin verici
   BSD-4-Clause.txt       Yok         Yok     İzin verici (eski)
   BSL-1.0.txt            Yok         Yok     İzin verici
   CC-BY-4.0.txt          Yok         Yok     İçerik (CC)
   CC-BY-NC-4.0.txt       Yok         Yok     İçerik (CC, ticari yok)
   CC-BY-NC-ND-4.0.txt    Yok         Yok     İçerik (CC, en kısıtlı)
   CC-BY-NC-SA-4.0.txt    Share-alike Yok     İçerik (CC, ticari yok)
   CC-BY-ND-4.0.txt       Yok         Yok     İçerik (CC, türev yok)
   CC-BY-SA-4.0.txt       Share-alike Yok     İçerik (CC)
   CC0-1.0.txt            Yok         Yok     Kamu malı
   CDDL-1.0.txt           Zayıf       Var     Zayıf copyleft
   CECILL-2.1.txt         Güçlü       Var     Copyleft (FR hukuku)
   ECL-2.0.txt            Yok         Var     İzin verici (eğitim)
   EPL-1.0.txt            Zayıf       Var     Zayıf copyleft
   EPL-2.0.txt            Zayıf       Var     Zayıf copyleft
   EUPL-1.2.txt           Güçlü       Var     Copyleft (AB)
   GPL-2.0.txt            Güçlü       Örtük   Güçlü copyleft
   GPL-3.0.txt            Güçlü       Var     Güçlü copyleft
   ISC.txt                Yok         Yok     İzin verici
   LGPL-2.1.txt           Zayıf       Örtük   Zayıf copyleft (kütüphane)
   LGPL-3.0.txt           Zayıf       Var     Zayıf copyleft (kütüphane)
   LPPL-1.3c.txt          Zayıf       Yok     Zayıf copyleft (LaTeX)
   MIT-0.txt              Yok         Yok     İzin verici (atıfsız)
   MIT.txt                Yok         Yok     İzin verici
   MPL-2.0.txt            Zayıf       Var     Zayıf copyleft
   MS-PL.txt              Yok         Var     İzin verici
   MS-RL.txt              Zayıf       Var     Zayıf copyleft
   MulanPSL-2.0.txt       Yok         Var     İzin verici
   NCSA.txt               Yok         Yok     İzin verici
   ODbL-1.0.txt           Güçlü       Yok     Veri (share-alike)
   OFL-1.1.txt            Share-alike Yok     Yazı tipi (font)
   OSL-3.0.txt            Güçlü       Var     Copyleft + ağ
   PostgreSQL.txt         Yok         Yok     İzin verici
   Proprietary.txt        Yok         Yok     Tescilli / kapalı
   Python-2.0.txt         Yok         Yok     İzin verici (PSF)
   Ruby.txt               Zayıf       Yok     Zayıf copyleft (ikili)
   Sleepycat.txt          Güçlü       Yok     Güçlü copyleft
   Unlicense.txt          Yok         Yok     Kamu malı
   Vim.txt                Zayıf       Yok     Zayıf copyleft (charityware)
   WTFPL.txt              Yok         Yok     Kamu malına yakın
   Zlib.txt               Yok         Yok     İzin verici


==============================================================================
  5.  LİSANS REFERANS ÖRNEKLERİ
==============================================================================

Aşağıda her lisans için ayrı ayrı: kısa tanım, dosyadaki yer tutucular ve üç
referans örnek yazı verilmiştir. Örneklerdeki 'Ada Yılmaz', 'Örnek Yazılım
A.Ş.' ve '2025' değerleri yalnızca gösterim amaçlıdır; kendi bilgilerinizle
değiştirin.

   ÖRNEK 1'İN İKİ AYRI BAŞLIĞI VAR — KARIŞTIRMAYIN:

   ► ÖRNEK 1 — Lisans dosyasındaki telif satırı (doldurulmuş):
     Bu başlık, metninde GERÇEK yer tutucu bulunan 16 lisansta kullanılır
     (MIT, ISC, BSD ailesi, 0BSD, MIT-0, Zlib, PostgreSQL, NCSA, OFL-1.1,
     Ruby, Sleepycat, Beerware, Apache-1.1, Proprietary). Gösterilen satır
     doğrudan LICENSE dosyasının İÇİNE, yer tutucunun yerine yazılır.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):
     Bu başlık, metninde doldurulacak yer tutucu BULUNMAYAN 34 lisansta
     kullanılır (GPL, AGPL, LGPL, MPL, EPL, Apache-2.0, CC ailesi,
     Unlicense, CC0, MulanPSL vb.). Bu lisanslarda LICENSE dosyası birebir
     kopyalanır ve içine HİÇBİR telif satırı eklenmez. Gösterilen satır
     yalnızca ÖRNEK 2'deki kaynak dosya başlığında ve ÖRNEK 3'teki README
     notunda kullanılır — telif hakkınızı bu lisanslarda oralarda beyan
     edersiniz.

   ÖRNEK 2 ve ÖRNEK 3'ün anlamı her lisansta aynıdır: ÖRNEK 2 kaynak dosya
   başlığına, ÖRNEK 3 projenin tanıtım metnine (README) yazılır.


------------------------------------------------------------------------------
  [01]  BSD Zero Clause License
------------------------------------------------------------------------------

   Dosya          : 0BSD.txt
   SPDX kimliği   : 0BSD
   Tür            : İzin verici (permissive)
   Copyleft       : Yok
   Patent hükmü   : Yok
   Yer tutucular  : [YEAR], [COPYRIGHT HOLDER], [EMAIL]

   Özet:
   ISC lisansından tüm koşulların çıkarılmış hâli. Atıf zorunluluğu bile
   yoktur; pratikte kamu malına en yakın OSI onaylı lisanstır. Örnek kod,
   şablon (boilerplate) ve eğitim materyalleri için uygundur.

   ► ÖRNEK 1 — Lisans dosyasındaki telif satırı (doldurulmuş):

      Copyright (C) 2025 by Ada Yılmaz <ada@ornek.com>

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      // SPDX-License-Identifier: 0BSD
      // Copyright (C) 2025 by Ada Yılmaz <ada@ornek.com>

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje BSD Zero Clause License (0BSD) ile lisanslanmıştır. Kodu
      atıf vermeden, koşulsuz olarak kullanabilirsiniz.


------------------------------------------------------------------------------
  [02]  Academic Free License v3.0
------------------------------------------------------------------------------

   Dosya          : AFL-3.0.txt
   SPDX kimliği   : AFL-3.0
   Tür            : İzin verici (permissive)
   Copyleft       : Yok
   Patent hükmü   : Var (açık hibe + misilleme)
   Yer tutucular  : Yok (lisans metni sabittir; telif satırı ayrıca eklenir)

   Özet:
   Apache-2.0'a benzer şekilde açık patent hibesi içeren, akademik kökenli
   izin verici bir lisans. Kaynak kodun sunulması ve atıf yükümlülüğü vardır.
   OSL-3.0'ın copyleft'siz kardeşidir.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Ada Yılmaz

      Licensed under the Academic Free License version 3.0

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      // SPDX-License-Identifier: AFL-3.0
      // Copyright (c) 2025 Ada Yılmaz
      // Licensed under the Academic Free License version 3.0

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje Academic Free License v3.0 koşullarıyla dağıtılmaktadır.


------------------------------------------------------------------------------
  [03]  GNU Affero General Public License v3.0
------------------------------------------------------------------------------

   Dosya          : AGPL-3.0.txt
   SPDX kimliği   : AGPL-3.0
   Tür            : Güçlü copyleft
   Copyleft       : Güçlü (+ ağ kullanımı)
   Patent hükmü   : Var
   Yer tutucular  : Yok (lisans metni sabittir; bildirim ayrıca eklenir)

   Özet:
   GPL-3.0'ın ağ boşluğunu kapatan sürümü. Yazılım bir sunucu üzerinden
   kullanıcılara hizmet olarak sunulduğunda (SaaS), kullanıcılara kaynak kodu
   sunma yükümlülüğü doğar. Sunucu tarafı uygulamalar için seçilir.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (C) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      Örnek Proje - kısa açıklama
      Copyright (C) 2025 Ada Yılmaz

      This program is free software: you can redistribute it and/or modify
      it under the terms of the GNU Affero General Public License as published
      by the Free Software Foundation, either version 3 of the License, or
      (at your option) any later version.

      This program is distributed in the hope that it will be useful,
      but WITHOUT ANY WARRANTY; without even the implied warranty of
      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
      GNU Affero General Public License for more details.

      You should have received a copy of the GNU Affero General Public License
      along with this program.  If not, see <https://www.gnu.org/licenses/>.

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje GNU AGPL v3 ile lisanslanmıştır. Yazılımı bir ağ üzerinden
      hizmet olarak sunuyorsanız, kullanıcılara tam kaynak kodu sağlamakla
      yükümlüsünüz.


------------------------------------------------------------------------------
  [04]  Apache Software License 1.1
------------------------------------------------------------------------------

   Dosya          : Apache-1.1.txt
   SPDX kimliği   : Apache-1.1
   Tür            : İzin verici (permissive)
   Copyleft       : Yok
   Patent hükmü   : Yok
   Yer tutucular  : [YEAR], [COPYRIGHT HOLDER], [ORGANIZATION], [SOFTWARE
                    NAME], [EMAIL], [PROJECT URL]

   Özet:
   Apache-2.0 öncesi, BSD-4-Clause tarzı reklam/onay koşulları içeren eski
   sürüm. Yeni projeler için ÖNERİLMEZ; yalnızca eski kod tabanlarını
   sürdürmek için bulundurulmuştur.

   ► ÖRNEK 1 — Lisans dosyasındaki telif satırı (doldurulmuş):

      Copyright (c) 2025 Örnek Yazılım A.Ş. All rights reserved.

      3. ... "This product includes software developed by Örnek Yazılım A.Ş.
         (https://ornek.com)."

      4. The names "OrnekLib" and "Örnek Yazılım A.Ş." must not be used to
         endorse ... please contact legal@ornek.com.

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      /* SPDX-License-Identifier: Apache-1.1 */
      /* Copyright (c) 2025 Örnek Yazılım A.Ş. All rights reserved. */

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu ürün Örnek Yazılım A.Ş. tarafından geliştirilen yazılım içerir
      (https://ornek.com).


------------------------------------------------------------------------------
  [05]  Apache License 2.0
------------------------------------------------------------------------------

   Dosya          : Apache-2.0.txt
   SPDX kimliği   : Apache-2.0
   Tür            : İzin verici (permissive)
   Copyleft       : Yok
   Patent hükmü   : Var (açık hibe + misilleme)
   Yer tutucular  : [yyyy], [name of copyright owner]  (yalnızca sondaki
                    APPENDIX bölümünde)

   Özet:
   Kurumsal dünyanın standart izin verici lisansı. Açık patent hibesi, ticari
   marka koruması ve değişikliklerin belgelenmesi (NOTICE) kuralları içerir.
   GPL-3.0 ile uyumludur, GPL-2.0 ile değildir.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright 2025 Örnek Yazılım A.Ş.

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      Copyright 2025 Örnek Yazılım A.Ş.

      Licensed under the Apache License, Version 2.0 (the "License");
      you may not use this file except in compliance with the License.
      You may obtain a copy of the License at

          http://www.apache.org/licenses/LICENSE-2.0

      Unless required by applicable law or agreed to in writing, software
      distributed under the License is distributed on an "AS IS" BASIS,
      WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
      See the License for the specific language governing permissions and
      limitations under the License.

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje Apache License 2.0 ile lisanslanmıştır. Ayrıca bkz. NOTICE
      dosyası. Kısa hâli:  SPDX-License-Identifier: Apache-2.0


------------------------------------------------------------------------------
  [06]  Artistic License 2.0
------------------------------------------------------------------------------

   Dosya          : Artistic-2.0.txt
   SPDX kimliği   : Artistic-2.0
   Tür            : İzin verici / zayıf copyleft
   Copyleft       : Zayıf
   Patent hükmü   : Var (sınırlı)
   Yer tutucular  : Yok (lisans metni sabittir)

   Özet:
   Perl topluluğunun lisansı. Telif hakkı sahibine paketin 'standart sürümü'
   üzerinde denetim bırakır; değiştirilmiş sürümlerin açıkça işaretlenmesini
   ister. GPL uyumludur.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      # SPDX-License-Identifier: Artistic-2.0
      # Copyright (c) 2025 Ada Yılmaz
      # This is free software; you can redistribute it and/or modify it
      # under the terms of the Artistic License 2.0.

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu paket Artistic License 2.0 koşullarıyla dağıtılmaktadır.


------------------------------------------------------------------------------
  [07]  Beerware License
------------------------------------------------------------------------------

   Dosya          : Beerware.txt
   SPDX kimliği   : Beerware
   Tür            : İzin verici (mizahi)
   Copyleft       : Yok
   Patent hükmü   : Yok
   Yer tutucular  : [COPYRIGHT HOLDER], [EMAIL]

   Özet:
   Poul-Henning Kamp tarafından yazılmış, tek paragraflık şakacı lisans. Tek
   şart bildirimi korumaktır. Kurumsal ve ticari kullanım için ÖNERİLMEZ;
   hukuki belirsizliği yüksektir.

   ► ÖRNEK 1 — Lisans dosyasındaki telif satırı (doldurulmuş):

      "THE BEER-WARE LICENSE" (Revision 42):

      Ada Yılmaz <ada@ornek.com> wrote this file. ...

      Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      /*
       * ----------------------------------------------------------------
       * "THE BEER-WARE LICENSE" (Revision 42):
       * Ada Yılmaz <ada@ornek.com> wrote this file. As long as you retain
       * this notice you can do whatever you want with this stuff. If we
       * meet some day, and you think this stuff is worth it, you can buy
       * me a beer in return.   Ada Yılmaz
       * ----------------------------------------------------------------
       */

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu kod Beerware lisansı ile dağıtılmaktadır.


------------------------------------------------------------------------------
  [08]  Blue Oak Model License 1.0.0
------------------------------------------------------------------------------

   Dosya          : BlueOak-1.0.0.txt
   SPDX kimliği   : BlueOak-1.0.0
   Tür            : İzin verici (permissive)
   Copyleft       : Yok
   Patent hükmü   : Var
   Yer tutucular  : Yok (lisans metni sabittir)

   Özet:
   Avukatlar tarafından sade, anlaşılır İngilizce ile yazılmış modern izin
   verici lisans. MIT'in belirsizliklerini (patent, katkıcı tanımı) giderir ve
   30 günlük ihlal düzeltme süresi tanır.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      // SPDX-License-Identifier: BlueOak-1.0.0
      // Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje Blue Oak Model License 1.0.0 ile lisanslanmıştır.
      https://blueoakcouncil.org/license/1.0.0


------------------------------------------------------------------------------
  [09]  BSD 2-Clause "Simplified" License
------------------------------------------------------------------------------

   Dosya          : BSD-2-Clause.txt
   SPDX kimliği   : BSD-2-Clause
   Tür            : İzin verici (permissive)
   Copyleft       : Yok
   Patent hükmü   : Yok
   Yer tutucular  : [YEAR], [COPYRIGHT HOLDER]

   Özet:
   MIT ile pratikte eşdeğer, iki maddelik klasik BSD lisansı: telif
   bildirimini kaynak ve ikili dağıtımda koruma şartı. 'FreeBSD License'
   olarak da bilinir.

   ► ÖRNEK 1 — Lisans dosyasındaki telif satırı (doldurulmuş):

      Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      // SPDX-License-Identifier: BSD-2-Clause
      // Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje BSD 2-Clause Lisansı ile lisanslanmıştır.


------------------------------------------------------------------------------
  [10]  BSD 3-Clause "New" or "Revised" License
------------------------------------------------------------------------------

   Dosya          : BSD-3-Clause.txt
   SPDX kimliği   : BSD-3-Clause
   Tür            : İzin verici (permissive)
   Copyleft       : Yok
   Patent hükmü   : Yok
   Yer tutucular  : [YEAR], [COPYRIGHT HOLDER]

   Özet:
   BSD-2-Clause'a 'onay/tanıtım için ismi kullanma yasağı' (no-endorsement)
   maddesi eklenmiş hâli. Marka karışıklığını önlemek isteyen kurumlar için
   MIT'e iyi bir alternatiftir.

   ► ÖRNEK 1 — Lisans dosyasındaki telif satırı (doldurulmuş):

      Copyright (c) 2025 Örnek Yazılım A.Ş. All rights reserved.

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      // SPDX-License-Identifier: BSD-3-Clause
      // Copyright (c) 2025 Örnek Yazılım A.Ş. All rights reserved.

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje BSD 3-Clause Lisansı ile lisanslanmıştır. Örnek Yazılım A.Ş.
      adı, türetilmiş ürünlerin tanıtımında yazılı izin olmadan kullanılamaz.


------------------------------------------------------------------------------
  [11]  BSD 4-Clause "Original" License
------------------------------------------------------------------------------

   Dosya          : BSD-4-Clause.txt
   SPDX kimliği   : BSD-4-Clause
   Tür            : İzin verici (reklam koşullu)
   Copyleft       : Yok
   Patent hükmü   : Yok
   Yer tutucular  : [YEAR], [COPYRIGHT HOLDER], [ORGANIZATION]

   Özet:
   Orijinal BSD lisansı. Meşhur 'reklam maddesi' (advertising clause)
   nedeniyle GPL ile UYUMSUZDUR ve yeni projeler için ÖNERİLMEZ. Bunun yerine
   BSD-3-Clause kullanın.

   ► ÖRNEK 1 — Lisans dosyasındaki telif satırı (doldurulmuş):

      Copyright (c) 2025 Örnek Yazılım A.Ş. All rights reserved.

      3. ... This product includes software developed by Örnek Yazılım A.Ş.

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      /* SPDX-License-Identifier: BSD-4-Clause */
      /* Copyright (c) 2025 Örnek Yazılım A.Ş. All rights reserved. */

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu ürün Örnek Yazılım A.Ş. tarafından geliştirilen yazılım içerir.
      UYARI: Bu lisans GPL ile uyumsuzdur.


------------------------------------------------------------------------------
  [12]  Boost Software License 1.0
------------------------------------------------------------------------------

   Dosya          : BSL-1.0.txt
   SPDX kimliği   : BSL-1.0
   Tür            : İzin verici (permissive)
   Copyleft       : Yok
   Patent hükmü   : Yok
   Yer tutucular  : Yok (lisans metni sabittir)

   Özet:
   C++ Boost kütüphanelerinin lisansı. Önemli farkı: ikili (binary) dağıtımda
   telif bildirimini tekrarlama zorunluluğu YOKTUR. Yalnızca başlıktan oluşan
   (header-only) kütüphaneler için idealdir.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      //          Copyright Ada Yılmaz 2025.
      // Distributed under the Boost Software License, Version 1.0.
      //    (See accompanying file LICENSE_1_0.txt or copy at
      //          https://www.boost.org/LICENSE_1_0.txt)

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu kütüphane Boost Software License 1.0 ile dağıtılmaktadır.


------------------------------------------------------------------------------
  [13]  Creative Commons Attribution 4.0 International
------------------------------------------------------------------------------

   Dosya          : CC-BY-4.0.txt
   SPDX kimliği   : CC-BY-4.0
   Tür            : İçerik lisansı (yazılım için önerilmez)
   Copyleft       : Yok
   Patent hükmü   : Yok (açıkça hariç)
   Yer tutucular  : Yok (lisans metni sabittir)

   Özet:
   Metin, görsel, ses, video ve dokümantasyon için standart lisans. Atıf
   verildiği sürece ticari kullanım dâhil her şeye izin verir. Kaynak kodu
   için UYGUN DEĞİLDİR (patent hükmü yoktur).

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      <a rel="license" href="https://creativecommons.org/licenses/by/4.0/">
        CC BY 4.0
      </a>

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      "Örnek Kılavuz" © 2025 Ada Yılmaz, CC BY 4.0 ile lisanslanmıştır.
      Lisans metni: https://creativecommons.org/licenses/by/4.0/


------------------------------------------------------------------------------
  [14]  Creative Commons Attribution-NonCommercial 4.0 International
------------------------------------------------------------------------------

   Dosya          : CC-BY-NC-4.0.txt
   SPDX kimliği   : CC-BY-NC-4.0
   Tür            : İçerik lisansı (özgür DEĞİL)
   Copyleft       : Yok
   Patent hükmü   : Yok
   Yer tutucular  : Yok (lisans metni sabittir)

   Özet:
   Atıf + ticari olmayan kullanım. Ticari kullanımı yasakladığı için açık
   kaynak/özgür kültür tanımına GİRMEZ. 'Ticari' tanımı belirsiz olduğundan
   kullanım öncesi dikkatle değerlendirin.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      <a rel="license" href="https://creativecommons.org/licenses/by-nc/4.0/">
        CC BY-NC 4.0
      </a>

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      "Örnek Kılavuz" © 2025 Ada Yılmaz, CC BY-NC 4.0 ile lisanslanmıştır.
      Ticari kullanım için izin gereklidir: ada@ornek.com


------------------------------------------------------------------------------
  [15]  Creative Commons Attribution-NonCommercial-NoDerivatives 4.0
        International
------------------------------------------------------------------------------

   Dosya          : CC-BY-NC-ND-4.0.txt
   SPDX kimliği   : CC-BY-NC-ND-4.0
   Tür            : İçerik lisansı (en kısıtlayıcı CC)
   Copyleft       : Yok
   Patent hükmü   : Yok
   Yer tutucular  : Yok (lisans metni sabittir)

   Özet:
   Atıf + ticari olmayan + türev üretilemez. CC ailesinin en kısıtlayıcı
   üyesidir: eseri yalnızca değiştirmeden ve ticari olmayan amaçla
   paylaşabilirsiniz.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      <a rel="license"
         href="https://creativecommons.org/licenses/by-nc-nd/4.0/">
        CC BY-NC-ND 4.0
      </a>

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      "Örnek Kılavuz" © 2025 Ada Yılmaz, CC BY-NC-ND 4.0 ile
      lisanslanmıştır. Türev eser üretimi ve ticari kullanım yasaktır.


------------------------------------------------------------------------------
  [16]  Creative Commons Attribution-NonCommercial-ShareAlike 4.0
        International
------------------------------------------------------------------------------

   Dosya          : CC-BY-NC-SA-4.0.txt
   SPDX kimliği   : CC-BY-NC-SA-4.0
   Tür            : İçerik lisansı (özgür DEĞİL)
   Copyleft       : Var (share-alike)
   Patent hükmü   : Yok
   Yer tutucular  : Yok (lisans metni sabittir)

   Özet:
   Atıf + ticari olmayan + aynı lisansla paylaşma. Türev eserler aynı lisansla
   dağıtılmalıdır. Ticari kısıtlama nedeniyle özgür kültür tanımına girmez.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      <a rel="license"
         href="https://creativecommons.org/licenses/by-nc-sa/4.0/">
        CC BY-NC-SA 4.0
      </a>

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      "Örnek Kılavuz" © 2025 Ada Yılmaz, CC BY-NC-SA 4.0 ile
      lisanslanmıştır. Türev eserler aynı lisansla paylaşılmalıdır.


------------------------------------------------------------------------------
  [17]  Creative Commons Attribution-NoDerivatives 4.0 International
------------------------------------------------------------------------------

   Dosya          : CC-BY-ND-4.0.txt
   SPDX kimliği   : CC-BY-ND-4.0
   Tür            : İçerik lisansı
   Copyleft       : Yok
   Patent hükmü   : Yok
   Yer tutucular  : Yok (lisans metni sabittir)

   Özet:
   Atıf + türev üretilemez. Ticari kullanıma izin verir, ancak eserin
   değiştirilmiş hâli dağıtılamaz. Resmî bildiriler, standart metinleri ve
   bütünlüğü korunması gereken belgeler için uygundur.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      <a rel="license" href="https://creativecommons.org/licenses/by-nd/4.0/">
        CC BY-ND 4.0
      </a>

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      "Örnek Bildiri" © 2025 Ada Yılmaz, CC BY-ND 4.0 ile lisanslanmıştır.
      Metin değiştirilmeden paylaşılmalıdır.


------------------------------------------------------------------------------
  [18]  Creative Commons Attribution-ShareAlike 4.0 International
------------------------------------------------------------------------------

   Dosya          : CC-BY-SA-4.0.txt
   SPDX kimliği   : CC-BY-SA-4.0
   Tür            : İçerik lisansı (copyleft)
   Copyleft       : Var (share-alike)
   Patent hükmü   : Yok
   Yer tutucular  : Yok (lisans metni sabittir)

   Özet:
   Atıf + aynı lisansla paylaşma. Vikipedi ve Stack Overflow'un lisansı.
   GPL-3.0 ile tek yönlü uyumludur. Dokümantasyon ve wiki içerikleri için
   yaygın tercihtir.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      <a rel="license" href="https://creativecommons.org/licenses/by-sa/4.0/">
        CC BY-SA 4.0
      </a>

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      "Örnek Kılavuz" © 2025 Ada Yılmaz, CC BY-SA 4.0 ile lisanslanmıştır.
      Türev eserler aynı lisansla paylaşılmalıdır.


------------------------------------------------------------------------------
  [19]  Creative Commons Zero v1.0 Universal
------------------------------------------------------------------------------

   Dosya          : CC0-1.0.txt
   SPDX kimliği   : CC0-1.0
   Tür            : Kamu malı ithafı
   Copyleft       : Yok
   Patent hükmü   : Yok (açıkça hariç)
   Yer tutucular  : Yok (lisans metni sabittir)

   Özet:
   Eseri mümkün olan en geniş ölçüde kamu malına bırakır; bunun mümkün
   olmadığı hukuk düzenlerinde koşulsuz bir lisans olarak çalışır. Veri
   kümeleri ve içerik için idealdir; patent hakkı vermez.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      (Telif satırı gerekmez — hak sahibi haklarından feragat eder.)

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      // SPDX-License-Identifier: CC0-1.0
      // Bu esere ilişkin tüm telif hakları CC0 1.0 ile kamu malına
      // bırakılmıştır.

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Ada Yılmaz, ilgili yasaların izin verdiği ölçüde bu esere ilişkin tüm
      telif ve komşu haklarından CC0 1.0 Universal ile feragat etmiştir.
      https://creativecommons.org/publicdomain/zero/1.0/


------------------------------------------------------------------------------
  [20]  Common Development and Distribution License 1.0
------------------------------------------------------------------------------

   Dosya          : CDDL-1.0.txt
   SPDX kimliği   : CDDL-1.0
   Tür            : Zayıf copyleft (dosya bazlı)
   Copyleft       : Zayıf (dosya bazlı)
   Patent hükmü   : Var
   Yer tutucular  : Yok (lisans metni sabittir; Exhibit A doldurulur)

   Özet:
   Sun Microsystems'in MPL-1.1 temelli lisansı (OpenSolaris, NetBeans).
   Copyleft yalnızca değiştirilen dosyalar düzeyinde işler. GPL ile UYUMSUZ
   kabul edilir.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Örnek Yazılım A.Ş.

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      /*
       * The contents of this file are subject to the terms of the Common
       * Development and Distribution License (the "License"). You may not use
       * this file except in compliance with the License.
       *
       * You can obtain a copy of the license at LICENSE.txt. See the License
       * for the specific language governing permissions and limitations under
       * the License.
       *
       * Copyright (c) 2025 Örnek Yazılım A.Ş. All rights reserved.
       */

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje CDDL 1.0 ile lisanslanmıştır. Değiştirdiğiniz dosyaları aynı
      lisansla yayımlamalısınız.


------------------------------------------------------------------------------
  [21]  CeCILL Free Software License Agreement v2.1
------------------------------------------------------------------------------

   Dosya          : CECILL-2.1.txt
   SPDX kimliği   : CECILL-2.1
   Tür            : Güçlü copyleft (Fransız hukuku)
   Copyleft       : Güçlü
   Patent hükmü   : Var
   Yer tutucular  : Yok (lisans metni sabittir)

   Özet:
   Fransız kamu araştırma kurumlarınca (CEA, CNRS, INRIA) hazırlanmış, Fransız
   hukukuna uyarlanmış GPL uyumlu lisans. Kıta Avrupası hukuk sistemlerinde
   geçerliliği daha güvenlidir.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      /*
       * Copyright (c) 2025 Ada Yılmaz
       *
       * This software is governed by the CeCILL license under French law and
       * abiding by the rules of distribution of free software. You can use,
       * modify and/or redistribute the software under the terms of the CeCILL
       * license as circulated by CEA, CNRS and INRIA at the following URL:
       * "http://www.cecill.info".
       */

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu yazılım Fransız hukukuna tabi CeCILL v2.1 lisansı ile
      dağıtılmaktadır. http://www.cecill.info


------------------------------------------------------------------------------
  [22]  Educational Community License v2.0
------------------------------------------------------------------------------

   Dosya          : ECL-2.0.txt
   SPDX kimliği   : ECL-2.0
   Tür            : İzin verici (permissive)
   Copyleft       : Yok
   Patent hükmü   : Var (genişletilmiş)
   Yer tutucular  : Yok (lisans metni sabittir)

   Özet:
   Apache-2.0'ın eğitim kurumları için uyarlanmış türevi. Patent hibesinin
   kapsamı, üniversitelerin farklı bölümlerinde bağımsız geliştirilen
   patentleri kapsamayacak şekilde daraltılmıştır.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright 2025 Örnek Üniversitesi

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      Copyright 2025 Örnek Üniversitesi

      Licensed under the Educational Community License, Version 2.0 (the
      "License"); you may not use this file except in compliance with the
      License. You may obtain a copy of the License at

          http://opensource.org/licenses/ECL-2.0

      Unless required by applicable law or agreed to in writing, software
      distributed under the License is distributed on an "AS IS" BASIS,
      WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje Educational Community License v2.0 ile lisanslanmıştır.


------------------------------------------------------------------------------
  [23]  Eclipse Public License 1.0
------------------------------------------------------------------------------

   Dosya          : EPL-1.0.txt
   SPDX kimliği   : EPL-1.0
   Tür            : Zayıf copyleft
   Copyleft       : Zayıf
   Patent hükmü   : Var
   Yer tutucular  : Yok (lisans metni sabittir)

   Özet:
   Eclipse vakfının ilk lisansı. Ticari dağıtımcılara yönelik tazminat
   (indemnification) hükümleri içerir. GPL ile uyumsuzdur; yeni projelerde
   EPL-2.0 tercih edilmelidir.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Örnek Yazılım A.Ş.

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      /*******************************************************************
       * Copyright (c) 2025 Örnek Yazılım A.Ş.
       * All rights reserved. This program and the accompanying materials
       * are made available under the terms of the Eclipse Public License v1.0
       * which accompanies this distribution, and is available at
       * http://www.eclipse.org/legal/epl-v10.html
       *******************************************************************/

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje Eclipse Public License 1.0 ile lisanslanmıştır.


------------------------------------------------------------------------------
  [24]  Eclipse Public License 2.0
------------------------------------------------------------------------------

   Dosya          : EPL-2.0.txt
   SPDX kimliği   : EPL-2.0
   Tür            : Zayıf copyleft
   Copyleft       : Zayıf (dosya bazlı)
   Patent hükmü   : Var
   Yer tutucular  : Yok (lisans metni sabittir; 'Secondary Licenses' notu
                    eklenebilir)

   Özet:
   EPL-1.0'ın modernleştirilmiş hâli. İsteğe bağlı 'Secondary License' hükmü
   sayesinde GPL-2.0+ ile birlikte ikili lisanslama yapılabilir. Eclipse,
   Jakarta EE ve Clojure ekosisteminin lisansıdır.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Örnek Yazılım A.Ş.

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      /*******************************************************************
       * Copyright (c) 2025 Örnek Yazılım A.Ş.
       *
       * This program and the accompanying materials are made available under
       * the terms of the Eclipse Public License 2.0 which is available at
       * http://www.eclipse.org/legal/epl-2.0
       *
       * SPDX-License-Identifier: EPL-2.0
       *******************************************************************/

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje Eclipse Public License 2.0 ile lisanslanmıştır.
      GPL-2.0 uyumluluğu isteniyorsa şu satır eklenir:
        SPDX-License-Identifier: EPL-2.0 OR GPL-2.0-or-later


------------------------------------------------------------------------------
  [25]  European Union Public Licence v1.2
------------------------------------------------------------------------------

   Dosya          : EUPL-1.2.txt
   SPDX kimliği   : EUPL-1.2
   Tür            : Güçlü copyleft
   Copyleft       : Güçlü (+ ağ kullanımı)
   Patent hükmü   : Var
   Yer tutucular  : Yok (lisans metni sabittir)

   Özet:
   Avrupa Komisyonu'nun lisansı; AB'nin 23 resmî dilinde eşit hukuki
   geçerliliğe sahip tek açık kaynak lisansıdır. Ek olarak GPL, AGPL, MPL, EPL
   gibi lisanslara geçişe izin veren bir uyumluluk listesi içerir.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Örnek Yazılım A.Ş.

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      /*
       * Copyright (c) 2025 Örnek Yazılım A.Ş.
       *
       * Licensed under the EUPL, Version 1.2 or - as soon as they will be
       * approved by the European Commission - subsequent versions of the EUPL
       * (the "Licence"); You may not use this work except in compliance with
       * the Licence. You may obtain a copy of the Licence at:
       *
       *   https://joinup.ec.europa.eu/software/page/eupl
       *
       * SPDX-License-Identifier: EUPL-1.2
       */

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje EUPL v1.2 ile lisanslanmıştır. Lisans, AB'nin 23 resmî
      dilinde eşit geçerliliğe sahiptir.


------------------------------------------------------------------------------
  [26]  GNU General Public License v2.0
------------------------------------------------------------------------------

   Dosya          : GPL-2.0.txt
   SPDX kimliği   : GPL-2.0
   Tür            : Güçlü copyleft
   Copyleft       : Güçlü
   Patent hükmü   : Örtük (açık madde yok)
   Yer tutucular  : Yok (lisans metni sabittir; bildirim ayrıca eklenir)

   Özet:
   Linux çekirdeğinin lisansı. Türev eserlerin tamamının aynı lisansla ve
   kaynak koduyla dağıtılmasını zorunlu kılar. Açık patent maddesi yoktur;
   Apache-2.0 ile UYUMSUZDUR.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (C) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      Örnek Proje - kısa açıklama
      Copyright (C) 2025 Ada Yılmaz

      This program is free software; you can redistribute it and/or modify
      it under the terms of the GNU General Public License as published by
      the Free Software Foundation; either version 2 of the License, or
      (at your option) any later version.

      This program is distributed in the hope that it will be useful,
      but WITHOUT ANY WARRANTY; without even the implied warranty of
      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
      GNU General Public License for more details.

      You should have received a copy of the GNU General Public License along
      with this program; if not, write to the Free Software Foundation, Inc.,
      51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje GNU GPL v2 ile lisanslanmıştır.
      Yalnızca v2:            SPDX-License-Identifier: GPL-2.0-only
      v2 veya sonrası:        SPDX-License-Identifier: GPL-2.0-or-later


------------------------------------------------------------------------------
  [27]  GNU General Public License v3.0
------------------------------------------------------------------------------

   Dosya          : GPL-3.0.txt
   SPDX kimliği   : GPL-3.0
   Tür            : Güçlü copyleft
   Copyleft       : Güçlü
   Patent hükmü   : Var
   Yer tutucular  : Yok (lisans metni sabittir; bildirim ayrıca eklenir)

   Özet:
   GPL'in modern sürümü: açık patent hibesi, donanım kilidi (tivoization)
   yasağı ve DRM karşıtı hükümler içerir. Apache-2.0 ile uyumludur,
   GPL-2.0-only ile değildir.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (C) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      Örnek Proje - kısa açıklama
      Copyright (C) 2025 Ada Yılmaz

      This program is free software: you can redistribute it and/or modify
      it under the terms of the GNU General Public License as published by
      the Free Software Foundation, either version 3 of the License, or
      (at your option) any later version.

      This program is distributed in the hope that it will be useful,
      but WITHOUT ANY WARRANTY; without even the implied warranty of
      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
      GNU General Public License for more details.

      You should have received a copy of the GNU General Public License
      along with this program.  If not, see <https://www.gnu.org/licenses/>.

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje GNU GPL v3 ile lisanslanmıştır.
      Yalnızca v3:            SPDX-License-Identifier: GPL-3.0-only
      v3 veya sonrası:        SPDX-License-Identifier: GPL-3.0-or-later


------------------------------------------------------------------------------
  [28]  ISC License
------------------------------------------------------------------------------

   Dosya          : ISC.txt
   SPDX kimliği   : ISC
   Tür            : İzin verici (permissive)
   Copyleft       : Yok
   Patent hükmü   : Yok
   Yer tutucular  : [YEAR], [COPYRIGHT HOLDER]

   Özet:
   MIT ve BSD-2-Clause ile hukuken eşdeğer, ancak Berne Sözleşmesi sonrasında
   gereksiz hâle gelen ifadelerden arındırılmış en kısa biçim. OpenBSD ve npm
   ekosisteminin varsayılan tercihidir.

   ► ÖRNEK 1 — Lisans dosyasındaki telif satırı (doldurulmuş):

      Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      // SPDX-License-Identifier: ISC
      // Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje ISC Lisansı ile lisanslanmıştır.


------------------------------------------------------------------------------
  [29]  GNU Lesser General Public License v2.1
------------------------------------------------------------------------------

   Dosya          : LGPL-2.1.txt
   SPDX kimliği   : LGPL-2.1
   Tür            : Zayıf copyleft (kütüphane)
   Copyleft       : Zayıf
   Patent hükmü   : Örtük
   Yer tutucular  : Yok (lisans metni sabittir; bildirim ayrıca eklenir)

   Özet:
   Kütüphaneler için tasarlanmıştır: kütüphaneye yalnızca bağlanan (link)
   kapalı kaynaklı programlar copyleft kapsamına GİRMEZ, ancak kütüphanenin
   kendisinde yapılan değişiklikler paylaşılmalıdır.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (C) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      Örnek Kütüphane - kısa açıklama
      Copyright (C) 2025 Ada Yılmaz

      This library is free software; you can redistribute it and/or modify it
      under the terms of the GNU Lesser General Public License as published by
      the Free Software Foundation; either version 2.1 of the License, or
      (at your option) any later version.

      This library is distributed in the hope that it will be useful, but
      WITHOUT ANY WARRANTY; without even the implied warranty of
      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
      Lesser General Public License for more details.

      You should have received a copy of the GNU Lesser General Public License
      along with this library; if not, write to the Free Software Foundation,
      Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu kütüphane GNU LGPL v2.1 ile lisanslanmıştır.
      SPDX-License-Identifier: LGPL-2.1-or-later


------------------------------------------------------------------------------
  [30]  GNU Lesser General Public License v3.0
------------------------------------------------------------------------------

   Dosya          : LGPL-3.0.txt
   SPDX kimliği   : LGPL-3.0
   Tür            : Zayıf copyleft (kütüphane)
   Copyleft       : Zayıf
   Patent hükmü   : Var
   Yer tutucular  : Yok (lisans metni sabittir; bildirim ayrıca eklenir)

   Özet:
   GPL-3.0'a ek izinler getiren kütüphane lisansı. Bu nedenle dosya, önce
   LGPL-3.0 ek izinlerini, ardından atıfta bulunduğu GPL-3.0 metninin tamamını
   içerir — ikisi birlikte tek bir lisansı oluşturur.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (C) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      Örnek Kütüphane - kısa açıklama
      Copyright (C) 2025 Ada Yılmaz

      This library is free software: you can redistribute it and/or modify it
      under the terms of the GNU Lesser General Public License as published by
      the Free Software Foundation, either version 3 of the License, or
      (at your option) any later version.

      This library is distributed in the hope that it will be useful, but
      WITHOUT ANY WARRANTY; without even the implied warranty of
      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
      Lesser General Public License for more details.

      You should have received a copy of the GNU Lesser General Public License
      along with this library.  If not, see <https://www.gnu.org/licenses/>.

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu kütüphane GNU LGPL v3 ile lisanslanmıştır.
      SPDX-License-Identifier: LGPL-3.0-or-later
      Not: Projelerde genellikle GPL-3.0 metni COPYING, LGPL-3.0 ek izinleri
      ise COPYING.LESSER dosyasına konur; buradaki dosya ikisini birleştirir.


------------------------------------------------------------------------------
  [31]  LaTeX Project Public License v1.3c
------------------------------------------------------------------------------

   Dosya          : LPPL-1.3c.txt
   SPDX kimliği   : LPPL-1.3c
   Tür            : Zayıf copyleft (belge dizgi)
   Copyleft       : Zayıf
   Patent hükmü   : Yok
   Yer tutucular  : Yok (lisans metni sabittir; dosyaya 'maintainer' bilgisi
                    eklenir)

   Özet:
   LaTeX paketlerinin lisansı. Ayırt edici koşulu, değiştirilen dosyanın
   ADININ da değiştirilmesi zorunluluğudur; böylece aynı ada sahip paketlerin
   farklı davranması engellenir.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      %% ornekpaket.sty
      %% Copyright 2025 Ada Yılmaz
      %
      % This work may be distributed and/or modified under the conditions of
      % the LaTeX Project Public License, either version 1.3c of this license
      % or (at your option) any later version.
      % The latest version of this license is in
      %   http://www.latex-project.org/lppl.txt
      %
      % This work has the LPPL maintenance status 'maintained'.
      % The Current Maintainer of this work is Ada Yılmaz.

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu paket LPPL v1.3c ile dağıtılmaktadır. Değiştirilmiş sürümler farklı
      bir dosya adıyla yayımlanmalıdır.


------------------------------------------------------------------------------
  [32]  MIT No Attribution License
------------------------------------------------------------------------------

   Dosya          : MIT-0.txt
   SPDX kimliği   : MIT-0
   Tür            : İzin verici (permissive)
   Copyleft       : Yok
   Patent hükmü   : Yok
   Yer tutucular  : [YEAR], [COPYRIGHT HOLDER]

   Özet:
   MIT'in atıf şartı kaldırılmış hâli (AWS tarafından yayımlandı). Kullanıcı
   telif bildirimini korumak zorunda değildir. Örnek kod ve kod parçacıkları
   için idealdir.

   ► ÖRNEK 1 — Lisans dosyasındaki telif satırı (doldurulmuş):

      Copyright 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      // SPDX-License-Identifier: MIT-0
      // Copyright 2025 Ada Yılmaz

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu örnek kod MIT-0 ile lisanslanmıştır; atıf vermeden serbestçe
      kullanabilirsiniz.


------------------------------------------------------------------------------
  [33]  MIT License
------------------------------------------------------------------------------

   Dosya          : MIT.txt
   SPDX kimliği   : MIT
   Tür            : İzin verici (permissive)
   Copyleft       : Yok
   Patent hükmü   : Yok (örtük)
   Yer tutucular  : [YEAR], [COPYRIGHT HOLDER]

   Özet:
   Dünyada en yaygın kullanılan açık kaynak lisansı. Tek şartı telif bildirimi
   ile lisans metnini kopyalarda korumaktır. Kısa, anlaşılır ve neredeyse tüm
   lisanslarla uyumludur; açık patent hibesi içermez.

   ► ÖRNEK 1 — Lisans dosyasındaki telif satırı (doldurulmuş):

      Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      // SPDX-License-Identifier: MIT
      // Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje MIT Lisansı ile lisanslanmıştır. Ayrıntılar için LICENSE
      dosyasına bakınız.


------------------------------------------------------------------------------
  [34]  Mozilla Public License 2.0
------------------------------------------------------------------------------

   Dosya          : MPL-2.0.txt
   SPDX kimliği   : MPL-2.0
   Tür            : Zayıf copyleft (dosya bazlı)
   Copyleft       : Zayıf (dosya bazlı)
   Patent hükmü   : Var
   Yer tutucular  : Yok (lisans metni sabittir; Exhibit A kaynak dosyalara
                    eklenir)

   Özet:
   Copyleft'i tek tek DOSYA düzeyinde uygular: MPL'li dosyalarda yapılan
   değişiklikler paylaşılmalı, ancak aynı projedeki diğer dosyalar kapalı
   kalabilir. GPL/LGPL/AGPL ile açıkça uyumludur.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Örnek Yazılım A.Ş.

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      /* This Source Code Form is subject to the terms of the Mozilla Public
       * License, v. 2.0. If a copy of the MPL was not distributed with this
       * file, You can obtain one at https://mozilla.org/MPL/2.0/. */

      /* Copyright (c) 2025 Örnek Yazılım A.Ş. */

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje Mozilla Public License 2.0 ile lisanslanmıştır. Yukarıdaki
      Exhibit A bildirimi her kaynak dosyanın başına eklenmelidir.


------------------------------------------------------------------------------
  [35]  Microsoft Public License
------------------------------------------------------------------------------

   Dosya          : MS-PL.txt
   SPDX kimliği   : MS-PL
   Tür            : İzin verici (permissive)
   Copyleft       : Yok
   Patent hükmü   : Var
   Yer tutucular  : Yok (lisans metni sabittir)

   Özet:
   Microsoft'un kısa, izin verici lisansı. Patent hibesi içerir; ancak türev
   eserler ikili (binary) olarak dağıtılırken MS-PL koşullarına uyulmasını
   ister. GPL ile uyumsuzdur.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Örnek Yazılım A.Ş.

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      // SPDX-License-Identifier: MS-PL
      // Copyright (c) 2025 Örnek Yazılım A.Ş.
      // Licensed under the Microsoft Public License (Ms-PL).

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje Microsoft Public License (Ms-PL) ile lisanslanmıştır.


------------------------------------------------------------------------------
  [36]  Microsoft Reciprocal License
------------------------------------------------------------------------------

   Dosya          : MS-RL.txt
   SPDX kimliği   : MS-RL
   Tür            : Zayıf copyleft (dosya bazlı)
   Copyleft       : Zayıf (dosya bazlı)
   Patent hükmü   : Var
   Yer tutucular  : Yok (lisans metni sabittir)

   Özet:
   MS-PL'in karşılıklılık (reciprocal) eklenmiş sürümü. MS-RL'li kaynak
   dosyalardan türetilen dosyalar aynı lisansla paylaşılmalı, projeye eklenen
   yeni dosyalar ise serbest kalabilir.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Örnek Yazılım A.Ş.

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      // SPDX-License-Identifier: MS-RL
      // Copyright (c) 2025 Örnek Yazılım A.Ş.
      // Licensed under the Microsoft Reciprocal License (Ms-RL).

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje Microsoft Reciprocal License (Ms-RL) ile lisanslanmıştır.


------------------------------------------------------------------------------
  [37]  Mulan Permissive Software License v2
------------------------------------------------------------------------------

   Dosya          : MulanPSL-2.0.txt
   SPDX kimliği   : MulanPSL-2.0
   Tür            : İzin verici (permissive)
   Copyleft       : Yok
   Patent hükmü   : Var
   Yer tutucular  : [YEAR], [COPYRIGHT HOLDER], [SOFTWARE NAME]  (yalnızca
                    ek/bildirim bölümünde)

   Özet:
   Çin'de geliştirilen, Apache-2.0'a yakın izin verici lisans. Çince ve
   İngilizce metinleri eşit hukuki geçerliliğe sahiptir; anlaşmazlık hâlinde
   Çince metin esas alınır.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Örnek Yazılım A.Ş.
      OrnekLib is licensed under Mulan PSL v2.

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      /*
       * Copyright (c) 2025 Örnek Yazılım A.Ş.
       * OrnekLib is licensed under Mulan PSL v2.
       * You can use this software according to the terms and conditions of
       * the Mulan PSL v2.
       * You may obtain a copy of Mulan PSL v2 at:
       *          http://license.coscl.org.cn/MulanPSL2
       * THIS SOFTWARE IS PROVIDED ON AN "AS IS" BASIS, WITHOUT WARRANTIES OF
       * ANY KIND, EITHER EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO
       * NON-INFRINGEMENT, MERCHANTABILITY OR FIT FOR A PARTICULAR PURPOSE.
       * See the Mulan PSL v2 for more details.
       */

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje Mulan PSL v2 ile lisanslanmıştır.
      http://license.coscl.org.cn/MulanPSL2


------------------------------------------------------------------------------
  [38]  University of Illinois/NCSA Open Source License
------------------------------------------------------------------------------

   Dosya          : NCSA.txt
   SPDX kimliği   : NCSA
   Tür            : İzin verici (permissive)
   Copyleft       : Yok
   Patent hükmü   : Yok
   Yer tutucular  : [YEAR], [ORGANIZATION], [DEVELOPMENT GROUP],
                    [INSTITUTION], [PROJECT URL]

   Özet:
   MIT'in izin dili ile BSD-3-Clause'un koşullarını birleştiren lisans. LLVM
   projesinin uzun yıllar kullandığı lisanstır (LLVM sonradan Apache-2.0 WITH
   LLVM-exception'a geçmiştir).

   ► ÖRNEK 1 — Lisans dosyasındaki telif satırı (doldurulmuş):

      Copyright (c) 2025 Örnek Üniversitesi. All rights reserved.

      Developed by: Derleyici Araştırma Grubu, Örnek Üniversitesi,
                    https://ornek.edu.tr/derleyici

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      //===-- ornek.cpp --------------------------------------------===//
      //
      // SPDX-License-Identifier: NCSA
      // Copyright (c) 2025 Örnek Üniversitesi. All rights reserved.
      //
      //===----------------------------------------------------------===//

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje University of Illinois/NCSA Open Source License ile
      lisanslanmıştır.


------------------------------------------------------------------------------
  [39]  Open Data Commons Open Database License v1.0
------------------------------------------------------------------------------

   Dosya          : ODbL-1.0.txt
   SPDX kimliği   : ODbL-1.0
   Tür            : Veritabanı lisansı (copyleft)
   Copyleft       : Güçlü (share-alike)
   Patent hükmü   : Yok
   Yer tutucular  : Yok (lisans metni sabittir)

   Özet:
   Veritabanları ve veri kümeleri için tasarlanmış share-alike lisansı
   (OpenStreetMap'in lisansı). Türetilmiş veritabanları aynı lisansla
   paylaşılmalıdır. Yazılım kodu için UYGUN DEĞİLDİR.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Örnek Veri Derneği

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      # SPDX-License-Identifier: ODbL-1.0
      # Bu veri kümesi © 2025 Örnek Veri Derneği katkıcılarına aittir ve
      # Open Database License (ODbL) v1.0 ile kullanıma sunulmuştur.

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      © Örnek Veri Derneği katkıcıları, ODbL 1.0. Bu veriyi kullandığınızda
      kaynak göstermeli ve türetilmiş veritabanlarını aynı lisansla
      paylaşmalısınız. https://opendatacommons.org/licenses/odbl/1-0/


------------------------------------------------------------------------------
  [40]  SIL Open Font License 1.1
------------------------------------------------------------------------------

   Dosya          : OFL-1.1.txt
   SPDX kimliği   : OFL-1.1
   Tür            : Yazı tipi lisansı (copyleft)
   Copyleft       : Var (yazı tipine özgü)
   Patent hükmü   : Yok
   Yer tutucular  : [YEAR], [COPYRIGHT HOLDER], [EMAIL], [RESERVED FONT NAME]

   Özet:
   Yazı tipleri (font) için standart lisans. Yazı tipini belgelere gömmeye ve
   değiştirmeye izin verir; ancak 'Reserved Font Name' olarak belirlenen ad,
   değiştirilmiş sürümlerde kullanılamaz.

   ► ÖRNEK 1 — Lisans dosyasındaki telif satırı (doldurulmuş):

      Copyright (c) 2025 Ada Yılmaz <ada@ornek.com>,
      with Reserved Font Name "OrnekSans".

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      /* SPDX-License-Identifier: OFL-1.1 */
      /* Copyright (c) 2025 Ada Yılmaz, with Reserved Font Name */
      /* "OrnekSans". Licensed under the SIL Open Font License 1.1. */

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      OrnekSans yazı tipi, SIL Open Font License 1.1 ile lisanslanmıştır.
      Değiştirilmiş sürümler "OrnekSans" adını taşıyamaz.


------------------------------------------------------------------------------
  [41]  Open Software License 3.0
------------------------------------------------------------------------------

   Dosya          : OSL-3.0.txt
   SPDX kimliği   : OSL-3.0
   Tür            : Güçlü copyleft
   Copyleft       : Güçlü (+ ağ kullanımı)
   Patent hükmü   : Var
   Yer tutucular  : Yok (lisans metni sabittir)

   Özet:
   Lawrence Rosen'in yazdığı, AGPL'e benzer şekilde ağ üzerinden 'External
   Deployment'ı dağıtım sayan güçlü copyleft lisansı. GPL ile uyumsuzdur; FSF
   tarafından önerilmez.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      // SPDX-License-Identifier: OSL-3.0
      // Copyright (c) 2025 Ada Yılmaz
      // Licensed under the Open Software License version 3.0

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje Open Software License 3.0 ile lisanslanmıştır. Yazılımı ağ
      üzerinden hizmet olarak sunmak da dağıtım sayılır.


------------------------------------------------------------------------------
  [42]  PostgreSQL License
------------------------------------------------------------------------------

   Dosya          : PostgreSQL.txt
   SPDX kimliği   : PostgreSQL
   Tür            : İzin verici (permissive)
   Copyleft       : Yok
   Patent hükmü   : Yok
   Yer tutucular  : [YEAR], [COPYRIGHT HOLDER]

   Özet:
   MIT/BSD ailesine çok yakın, PostgreSQL projesinin kullandığı sade izin
   verici lisans. Yazılı bir sözleşme olmaksızın ücretsiz kullanım, değiştirme
   ve dağıtım hakkı verir.

   ► ÖRNEK 1 — Lisans dosyasındaki telif satırı (doldurulmuş):

      Copyright (c) 2025 Örnek Yazılım A.Ş.

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      /* SPDX-License-Identifier: PostgreSQL */
      /* Copyright (c) 2025 Örnek Yazılım A.Ş. */

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje PostgreSQL Lisansı ile lisanslanmıştır.


------------------------------------------------------------------------------
  [43]  Tescilli Yazılım Lisans Sözleşmesi (Tüm Hakları Saklıdır)
------------------------------------------------------------------------------

   Dosya          : Proprietary.txt
   SPDX kimliği   : LicenseRef-Proprietary
   Tür            : Tescilli / kapalı kaynak
   Copyleft       : Yok
   Patent hükmü   : Yok (hak verilmez)
   Yer tutucular  : [YEAR], [COPYRIGHT HOLDER], [JURISDICTION], [EMAIL]

   Özet:
   Kapalı kaynak ticari yazılım için genel amaçlı bir sözleşme taslağıdır. OSI
   onaylı bir açık kaynak lisansı DEĞİLDİR ve resmî bir SPDX kimliği yoktur;
   SPDX'te 'LicenseRef-Proprietary' gibi özel bir ad kullanılır. Kullanmadan
   önce mutlaka bir hukukçuya danışılmalıdır.

   ► ÖRNEK 1 — Lisans dosyasındaki telif satırı (doldurulmuş):

      Copyright (c) 2025 Örnek Yazılım A.Ş. All rights reserved.

      9. GENERAL
         ... governed by the laws of Türkiye ...
         ... contact: legal@ornek.com

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      /*
       * Copyright (c) 2025 Örnek Yazılım A.Ş. All rights reserved.
       *
       * CONFIDENTIAL AND PROPRIETARY.
       * Unauthorized copying, distribution or use of this file, via any
       * medium, is strictly prohibited. See LICENSE.txt for the full
       * license agreement.
       *
       * SPDX-License-Identifier: LicenseRef-Proprietary
       */

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      © 2025 Örnek Yazılım A.Ş. Tüm hakları saklıdır. Bu yazılım tescilli
      olup yalnızca geçerli bir lisans sözleşmesi kapsamında kullanılabilir.


------------------------------------------------------------------------------
  [44]  Python Software Foundation License 2.0
------------------------------------------------------------------------------

   Dosya          : Python-2.0.txt
   SPDX kimliği   : Python-2.0
   Tür            : İzin verici (permissive)
   Copyleft       : Yok
   Patent hükmü   : Yok
   Yer tutucular  : Yok (lisans metni sabittir; PSF'ye özgü metindir)

   Özet:
   CPython yorumlayıcısının lisansı. GPL uyumlu, izin verici bir lisanstır;
   ancak metin doğrudan Python Software Foundation'a atıf yapar. Kendi
   projeniz için genellikle uygun DEĞİLDİR.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      Copyright (c) 2025 Python Software Foundation; All Rights Reserved

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      # SPDX-License-Identifier: Python-2.0
      # Bu dosya CPython kaynak ağacından türetilmiştir.
      # Copyright (c) 2025 Python Software Foundation; All Rights Reserved

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu bileşen Python Software Foundation License 2.0 kapsamındadır.
      UYARI: Bu metin PSF'ye özgüdür; kendi projeniz için MIT, BSD veya
      Apache-2.0 tercih edin.


------------------------------------------------------------------------------
  [45]  Ruby License
------------------------------------------------------------------------------

   Dosya          : Ruby.txt
   SPDX kimliği   : Ruby
   Tür            : Zayıf copyleft (ikili lisans)
   Copyleft       : Zayıf
   Patent hükmü   : Yok
   Yer tutucular  : [SOFTWARE NAME], [COPYRIGHT HOLDER], [EMAIL]

   Özet:
   Ruby dilinin lisansı. Kullanıcıya BSD-2-Clause ile bu lisans arasında seçim
   hakkı tanır. Değiştirilmiş ikili dosyaların ayırt edilebilir biçimde
   adlandırılmasını ister.

   ► ÖRNEK 1 — Lisans dosyasındaki telif satırı (doldurulmuş):

      OrnekGem is copyrighted free software by Ada Yılmaz
      <ada@ornek.com>. You can redistribute it and/or modify it under
      either the terms of the 2-clause BSD License, or the conditions below:

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      # SPDX-License-Identifier: Ruby OR BSD-2-Clause
      # Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje Ruby Lisansı veya BSD-2-Clause koşullarıyla (tercihinize
      göre) dağıtılmaktadır.


------------------------------------------------------------------------------
  [46]  Sleepycat License (Berkeley DB)
------------------------------------------------------------------------------

   Dosya          : Sleepycat.txt
   SPDX kimliği   : Sleepycat
   Tür            : Güçlü copyleft
   Copyleft       : Güçlü
   Patent hükmü   : Yok
   Yer tutucular  : [YEAR], [COPYRIGHT HOLDER]

   Özet:
   Berkeley DB'nin lisansı. BSD görünümlü olmasına rağmen GÜÇLÜ copyleft'tir:
   yazılımı kullanan uygulamanın tamamının kaynak kodunun sunulmasını zorunlu
   kılar. Ticari projelerde dikkatle kullanın.

   ► ÖRNEK 1 — Lisans dosyasındaki telif satırı (doldurulmuş):

      Copyright (c) 2025 Örnek Yazılım A.Ş. All rights reserved.

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      /* SPDX-License-Identifier: Sleepycat */
      /* Copyright (c) 2025 Örnek Yazılım A.Ş. All rights reserved. */

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje Sleepycat Lisansı ile lisanslanmıştır. Yazılımı kullanan
      uygulamaların kaynak kodu da yayımlanmak zorundadır.


------------------------------------------------------------------------------
  [47]  The Unlicense
------------------------------------------------------------------------------

   Dosya          : Unlicense.txt
   SPDX kimliği   : Unlicense
   Tür            : Kamu malı ithafı
   Copyleft       : Yok
   Patent hükmü   : Yok
   Yer tutucular  : Yok (lisans metni sabittir)

   Özet:
   Eseri kamu malına bırakma bildirimi. CC0'a benzer, ancak çok daha kısadır.
   Kamu malı kavramının tanınmadığı hukuk düzenlerinde geçerliliği
   tartışmalıdır; bu durumda 0BSD veya MIT-0 daha güvenlidir.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      (Telif satırı gerekmez — hak sahibi haklarından feragat eder.)

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      // SPDX-License-Identifier: Unlicense
      // This is free and unencumbered software released into the public
      // domain. For more information, see <https://unlicense.org/>

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu yazılım kamu malına bırakılmıştır (The Unlicense). Herhangi bir
      amaçla, koşulsuz olarak kullanabilirsiniz. https://unlicense.org/


------------------------------------------------------------------------------
  [48]  Vim License
------------------------------------------------------------------------------

   Dosya          : Vim.txt
   SPDX kimliği   : Vim
   Tür            : Hayırseverlik koşullu copyleft
   Copyleft       : Zayıf
   Patent hükmü   : Yok
   Yer tutucular  : Yok (metin Vim projesine özgüdür; olduğu gibi korunur)

   Özet:
   Vim editörünün kendine özgü lisansı. Değiştirilmiş sürümleri dağıtan
   kişinin, isteyen bakımcıya değişiklikleri iletmesini ister ve Uganda'daki
   çocuklara bağış yapmayı teşvik eden bir 'charityware' hükmü içerir.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      (Lisans metni Vim projesine özgüdür; telif satırı eklenmez.)

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      " SPDX-License-Identifier: Vim
      " Bu dosya Vim Lisansı kapsamındadır; ayrıntılar için :help license

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu bileşen Vim Lisansı kapsamındadır.
      UYARI: Metin Vim projesine ve bakımcısına doğrudan atıf yapar; kendi
      bağımsız projeniz için uygun değildir.


------------------------------------------------------------------------------
  [49]  Do What The F*ck You Want To Public License v2
------------------------------------------------------------------------------

   Dosya          : WTFPL.txt
   SPDX kimliği   : WTFPL
   Tür            : Kamu malına yakın (mizahi)
   Copyleft       : Yok
   Patent hükmü   : Yok
   Yer tutucular  : Yok (lisans metnindeki telif, lisans belgesinin kendisine
                    aittir)

   Özet:
   Tek maddelik, azami serbestlik tanıyan lisans. Kurumsal ortamlarda argo
   içeriği ve hukuki belirsizliği nedeniyle ÖNERİLMEZ; aynı etki için 0BSD,
   MIT-0 veya CC0 tercih edilmelidir.

   ► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):

      (Metindeki 'Copyright (C) 2004 Sam Hocevar' satırı lisans belgesinin
      kendi telifidir ve DEĞİŞTİRİLMEZ. Kendi telif satırınızı ayrıca
      ekleyebilirsiniz.)

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      // SPDX-License-Identifier: WTFPL
      // Copyright (c) 2025 Ada Yılmaz
      // This work is free. You can redistribute it and/or modify it under
      // the terms of the Do What The Fuck You Want To Public License,
      // Version 2, as published by Sam Hocevar. See LICENSE for details.

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje WTFPL v2 ile lisanslanmıştır.


------------------------------------------------------------------------------
  [50]  zlib License
------------------------------------------------------------------------------

   Dosya          : Zlib.txt
   SPDX kimliği   : Zlib
   Tür            : İzin verici (permissive)
   Copyleft       : Yok
   Patent hükmü   : Yok
   Yer tutucular  : [YEAR], [COPYRIGHT HOLDER]

   Özet:
   zlib ve libpng kütüphanelerinin lisansı. Kaynağın yanlış tanıtılmasını
   yasaklar ve değiştirilmiş sürümlerin açıkça işaretlenmesini ister; ikili
   dağıtımda bildirimi tekrarlama zorunluluğu yoktur.

   ► ÖRNEK 1 — Lisans dosyasındaki telif satırı (doldurulmuş):

      Copyright (c) 2025 Ada Yılmaz

   ► ÖRNEK 2 — Kaynak dosya başlığı / bildirim:

      /*
       * ornek.c -- kısa açıklama
       * Copyright (c) 2025 Ada Yılmaz
       *
       * This software is provided 'as-is', without any express or implied
       * warranty. In no event will the authors be held liable for any damages
       * arising from the use of this software. See LICENSE for details.
       *
       * SPDX-License-Identifier: Zlib
       */

   ► ÖRNEK 3 — Proje tanıtım metni (README) notu:

      Bu proje zlib Lisansı ile lisanslanmıştır.



==============================================================================
  6.  SIK YAPILAN HATALAR
==============================================================================

   ✗  Lisans metnini değiştirmek
      Tek bir cümleyi bile düzenlerseniz artık o lisansı kullanmıyor
      olursunuz; otomatik araçlar lisansı tanıyamaz ve hukuki belirsizlik
      doğar. Yalnızca yer tutucuları doldurun.

   ✗  Lisans dosyasının başına açıklama eklemek
      LICENSE dosyası SADECE lisans metnini içermelidir. Açıklamalar README'ye
      yazılır. Aksi hâlde lisans tespit araçları (bu projedeki checker dâhil)
      yanlış sonuç verir.

   ✗  Sürüm ayrımını atlamak
      GPL-2.0-only ile GPL-2.0-or-later farklı şeylerdir. Kaynak dosya
      bildiriminizde 'either version 2, or (at your option) any later version'
      yazıyorsa SPDX kimliğiniz GPL-2.0-or-later olmalıdır.

   ✗  Yıl alanını her yıl güncellemeye çalışmak
      Genel kabul: ilk yayım yılı yazılır. İsterseniz aralık kullanın
      (2023-2025). Her dosyada yılı güncel tutmak zorunlu değildir.

   ✗  Uyumsuz lisansları birleştirmek
      GPL-2.0-only + Apache-2.0, GPL + CDDL, GPL + BSD-4-Clause birleşimleri
      uyumsuzdur. Bağımlılıklarınızın lisanslarını dağıtımdan ÖNCE denetleyin.

   ✗  Yazılıma Creative Commons uygulamak
      CC lisansları kaynak kodu için tasarlanmamıştır ve patent hükmü içermez.
      Creative Commons kuruluşu da bunu açıkça önermez. Kod için MIT,
      Apache-2.0, GPL vb. kullanın.

   ✗  Yer tutucusu olmayan lisansa telif satırı eklemek
      GPL, AGPL, LGPL, MPL, EPL, Apache-2.0 ve CC ailesi gibi 34 lisansın
      metninde doldurulacak alan yoktur. LICENSE dosyasının başına
      'Copyright (c) 2025 ...' satırı eklemek metni bozar ve lisans tespit
      araçlarını yanıltır. Bu lisanslarda telifinizi kaynak dosya başlığına
      (Bölüm 5, ÖRNEK 2) ve README'ye (ÖRNEK 3) yazarsınız.

   ✗  Sadece LICENSE dosyası koyup bildirim eklememek
      GPL, LGPL, AGPL, MPL, EPL ve Apache-2.0 gibi lisanslar kaynak dosyaların
      başına bildirim konulmasını ister veya güçlü biçimde tavsiye eder. Bölüm
      5'teki ÖRNEK 2 metinleri bunun içindir.

   ✗  Katkı sahiplerini yok saymak
      Dışarıdan gelen katkılarla telif hakkı paylaşılır. Çok katkıcılı
      projelerde AUTHORS/CONTRIBUTORS dosyası tutun; gerekirse bir Katkı
      Sözleşmesi (CLA/DCO) benimseyin.


==============================================================================
  7.  BİÇİM VE KODLAMA BİLGİSİ
==============================================================================

   Dosya biçimi     : Düz metin (.txt)
   Karakter kodlama : UTF-8
   Satır sonu       : CRLF (Windows)
   Satır genişliği  : En fazla 78 sütun
   Yer tutucu biçimi: [BÜYÜK HARF] — köşeli parantez içinde

   Lisans metinleri resmî kaynaklardan alınmış, satır genişliği 78 sütuna göre
   düzenlenmiştir. İçerik değiştirilmemiştir; yalnızca satır sarmalama ve
   telif yer tutucuları düzenlenmiştir.

   Bu dosyaları bir Git deposuna eklerken satır sonlarını korumak için
   .gitattributes içine şu satırı ekleyebilirsiniz:

      LICENSE*  -text
      *.txt     text eol=crlf


==============================================================================
  8.  KAYNAKLAR
==============================================================================

   SPDX Lisans Listesi          https://spdx.org/licenses/
   OSI Onaylı Lisanslar         https://opensource.org/licenses/
   Choose a License             https://choosealicense.com/
   GNU Lisansları               https://www.gnu.org/licenses/
   GNU Lisans Uyumluluk Listesi https://www.gnu.org/licenses/license-list.html
   Apache Lisansları            https://www.apache.org/licenses/
   Mozilla Public License 2.0   https://www.mozilla.org/MPL/2.0/
   Creative Commons             https://creativecommons.org/licenses/
   Eclipse Public License       https://www.eclipse.org/legal/epl-2.0/
   EUPL (Avrupa Komisyonu)      https://joinup.ec.europa.eu/collection/eupl
   SIL Open Font License        https://openfontlicense.org/
   Open Data Commons            https://opendatacommons.org/licenses/
   Blue Oak Council             https://blueoakcouncil.org/list
   TÜBİTAK / Kamu Açık Kaynak   https://acikkaynak.gov.tr/


==============================================================================
  9.  YASAL UYARI
==============================================================================

   Bu klasördeki metinler bilgilendirme ve kolaylık amacıyla derlenmiştir;
   HUKUKİ DANIŞMANLIK DEĞİLDİR. Lisans seçimi, projenizin bağımlılıkları, iş
   modeliniz, çalıştığınız hukuk düzeni ve varsa iş sözleşmelerinizdeki fikri
   mülkiyet hükümleriyle doğrudan ilgilidir.

   Ticari bir ürün yayımlamadan, kurumsal bir kod tabanını açık kaynağa
   çevirmeden veya Proprietary.txt taslağını kullanmadan önce bir fikri
   mülkiyet hukukçusuna danışmanız önerilir.

   Lisans metinlerinin bağlayıcı ve güncel hâli her zaman Bölüm 8'de verilen
   resmî kaynaklardaki metinlerdir. Herhangi bir farklılık durumunda resmî
   metin geçerlidir.

   Proprietary.txt dosyası OSI onaylı bir açık kaynak lisansı DEĞİLDİR; genel
   amaçlı bir sözleşme taslağıdır ve olduğu gibi kullanılmaya uygun değildir.
   Mutlaka hukuki inceleme gerektirir.

==============================================================================
  Belge sonu — 50 lisans taslağı listelendi.
==============================================================================
