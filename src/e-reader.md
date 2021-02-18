# Tips for e-readers

I've read on both Kindle PaperWhites and a Kobo Libra H2O. They're both fine!

## Fonts

[How to add custom fonts to a Kobo e-reader + Bookerly link](https://goodereader.com/blog/e-book-news/how-to-add-custom-fonts-to-your-kobo-e-reader): Plug in your Kobo e-reader, create a folder called "fonts" in the main directory. Add the `.tff` files directly to that folder (no subfolders). They must be named in the pattern of `FontName-Style`, and for style Kobo seems to accept Bold, Italic, and BoldItalic. So for example:

```text
fonts/ 
    Bookerly-Bold.ttf        
    Bookerly-BoldItalic.ttf  
    Bookerly-Italic.ttf      
    Bookerly-Regular.ttf
    LibreBaskerville-Bold.tff
    LibreBaskerville-BoldItalic.tff
    LibreBaskerville-Italic.tff
    LibreBaskerville-Regular.tff
    Spectral-Bold.ttf
    Spectral-BoldItalic.ttf
    Spectral-Italic.ttf
    Spectral-Regular.ttf
```

### Some good fonts for e-reading

- Bookerly is the current default font for Amazon's Kindles, and I think it's my current favorite. One might be able to get a copy [here](https://goodereader.com/blog/e-book-news/how-to-add-custom-fonts-to-your-kobo-e-reader).
- [Libre Baskerville](https://fonts.google.com/specimen/Libre+Baskerville) is a decent second choice. 
- [Literata](https://fonts.google.com/specimen/Literata) is a font associated with Google Books I think.
- [Source Serif Pro](https://fonts.google.com/specimen/Source+Serif+Pro)
- [EB Garamond](https://fonts.google.com/specimen/EB+Garamond)
- [Crimson Text](https://fonts.google.com/specimen/Crimson+Text)
- [Spectral](https://fonts.google.com/specimen/Spectral) is the SubStack serif font.

- [HT Ashbury](https://www.fontshop.com/families/ht-ashbury) is one I know I like in print but haven't gotten on an e-reader.

## Managing e-books on a Linux desktop

I have used and like [Calibre](https://calibre-ebook.com/demo#screenshots).

## For improved reading/organization of certain file types _on your Kobo device_

I think [koreader](https://github.com/koreader/koreader) is a replacement for the default software on your e-reader?

There's also a Rust program for handling PDFs and other difficult filetypes: [https://github.com/baskerville/plato](https://github.com/baskerville/plato)

## More Kobo links

[Kobo ebook store](https://us.kobobooks.com/collections/all)

[How to add books to a Kobo e-reader](https://help.kobo.com/hc/en-us/sections/360002811674-Add-and-Find-Books)
