# C-Tahmin-Oyunu
Tahmin oyunudur güncellemeler gelecektir.
Not: Telefondan kodlanmıştır.
uygulama ismi: C# Sheel .NET IDE
Kendiniz Yazılar da düzenleme yapabilirsiniz.
KOD:
using System;

namespace SayiBulmaOyunu
{
    class Program
    {
        static void Main(string[] args)
        {
            bool oyunDevamEdiyor = true;
            while (oyunDevamEdiyor)
            {
                OyunuBaslat();

                Console.WriteLine("Var mısın bir daha oynamak için? (Evet/Hayır)");
                string cevap = Console.ReadLine();

                if (cevap.ToLower() != "evet")
                {
                    oyunDevamEdiyor = false;
                    Console.WriteLine("Beni yenebileceğine inanıyordum. Başarının çözümü sabırdır!");
                }

                Console.WriteLine();
            }

            Console.WriteLine("Beni yenebileceğine inanıyordun ama başaramadın. Başarının çözümü sabırdır!");
        }

        static void OyunuBaslat()
        {
            Random random = new Random();
            int tutulanSayi = random.Next(1, 31); // 1 ile 30 arasında rastgele bir sayı tutulur
            int tahmin;
            int denemeSayisi = 0;
            bool sayiBulundu = false;

            Console.WriteLine("1 ile 30 arasında bir sayı tutuldu. 3 deneme hakkın var. Bakalım bulabilecek misin!");

            while (denemeSayisi < 3 && !sayiBulundu)
            {
                Console.Write("Tahmininizi girin: ");
                tahmin = Convert.ToInt32(Console.ReadLine());
                denemeSayisi++;

                if (tahmin == tutulanSayi)
                {
                    sayiBulundu = true;
                    Console.WriteLine($"Tebrikler! {tutulanSayi} sayısını {denemeSayisi}. denemede buldun!");
                    Console.WriteLine("Sen o olamazsın, merak uyandırdın!");
                }
                else if (tahmin < tutulanSayi)
                {
                    Console.WriteLine("Daha yüksek bir sayı girin.");
                }
                else
                {
                    Console.WriteLine("Daha düşük bir sayı girin.");
                }
            }

            if (!sayiBulundu)
            {
                Console.WriteLine("Üzgünüm, 3 deneme hakkını da kullandın. Bir daha denemek ister misin? (Evet/Hayır)");
                string cevap = Console.ReadLine();

                if (cevap.ToLower() == "evet")
                {
                    Console.WriteLine();
                    OyunuBaslat();
                }
            }
        }
    }
}
