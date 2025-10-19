import random


secenekler = ["taş", "kağıt", "makas"]

def oyunu_oyna_limitli_gecerli_giris():
    
   
    kullanici_skoru = 0
    bilgisayar_skoru = 0
    toplam_gecerli_tur = 0  
    maksimum_tur = 5

    print("\n" + "="*40)
    print(f"Taş-Kağıt-Makas oyununa hoş geldiniz! (Toplam {maksimum_tur} Geçerli Tur)")
    print("İstediğiniz zaman 'çık' yazarak çıkış yapabilirsiniz.")
    print("Geçersiz giriş yaptığınızda hakkınız tükenmez.")
    print("="*40)

  
    while toplam_gecerli_tur < maksimum_tur:
        
  
        tur_numarasi = toplam_gecerli_tur + 1
        
        try:
      
            kullanici_secimi = input(f"[{tur_numarasi}. Tur] Taş, kağıt veya makas (ya da 'çık')seçin : ").lower()
            
        except EOFError:
            print("\n[Oyun Sonlandırıldı] Giriş akışı beklenmedik şekilde sona erdi.")
            break
            
        if kullanici_secimi == "çık":
            print("\nOyun kullanıcı isteğiyle sonlandırılıyor.")
            break

        if kullanici_secimi not in secenekler:
            print("Geçersiz seçim! Lütfen sadece 'taş', 'kağıt' veya 'makas' girin.")
            print(f"Mevcut Skor: Sen {kullanici_skoru} - Bilgisayar {bilgisayar_skoru}")
            print(f"Kalan Geçerli Tur Hakkı: {maksimum_tur - toplam_gecerli_tur}")
            print("-" * 20)
            continue 

  
        toplam_gecerli_tur += 1 
        

        bilgisayar_secimi = random.choice(secenekler)

        print(f"Sen: {kullanici_secimi.capitalize()}")
        print(f"Bilgisayar: {bilgisayar_secimi.capitalize()}")

        if kullanici_secimi == bilgisayar_secimi:
            print(" Berabere, skorlar değişmedi.")
        
        elif (kullanici_secimi == "taş" and bilgisayar_secimi == "makas") or \
             (kullanici_secimi == "kağıt" and bilgisayar_secimi == "taş") or \
             (kullanici_secimi == "makas" and bilgisayar_secimi == "kağıt"):
            print("Sen kazandın!")
            kullanici_skoru += 1
        
        else:
            print("Bilgisayar kazandı.")
            bilgisayar_skoru += 1

        print(f"Mevcut Skor: Sen {kullanici_skoru} - Bilgisayar {bilgisayar_skoru}")
        print(f"Kalan Geçerli Tur Hakkı: {maksimum_tur - toplam_gecerli_tur}")
        print("-" * 20)


    print("\n" + "="*40)
    print("Oyun sona erdi.")
    print("="*40)
    print(f"Sonuç: SEN {kullanici_skoru} - BİLGİSAYAR {bilgisayar_skoru}")

    if kullanici_skoru > bilgisayar_skoru:
        print("Sen Kazandın!")
    elif bilgisayar_skoru > kullanici_skoru:
        print("Bilgisayar kazandı.")
    else:
        print("Genel skor berabere.")
        
    print("\nOynadığınız için teşekkürler.")


if __name__ == "__main__":
    oyunu_oyna_limitli_gecerli_giris()


