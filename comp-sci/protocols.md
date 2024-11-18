# ⛩️

## 参考

🗄️ `data/modeling.md`

## 进步

SEGMENTS
> 📍 can you give me a breakdown of the elements in the following x12 segments: ISA, GS, IEA
> 📍 what are the most common segment IDs in an x12 850 document?
```sh
BEG*00*SA*12345**20231014~
BEG # segment ID
SA # order type
12345 # order number
20231014 # date
```

STEDI TEACHING https://www.stedi.com/edi
* https://www.stedi.com/blog/getting-started-with-the-x12-file-format
* https://www.stedi.com/docs/edi-platform/edi-essentials/what-is-edi#what-is-edi
* https://www.stedi.com/blog/edi-for-developers-turn-edi-into-json
* https://www.stedi.com/blog/transaction-set-variants-in-the-amazon-850-purchase-order
* control numbers https://www.stedi.com/blog/control-numbers-in-x12-edi
* https://www.stedi.com/blog/date-and-time-in-edi
* standards at national level https://increment.com/apis/introduction-apis-egovernment/

CLEANUP
* https://chatgpt.com/c/671fa6c4-e0bc-8004-9937-f66fd3ce06b2
* grok segments from chatgpt code block
* https://chatgpt.com/c/670d4d6e-c8c4-8004-91d1-052b4c33c416
* segment types https://github.com/sezna/edi

STEDI THE COMPANY
* https://www.stedi.com/edi/network
* https://www.stedi.com/blog/excerpts-from-the-annual-letter
* https://www.stedi.com/blog/two-messy-kittens-and-a-missing-edi-214
* https://www.stedi.com/blog/shareable-edi-implementation-guides-for-modern-edi-integrations
* https://www.stedi.com/blog/hello-buckets https://www.stedi.com/blog/introducing-serverless-sftp-and-infinitely-scalable-data-storage
* https://www.stedi.com/blog/translate-between-json-and-edi
* https://www.stedi.com/blog/stedi-core-edi-integrations-in-minutes
* https://www.stedi.com/blog/stedi-platform-no-code-edi
* https://www.stedi.com/blog/introducing-stedis-x12-hipaa-guides
* https://www.stedi.com/blog/stedi-process-large-files https://www.stedi.com/blog/stedi-core-large-file-support
* create account? https://www.stedi.com/edi/inspector

* _24_: split into own file, file fmts (Cuelang, INI, KDL, YAML, EDI)
* _22_: protocol (encoding, serialization)
* _21_: prefix code

# 🟪️ EDI

COMPONENTS
* versions https://x12.org/news-and-events/release-schedule https://www.stedi.com/edi/x12-008050 https://www.stedi.com/blog/getting-started-with-the-x12-file-format
* _mailbag_: n envelopes
* _envelope_: a single x12 document and its transmission
* _segment_: LOC; terminated w/ `~`
* order: ISA, GSA (metadata), IEA comes last (InterchangeEnvelope)
* _element_: segment subcomponent; separated w/ `*`, dupe `**` = blank el

DOCUMENT LISTS
* _document list (DL)_: type of x12 document https://en.wikipedia.org/wiki/X12_Document_List
* aka transaction set https://www.stedi.com/edi/x12 https://x12.org/products/transaction-sets https://en.wikipedia.org/wiki/X12_Document_List
* each company picks a subset that they want to work with https://static.fishersci.com/cmsassets/downloads/segment/Scientific/pdf/WebServices/EDIspecGuideCust832.pdf
* file extension: `.edi`, `.x12`, `.dat`, `.txt`
* _832_: DL for catalog
* _850_: DL purchase order
* _855_: DL purchase order (= HTTP 200)
* _997_: DL for ack https://github.com/azoner/pyx12
* _999_: ? https://github.com/azoner/pyx12

ZA
* _qualifiers_: type for ID https://chatgpt.com/c/671fa56b-6de4-8004-a31a-7dc361d40c8b
* `ZZ` custom `01` DUNS `20` Health Industry Number (HIN) `30` U.S. Federal Tax Identification
* _transaction set purpose codes_: "why is document being sent?", only shows up in (typically) a single segment, can apply to multiple document lists (832, 850)
* `00` new `01` cancel previously sent doc `04` update `05` replace `06` ack receipt of sent doc `24` draft

## ISA

🧠 https://chatgpt.com/c/6723ec93-f688-8004-9390-f69468340e26 https://chatgpt.com/c/6723e31b-bf8c-8004-a801-41b1b4e52419

| EL      | DESC                     | TYPE | LEN |
|---------|--------------------------|------|-----|
| ISA01   | Auth Info Qualifier      | ID   | 2   |
| ISA02   | Auth Info                | AN   | 10  |
| ISA03   | Security Info Qualifier  | ID   | 2   |
| ISA04   | Security Info            | AN   | 10  |
| ISA05   | Sender ID Qualifier      | ID   | 2   |
| ISA06   | Sender ID                | AN   | 15  |
| ISA07   | Receiver ID Qualifier    | ID   | 2   |
| ISA08   | Receiver ID              | AN   | 15  |
| ISA09   | Date                     | DT   | 6   |
| ISA10   | Time                     | TM   | 4   |
| ISA11   | Repetition Separator     | 1B   | 1   |
| ISA12   | Version Number           | ID   | 5   |
| ISA13   | Control Number           | N0   | 9   |
| ISA14   | Acknowledgment Requested | ID   | 1   |
| ISA15   | Test Indicator           | ID   | 1   |
| ISA16   | Subelement Separator     | AN   | 1   |

---

> An X12 file starts with a fixed-length 106-byte header called an ISA segment. Among other things, this header specifies three different terminator characters to be used in the rest of the document...it's up to the author to ensure that the chosen terminators do not appear in any of the data fields. This is why each document can specify its own terminators. https://www.lambdafunctions.com/articles/racing-sed-with-rust

ISA15 (usage - test|prod)

## LIN

🧠 https://chatgpt.com/c/672a2132-cf28-8004-9afa-c0bd20a0ffa0

* _LIN_: ID e.g. UPC, SKU

## meta

STANDARDS BODIES
* _EDI_: fmt for business transactions (purchases orders, sales) https://en.wikipedia.org/wiki/Electronic_data_interchange
* _ASC x12_: US standards body for x12, created by ANSI https://en.wikipedia.org/wiki/ASC_X12 https://www.nist.gov/
* _x12_: USA EDI spec
* _EDIFACT_: EU EDI spec https://en.wikipedia.org/wiki/EDIFACT

MIDDLEMEN https://chatgpt.com/share/9b405f7d-4879-4985-be22-39fc267349f7
* new guys: https://www.stedi.com/edi/network https://www.orderful.com/
* _Conexiom_: PDF to EDI https://conexiom.com/
* _Kleinschmidt_: does EDI for Steersman
* _SPS_: does EDI for ERPs (Odoo) https://www.spscommerce.com/
* _AS2_: HTTPS for EDI, can just use SFTP
* _VAN_: third-party that provides message tracking

BIG PICTURE
* who uses: GSA, B2B (healthcare, manufacturing, railroad frieight) https://www.remedi.com/blog/edi-for-railway-freight
* who controls: corporate hacks https://x12.org/about/committees/subcommittee-x12-03-external-code-list-oversight-eco https://www.linkedin.com/in/tina-martinez-8511192/ https://cognosante.com/

BAD
* maybe standards bodies are just slow and bad in general? https://news.ycombinator.com/item?id=41976529
* hostile to UNIX / typical tooling
> It could be considered a very distant spiritual ancestor of XML; it was designed to meet the same kind of need, but way back in days of yore when individual bytes were valuable things to be cherished. The standards committee was originally chartered back in 1979...a file often contains just a single line...The problem with everything being on a single line is that the vast majority of the standard Unix toolbox for data processing and exploration is designed to work with data a line at a time. For example, say you want to take a peek at the beginning of a large file to see what sort of records it contains: $ head < file will print the first 10 lines to your terminal. If the entire file you’re dealing with is a single 1.3 gigabyte line, this is less than helpful. https://www.lambdafunctions.com/articles/racing-sed-with-rust
* goofy semantics
> These identifiers, ISA and GS, likely follow a convention used when the ANSI X12 standards were first developed in the late 1970s and 1980s. The X12 committee aimed to make EDI transactions compact and machine-readable. Short, non-ambiguous codes like ISA, GS, and others (e.g., ST, BEG, REF) were chosen as simple identifiers, often favoring brevity over human readability. https://chatgpt.com/c/671fa6c4-e0bc-8004-9937-f66fd3ce06b2

POINT TO POINT IS INHERENTLY COMPLEX https://www.stedi.com/blog/what-makes-edi-so-hard
> Since each business has multiple trading partners, and each of its trading partner operates on different business systems, “point to point” integration of these transactions (that is, mapping Walmart’s internal database format directly to the QuickBooks JSON API) would require the recipient to have detailed knowledge of many different transaction formats – for example, a company selling to three customers running on NetSuite, SAP, and QuickBooks, respectively, would need to understand NetSuite XML, SAP IDoc, and QuickBooks JSON. Maintaining familiarity with so many systems isn’t practical; to avoid this explosion of complexity, businesses instead use commonly-accepted intermediary formats, which are broadly known as Electronic Data Interchange - EDI.
> It is designed to eliminate only the unrealistic requirement that a trading partner be able to understand each of its trading partner’s internal syntax and vocabulary.  Instead of businesses having to work with many different syntaxes (e.g., JSON, XML, CSV) and vocabularies (e.g., PO No. and Purchase Order #), frameworks like X12 and EDIFACT provide highly structured, opinionated alternatives intended to reduce the surface area of knowledge required to successfully integrate with trading partners.
> The vast majority of fields cannot be standardized to this degree. Take, for example, the product identifier of a line item on a Purchase Order - while X12 specifies that the 850 Purchase Order's PO107 element should be used to specify the product identifier value, the standard cannot possibly mandate which type of product identifier should be used. Some companies use SKUs (Stock Keeping Units), while others use Part Numbers, UPCs (Universal Product Codes), or GTINs (Global Trade Item Numbers); all in all, the X12 standard specifies a dictionary of 544 different possible product identifier values that can be populated in the PO106 element
> What we’re seeing here is that while a standard can be opinionated about the structure of a document and the naming of fields, it cannot be opinionated about the contents of a business transaction – the contents of a business transaction are dictated by the idiosyncrasies of the business itself.

ATTEMPTS AT REPLACEMENT https://chatgpt.com/c/670d82d9-c488-8004-967f-2a987b16c9e9
* XML, s-expressions https://en.wikipedia.org/wiki/S-expression#Parsing https://news.ycombinator.com/item?id=31840852
* JSON Schema https://www.stedi.com/blog/getting-started-with-the-x12-file-format
> In the healthcare sector, the Health Insurance Portability and Accountability Act of 1996 (HIPAA) requires that all insurance carriers exchange transactions such as claims, eligibility checks, prior authorizations, and enrollments using a standardized EDI format called X12 HIPAA. A small group of legacy clearinghouses process the majority of these transactions, offering consolidated connectivity to carriers and providers. Stedi is building the world's only API-first clearinghouse. By offering modern API interfaces alongside traditional real-time and batch EDI processes, we enable both healthcare technology businesses and established players to exchange mission-critical transactions...by offering a modern API interface for running eligibility checks, processing claims, and ingesting ERAs, healthcare technology businesses can exchange transactions with payers without dealing with the EDI protocol or carrier-specific connectivity. - Stedi job posting

## tooling

🔍 https://github.com/michaelachrisco/Electronic-Interchange-Github-Resources

YES
* _pyedi_: parse (x12-JSON) https://github.com/freestream/pyedi 💻 https://github.com/zachvalenta/capp-pyedi
* not on PyPI; fork and publish? https://realpython.com/pypi-publish-python-package/#prepare-your-package-for-publication
```python
import json
from pyedi import parse_file
from pyedi.settings import Settings
ts = parse_file('./edi.txt', Settings())
with open("data.json", "w") as f:
    json.dump(ts, f)
```
* _Stedi_: syntax highlight https://www.stedi.com/edi/inspector https://www.stedi.com/blog/the-foundation-of-any-reliable-edi-system
* _x12-edi-tools_: parse (Python-x12) https://github.com/copyleftdev/x12-edi-tools https://pypi.org/project/x12-edi-tools/

EVALUATE
* _AWS B2Bi_: https://docs.aws.amazon.com/b2bi/ history, usage https://aws.amazon.com/blogs/aws/introducing-aws-b2b-data-interchange-simplified-connections-with-your-trading-partners/
* _edi-support_: syntax https://github.com/Silvenga/vscode-edi-x12-support
* _edifact_: syntax https://github.com/DAXaholic/vscode-edifact
* _sezna_: parse (x12-JSON) https://github.com/sezna/edi
> It has been already used commercially for multiple EDI pipelines and is able to handle any X12 document which is specification-compliant. It can both parse and output valid EDI documents while maintaining versatility to cover the entire spec. There is also a `loose_parse` mode which is less strict on the spec, in case the incoming data is slightly malformed. https://news.ycombinator.com/item?id=23786634
* _vs-edi_: syntax highlight https://github.com/hellooops/vscode-edi-support https://github.com/michaelachrisco/Electronic-Interchange-Github-Resources#syntax-highlighters
* _x12pp_: https://github.com/clarkema/x12pp
* _x12-parser_: JS, for large files https://www.npmjs.com/package/x12-parser

NO
* _bots_: bad docs https://pypi.org/project/bots/ https://github.com/eppye-bots/bots
* _pyedi830_: parse (x12-CSV) https://github.com/dev0088/pyedi830
* _pyx12_: validate x12; `ModuleNotFoundError: No module named 'pkg_resources'` https://github.com/azoner/pyx12
* _Smooks_: Java, XML https://www.smooks.org/

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

## semantics

* _encode_: 动 convert to diff fmt 📙 MacCormick 5.66
* typically byte per/char https://stackoverflow.com/a/31322359
> Each byte represents some text character in the program. 📙 Bryant 1.1
* multibyte = n byte per/char e.g. Japanese 📙 Beaulieu 2.19
* can be anything e.g. Morse code (dot/dash to text) 📙 Sweigart 1.3
* QR/bar code https://boonepeter.github.io/posts/2020-11-10-spotify-codes/ https://news.ycombinator.com/item?id=32837565 https://github.com/fumiyas/qrc
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

## ascii

🗄️ `info.md` diagrams

---

* _ASCII_: mapping from number to glyph (char) 📍 Petzold 15.181, computerphile 📚 Petzold code ch. 20 https://www.youtube.com/watch?v=XaGXPObx2Gs from pre 8-bit era; `man ascii` https://increment.com/programming-languages/unplain-text-primer-on-non-latin/

## Unicode

📜 https://www.unicode.org/main.html

---

https://taskwarrior.org/docs/unicode/
https://sw.kovidgoyal.net/kitty/faq/#some-special-symbols-are-rendered-small-truncated-in-kitty
https://crates.io/crates/ucd-trie
https://docs.python.org/2/howto/unicode.html
https://docs.python.org/3/howto/unicode.html
https://mcilloni.ovh/2023/07/23/unicode-is-hard/
https://lucumr.pocoo.org/2014/1/5/unicode-in-2-and-3/
https://codepoints.net/
https://www.pythonmorsels.com/cli-tools/#quopri
https://pyatl.dev/2024/09/01/bitten-by-unicode/
https://text.makeup/about/
📍 utf-8 vs. unicode https://youtu.be/SM9gJv08dm0 2:30 https://stackoverflow.com/questions/643694/what-is-the-difference-between-utf-8-and-unicode https://nbviewer.org/gist/guocheng/1ae6c2d76461a66cfc5ec6009b5791d1 https://docs.python.org/3/howto/unicode.html
* emoji, kanji https://www.fluentpython.com/extra/multi-character-emojis/ https://www.textualize.io/blog/posts/7-things-about-terminals how emojis make it into the standard https://www.unicode.org/emoji/proposals.html#frequency-evidence https://news.ycombinator.com/item?id=41844624

* _UTF8_: multi-byte i.e. characters outside of English just get more bytes thrown at them https://sethmlarson.dev/blog/utf-8 https://news.ycombinator.com/item?id=30259097 https://viralinstruction.com/posts/utf8/
* _Unicode_: char set https://stackoverflow.com/a/13212528/6813490 https://github.com/arp242/uni https://www.youtube.com/watch?v=MijmeoH9LT4 https://rentafounder.com/how-to-count-unicode-string-characters/ https://www.dampfkraft.com/ghost-characters.html code point, glyph, octal, hex https://realpython.com/courses/python-unicode/ `unicode-standard.pdf` https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/ https://en.wikipedia.org/wiki/Code_point CLI tool https://github.com/arp242/uni/ in Python https://blog.phylum.io/malicious-actors-use-unicode-support-in-python-to-evade-detection https://news.ycombinator.com/item?id=37735801 https://realpython.com/python-sort-unicode-strings/
* unicode, emoji in the terminal https://news.ycombinator.com/item?id=37047785
> Since the distinction between string and unicode has been done away with in Python 3, __unicode__ is gone and __bytes__ (which behaves similarly to __str__ and __unicode__ in 2.7) exists for a new built-in for constructing byte arrays. https://rszalski.github.io/magicmethods/#appendix2

# 🗃️ FILE FMT

📙 Kleppmann ch. 4
🗄 `eng.md` clean

---

https://drewdevault.com/2021/07/28/The-next-YAML.html

QUERY TOOLS
* query Google Sheets with SQL https://github.com/julien040/anyquery
* _qq_: https://github.com/JFryy/qq
* https://github.com/simonw/sqlite-utils
* https://github.com/datafold/data-diff
* https://github.com/mithrandie/csvq
* https://github.com/dinedal/textql
* https://github.com/noborus/trdsql

## CSV

🗄️ `analytics.md` visidata

TOOLS
* _moderncsv_: editor https://www.moderncsv.com/ 🗄️ `data/analytics.md` visidata
* _csvdiff_: ✅ diff https://github.com/aswinkarthik/csvdiff
* _csview_: ✅ cat https://github.com/wfxr/csview
* _csvlens_: ✅ less/pager https://github.com/YS-L/csvlens https://news.ycombinator.com/item?id=38889820
* _tabiew_: cat https://github.com/shshemi/tabiew

QUERY
* _qsv_: https://github.com/jqnatividad/qsv
* _sq_: query with SQL https://github.com/neilotoole/sq
* _textql_: query with SQL https://github.com/dinedal/textql

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

## Cuelang

📜 https://cuelang.org/

* use cases https://news.ycombinator.com/item?id=34074386 https://chatgpt.com/c/670d7768-62c8-8004-89e2-fd5a876700d7
* alternative https://github.com/bazelbuild/starlark https://github.com/systeminit/si
* not supported by VS Code's Markdown syntax highlighting https://stackoverflow.com/a/70456058/6813490 https://highlightjs.readthedocs.io/en/latest/language-requests.html
```json
// Define a schema for a person
person: {
    name: string & len(name) > 1 // Name must be a string and at least 2 characters long
    age:  int & >= 0             // Age must be an integer and at least 0
    email: string & =~ "^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}$" // Valid email format
}

// Instance of a valid person
person: {
    name:  "John Doe"
    age:   30
    email: "johndoe@example.com"
}
```
```sh
# validate
cue vet person.cue
```

## INI

* used by `.gitconfig`
* comments: `;`, hash (for Git at least)
* _pyinilint_: validate https://pypi.org/project/pyinilint/ https://gitlab.com/danieljrmay/pyinilint alternative https://github.com/Boeing/config-file-validator

## JSON

🛠 https://github.com/burningtree/awesome-json
🗄️
* `algos.md` tree
* `dbms.md` JSON
* `python/stdlib.md` serde

OPERATIONS
* fmt: `python3 -m json.tool music-lib.json > music-lib-fmt.json` https://orbifold.xyz/check-in-json.html
* to SQL https://github.com/simonw/claude-to-sqlite
* _csv-diff_: diff https://github.com/simonw/csv-diff
* _dasel_: edit https://github.com/TomWright/dasel
* _jo_: ✅ generate https://github.com/jpmens/jo
> just use Python https://news.ycombinator.com/item?id=30224063
* _graphtage_: ❌ diff https://github.com/trailofbits/graphtage broken https://github.com/trailofbits/graphtage/issues/91 🗄️ `shell.md` file / diff

### design

📜 http://www.json.org/
🗄️ `telemetry.md` logging / JSONL

* basic
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

NUMBERS https://chatgpt.com/c/671266a2-7fa4-8004-b1d3-c43acb773f7d
* types: int, floating point, exponential notation
* use strings to represent monetary amounts
* use strings for big ints
* no leading zeros
* largest safe int `2^53 - 1` (`9007199254740991`) 📜 IEEE-754 double-precision floating-point

ZA
* benefits: readable, tooling, mindshare 📙 Jeffrey distributed [4]

---

* https://seriot.ch/projects/parsing_json.html
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
* _jello_: 🎯 Python syntax https://github.com/kellyjonbrazil/jello https://github.com/kellyjonbrazil/jellex
* _jmespath_: https://github.com/jmespath/jp https://github.com/birchb1024/frangipanni/blob/cf997721e2c5793e062d1c16908d7ddf2a325173/frangipanni.go
* _jnv_: 🎯 interactive https://github.com/ynqa/jnv
* _jqp_: TUI https://github.com/noahgorstein/jqp 
* _jsonata_: https://jsonata.org/ https://www.stedi.com/blog/jsonata-playground
* _qq_: ⭐️ https://github.com/JFryy/qq/
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

## KDL

https://kdl.dev/ https://zellij.dev/documentation/layouts
> this is what started me to split protocols into own file apart from `computation.md`

## Parquet

---

* Vortex https://news.ycombinator.com/item?id=41839773
* https://www.crunchydata.com/blog/pg_parquet-an-extension-to-connect-postgres-and-parquet
* https://csvbase.com/blog/3
* https://r4ds.hadley.nz/arrow#sec-parquet
* partition elimination https://duckdb.org/2021/12/03/duck-arrow.html
* https://pythonspeed.com/articles/best-file-format-for-pandas/
* https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page
* _Parquet_: column-oriented file format, like CSV https://www.youtube.com/watch?v=H_dLfHETO0g https://news.ycombinator.com/item?id=35418933 https://news.ycombinator.com/item?id=29010103
* easier to use now vs. CSV https://news.ycombinator.com/item?id=30595026
* use to build no-code API https://tech.marksblogg.com/roapi-rust-data-api.html
* pyarrow https://www.blog.pythonlibrary.org/2024/05/06/how-to-read-and-write-parquet-files-with-python/

## XML

🗄️ `algos.md` tree

* usage: EDI, Maven, Claude https://github.com/simonw/files-to-prompt
* element types: prolog, root node/element, child node/elements, comments (same as HTML)
* _XSLT_: CSS for XML https://github.com/azoner/pyx12
* _XPath_: CSS selector for XML

---

HISTORY
* _cXML_: owned by SAP https://en.wikipedia.org/wiki/CXML https://cxml.org/
* https://news.ycombinator.com/item?id=35467711
* previously more popular 📙 Beaulieu 2.34

## YAML

YQ 📜 https://github.com/mikefarah/yq
* edit
* query
* to JSON
* Github Action
```sh
yq 'true' $FILE  # validate https://mikefarah.gitbook.io/yq/upgrading-from-v3#validate-documents
```

SYNTAX 📜 https://yaml.org/
* spacing err: `mapping values are not allowed in this context` https://chatgpt.com/c/671d7065-3644-8004-9967-e49a83ef4810
* scalars
```yaml
name: John Doe                # string
age: 30                       # int
height: 1.75                  # floating-point
is_employee: true             # boolean
nickname: null                # null
```
* list/map
```yaml
# SEQUENCE/LIST
languages:
  - Python
  - JavaScript
  - Go

# MAP/DICTIONARY
address:
  street: 123 Main St
  city: Sampleville
  zip_code: 12345

# NESTED
projects:
  - name: Project Alpha
    team:
    completed: false
      - name: Alice
        role: dev
      - name: Bob
        role: design
  - name: Project Beta
    completed: true
    team:
      - name: Carol
        role: pm
      - name: Dave
        role: dev
```
* anchors
```yaml
default_user: &default_user
  name: John Doe
  email: johndoe@example.com
  roles:
    - user
    - editor

users:
  - <<: *default_user  # use anchor
    id: 1001
  - <<: *default_user  # use anchor + override
    id: 1002
    name: Alice Doe
    email: alicedoe@example.com
```

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

📚
* Petzold code 3, 9, 12-13
* Evans ints floats

SCALE 📙 Kozierok 4.63
* _bit_: binary digit; aka 'flag' [Kozierok 4.63]
* _byte_: 8 bits
* aka octet, octet string = sequence of bytes https://stackoverflow.com/a/21463473 https://stackoverflow.com/a/1241234
* 255 possible values https://www.youtube.com/watch?v=dPxCGlW9lfM 5:10
* _kilobyte (KB)_: 1k bytes
* _megabyte (MB)_: 
* _gigabyte (GB)_: 1024^3 bytes
* _terabyte (TB)_: 
* _petabyte_: 1024 TB?
* _exabyte_: 1B GB

---

* _bitmask_: toggling bit https://www.arp242.net/bitmask.html set (to 1) reset/clear (to 0) [Kozierok 4.63]
* _nybble_: 4 bits [Petzold code 181]
* _byte string_: sequence of bytes https://stackoverflow.com/a/31322359 https://www.fluentpython.com/lingo/#byte_string
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

📍 learn C, learn how to edit binary https://www.youtube.com/watch?v=-eDY7yh-CyA https://github.com/sharkdp/hexyl https://danluu.com/edit-binary/

* used bc easier to convert to binary than decimal [Petzold code 181 https://www.youtube.com/watch?v=dPxCGlW9lfM 4:20]
* _hexit_: hex digit (1 nybble) https://www.youtube.com/watch?v=dPxCGlW9lfM [4:30]

TOOLING
* used for reverse engineering? https://github.com/radareorg/radare2
* `hexdump -C <file>` https://www.youtube.com/watch?v=-eDY7yh-CyA 1:50
* _fq_: query https://github.com/wader/fq 
* _hexabyte_: 🎯 editor https://github.com/thetacom/hexabyte
* _hexedit_: Ubuntu https://news.ycombinator.com/item?id=23762626
* _hexed_: 🎯 browser https://hexed.it/
* _HexFiend_: macOS https://github.com/HexFiend/HexFiend
* _hexyl_: viewer https://github.com/sharkdp/hexyl
* _ImHex_: 🎯 editor https://github.com/WerWolv/ImHex 

# 🟨 ZA

CASES
* snake: `hello_world`
* kebab: `hello-world`
* camel: `helloWorld`
* Pascal: `HelloWorld`

## identifiers

* _SKU_: internal to retailer/warehouse; variable length, fmt repr product characteristics/location
* _ASIN_: Amazon SKU; 10 char; per product i.e. if multiple sellers sell same product they use same ASIN https://inventlikeanowner.com/blog/the-story-behind-asins-amazon-standard-identification-numbers/
* _UPC_: unique across retailers; 12 char; overseen by GS1
* syntax: manufacturer + product + check digit (proof of correct reading of previous digits)
```sh
049000000156  # coke classic 12 oz can
049000000163  # coke diet 12 oz can
049000000187  # sprite 12 oz can
```
```python
def calculate_check_digit(upc_without_check_digit):
    """
    calculate check digit for given UPC w/ Modulo 10 algo
    args: upc_without_check_digit (str): first 11 digits of the UPC w/o the check digit
    returns: int: calculated check digit
    """
    # convert input string to list of ints
    digits = [int(d) for d in upc_without_check_digit]
    # multiply odd-positioned digits (0-indexed) by 3 and even-positioned digits by 1
    total = 0
    for i, digit in enumerate(digits):
        if i % 2 == 0:  # Odd positions in 0-indexed (1, 3, 5...)
            total += digit * 3
        else:  # Even positions in 0-indexed (2, 4, 6...)
            total += digit
    # calc check digit
    remainder = total % 10
    check_digit = (10 - remainder) if remainder != 0 else 0
    return check_digit

# diet coke 12 oz can
upc_input_diet_coke = "049000028911"
# extract first 11 digits (excluding the check digit)
upc_without_check_digit_diet_coke = upc_input_diet_coke[:11]
# calc check digit for the provided UPC
calculated_check_digit_diet_coke = calculate_check_digit(upc_without_check_digit_diet_coke)
# construct full UPC with the calculated check digit
full_upc_diet_coke = upc_without_check_digit_diet_coke + str(calculated_check_digit_diet_coke)
# output
print(f"UPC without check digit: {upc_without_check_digit_diet_coke}")
print(f"Calculated check digit: {calculated_check_digit_diet_coke}")
print(f"Full UPC: {full_upc_diet_coke}")
```

---

UUID https://www.rfc-editor.org/rfc/rfc9562.html https://www.ntietz.com/blog/til-uses-for-the-different-uuid-versions/ https://en.wikipedia.org/wiki/Universally_unique_identifier https://taskwarrior.org/docs/dom/
```sh
# https://weiyen.net/articles/useful-macos-cmd-line-utilities
uuidgen
uuidgen | tr '[:upper:]' '[:lower:]' | pbcopy
```
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

## Markdown

🔗 https://www.markdownguide.org/

FLAVORS
* _Djot_: https://djot.net/ https://www.jonashietala.se/blog/2024/07/09/microfeatures_in_my_blog/
* _CommonMark_: https://meta.stackexchange.com/q/348746
* _GFM_: https://github.com/github/markup/issues/498#issuecomment-158257453 
* _MyST_: https://github.com/executablebooks/MyST-Parser

PARSERS
* _MDX_: jsx in markdown (for tables, charting) by transpiling Markdown to JS via JS runtime (e.g. React) and then running in the browser https://github.com/mdx-js/mdx/ https://signalsandthreads.com/writing-technically/ re: Next https://zackproser.com/blog/maintaining-this-site-no-longer-fucking-sucks
* time suck https://www.joshwcomeau.com/blog/how-i-built-my-blog-v2/
* _markdown-it-py_: https://github.com/executablebooks/markdown-it-py https://pythonbytes.fm/episodes/show/320/the-bug-is-in-the-javascript
* _commonmark_: https://github.com/readthedocs/commonmark.py https://github.com/Textualize/rich/pull/2439/files
* _goldmark_: https://github.com/yuin/goldmark
* HTML to Markdown https://github.com/JohannesKaufmann/html-to-markdown https://html-to-markdown.com/

RENDER
* _frogmouth_: https://github.com/Textualize/frogmouth
* _glow_: https://github.com/charmbracelet/glow
* _mdcat_: ✅ https://github.com/swsnr/mdcat https://github.com/charmbracelet/mods/blob/main/examples.md
* _rich_: https://rich.readthedocs.io/en/latest/markdown.html

EDITOR
* https://simplemde.com/ https://tunalog.org/en-us/index.html

---

* writing on mobile, comments for editing https://conroy.org/blogging-on-paper
* vs. RST https://buttondown.com/hillelwayne/archive/why-i-prefer-rst-to-markdown/
* use image (w/ Github renderer) https://github.com/catppuccin/python/blob/main/README.md

* links https://jordanelver.co.uk/blog/2021/03/13/til-about-markdown-reference-style-links/
* convert to HTML with Vim http://vimcasts.org/episodes/converting-markdown-to-structured-html-with-a-macro/
* Github https://docs.github.com/en/issues/tracking-your-work-with-issues/about-slash-commands
* RENDERME https://news.ycombinator.com/item?id=30336703
* metadata https://github.com/blacksmithgu/obsidian-dataview
* spec https://github.blog/2017-03-14-a-formal-spec-for-github-markdown/
* asciidoc vs. Markdown https://news.ycombinator.com/item?id=27744509
* href https://github.com/pemistahl/grex
* linting https://mkaz.blog/code/linting-markdown-syntax/
* Latex http://www.danielallington.net/2016/09/the-latex-fetish/ https://increment.com/open-source/the-lingua-franca-of-latex/ alternative https://sile-typesetter.org/ https://news.ycombinator.com/item?id=35242299 https://news.ycombinator.com/item?id=35250210 Typst https://www.youtube.com/watch?v=sWmlbMh3ol8 Overleaf, Markdown https://brainbaking.com/post/2021/02/writing-academic-papers-in-markdown/
* formal spec https://githubengineering.com/a-formal-spec-for-github-markdown/
* code syntax support https://github.com/github/linguist/blob/master/lib/linguist/languages.yml
* Pandoc has their own version of Markdown? https://yihui.name/en/2018/09/target-blank/
* Markdown to PowerPoint https://yhatt.github.io/marp https://www.youtube.com/watch?v=CkIweDviGH8
* HTML to Markdown https://github.com/JohannesKaufmann/html-to-markdown
* [dropdowns!](https://raw.githubusercontent.com/30-seconds/30-seconds-of-code/master/README.md)
* [diff](https://stackoverflow.com/a/40883538)
* table fmt: Jira, Markdown/RST, Latex https://jsvine.github.io/intro-to-visidata/basics/saving-sheets/
* Markdown for Google Docs https://www.theverge.com/2022/3/29/23002138/google-docs-markdown-support-formatting-update

conversion to HTML
* https://github.com/susam/texme
* Markdown to HTML w/ Python CLI https://python-markdown.github.io/cli/ `python -m markdown 1997-graham-hackers-painters.md > pg.html` -> doesn't handle quotes, output is vanilla would need to figure way to add CSS
* _mistune_: https://github.com/lepture/mistune
* _markdown_: `python -m markdown rn.md > rn.html` https://python-markdown.github.io/cli/ used in MkDocs https://github.com/mkdocs/mkdocs/blob/master/requirements/project.txt
* _markdown2_: https://github.com/trentm/python-markdown2 supports (maybe) ghfm https://github.com/mkdocs/mkdocs/issues/263#issuecomment-65362418
```sh
python -m markdown2 --extras fenced-code-blocks my-debug-checklist.md > debug.html
```

add styles
* `water.css` w/ Beatiful Soup in script https://stackoverflow.com/a/19123463/6813490 
* more advanced https://github.com/cburmeister/cburmeister.github.io/blob/master/Makefile pandoc https://serverless.pub/lambda-utility-layers/ https://github.com/kickstartcoding/cheatsheets

## PDF

TOOLING
* _baca_: ebook/epub TUI reader https://github.com/wustho/baca
* _poppler_: https://github.com/sxyazi/yazi
* _tdf_: https://github.com/itsjunetime/tdf
* _termpdf_: kitty https://github.com/dsanson/termpdf.py

---

* grep https://github.com/darrenldl/docfd
* Sioyek https://news.ycombinator.com/item?id=34069804
* https://docs.racket-lang.org/quad/
* Markdown https://docs.racket-lang.org/quad/
* https://rtpg.co/2016/09/17/make-an-ebook.html
* _design_: https://news.ycombinator.com/item?id=24108950 https://gds.blog.gov.uk/2018/07/16/why-gov-uk-content-should-be-published-in-html-and-not-pdf/
* _annotation_: PDF Expert, Flexcil, https://news.ycombinator.com/item?id=23230218 https://github.com/xournalpp/xournalpp
* _archival_: https://github.com/danburzo/percollate https://github.com/pirate/ArchiveBox
* _readers - macOS_: PDF Expert (freemium version won't let you save) PDF Element ($90/year) Preview (search doesn't seem to work for most documents https://duckduckgo.com/?q=macos+preview+search+doesn%27t+work&atb=v161-1&ia=web text in sidebar doesn't correspond to hightlight, some hightlights produce no text in sidebar, can't enter emoji into notes, limited keyboard shortcuts) Nitro PDF
* _to plain text_: https://github.com/axa-group/Parsr https://github.com/jsvine/pdfplumber
* _from plain text_: http://richardmavis.info/using-web-technologies-to-print-a-book https://coreyburmeister.com/continuous-integration-and-deployment-for-my-resume/
* _from HTML_: https://jvns.ca/blog/2020/06/19/a-little-bit-of-plain-javascript-can-do-a-lot/ https://www.princexml.com/
* _split_: select subset and drag into Finder
https://github.com/jorisschellekens/borb
https://news.ycombinator.com/item?id=26691626
* _ereader_ https://johnfactotum.github.io/foliate/
[PDF is bad]()
* PDF reader w/ Vim bindings: Zathura http://jhshi.me/2016/03/09/zathura-pdf-viewer-for-vim-lovers/index.html#.Xg4gThdKh-U not available on macOS https://www.reddit.com/r/vim/comments/3prfd0/pdf_reader_with_vim_keybindings_for_mac_osx/
* https://github.com/burtonator/polar-bookshelf https://pwmt.org/projects/zathura/ https://goodreader.com/
* mobile: [Joplin](https://github.com/laurent22/joplin), IAWriter
* https://www.pdfa.org/a-technical-and-cultural-assessment-of-the-mueller-report-pdf/

## serde

🗄 `python/stdlib.md` serde

---

Rust serde to OCaml https://www.youtube.com/watch?v=Qs6Di6vjEGs

* _serialize_: convert obj to interchange fmt
* _deserialize_: convert interchange fmt to obj
* _schema_: mapping of obj to interchange fmt structure
* you typically want to specify
> Pickles are implicit: they serialize everything in your objects, even data you didn’t want to serialize. For example, you might have an attribute that is a cache of computation that you don’t want serialized. Pickle doesn’t have a convenient way to skip that attribute. https://nedbatchelder.com/blog/202006/pickles_nine_flaws.html

BINARY
> ❓ how is BSON more binary than JSON itself? https://stackoverflow.com/questions/3554325/why-is-it-called-bson 📙 Kleppmann ch. 4
* e.g. HTTP/2 https://news.ycombinator.com/item?id=27431998
* db res in binary which is parsed by language-specific API 📙 Kleppmann 4.128
📙 Kleppmann 4.117, 4.122, 4.130
* _BSON_: binary JSON + SQL datatypes https://bsonspec.org/
* can be less space efficient due to datatypes https://en.wikipedia.org/wiki/BSON#Efficiency
* faster to parse https://bsonspec.org/faq.html
* datatypes: JSON + date, binary, num (int, long, float) https://youtu.be/SM9gJv08dm0 2:25
* _Capn Proto_: https://capnproto.org/
* sustainable? https://github.com/capnproto/capnproto/issues/2067
* _MessagePack_: like BSON https://msgpack.org/ https://neovim.io/ 📙 Kleppmann [4.116]

### Avro

* serialization format https://avro.apache.org/docs/current/
* better than CSV bc handles typing, cells missing data
* CSV disadvantages: inferred data types https://www.youtube.com/watch?v=SZX9DM_gyOE 1:20
* SQL disadvantages: flat
* competes with Thrift, Protocol Buffers https://avro.apache.org/docs/current/
* Python tutorial https://avro.apache.org/docs/current/gettingstartedpython.html
* https://www.youtube.com/watch?v=kq_JCVcHJLE

### protobuf

🗄️ `api.md` RPC
🧠 https://chatgpt.com/c/673cf346-ae54-8004-84c2-fd989e922c51

* _wireman_: client https://github.com/preiter93/wireman

---

* convert/query https://github.com/dflemstr/rq
* like BSON https://bsonspec.org/ https://github.com/bufbuild/buf
* https://vincent.bernat.ch/en/blog/2023-dynamic-protobuf-golang
* https://news.ycombinator.com/item?id=36798824
* curl for https://github.com/qaware/protocurl https://news.ycombinator.com/item?id=34866155
* compared to docarray, JSON https://docarray.jina.ai/get-started/what-is/#comparing-to-alternatives
* features that JSON doesn't have like versioning, types 📙 Jeffrey distributed [5]
* in Python https://www.fluentpython.com/extra/parsing-binary-struct/ https://www.blog.pythonlibrary.org/2023/08/30/an-intro-to-protocol-buffers-with-python/
