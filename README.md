# SSML DOCUMENTATION
This document is **SSML** documentation, what is **SSML**, how to use **SSML**, and **SSML** example


## Introduction
- **What is **SSML**?**
    - Speech Synthesis Markup Language (**SSML**)<sup>[(1)](https://www.w3.org/TR/speech-synthesis/)</sup> is an XML-based markup language for speech synthesis applications. It is a recommendation of the W3C's Voice Browser Working Group. **SSML** is often embedded in VoiceXML scripts to drive interactive telephony systems. However, it also may be used alone, such as for creating audio books.
    - **SSML** is based on the Java Speech Markup Language (**JSML**)<sup>[(2)](https://www.w3.org/TR/jsml/)</sup> developed by Sun Microsystems, although the current recommendation was developed mostly by speech synthesis vendors. It covers virtually all aspects of synthesis, although some areas have been left unspecified, so each vendor accepts a different variant of the language. Also, in the absence of markup, the synthesizer is expected to do its own interpretation of the text.
- **Design Concept**
    - The design and standardization process has followed from the Speech Synthesis Markup Requirements for Voice Markup Languages
        - Consistency: provide predictable control of voice output across platforms and across speech synthesis implementations.
        - Interoperability: support use along with other W3C specifications including (but not limited to) VoiceXML, aural Cascading Style Sheets and SMIL.
        - Generality: support speech output for a wide range of applications with varied speech content.
        - Internationalization: Enable speech output in a large number of languages within or across documents.
        - Generation and Readability: Support automatic generation and hand authoring of documents. The documents should be human-readable.
        - Implementable: The specification should be implementable with existing, generally available technology, and the number of optional features should be minimal.
- **Element**
    - The Speech Synthesis Markup Language is an XML application. The root element is `speak`.
        - Example:
        ```xml
        <speak>
            coba baca ini
        </speak>
        ```
        ![](audio-ssml/ssml-0.wav)
        <!-- <body>
        <audio controls>
        <source src="audio-ssml/ssml-0.wav" type="audio/wav">
        </audio>
        </body> -->
    - A `p` element represents a paragraph. An `s` element represents a sentence.
        - Example:
        ```xml
        <speak>
            <p>
                <s>Ini adalah kalimat pertama.</s>
                <s>Ini adalah kalimat kedua.</s>
            </p>
        </speak>
        ```
        ![](audio-ssml/ssml-1.wav)

## Features
- **Say-as**
    - This element lets you indicate information about the type of text construct that is contained within the element. It also helps specify the level of detail for rendering the contained text.

        The `<say‑as>` element has the required attribute, `interpret-as`, which determines how the value is spoken. Optional attributes format and detail may be used depending on the particular `interpret-as` value.
    - The `<say-as>` element has many attributes: `interpret-as`, `format`, (`detail` or `type`), etc. The `interpret-as` attribute is always required, and the others attributes are optional
    - The `interpret-as` attribute supports the following values:
        - **Ordinal**
            - Spoke as ordinal-numbering
        - **Cardinal**
            - Spoke as cardinal-numbering
        - **Currencies**
            - Spoke as money-currencies
        - **Characters**
            - Spoke as characters one by one
        - **Fraction**
            - Spoke as fraction-numbering
        - **Unit**
            - Spoke as metrics unit
        - **Verbatim**
            - Spoke like Characters
        - **Phonenumber**
            - Phone-numbering spoke
        - **Webmail**
            - Spoke as website or e-mail
        - **Name**
            - Spoke name with title name
        - **Roman-Number**
            - Spoke as Roman-Number
        - **Date**
            - Spoke as date
        - **Duration**
            - Spoke as Duration
        - **Time**
            - Spoke as time

- **Sub**
    - Indicate that the text in the alias attribute value replaces the contained text for pronunciation.

- **Audio**
    - Supports the insertion of other audio formats in conjunction with synthesized speech output.
    - Attributes:
        - Speed (Speed-Rate)
            - Set audio speed
        - SoundLevel (Volume)
            - Set audio volume

- **Break**
    - An empty element that controls pausing or other prosodic boundaries between words.

- **Prosody**
    - COMING SOON

- **Emphasis**
    - COMING SOON

## How to use
- **Say-as**:
    - **Ordinal**:
        - Attribute: 
            - `interpret-as="ordinal"`
        - Example:
            ```xml
            <speak>
                Kamu urutan <say-as interpret-as="ordinal">10</say-as> dalam baris.
            </speak>
            ```
            ![](audio-ssml/ssml-use-1.wav)

    - **Cardinal**:
        - Attribute: 
            - `interpret-as="cardinal"`
        - Example:
            ```xml
            <speak>
                Angkamu adalah <say-as interpret-as="cardinal">10</say-as>.
            </speak>
            ```
            ![](audio-ssml/ssml-use-12.wav)

    - **Currencies**:
        - Attribute: 
            - `interpret-as="currencies"`
        - Example:
            ```xml
            <speak>
                Uangku tinggal <say-as interpret-as="currencies">Rp100.000</say-as> di bank.
            </speak>
            ```
            ![](audio-ssml/ssml-use-2.wav)

    - **Characters**:
        - Attribute: 
            - `interpret-as="characters"`
            - `format="characters"` or `format="glyphs"` default: `characters`
                - *Characters* → Read characters one by one.
                - *Glyphs* → This indicates all characters should be read with glyph information, explicitly specifying uppercase/lowercase, accents, diacritics etc.
        - Example:
            ```xml
            <speak>
                coba baca ini <say-as interpret-as="characters" format="glyphs">SSML</say-as>.
            </speak>
            ```
            ![](audio-ssml/ssml-use-3.wav)

    - **Fraction**:
        - Attribute: 
            - `interpret-as="fraction"`
        - Example:
            ```xml
            <speak>
                angka ini dibaca <say-as interpret-as="fraction">1/2, 1/4, 2/5</say-as>.
            </speak>
            ```
            ![](audio-ssml/ssml-use-4.wav)

    - **Unit**:
        - Attribute: 
            - `interpret-as="unit"`
        - Example:
            ```xml
            <speak>
                Jarak tempuhnya bisa <say-as interpret-as="unit">50 km/L</say-as>.
            </speak>
            ```
            ![](audio-ssml/ssml-use-17.wav)

    - **Verbatim**:
        - Attribute: 
            - `interpret-as="verbatim"`
        - Example:
            ```xml
            <speak>
                ini dibaca <say-as interpret-as="verbatim">abcdefghijklmnopqrstuvwxyz</say-as>.
            </speak>
            ```
            ![](audio-ssml/ssml-use-5.wav)

    - **Phonenumber**:
        - Attribute: 
            - `interpret-as="phonenumber"`
        - Example:
            ```xml
            <speak>
                ini dibaca <say-as interpret-as="phonenumber">+62812-7337-7666</say-as>.
            </speak>
            ```
            ![](audio-ssml/ssml-use-13.wav)

    - **Webmail**:
        - Attribute: 
            - `interpret-as="webmail"`
        - Example:
            ```xml
            <speak>
                coba buka situs ini <say-as interpret-as="webmail">www.detik.com</say-as>.
            </speak>
            ```
            ![](audio-ssml/ssml-use-6.wav)
    
    - **Name**:
        - Attribute: 
            - `interpret-as="name"`
        - Example:
            ```xml
            <speak>
                nama saya <say-as interpret-as="name">Prof. Dr. Jauhari Nasution, S.T., M.T., Ph.D.</say-as>.
            </speak>
            ```
            ![](audio-ssml/ssml-use-14.wav)
    
    - **Roman-Number**:
        - Attribute: 
            - `interpret-as="roman-number"`
        - Example:
            ```xml
            <speak>
                angka romawi berikut adalah <say-as interpret-as="roman-number">XXXIII</say-as>.
            </speak>
            ```
            ![](audio-ssml/ssml-use-7.wav)
    
    - **Date**:
        - Attribute: 
            - `interpret-as="date"`
            - `format="mdy"` defaut: `dmy`
                - *dmy* → date - month - year
                - *mdy* → month - date - year
                - *ymd* → year - month - date
                - *dm* → date - month
                - *md* → month - date
                - *my* → month - year
                - *ym* → year - month
                - *d* → date
                - *m* → month
                - *y* → year
        - Example:
            ```xml
            <speak>
                Mengucapkan tanggal <say-as interpret-as="date" format="dmy">10-9-1960</say-as>.
            </speak>
            ```
            ![](audio-ssml/ssml-use-15.wav)
    
    - **Duration**:
        - Attribute: 
            - `interpret-as="duration"`
            - `format="h:m:s"` default: `h:m`
                - *h:m:s:ms* → hour - minute - second - milisecond
                - *h:m:s* → hour - minute - second
                - *h:m* → hour - minute
                - *m:s* → minute - second
                - *h* → hour
                - *m* → minute
                - *s* → second
                - *ms* → milisecond

        - Example:
            ```xml
            <speak>
                Mengucapkan durasi <say-as interpret-as="duration" format="h:m:s">10:12:45</say-as>.
            </speak>
            ```
            ![](audio-ssml/ssml-use-16.wav)
    
    - **Time**:
        - Attribute: 
            - `interpret-as="time"`
            - `format="hms12"` default: `hms24`
                - *hms24* → 24 hours format
                - *hms12* → 12 hours format (AM - PM)
            - `type="2"` default: `1`
                - *type-hms24* → 1-8 pronunciation type
                - *type-hms12* → 1-6 pronunciation type
            - `prefix="jam"` default: `pukul`
        - Example:
            ```xml
            <speak>
                Mengucapkan waktu <say-as interpret-as="time" format="hms24" type="1" prefix="pukul">2:30 WIB</say-as>.
            </speak>
            ```
            ![](audio-ssml/ssml-use-8.wav)

- **Sub**:
    - Attribute:
        - `alias="text-to-replace"`
    - Example:
        ```xml
        <speak>
            Saya bisa menggantikan suatu frasa, seperti <sub alias="World Wide Web Consortium">W3C</sub>.
        </speak>
        ```
        ![](audio-ssml/ssml-use-9.wav)

- **Break**:
    - Attribute:
        - `time="3s"`
    - Example:
        ```xml
        <speak>
           Saya bisa jeda 3 detik <break time="3s"/> seperti tadi.
        </speak>
        ```
        ![](audio-ssml/ssml-use-10.wav)

- **Audio**
    - Attribute:
        - `speed="1.2"` default: `1.0`
        - `soundlevel="5"` default: `0`
    - Example:
        ```xml
        <speak>
            <audio speed="1.2"> saya bisa percepat audio </audio>.
            <audio speed="0.8"> saya bisa perlambat audio </audio>.
            <audio soundlevel="5"> Saya bisa naikan volume </audio>.
            <audio soundlevel="-5"> Saya bisa kurangi volume </audio>.
        </speak>
        ```
        ![](audio-ssml/ssml-use-11.wav)

- **Voice**
    - Attribute:
        - `name="Female 4"`
        - `name="Male 8"`
    - Example:
        ```xml
        <speak>
            <voice name="Female 4"> Selamat siang </voice>
            <voice name="Male 8"> Selamat siang juga </voice>
        </speak>
        ```
        ![](audio-ssml/ssml-use-18.wav)

## Example
- Input:
    ```xml
    <speak>
        Ini adalah contoh <say-as interpret-as="characters">SSML</say-as>.
        Saya bisa jeda 3 detik <break time="3s"/>.
        Saya bisa mengucapkan cardinal. Angkamu adalah <say-as interpret-as="cardinal">10</say-as>.
        Atau saya bisa mengucapkan ordinal. Kamu urutan <say-as interpret-as="ordinal">10</say-as> dalam baris.
        Atau saya bahkan bisa mengucapkan digit. Digit untuk angka sepuluh adalah <say-as interpret-as="characters">10</say-as>.
        Saya juga bisa menggantikan suatu frasa, seperti <sub alias="World Wide Web Consortium">W3C</sub>.
        Mengucapkan tanggal <say-as interpret-as="date" format="dmy">10-9-1960</say-as>.
        Mengucapkan waktu <say-as interpret-as="time" format="hms24" type="1" prefix="pukul">2:30 WIB</say-as>.
        akhirnya, saya bisa mengucapkan satu paragraf dengan dua kalimat.
        <p><s>Ini adalah kalimat pertama.</s><s>Ini adalah kalimat kedua.</s></p>
    </speak>
    ```

- Ouput Normalization text:
    ```json
    [
        "ini adalah contoh és és ém él." ,
        [
            "saya bisa jeda tiga detik." ,
            "<speak> <break time="3s"/> </speak>"
        ] ,
        "saya bisa mengucapkan kardenel." ,
        "angkamu adalah sepuluh." ,
        "atau saya bisa mengucapkan ordinal." ,
        "kamu urutan kesepuluh dalam baris." ,
        "atau saya bahkan bisa mengucapkan digit." ,
        "digit untuk angka sepuluh adalah satu nol." ,
        "saya juga bisa menggantikan suatu frasa, seperti werld wayd wéb kensowrsyiem." ,
        "mengucapkan tanggal sepuluh séptémber seribu sembilan ratus enam puluh." ,
        "mengucapkan waktu pukul dua léwat tiga puluh menit wé i bé." ,
        "akhirnya, saya bisa mengucapkan satu paragraf dengan dua kalimat." ,
        "ini adalah kalimat pertama." ,
        "ini adalah kalimat kedua."
    ]
    ```

- Result:
    - ![](audio-ssml/ssml-example-all.wav)

## Reference

> Note: Full documentation is here [W3C](https://www.w3.org/TR/speech-synthesis/)

> Google SSML documentation is here [SSML-Google](https://cloud.google.com/text-to-speech/docs/ssml)

> Amazon-Alexa SSML Reference is here [SSML-Alexa](https://developer.amazon.com/en-US/docs/alexa/custom-skills/speech-synthesis-markup-language-ssml-reference.html)

> Microsoft-Azure SSML documentation is here [SSML-Azure](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/speech-synthesis-markup?tabs=csharp)

> IBM-Watson SSML documentation is here [SSML-Watson](https://cloud.ibm.com/docs/text-to-speech?topic=text-to-speech-ssml)

> (1): [https://www.w3.org/TR/speech-synthesis/](https://www.w3.org/TR/speech-synthesis/)

> (2): [https://www.w3.org/TR/jsml/](https://www.w3.org/TR/jsml/)



```
>>> Author: Anggit Yogo N., Gugi Asgaruning
>>> Сopyright PT Bahasa Kinerja Utama @ 2022
```