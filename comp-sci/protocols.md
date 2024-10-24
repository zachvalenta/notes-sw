# ⛩️

## 参考

## 进步

* grok segments from chatgpt code block https://github.com/dev0088/pyedi830
* https://github.com/lusingander/btox

* _24_: split into own file, file fmts (Cuelang, INI, KDL, YAML, EDI)
* _22_: protocol (encoding, serialization)
* _21_: prefix code

# 🟪️ EDI

🔗 https://en.wikipedia.org/wiki/Electronic_data_interchange

TRANSFER https://chatgpt.com/share/9b405f7d-4879-4985-be22-39fc267349f7
* can just do over SFTP
* _AS2_: HTTPS EDI
* _VAN_: third-party that provides message tracking

---

TO READ
* https://www.lambdafunctions.com/articles/racing-sed-with-rust
* https://news.ycombinator.com/item?id=31840852
* https://chatgpt.com/c/670d4d6e-c8c4-8004-91d1-052b4c33c416

## document lists

* _document list (DL)_: type of x12 document https://en.wikipedia.org/wiki/X12_Document_List
* each company picks a subset that they want to work with https://static.fishersci.com/cmsassets/downloads/segment/Scientific/pdf/WebServices/EDIspecGuideCust832.pdf
* file extension: `.edi`, `.x12`, `.dat`, `.txt`
* _832_: DL for catalog
* _850_: DL purchase order
* _855_: DL purchase order (= HTTP 200)
* _997_: DL for ack https://github.com/azoner/pyx12
* _999_: ? https://github.com/azoner/pyx12

## semantics

SPEC
* _EDI_: fmt for business transactions (purchases orders, sales)
* used by GSA, B2B (healthcare, manufacturing, railroad frieight) https://www.remedi.com/blog/edi-for-railway-freight
* _ASC x12_: US standards body for x12 https://en.wikipedia.org/wiki/ASC_X12
* _x12_: USA EDI spec
* _EDIFACT_: EU EDI spec https://en.wikipedia.org/wiki/EDIFACT
> For those who haven't had the pleasure, X12 is an ANSI standard for "electronic data interchange." It could be considered a very distant spiritual ancestor of XML; it was designed to meet the same kind of need, but way back in days of yore when individual bytes were valuable things to be cherished. The standards committee was originally chartered back in 1979. https://www.lambdafunctions.com/articles/racing-sed-with-rust

PROVIDERS
* _SPS_: does EDI for ERPs (Odoo) https://www.spscommerce.com/
* _Kleinschmidt_: does EDI for Steersman

---

* _envelope_: collection of documents of a type
* _mailbag_: collection of envelopes

## spec

segment types https://github.com/sezna/edi

```sh
# ISA (Interchange Control Header): sender, receiver
ISA*00*          *00*          *ZZ*SENDERID       *ZZ*RECEIVERID     *200710*1253*U*00401*000000905*0*T*>
# ?
GS*PO*SENDERID*RECEIVERID*20200710*1253*1*X*004010
ST*850*0001
BEG*00*SA*1234567890**20200710
REF*DP*038
PER*BD*John Doe*TE*555-123-4567
N1*BT*BUYER NAME
N3*1234 Buyer St
N4*Buyertown*CA*94005
N1*ST*SHIP TO NAME
N3*5678 Ship St
N4*Shiptown*CA*94006
PO1*1*10*EA*15.00**CB*123456*VP*ABC123
PO1*2*20*EA*45.00**CB*654321*VP*XYZ789
CTT*2
AMT*TT*1200.00
SE*14*0001
GE*1*1
IEA*1*000000905
```

## tooling

🔍 https://github.com/michaelachrisco/Electronic-Interchange-Github-Resources

* _AWS B2Bi_: 🎯 https://docs.aws.amazon.com/b2bi/ history, usage https://aws.amazon.com/blogs/aws/introducing-aws-b2b-data-interchange-simplified-connections-with-your-trading-partners/
* _bots_: ❌ bad docs https://pypi.org/project/bots/ https://github.com/eppye-bots/bots
* _pyedi_: ✅ parse (x12-JSON) https://github.com/freestream/pyedi 💻 https://github.com/zachvalenta/capp-pyedi
* not on PyPI; fork and publish? https://realpython.com/pypi-publish-python-package/#prepare-your-package-for-publication
```python
import json
from pyedi import parse_file
from pyedi.settings import Settings
ts = parse_file('./edi.txt', Settings())
with open("data.json", "w") as f:
    json.dump(ts, f)
# fmt -> python -m json.tool data.json
```
* _pyedi830_: ❌ parse (x12-CSV) https://github.com/dev0088/pyedi830
* _pyx12_: ❌ validate x12; `ModuleNotFoundError: No module named 'pkg_resources'` https://github.com/azoner/pyx12
* _sezna_: parse (x12-JSON) https://github.com/sezna/edi
> It has been already used commercially for multiple EDI pipelines and is able to handle any X12 document which is specification-compliant. It can both parse and output valid EDI documents while maintaining versatility to cover the entire spec. There is also a `loose_parse` mode which is less strict on the spec, in case the incoming data is slightly malformed. https://news.ycombinator.com/item?id=23786634
* _Smooks_: ❌ Java, XML https://www.smooks.org/
* _Stedi_: ✅ syntax highlight https://www.stedi.com/edi/inspector
* _vs-edi_: 🎯 syntax highlight https://github.com/hellooops/vscode-edi-support https://github.com/michaelachrisco/Electronic-Interchange-Github-Resources#syntax-highlighters
* _x12-edi-tools_: parse (Python-x12) https://github.com/copyleftdev/x12-edi-tools https://pypi.org/project/x12-edi-tools/
* _x12-parser_: JS, for large files https://www.npmjs.com/package/x12-parser

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
* emoji, kanji https://www.fluentpython.com/extra/multi-character-emojis/ https://www.textualize.io/blog/posts/7-things-about-terminals how emojis make it into the standard https://www.unicode.org/emoji/proposals.html#frequency-evidence https://news.ycombinator.com/item?id=41844624

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

TOOLS
* _moderncsv_: editor https://www.moderncsv.com/ 🗄️ `data/analytics.md` visidata
* _csvdiff_: ✅ diff https://github.com/aswinkarthik/csvdiff
* _csview_: ✅ cat https://github.com/wfxr/csview
* _csvlens_: ✅ less/pager https://github.com/YS-L/csvlens https://news.ycombinator.com/item?id=38889820

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
* `python/stdlib.md` serde

OPERATIONS
* fmt: `python3 -m json.tool music-lib.json > music-lib-fmt.json` https://orbifold.xyz/check-in-json.html
* to SQL https://github.com/simonw/claude-to-sqlite
* _dasel_: edit https://github.com/TomWright/dasel
* _jo_: ✅ generate https://github.com/jpmens/jo
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
* _jello_: 🎯 Python syntax https://github.com/kellyjonbrazil/jello https://github.com/kellyjonbrazil/jellex
* _jnv_: 🎯 interactive https://github.com/ynqa/jnv
* _jqp_: TUI https://github.com/noahgorstein/jqp 
* _jsonata_: https://jsonata.org/
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

📜 https://yaml.org/
🔍 query https://github.com/mikefarah/yq
> can validate as well https://chatgpt.com/c/67141929-cb80-8004-86dc-201dc864fdad

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

📚 Petzold code 3, 9, 12-13

---

* https://wizardzines.com/zines/integers-floats/

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

## Markdown

🔗 https://www.markdownguide.org/

FLAVORS
* _Djot_: https://djot.net/ https://www.jonashietala.se/blog/2024/07/09/microfeatures_in_my_blog/
* _CommonMark_: https://meta.stackexchange.com/q/348746
* _GFM_: https://github.com/github/markup/issues/498#issuecomment-158257453 
* _MyST_: https://github.com/executablebooks/MyST-Parser

PARSERS
* _MDX_: jsx in markdown (for tables, charting) by transpiling Markdown to JS via JS runtime (e.g. React) and then running in the browser https://github.com/mdx-js/mdx/ https://signalsandthreads.com/writing-technically/
* time suck https://www.joshwcomeau.com/blog/how-i-built-my-blog-v2/
* _markdown-it-py_: https://github.com/executablebooks/markdown-it-py https://pythonbytes.fm/episodes/show/320/the-bug-is-in-the-javascript
* _commonmark_: https://github.com/readthedocs/commonmark.py https://github.com/Textualize/rich/pull/2439/files
* _goldmark_: https://github.com/yuin/goldmark
* HTML to Markdown https://github.com/JohannesKaufmann/html-to-markdown

RENDER
* mdcat https://github.com/swsnr/mdcat
* rich https://rich.readthedocs.io/en/latest/markdown.html
* https://github.com/Textualize/frogmouth
* glow https://github.com/charmbracelet/bubbletea

EDITOR
* https://simplemde.com/ https://tunalog.org/en-us/index.html

---

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

## serde

🗄 `python/stdlib.md` serde

---

* _serialize_: convert obj to interchange fmt
* _deserialize_: convert interchange fmt to obj
* _schema_: mapping of obj to interchange fmt structure
* you typically want to specify
> Pickles are implicit: they serialize everything in your objects, even data you didn’t want to serialize. For example, you might have an attribute that is a cache of computation that you don’t want serialized. Pickle doesn’t have a convenient way to skip that attribute. https://nedbatchelder.com/blog/202006/pickles_nine_flaws.html

BINARY
> ❓ how is BSON more binary than JSON itself? https://stackoverflow.com/questions/3554325/why-is-it-called-bson 📙 Kleppmann ch. 4
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
