# ⛩️

## 参考

## 进步

* ❓ how is BSON more binary than JSON itself? https://stackoverflow.com/questions/3554325/why-is-it-called-bson 📙 Kleppmann ch. 4
* https://wizardzines.com/zines/integers-floats/

* _24_: split into own file
* _22_: protocol (encoding, serialization)
* _21_: prefix code

# 🪪 ENCODING

🔍 https://bestasciitable.com/

---

OVERVIEW https://www.youtube.com/watch?v=DntKZ9xJ1sM
* _ASCII_: maps character to bit e.g. `A` -> 1000001 (65)
* _Unicode_: maps character to code point e.g. `A` -> U+0041
* _code point_: hex repr character
* _UTF-8_: maps Unicode code point to byte sequence https://csvbase.com/blog/9
* variable length = can use single byte for `A` but more bytes (up to 4) if necessary

https://en.wikipedia.org/wiki/Character_encoding

```sh
# app reads bytes from disk
1101000 1100101 1101100 1101100 1101111 
# app uses UTF-8 to decode
104 101 108 108 111 
# app uses Unicode
"hello"
```

CHARACTER SET
* _Unicode_: character set https://stackoverflow.com/a/13212528
* i.e. way to identify each character uniquely https://practicaltypography.com/ligatures-in-programming-fonts-hell-no.html
* _character set_: KV set in which K = characters and V = code point e.g. A = 41
* single byte (Latin) vs. multibyte (Japanese) 📙 Beaulieu [21]
* _code point_: numerical value in character set e.g. `0x0394 `https://www.fluentpython.com/lingo/#code_point 📍 https://www.textualize.io/blog/posts/7-things-about-terminals
* file types have https://the.exa.website/features/icons

encoding
* UTF-8: encoding
* encoding: algo that transforms number to binary and vice versa
```python
def utf8(num):
    return binary

utf8(1)  # 00000001
utf8(2)  # 00000010
utf8(3)  # 00000011
utf8(4)  # 00000100
```

* 📙 Bryant computer systems chapter 1
* _error correction_: 📙 MacCormick 5 https://en.wikipedia.org/wiki/Error_detection_and_correction
* _code point_: char https://en.wikipedia.org/wiki/Code_point https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/ 

* _iconv_: convert encoding https://kadekillary.work/post/cli-4-ds/
* emoji https://darrenburns.net/posts/unicode-emoji/

DIGRAPHS
* digraph: two letters forming single phoneme e.g. "ea" in "bread"
* __digraph__: Unicode char not on typical keyboard e.g. °∆ http://vimdoc.sourceforge.net/htmldoc/digraph.html#digraph-table
* specified in RFC 1345 https://datatracker.ietf.org/doc/html/rfc1345
* `^M` = newline/carriage return

prefix codes https://gist.github.com/joepie91/26579e2f73ad903144dd5d75e2f03d83
* _prefix code_: encoding mechanism
```yaml
161133
```
* _codeword_: individual values
* cannot share prefix e.g. `[3, 11, 22]` valid but `[1, 11, 22]` invalid bc `1` and `11` share prefix
* decode prefix code by applying codewords
```yaml
# prefix
161133
# codewords
[1, 2, 33, 50, 61]

# must be 1 bc no other codeword can start w/ 1
1 61133
# and so on for rest
1 61 1 33
```
https://en.wikipedia.org/wiki/Mojibake
https://terminaltrove.com/lemmeknow/
https://github.com/abhimanyu003/sttr


* `\r`: carriage return https://stackoverflow.com/a/1761086/6813490
* `\n`: new line
* `\t`: in a string literal is an escape sequence for tab character, horizontal whitespace, ASCII codepoint 9 https://stackoverflow.com/a/22116523/6813490

* _EOF_: not a char https://ruslanspivak.com/eofnotchar/
* _BOM_: https://www.fluentpython.com/lingo/#BOM
* en-dash, m-dash, hyphen https://www.punctuationmatters.com/en-dash-em-dash-hyphen/

* `r`: carriage return https://stackoverflow.com/a/1761086/6813490
* `n`: new line
* `\t`: in a string literal is an escape sequence for tab character, horizontal whitespace, ASCII codepoint 9 https://stackoverflow.com/a/22116523/6813490

## ascii

🗄️ `info.md` diagrams

TOOLS
* editor https://monodraw.helftone.com/
* art https://www.asciiart.eu/
* to SVG https://code.sgo.to/2022/06/20/typographic-diagrams.html https://github.com/ivanceras/svgbob https://github.com/google/typograms https://ditaa.sourceforge.net/ https://casual-effects.com/markdeep/features.md.html#basicformatting/diagrams http://asciiflow.com/ https://github.com/ArthurSonzogni/Diagon

---

* _ASCII_: mapping from number to glyph (char) 📍 Petzold 15.181, computerphile 📚 Petzold code ch. 20 https://www.youtube.com/watch?v=XaGXPObx2Gs from pre 8-bit era; `man ascii` https://increment.com/programming-languages/unplain-text-primer-on-non-latin/

## Unicode

---

https://crates.io/crates/ucd-trie
https://docs.python.org/2/howto/unicode.html
https://docs.python.org/3/howto/unicode.html
https://mcilloni.ovh/2023/07/23/unicode-is-hard/
https://lucumr.pocoo.org/2014/1/5/unicode-in-2-and-3/
https://codepoints.net/
https://pyatl.dev/2024/09/01/bitten-by-unicode/
https://text.makeup/about/
📍 utf-8 vs. unicode https://youtu.be/SM9gJv08dm0 2:30 https://stackoverflow.com/questions/643694/what-is-the-difference-between-utf-8-and-unicode https://nbviewer.org/gist/guocheng/1ae6c2d76461a66cfc5ec6009b5791d1 https://docs.python.org/3/howto/unicode.html
* emoji, kanji https://www.fluentpython.com/extra/multi-character-emojis/ https://www.textualize.io/blog/posts/7-things-about-terminals

* _UTF8_: multi-byte i.e. characters outside of English just get more bytes thrown at them https://sethmlarson.dev/blog/utf-8 https://news.ycombinator.com/item?id=30259097 https://viralinstruction.com/posts/utf8/
* _Unicode_: char set https://stackoverflow.com/a/13212528/6813490 https://github.com/arp242/uni https://www.youtube.com/watch?v=MijmeoH9LT4 https://rentafounder.com/how-to-count-unicode-string-characters/ https://www.dampfkraft.com/ghost-characters.html code point, glyph, octal, hex https://realpython.com/courses/python-unicode/ `unicode-standard.pdf` https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/ https://en.wikipedia.org/wiki/Code_point CLI tool https://github.com/arp242/uni/ in Python https://blog.phylum.io/malicious-actors-use-unicode-support-in-python-to-evade-detection https://news.ycombinator.com/item?id=37735801 https://realpython.com/python-sort-unicode-strings/
* unicode, emoji in the terminal https://news.ycombinator.com/item?id=37047785
> Since the distinction between string and unicode has been done away with in Python 3, __unicode__ is gone and __bytes__ (which behaves similarly to __str__ and __unicode__ in 2.7) exists for a new built-in for constructing byte arrays. https://rszalski.github.io/magicmethods/#appendix2

## UUID

🔗 https://en.wikipedia.org/wiki/Universally_unique_identifier

VERSIONS https://www.rfc-editor.org/rfc/rfc9562.html https://www.ntietz.com/blog/til-uses-for-the-different-uuid-versions/
* version 1: generated from timestamp, monotonic counter, and a MAC address
> don't use
* version 2: reserved for security IDs with no known details
* version 3: generated from MD5 hashes of some data you provide; RFC suggests DNS and URLs among the candidates for data.
> superseded by version 5
* version 4: generated from entirely random data; this is probably what most people think of and run into with UUIDs.
> default
* version 5: generated from SHA1 hahes of some data you proivde; RFC suggests DNS or URLs as candidates for data.
> if you have your own data you want in the UUID
* version 6: generated from timestamp, monotonic counter, and a MAC address; same data as Version 1 but they change the order so that sorting them will sort by creation time.
> don't use
* version 7: generated from a timestamp and random data.
> if you're using in a context where you want to be able to sort e.g. database keys
* version 8: entirely custom (besides the required version/variant fields that all versions contain).
> if you have your own data you want in the UUID

# 🗃️ FILE FMT

🗄️ `eng.md` munge

QUERY TOOLS
* https://github.com/julien040/anyquery
* _qq_: https://github.com/JFryy/qq
* https://github.com/simonw/sqlite-utils
* https://github.com/harelba/q
* https://github.com/multiprocessio/dsq
* https://github.com/datafold/data-diff
* https://github.com/mithrandie/csvq
* https://github.com/dinedal/textql
* https://github.com/noborus/trdsql

---

https://kdl.dev/ https://zellij.dev/documentation/layouts
> this is what started me to split protocols into own file apart from `computation.md`

XML
* https://news.ycombinator.com/item?id=35467711
* element types: prolog, root node/element, child node/elements
* _XSLT_: CSS for XML
* _XPath_: CSS selector for XML
* comments: same as HTML
* previously more popular 📙 Beaulieu 2.34

YAML
* query https://github.com/mikefarah/yq
* _CUE_: https://cuelang.org/ https://news.ycombinator.com/item?id=34074386 alternative https://dagger.io/ CI https://news.ycombinator.com/item?id=30857012

📙 Kleppmann ch. 4
🗄
* `python.md` serialization
* `shell.md` design
* `sql.md` munge/sanitization

* _serialize_: convert obj to interchange fmt
* _deserialize_: convert interchange fmt to obj
* _schema_: mapping of obj to interchange fmt structure
* you typically want to specify
> Pickles are implicit: they serialize everything in your objects, even data you didn’t want to serialize. For example, you might have an attribute that is a cache of computation that you don’t want serialized. Pickle doesn’t have a convenient way to skip that attribute. https://nedbatchelder.com/blog/202006/pickles_nine_flaws.html

## CSV

TOOLS
* query https://news.ycombinator.com/item?id=38889820 https://github.com/jqnatividad/qsv https://github.com/neilotoole/sq
* editor https://www.moderncsv.com/
* _csvdiff_: ✅ diff https://github.com/aswinkarthik/csvdiff
* _csview_: ✅ cat https://github.com/wfxr/csview
* _csvlens_: ✅ less page https://github.com/YS-L/csvlens

SEMANTICS
* _header line_: line with col names https://miller.readthedocs.io/en/latest/glossary/#header-line
* header not always first line, detection non-trivial https://news.ycombinator.com/item?id=28299015
* _data line_: line with data https://miller.readthedocs.io/en/latest/customization/
* _field_: value, either in header line or data line https://miller.readthedocs.io/en/latest/10min/#handling-field-names-with-spaces

DESIGN
* no firm spec https://peps.python.org/pep-0305/#abstract
* better for streaming bc each line of file is valid CSV (unlike JSON) https://jfhr.me/consider-using-csv/
* gaining in popularity https://twobithistory.org/2017/09/21/the-rise-and-rise-of-json.html#fnref:2 
* some parsers don't impl escaping rules correctly 📙 Kleppmann 4.145
* comments: no standard from RFC 4180, parser can set https://stackoverflow.com/a/14428538 https://stackoverflow.com/a/1961018
* _DSV_: same as `.dat` https://en.wikipedia.org/wiki/Delimiter-separated_values https://www.thoughtspot.com/blog/csv-vs-delimited-flat-files-how-choose
* _TSV_: https://news.ycombinator.com/item?id=40622760

## JSON

🗄️ `algos.md` tree
🛠 https://github.com/burningtree/awesome-json

OPERATIONS
* fmt: `python3 -m json.tool music-lib.json > music-lib-fmt.json` https://orbifold.xyz/check-in-json.html
* _dasel_: edit https://github.com/TomWright/dasel
* _jo_: ✅ generate https://github.com/jpmens/jo
* _graphtage_: ❌ diff https://github.com/trailofbits/graphtage broken https://github.com/trailofbits/graphtage/issues/91 🗄️ `shell.md` file / diff

### design

📜 http://www.json.org/
🗄️ `telemetry.md` logging / JSONL

```json
{"a": "b"}

{
    "topLevel": "val",
    "myList": [1,2,3],
    "topObj": {
        "foo": false
    }
}
```

---

* https://seriot.ch/projects/parsing_json.html
* benefits: readable, tooling, mindshare 📙 Jeffrey distributed [4]
* objs: colloquially (start/end w/ braces) https://youtu.be/SM9gJv08dm0 0:30 literally (doesn't exist) http://benalman.com/news/2010/03/theres-no-such-thing-as-a-json/
* typing: str, bool, array, num (int/float considered the same, which can be problem w/ large numbers) 📙 Kleppmann [144]
* no comments https://stackoverflow.com/a/4183018
* no binary strings 📙 Kleppmann [144]
* history https://twobithistory.org/2017/09/21/the-rise-and-rise-of-json.html
* as output for Unix utils https://blog.kellybrazil.com/2019/11/26/bringing-the-unix-philosophy-to-the-21st-century/ https://github.com/kellyjonbrazil/jc https://news.ycombinator.com/item?id=22608045 https://kellyjonbrazil.github.io/jc/
* for sharing logic btw frontend/backend https://news.ycombinator.com/item?id=27306263

### query (jq)

ALTERNATIVES
* SQLite CLI
* DuckDB https://www.pgrs.net/2024/03/21/duckdb-as-the-new-jq/ https://news.ycombinator.com/item?id=35009612 https://duckdb.org/2023/03/03/json.html 
* _jaq_: rewrite https://github.com/01mf02/jaq
* _jnv_: 🎯 interactive https://github.com/ynqa/jnv
* _jqp_: TUI https://github.com/noahgorstein/jqp 
* _mistql_: Python and CLI https://www.mistql.com/
* _sq_: https://news.ycombinator.com/item?id=41760697

JQ 📜 https://stedolan.github.io/jq/manual 
* intro https://earthly.dev/blog/jq-select/
* guide https://sequoia.makes.software/parsing-json-at-the-cli-a-practical-introduction-to-jq-and-more
```sh
# test dats
curl https://api.github.com/repos/stedolan/jq/issues?per_page=5 | jq
cat foo.json | jq

jq .  # pretty print
jq -r  # unquoted/raw output https://stackoverflow.com/a/44656583
jq '.[4]'  # get el in array
jq ' .key.subkey'  # get key
jq '.[4].title'  # get key from el in array
jq '.[].title'  # get key from every el in array
jq '.title'  # get key from streams of obj
jq '.[].reactions|select(.total_count>8)'  # filter
jq '.[]|select(.num_receipts>0)|select(.is_migrated == true)|.artist_id'  # filter
```

### view (jless)

💡 drilldown as a general category (fs, JSON, trees) https://github.com/xgi/castero

JLESS 📜 https://jless.io/
* theme https://github.com/PaulJuliusMartinez/jless/issues/4
* commands
```sh
# GOTO
H    # parent
g    # top
gg   # bottom

# NAV
j/k  # scroll children
J/K  # scroll parents
CTRL d/u  # page

# DISPLAY
space | h/l  # collapse/expand
c  # collapse all
pp  ## print
zz  # center
```

---

* https://github.com/fioncat/otree
* https://github.com/gulyasm/jsonui
* _JSON Viewer_: browser syntax highlighting https://chromewebstore.google.com/detail/json-viewer/gbmdgpbipfallnflgajpaliibnhdgobh
* _JSON crack_: visualize https://github.com/AykutSarac/jsoncrack.com https://jsoncrack.com/
* _json4u_: jsoncrack clone https://news.ycombinator.com/item?id=41634356

## Parquet

---

* https://csvbase.com/blog/3
* https://r4ds.hadley.nz/arrow#sec-parquet
* partition elimination https://duckdb.org/2021/12/03/duck-arrow.html
* https://pythonspeed.com/articles/best-file-format-for-pandas/
* https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page
* _Parquet_: column-oriented file format, like CSV https://www.youtube.com/watch?v=H_dLfHETO0g https://news.ycombinator.com/item?id=35418933 https://news.ycombinator.com/item?id=29010103
* easier to use now vs. CSV https://news.ycombinator.com/item?id=30595026
* use to build no-code API https://tech.marksblogg.com/roapi-rust-data-api.html
* pyarrow https://www.blog.pythonlibrary.org/2024/05/06/how-to-read-and-write-parquet-files-with-python/

# 🧮 NUMBERS

---

📚
* Bryant computer systems ch. 2
* Petzold annotated turing
* Petzold code ch. 7-9
* Shibuya microprocessors ch. 1

SEMANTICS
* _number_: idea used for proofs https://en.wikipedia.org/wiki/Number
* _numeral system_: math notation for representing numbers
* more symbols = less space e.g. hex requires less places than binary
* _radix (base)_: number of digits in number system 📙 Petzold code 186
* fewer number of states = less ambiguity i.e. we don't use ternary or quinary for transistor 📙 Kozeriok 4.63 https://www.youtube.com/watch?v=gI-qXk7XojA 1:20
* _digit_: symbol to represent a number https://en.wikipedia.org/wiki/Numerical_digit

| SYSTEM      | RADIX         | REPR OF 231 | USE [PETZOLD CODE 181]
| ----------- | ------------- | ----------- | ---------------------------------------- |
| binary      | two (0-1)     | 1110111     | precise                                  |
| decimal     | ten (0-9)     | 231         | readable                                 |
| hexademical | sixteen (0-f) | e7          | easy converion to binary (unlike decimal)|
| ----------- | ------------- | ----------- | -----------------------------------------|

## binary

📚 Petzold code 3, 9, 12-13

---

* _bit_: binary digit; aka 'flag' [Kozierok 4.63]
* _bitmask_: toggling bit https://www.arp242.net/bitmask.html set (to 1) reset/clear (to 0) [Kozierok 4.63]
* _nybble_: 4 bits [Petzold code 181]
* _byte_: 8 bits
* aka octet https://stackoverflow.com/a/21463473/6813490
* 255 possible values https://www.youtube.com/watch?v=dPxCGlW9lfM 5:10
* _byte string_: sequence of bytes https://stackoverflow.com/a/31322359 https://www.fluentpython.com/lingo/#byte_string
* _kilobyte_: 1k bytes
* other sizes: MB, GB, TB, petabyte (1024 tb) exabyte (1B GB) https://stackoverflow.com/a/1241234 [Kozierok 4.63]
* _bit width_: number of bits needed to represent an int e.g. on Intel processors ints are 4 bytes wide https://boredzo.org/pointers/#starting
* add by carrying over e.g. 1 + 1 = 10 [Manga 1.43]
* _two's complement_: how to do substraction on binary, represent negative numbers [Petzold code 15.180, Petzold code 12-13 Manga 1.44-46]
* _high-order bit (MSB)_: bit position w/ greatest value e.g. in 101 the eighths position is the MSB https://en.wikipedia.org/wiki/Bit_numbering also used to mean "most salient point"  https://danluu.com/corp-eng-blogs/ https://diff.substack.com/p/big-tech-sees-like-a-state

decimal in binary
* _unsigned_: positive
* _signed_: positive and negative; can reserve leftmost bit for sign https://www.interviewcake.com/article/python3/data-structures-coding-interview#binary-numbers
* _fixed width_: has specific size e.g. 32 or 64 bits https://www.interviewcake.com/article/python3/data-structures-coding-interview#fixed-width-nums
* _floating point_: 1,230,000 as 1.23 (significand) * 10^6 (exponent) w/ significand as always greater than 1 but less than 2 [manga 42-3]; faster for CPU computation; makes getting a high-level language to behave like your desktop calculator more difficult than you'd expect https://stefanoborini.com/why-01-plus-02-is-not-03-in-python/ https://docs.python.org/3/tutorial/floatingpoint.html https://stackoverflow.com/a/46700365/6813490 https://stackoverflow.com/a/50340297/6813490 https://0.30000000000000004.com/ fractions also get weird, too https://orbifold.xyz/numbers.html 📜 Van Rossum ch. 8 https://jvns.ca/blog/2023/01/13/examples-of-floating-point-problems/ https://jvns.ca/blog/2023/01/13/examples-of-floating-point-problems/ https://github.com/francisrstokes/githublog/blob/main/2024%2F5%2F29%2Ffast-inverse-sqrt.md
> 10000 is 100%. We're using integers so that we're not using floats. Floats and money are a bad combination. https://jvns.ca/blog/2023/02/08/why-does-0-1-plus-0-2-equal-0-30000000000000004/
> https://ciechanow.ski/exposing-floating-point/
```python
value = 0.1 + 0.2
f"{val:.{1}}"  # 0.3
val = 45 * (0.1 + 0.2)
f"{val:.{4}}"  # 13.5
```

## hex

📚 Petzold code ch. 15

---

* _hexit_: hex digit (1 nybble) https://www.youtube.com/watch?v=dPxCGlW9lfM 4:30
* used bc easier to convert to binary than decimal [Petzold code 181 https://www.youtube.com/watch?v=dPxCGlW9lfM 4:20]
* _viewer_: https://github.com/sharkdp/hexyl https://github.com/wader/fq https://github.com/WerWolv/ImHex `hexdump -C <file>` https://www.youtube.com/watch?v=-eDY7yh-CyA 1:50 https://github.com/wader/fq
* _editor_: online https://hexed.it/ macOS https://ridiculousfish.com/hexfiend/ hexedit https://news.ycombinator.com/item?id=23762626 https://github.com/thetacom/hexabyte

# 🟨 ZA

CASE
* snake case: `hello_world`
* kebab case: `hello-world`
* camel case: `helloWorld`
* Pascal case: `HelloWorld`

---

* _encode_: 动 convert to diff fmt 📙 MacCormick 5.66
* typically byte per/char https://stackoverflow.com/a/31322359
> Each byte represents some text character in the program. 📙 Bryant 1.1
* multibyte = n byte per/char e.g. Japanese 📙 Beaulieu 2.19
* can be anything e.g. Morse code (dot/dash to text) 📙 Sweigart 1.3
* QR/bar code https://boonepeter.github.io/posts/2020-11-10-spotify-codes/ https://news.ycombinator.com/item?id=32837565&utm_term=comment
* _decode_: 动 convert back to original fmt https://stackoverflow.com/a/31322359
```yaml
1: "A"  # encode
"A": 1  # decode
```
* _character set_: alphabet + syllabary https://en.wikipedia.org/wiki/Character_encoding#Terminology 🗄 `sociology.md` linguistics/grammar
* used synonymously with 'encoding'
> When I discovered that the popular web development tool PHP has almost complete ignorance of character encoding issues, blithely using 8 bits for characters, making it darn near impossible to develop good international web applications, I thought, enough is enough. https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/

🗄 `sociology.md` linguistics
📙
* Bhargava ch. 5
* MacCormick ch. 4

* _format_: rules for information structure https://format.wtf/examples https://en.wikipedia.org/wiki/Format
* _encoding_: rules for conversion from one fmt to another https://en.wikipedia.org/wiki/Code
* used as both noun and verb
* _serialization_: encoding for obj in-mem to text/binary and vice versa https://www.fluentpython.com/lingo/#serialization 📙 Kleppmann [113]
* _protocol_: rules for communication system https://en.wikipedia.org/wiki/Communication_protocol
* sometimes used synonymously with "encoding" https://blainsmith.com/articles/plain-text-protocols/

* _unstructured text_: e.g. Unix tools
* flexible http://www.catb.org/~esr/writings/taoup/html/ch05s01.html https://news.ycombinator.com/item?id=23630640
* leads to complexity https://danluu.com/cli-complexity/ 
* _structured text_: e.g. Powershell, JSON, CSV, XML, HTTP/1 https://news.ycombinator.com/item?id=27431998
* operating systems use of https://news.ycombinator.com/item?id=28301646

* _codec_: https://www.fluentpython.com/lingo/#codec https://en.wikipedia.org/wiki/Code

semantics https://stackoverflow.com/a/41217889
* _protocol_: encoding for computer networking https://blainsmith.com/articles/plain-text-protocols/
* impl can interact; e.g. HTTP - JS client can talk to Python server
* overlap with linguistics https://www.unicode.org/versions/Unicode14.0.0/appE.pdf
* representing integers, Google had to switch from 32-bit to 64-bit for Gangnam Style https://www.interviewcake.com/article/python3/data-structures-coding-interview#fixed-width-nums https://danielmiessler.com/study/encoding/ https://kunststube.net/encoding/ https://kunststube.net/frontback/ https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/
* _base64_: 🗄 `4-application.md` 'headers' https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication#Authentication_schemes

semantics
* _protocol_: fmt https://blainsmith.com/articles/plain-text-protocols/
* "implement protocol/spec" = create library for language to read/write data in that protocol https://msgpack.org/ https://github.com/polyglotted/msgpack-python/tree/master/msgpack https://github.com/aviramha/ormsgpack https://bsonspec.org/faq.html https://bsonspec.org/spec.html
* _serialization_: convert obj to protocol for network transmission 
* _encoding_: protocol to represent non-digital (text, audio) as digital 📙 Petzold ch. 20
* i.e. binary files don't have encoding themselves but have text fields w/ encoding https://stackoverflow.com/a/38264655
* synonym for conversion in general e.g. Morse code dot/dash to electrical signal 📙 Sweigart ciphers 3 https://www.reddit.com/r/AskProgramming/comments/c8pssr/comment/esom0gi/

semantics
* _serialization_: encoding for data interchange 📙 Kleppmann [115] https://www.fluentpython.com/lingo/#serialization
* no one uses language-specific versions e.g. Pickle 📙 Kleppmann [114]

* _encoding_: spec for conversion https://en.wikipedia.org/wiki/Code
* e.g. mp3 spec for how to encode audio 📙 Sweigart 1.3

## serialization

---

BINARY
* e.g. HTTP/2 https://news.ycombinator.com/item?id=27431998
* used more for internal services 📙 Jeffrey distributed [5]
* db res in binary which is parsed by language-specific API 📙 Kleppmann 4.128
📙 Kleppmann 4.117, 4.122, 4.130
* _BSON_: binary JSON + SQL datatypes https://bsonspec.org/
* can be less space efficient due to datatypes https://en.wikipedia.org/wiki/BSON#Efficiency
* faster to parse https://bsonspec.org/faq.html
* datatypes: JSON + date, binary, num (int, long, float) https://youtu.be/SM9gJv08dm0 2:25
* _Capn Proto_: https://capnproto.org/
* sustainable? https://github.com/capnproto/capnproto/issues/2067
* _MessagePack_: like BSON https://msgpack.org/ https://neovim.io/ 📙 Kleppmann [4.116]

AVRO
* serialization format https://avro.apache.org/docs/current/
* better than CSV bc handles typing, cells missing data
* CSV disadvantages: inferred data types https://www.youtube.com/watch?v=SZX9DM_gyOE 1:20
* SQL disadvantages: flat
* competes with Thrift, Protocol Buffers https://avro.apache.org/docs/current/
* Python tutorial https://avro.apache.org/docs/current/gettingstartedpython.html
* https://www.youtube.com/watch?v=kq_JCVcHJLE

PROTOCOL BUFFERS (PROTOBUF)
* convert/query https://github.com/dflemstr/rq
* like BSON https://bsonspec.org/ https://github.com/bufbuild/buf
* https://vincent.bernat.ch/en/blog/2023-dynamic-protobuf-golang
* https://news.ycombinator.com/item?id=36798824
* curl for https://github.com/qaware/protocurl https://news.ycombinator.com/item?id=34866155
* compared to docarray, JSON https://docarray.jina.ai/get-started/what-is/#comparing-to-alternatives
* features that JSON doesn't have like versioning, types 📙 Jeffrey distributed [5]
* in Python https://www.fluentpython.com/extra/parsing-binary-struct/ https://www.blog.pythonlibrary.org/2023/08/30/an-intro-to-protocol-buffers-with-python/
