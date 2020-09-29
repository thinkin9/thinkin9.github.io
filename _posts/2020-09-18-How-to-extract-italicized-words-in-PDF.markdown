---
layout: post
title:  "How to extract italicized words in PDF "
date:   2020-09-18 01:31:43 +0900
categories: Etc
---

<div style="text-align: center"><i><b>Last Updated on September 29th, 2020</b></i></div>

## Reference
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* Get italic lines from a pdf - [stackoverflow](https://stackoverflow.com/questions/18675839/get-italic-lines-from-a-pdf)


## IText
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

* [API Document](https://api.itextpdf.com/)
    * [iText5 5.5.13 API Document](https://api.itextpdf.com/iText5/java/5.5.13/)
    * [iText7 7.1.12 API Document](https://api.itextpdf.com/iText7/java/7.1.12/)
* [iText5 5.5.13 API Download](http://www.java2s.com/example/jar/i/download-itextpdf5513jar-file.html)

## JAVA
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

```java
import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.PrintWriter;

import com.itextpdf.text.pdf.BaseFont;
import com.itextpdf.text.pdf.DocumentFont;
import com.itextpdf.text.pdf.PdfReader;
import com.itextpdf.text.pdf.parser.PdfTextExtractor;
import com.itextpdf.text.pdf.parser.SimpleTextExtractionStrategy;
import com.itextpdf.text.pdf.parser.TextRenderInfo;

public class ExtractItalicText {

    final static class ItalicTextExtractionStrategy extends SimpleTextExtractionStrategy {
        @Override
        public void renderText(TextRenderInfo arg0) {
            DocumentFont font = arg0.getFont();
            String[][] familyFontNamesArray = font.getFamilyFontName();
            for(String[] familyFontNames : familyFontNamesArray) {
                for(String familyFontName : familyFontNames) {
                    if(familyFontName.toLowerCase().contains("italic")) {
                        float italicAngle = font.getFontDescriptor(BaseFont.ITALICANGLE, 0);
                        if(italicAngle < 0) {
                            super.renderText(arg0);
                        }
                        break;
                    }
                }
            }
        }
    }

    public static void extractItalicText(String pdf) throws IOException {
        PdfReader reader = null;
        PrintWriter out = null;
        PrintWriter outItalic = null;
        long s = System.currentTimeMillis();
        try {
            System.out.println("Processing: " + pdf + " ...");
            // output for italic styled text only
            outItalic = new PrintWriter(new FileOutputStream("src/main/resources/" + new File(pdf).getName() + "_italic.txt"));
            reader = new PdfReader(pdf);
            int numberOfPages = reader.getNumberOfPages();
            for(int pageNumber = 1; pageNumber <= numberOfPages; pageNumber++) {
                // extract italic text
                String pageItalicText = PdfTextExtractor.getTextFromPage(reader, pageNumber, new ItalicTextExtractionStrategy());
                if(pageItalicText.trim().length() > 0) {
                    // we have some italic text in the current page, so we get the hole text of the page
                    // to search for the lines where the italic text is located
                    String textFromPage = PdfTextExtractor.getTextFromPage(reader, pageNumber);
                    String[] textLinesFromPage = textFromPage.split("[\r\n]");

                    // split the italic text into lines
                    String[] italicTextLines = pageItalicText.split("[\r\n]");
                    for(String italicText : italicTextLines) {
                                outItalic.println(italicText + "\n");
                    }
                }
                outItalic.println("==== Page " + (pageNumber+7) + " =========================================================\n");
            }

        } finally {
            if(out != null) {
                out.close();
            }
            if(outItalic != null) {
                outItalic.close();
            }
            if(reader != null) {
                reader.close();
            }
            long e = System.currentTimeMillis();
            System.out.println("done (" + (e-s) + " ms)");
        }
    }

    /**
     * @param args
     * @throws IOException
     */
    public static void main(String[] args) throws IOException {
        System.out.println("Hi");
        extractItalicText("textbook.pdf");
    }
}

```