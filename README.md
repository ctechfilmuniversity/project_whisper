# Whisper Anleitung

Version 01 - 14.02.2024

Die folgende Anleitung ist aktuell nur für Macs getestet.

## Installationen

### Python 

* Unter https://www.python.org/downloads/ die letzte Python-Version herunterladen und installieren.

#### Verifizierung der Python Installation

Um sicherzustellen, dass ein Kommandozeilen-Befehl, wie z.B. für Python, korrekt installiert worden ist, kann man sich die Version des zugrunde liegenden Programms anzeigen lassen. Wenn die Version angezeigt wird, ist alles gut, ansonsten gibt es einen Fehler in Richtung "command not found".

Um die gerade installierte Python-Version anzeigen zu lassen, den Terminal öffnen und folgende Zeile eintippen oder reinkopieren und zum Ausführen *Enter* drücken:

```
python3 --version
```

Wenn die Ausgabe eine Versionsnummer angibt, z.B. `Python 3.12.1`, ist alles gut! 


### PIP

Um weitere Funktionalität, sogenannte *packages*, für Python zu installieren, verwenden wir das Standardprogramm `pip` (ein *package manager* für Python). `pip` wird mit Python-Versionen > 3.5. automatisch zusammen mit Python installiert.


#### Verifizierung der pip Installation

```
pip3 --version
```

### Whisper

Nun können wir mit `pip` das [Whisper Paket](https://github.com/openai/whisper/tree/main?tab=readme-ov-file) installieren. Wir installieren Whisper global, was heißt, dass es erst einmal egal ist, in welchem Ordner wir uns im Terminal befinden.

Dafür im Terminal die folgende Zeile eintippen oder reinkopieren und zum Ausführen *Enter* drücken:

```
pip3 install -U openai-whisper
```

Die Ausführung dauert einen kleinen Moment und im Terminal sollte der Installationsprozess dokumentiert sein. Wenn nicht explizit ein *Error* betont wird, kann man den Ausgabetext ignorieren.

#### Verifizierung der Whisper Installation

Die Macher von Whisper habe die Ausgabe einer Programmversion nicht implementiert, der Befehl `whisper --version` funktioniert somit nicht. Alternativ, können wir die korrekte Installation mit dem Parameter `--help` überprüfen. `--help` beschreibt einen Befehl und gibt alle vorhandenen Optionen an.


Die folgende Zeile eintippen oder reinkopieren und zum Ausführen *Enter* drücken:

```
whisper --help
```

Die Ausgabe beschreibt, wie man Whisper verwenden kann und sollte in etwa wie folgt aussehen:

```
usage: whisper [-h] [--model MODEL] [--model_dir MODEL_DIR] [--device DEVICE] [--output_dir OUTPUT_DIR]
               [--output_format {txt,vtt,srt,tsv,json,all}] [--verbose VERBOSE] [--task {transcribe,translate}]
               [--language {af,am,ar,as,az,ba,be,bg,bn,bo,br,bs,ca,cs,cy,da,de,el,en,es,et,eu,fa,fi,fo,fr,gl,gu,ha,haw,he,hi,hr,ht,hu,hy,id,is,it,ja,jw,ka,kk,km,kn,ko,la,lb,ln,lo,lt,lv,mg,mi,mk,ml,mn,mr,ms,mt,my,ne,nl,nn,no,oc,pa,pl,ps,pt,ro,ru,sa,sd,si,sk,sl,sn,so,sq,sr,su,sv,sw,ta,te,tg,th,tk,tl,tr,tt,uk,ur,uz,vi,yi,yo,yue,zh,Afrikaans,Albanian,Amharic,Arabic,Armenian,Assamese,Azerbaijani,Bashkir,Basque,Belarusian,Bengali,Bosnian,Breton,Bulgarian,Burmese,Cantonese,Castilian,Catalan,Chinese,Croatian,Czech,Danish,Dutch,English,Estonian,Faroese,Finnish,Flemish,French,Galician,Georgian,German,Greek,Gujarati,Haitian,Haitian Creole,Hausa,Hawaiian,Hebrew,Hindi,Hungarian,Icelandic,Indonesian,Italian,Japanese,Javanese,Kannada,Kazakh,Khmer,Korean,Lao,Latin,Latvian,Letzeburgesch,Lingala,Lithuanian,Luxembourgish,Macedonian,Malagasy,Malay,Malayalam,Maltese,Mandarin,Maori,Marathi,Moldavian,Moldovan,Mongolian,Myanmar,Nepali,Norwegian,Nynorsk,Occitan,Panjabi,Pashto,Persian,Polish,Portuguese,Punjabi,Pushto,Romanian,Russian,Sanskrit,Serbian,Shona,Sindhi,Sinhala,Sinhalese,Slovak,Slovenian,Somali,Spanish,Sundanese,Swahili,Swedish,Tagalog,Tajik,Tamil,Tatar,Telugu,Thai,Tibetan,Turkish,Turkmen,Ukrainian,Urdu,Uzbek,Valencian,Vietnamese,Welsh,Yiddish,Yoruba}]
               [--temperature TEMPERATURE] [--best_of BEST_OF] [--beam_size BEAM_SIZE] [--patience PATIENCE]
               [--length_penalty LENGTH_PENALTY] [--suppress_tokens SUPPRESS_TOKENS] [--initial_prompt INITIAL_PROMPT]
               [--condition_on_previous_text CONDITION_ON_PREVIOUS_TEXT] [--fp16 FP16]
               [--temperature_increment_on_fallback TEMPERATURE_INCREMENT_ON_FALLBACK]
               [--compression_ratio_threshold COMPRESSION_RATIO_THRESHOLD] [--logprob_threshold LOGPROB_THRESHOLD]
               [--no_speech_threshold NO_SPEECH_THRESHOLD] [--word_timestamps WORD_TIMESTAMPS]
               [--prepend_punctuations PREPEND_PUNCTUATIONS] [--append_punctuations APPEND_PUNCTUATIONS]
               [--highlight_words HIGHLIGHT_WORDS] [--max_line_width MAX_LINE_WIDTH] [--max_line_count MAX_LINE_COUNT]
               [--max_words_per_line MAX_WORDS_PER_LINE] [--threads THREADS]
               audio [audio ...]

positional arguments:
  audio                 audio file(s) to transcribe

options:
  -h, --help            show this help message and exit
  --model MODEL         name of the Whisper model to use (default: small)
  --model_dir MODEL_DIR
                        the path to save model files; uses ~/.cache/whisper by default (default: None)
  --device DEVICE       device to use for PyTorch inference (default: cpu)
  --output_dir OUTPUT_DIR, -o OUTPUT_DIR
                        directory to save the outputs (default: .)
  --output_format {txt,vtt,srt,tsv,json,all}, -f {txt,vtt,srt,tsv,json,all}
                        format of the output file; if not specified, all available formats will be produced (default: all)
  --verbose VERBOSE     whether to print out the progress and debug messages (default: True)
  --task {transcribe,translate}
                        whether to perform X->X speech recognition ('transcribe') or X->English translation ('translate') (default:
                        transcribe)
  --language {af,am,ar,as,az,ba,be,bg,bn,bo,br,bs,ca,cs,cy,da,de,el,en,es,et,eu,fa,fi,fo,fr,gl,gu,ha,haw,he,hi,hr,ht,hu,hy,id,is,it,ja,jw,ka,kk,km,kn,ko,la,lb,ln,lo,lt,lv,mg,mi,mk,ml,mn,mr,ms,mt,my,ne,nl,nn,no,oc,pa,pl,ps,pt,ro,ru,sa,sd,si,sk,sl,sn,so,sq,sr,su,sv,sw,ta,te,tg,th,tk,tl,tr,tt,uk,ur,uz,vi,yi,yo,yue,zh,Afrikaans,Albanian,Amharic,Arabic,Armenian,Assamese,Azerbaijani,Bashkir,Basque,Belarusian,Bengali,Bosnian,Breton,Bulgarian,Burmese,Cantonese,Castilian,Catalan,Chinese,Croatian,Czech,Danish,Dutch,English,Estonian,Faroese,Finnish,Flemish,French,Galician,Georgian,German,Greek,Gujarati,Haitian,Haitian Creole,Hausa,Hawaiian,Hebrew,Hindi,Hungarian,Icelandic,Indonesian,Italian,Japanese,Javanese,Kannada,Kazakh,Khmer,Korean,Lao,Latin,Latvian,Letzeburgesch,Lingala,Lithuanian,Luxembourgish,Macedonian,Malagasy,Malay,Malayalam,Maltese,Mandarin,Maori,Marathi,Moldavian,Moldovan,Mongolian,Myanmar,Nepali,Norwegian,Nynorsk,Occitan,Panjabi,Pashto,Persian,Polish,Portuguese,Punjabi,Pushto,Romanian,Russian,Sanskrit,Serbian,Shona,Sindhi,Sinhala,Sinhalese,Slovak,Slovenian,Somali,Spanish,Sundanese,Swahili,Swedish,Tagalog,Tajik,Tamil,Tatar,Telugu,Thai,Tibetan,Turkish,Turkmen,Ukrainian,Urdu,Uzbek,Valencian,Vietnamese,Welsh,Yiddish,Yoruba}
                        language spoken in the audio, specify None to perform language detection (default: None)
  --temperature TEMPERATURE
                        temperature to use for sampling (default: 0)
  --best_of BEST_OF     number of candidates when sampling with non-zero temperature (default: 5)
  --beam_size BEAM_SIZE
                        number of beams in beam search, only applicable when temperature is zero (default: 5)
  --patience PATIENCE   optional patience value to use in beam decoding, as in https://arxiv.org/abs/2204.05424, the default (1.0) is
                        equivalent to conventional beam search (default: None)
  --length_penalty LENGTH_PENALTY
                        optional token length penalty coefficient (alpha) as in https://arxiv.org/abs/1609.08144, uses simple length
                        normalization by default (default: None)
  --suppress_tokens SUPPRESS_TOKENS
                        comma-separated list of token ids to suppress during sampling; '-1' will suppress most special characters except
                        common punctuations (default: -1)
  --initial_prompt INITIAL_PROMPT
                        optional text to provide as a prompt for the first window. (default: None)
  --condition_on_previous_text CONDITION_ON_PREVIOUS_TEXT
                        if True, provide the previous output of the model as a prompt for the next window; disabling may make the text
                        inconsistent across windows, but the model becomes less prone to getting stuck in a failure loop (default: True)
  --fp16 FP16           whether to perform inference in fp16; True by default (default: True)
  --temperature_increment_on_fallback TEMPERATURE_INCREMENT_ON_FALLBACK
                        temperature to increase when falling back when the decoding fails to meet either of the thresholds below (default:
                        0.2)
  --compression_ratio_threshold COMPRESSION_RATIO_THRESHOLD
                        if the gzip compression ratio is higher than this value, treat the decoding as failed (default: 2.4)
  --logprob_threshold LOGPROB_THRESHOLD
                        if the average log probability is lower than this value, treat the decoding as failed (default: -1.0)
  --no_speech_threshold NO_SPEECH_THRESHOLD
                        if the probability of the <|nospeech|> token is higher than this value AND the decoding has failed due to
                        `logprob_threshold`, consider the segment as silence (default: 0.6)
  --word_timestamps WORD_TIMESTAMPS
                        (experimental) extract word-level timestamps and refine the results based on them (default: False)
  --prepend_punctuations PREPEND_PUNCTUATIONS
                        if word_timestamps is True, merge these punctuation symbols with the next word (default: "'“¿([{-)
  --append_punctuations APPEND_PUNCTUATIONS
                        if word_timestamps is True, merge these punctuation symbols with the previous word (default: "'.。,，!！?？:：”)]}、)
  --highlight_words HIGHLIGHT_WORDS
                        (requires --word_timestamps True) underline each word as it is spoken in srt and vtt (default: False)
  --max_line_width MAX_LINE_WIDTH
                        (requires --word_timestamps True) the maximum number of characters in a line before breaking the line (default:
                        None)
  --max_line_count MAX_LINE_COUNT
                        (requires --word_timestamps True) the maximum number of lines in a segment (default: None)
  --max_words_per_line MAX_WORDS_PER_LINE
                        (requires --word_timestamps True, no effect with --max_line_width) the maximum number of words in a segment
                        (default: None)
  --threads THREADS     number of threads used by torch for CPU inference; supercedes MKL_NUM_THREADS/OMP_NUM_THREADS (default: 0)
```


Jetzt haben wir alle benötigen, einmaligen Installationen und können Whisper verwenden.


## Benutzung Whisper 

### "Ort" Im Terminal

Im Terminal ist man immer an einer bestimmten Stelle in der Ordnerstruktur des Rechners. Alle Befehle, die man im Terminal ausführt, beziehen sich auf die Stelle in der Ordnerstruktur, an der man sich gerade befindet.

Mit `pwd` kann man sich den aktuellen "Ort", also das Verzeichnis, in dem man sich mit dem Termin befindet, anzeigen lassen. Nach dem ersten Öffnen des Terminals ist der Ort vermutlich etwas Entsprechendes zu `/Users/legie`.

Nun wollen wir den Ort wechseln, um in dem Ordner zu arbeiten, wo unsere Audiodateien liegen und die Transkriptionen abgespeichert werden. Man kann sowohl für Eingabe- als auch Ausgabedateien individuelle Pfade angeben, aber wir vereinfachen das Szenario erst einmal dahin gehend, als dass wir alles in genau einem Ordner machen.

In welchem Ordner man genau arbeiten möchte, ist frei wählbar. Ihr müsst nur den Pfad zum Ordner wissen, z.B. `~/Documents/filmuni/01_project/whisper/`.

Um in diesen Ordner zu wechseln, verwenden wir den Befehl `cd` (change directory). Mit `cd` nimmt als Argument, also als Wert, den man nach dem Befehle selbst (`cd`) angeben muss, den Pfad zu dem Ort (also Verzeichnis) zu dem man wechseln möchte.

Zum Beispiel, aktuell befinde ich mich im Terminal in `/Users/legie` (mit `pwd` angezeigt). Nun kann man mit folgendem Befehl in den gewünschten Ordner wechseln"

```
cd Documents/filmuni/01_project/whisper/
```

Test, ob alles gut gegangen ist: `pwd` gibt `~/Documents/filmuni/01_project/whisper` zurück.

Alternativ zum Eintippen des Pfads kann man `cd` im Terminal eintippen (ohne Enter zu drücken!) und dann den Ordner, zu dem man navigieren möchte, per Drag-and-drop aus dem Finder als Pfad angeben. Also

* `cd`
* Dann Ordner, in den man möchte, in den Terminal ziehen. Dadurch wird der Befehl zu
* `cd ~/Documents/filmuni/01_project/whisper`
* Enter


### Whisper Ausführen

Die folgende Beschreibung geht davon, dass die zu transkribierende Audiodatei in dem Ordner liegt, in dem man sich im Terminal befindet. Alles andere würde zu einem Fehler führen. Z.B. in `~/Documents/filmuni/01_project/whisper` gibt es die Datei `Int_8-2_DS.m4a`.

Als ersten Test verwenden wir whisper mit den Voreinstellung. Dafür den Befehl `whisper` mit dem Namen der Audiodatei als Argument ausführen, z.B.:

```
whisper Int_8-2_DS.m4a
```

Enter drücken und warten, bis die Berechnungen fertig sind (das kann etwas dauern). Im Terminal wird der Prozess textuell dokumentiert - was man ignorieren kann. Wenn das Ausführen fertig ist, erscheint im Terminal eine neue, leere Zeile, bereit für weitere Befehle. Danach sollten im Ordner selbst die verschiedenen Transkiptionsdateien liegen.

*To be continued...*

