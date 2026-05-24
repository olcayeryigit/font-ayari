1. Adım: Fontu layout.js İçinde Tanımlayın
İlk olarak src/app/layout.js dosyanızı açın ve Google Fonts'tan gelen fontu bir CSS değişkenine (--font-cormorant) bağlayarak <html> etiketine ekleyin:

JavaScript
import { Cormorant_Garamond, Inter } from "next/font/google";
import "./globals.css";

const inter = Inter({
  subsets: ["latin"],
  variable: "--font-inter",
});

const cormorant = Cormorant_Garamond({
  subsets: ["latin"],
  weight: ["300", "400", "500", "600", "700"],
  style: ["normal", "italic"],
  variable: "--font-cormorant",
});

export default function RootLayout({ children }) {
  return (
    // Değişkenleri HTML sınıfına ekliyoruz
    <html lang="tr" className={`${inter.variable} ${cormorant.variable}`}>
      <body>{children}</body>
    </html>
  );
}
2. Adım: globals.css İçinde Tailwind v4 Yapılandırması
Şimdi src/app/globals.css dosyanızı açın. Tailwind v4'te yeni font tanımlamak için @theme bloğunu kullanırız. Dosyanın en üstüne şu satırları ekleyin:

CSS
@import "tailwindcss";

@theme {
  /* layout.js'ten gelen CSS değişkenini Tailwind font ailesine eşliyoruz */
  --font-serif: var(--font-cormorant), serif;
  --font-sans: var(--font-inter), sans-serif;
}
Artık Kullanabilirsiniz!
Bu iki adımı yaptıktan sonra projenizde hiçbir ayar dosyası aramadan doğrudan Tailwind sınıflarını çağırabilirsiniz:

Tırnaklı Başlık Fontu İçin: font-serif sınıfını kullanın.

JavaScript
<h1 className="font-serif text-5xl italic text-[#c5a880]">
  Diyarbakır Avukatı Av. Özgür Atlı
</h1>
Düz Metin Fontu İçin: font-sans sınıfını kullanın.

JavaScript
<p className="font-sans text-sm text-gray-300">
  Miras hukuku, aile ve boşanma hukuku...
</p>
