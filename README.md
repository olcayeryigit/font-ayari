##  1

Fontların `layout.js` İçinde Tanımlanması

İlk olarak **`src/app/layout.js`** dosyasını açın. Google Fonts'tan gelen fontları Next.js yerleşik font optimizasyonu (`next/font/google`) ile yükleyip, CSS değişkenlerine (`variable`) bağlayarak `<html>` etiketine sınıf olarak ekleyin:

```javascript
import { Cormorant_Garamond, Inter } from "next/font/google";
import "./globals.css";

// Düz metin fontu (Inter)
const inter = Inter({
  subsets: ["latin"],
  variable: "--font-inter",
});

// Başlık fontu (Cormorant Garamond)
const cormorant = Cormorant_Garamond({
  subsets: ["latin"],
  weight: ["300", "400", "500", "600", "700"],
  style: ["normal", "italic"],
  variable: "--font-cormorant",
});

export default function RootLayout({ children }) {
  return (
    // CSS değişkenlerini HTML etiketine class olarak tanımlıyoruz
    <html lang="tr" className={`${inter.variable} ${cormorant.variable}`}>
      <body>{children}</body>
    </html>
  );
}

##  2

global.css

@import "tailwindcss";

@theme {
  /* layout.js'ten gelen değişkenleri Tailwind font sınıflarına bağlıyoruz */
  --font-serif: var(--font-cormorant), serif;
  --font-sans: var(--font-inter), sans-serif;
}

##  3

<h1 className="font-serif text-4xl italic text-[#c5a880]">Başlık Yazısı</h1>

<p className="font-sans text-base text-gray-300">Açıklama metni...</p>
