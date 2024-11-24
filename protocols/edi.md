# ⛩️

## 参考

STEDI TEACHING
* https://www.stedi.com/blog/the-foundation-of-any-reliable-edi-system
* https://www.stedi.com/blog/getting-started-with-the-x12-file-format
* https://www.stedi.com/docs/edi-platform/edi-essentials/what-is-edi#what-is-edi
* https://www.stedi.com/blog/edi-for-developers-turn-edi-into-json
* https://www.stedi.com/blog/transaction-set-variants-in-the-amazon-850-purchase-order
* control numbers https://www.stedi.com/blog/control-numbers-in-x12-edi
* https://www.stedi.com/blog/date-and-time-in-edi
* standards at national level https://increment.com/apis/introduction-apis-egovernment/

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

## 进步

* _24_: Capp

# 🧬 SEGMENTS

## metadata

ST
* _ST01_: transaction set type; `832`
> don't understand how this isn't duping GS01
* _ST02_: control number
> don't understand how this isn't duping GS06
* _SE_: closes transaction set
```sh
# SE * number of segments * same control number as ST
SE*6*0001~
```

### ISA

> An X12 file starts with a fixed-length 106-byte header called an ISA segment...specifies three different terminator characters to be used in the rest of the document. https://www.lambdafunctions.com/articles/racing-sed-with-rust

* _ISA05_: sender ID qualifier
* _ISA06_: sender ID
* _ISA07_: receiver ID qualifier
* _ISA08_: receiver ID
* _ISA09_: date
* _ISA10_: time
* _ISA12_: version number
* _ISA13_: control number
* _ISA14_: request for ack
* _ISA15_: indicator whether test|prod

### GS

* _GS01_: transaction set type; `SC` 832 `PO` 850
* _GS02_: sender code; `014654966`
* _GS03_: receiver code; `Fastenal`
* _GS04_: date
* _GS05_: time
* _GS06_: control number
* _GS07_: standards body; `X` for ASC x12
* _GS08_: version; `004010`

### summary

* _CTT01_: sum of line items (e.g. `LIN`)
* _CTT02_: hash of total
* _GE01_: sum of transaction sets
* _GE02_: control number; matches GS06
* _IEA_: control number; matches GS06

## 832 (prod cat)

🔍 https://www.stedi.com/edi/x12/transaction-set/832

* _G53_: CRUD ("maintenance operation"); `001` update `002` delete `003` create
* _DTM_: date range for CTP
* _LDT_: lead time
```sh
# type * quantity * unit of time
# from date of purchase order to shipment * 10 * workdays
LDT*AE*10*DW~

# valid 2024.11.01-30
DTM*196*20241101~
DTM*197*20241130~
```

### BCT

```sh
BCT*05*CAT123*V1~
```
* _BCT01_: purpose code
* 02 add 04 change 05 replace ("used for full updates, such as a monthly refresh")
* `SC` sales catalog PS price sheet PC catalog
* _BCT02_: catalog id
* _BCT03_: catalog version

### LIN

* _LIN_: UUID e.g. UPC|SKU
* _LIN01_: internal line number for tracking
* _LIN02_: qualifier
* _LIN03_: ID itself
```sh
# UP = UPC, ID = 012345678905
LIN**UP*012345678905
```

### PID

* _PID_: desc
* _PID01_: desc type e.g. `F` free-form `S` structured
* _PID05_: actual desc
```sh
# F = free-form
PID*F****Blue T-Shirt, Size Large
```

### CTP

* _CTP_: price
* _CTP01_: price tier e.g. CN consumer WS wholesale RT retail IN industrial GO government HV healthcare
* _CTP02_: qualifier e.g. UCP (unit cost price)
* _CTP03_: unit price
* _CTP05_: unit type (composite unit of measure) e.g. each, dozen
```sh
CTP**UCP*10.50**1*EA
```

# 🛠️ TOOLING

📜 https://www.stedi.com/edi/x12
🔍 https://github.com/michaelachrisco/Electronic-Interchange-Github-Resources

YES
* _edifabric_: https://www.edifabric.com/
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

## pyedi

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

## Stedi

🔍 https://www.stedi.com/edi

* syntax highlight https://www.stedi.com/edi/inspector

# 🟨 ZA

## components

* file extension: `.edi`, `.x12`, `.dat`, `.txt`
* _implementation guideline_: additional instructions from receiver re: how sender should impl 🧠 https://chatgpt.com/c/673d0121-f4d8-8004-b903-4d083157a552
* _guideline position_: location of segment w/in implementation guideline e.g. CTP at position 170 in Fastenal 823 implementation guideline
* _element_: segment subcomponent; `*` delimiter, `**` = blank
* data types: ID + NO (numeric) AN (alphanumeric) DT (date) TM (time)
* _segment_: ID + data; `~` terminal delimiter
* order: ISA (initial), GSA (metadata), IEA (InterchangeEnvelope; terminal)
* _loop_: list of common segments
* _envelope_: a single x12 document and its transmission
* _mailbag_: n envelopes
* _transaction set (TS)_: group of segments https://en.wikipedia.org/wiki/X12_Document_List https://x12.org/products/transaction-sets 
```csv
number,code,type
810,IN,invoice
820,RA,payment order
832,SC,catalog
850,PO,purchase order
870,RS,order status
997,FA,ack
```
* _transaction set purpose codes_: "why is document being sent?", only shows up in (typically) a single segment, can apply to multiple document lists (832, 850)
* `00` new `01` cancel previously sent doc `04` update `05` replace `06` ack receipt of sent doc `24` draft
* _qualifiers_: type for ID
* `ZZ` custom `01` DUNS `20` Health Industry Number (HIN) `30` U.S. Federal Tax Identification

## ecosystem

🗄️ standards bodies
🗓️️ versions https://x12.org/news-and-events/release-schedule https://www.stedi.com/edi/x12-008050 https://www.stedi.com/blog/getting-started-with-the-x12-file-format

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
* you need to buy their documentation https://chatgpt.com/c/6723e31b-bf8c-8004-a801-41b1b4e52419
* maybe standards bodies are just slow and bad in general? https://news.ycombinator.com/item?id=41976529
* hostile to UNIX / typical tooling
> It could be considered a very distant spiritual ancestor of XML; it was designed to meet the same kind of need, but way back in days of yore when individual bytes were valuable things to be cherished. The standards committee was originally chartered back in 1979...a file often contains just a single line...The problem with everything being on a single line is that the vast majority of the standard Unix toolbox for data processing and exploration is designed to work with data a line at a time. For example, say you want to take a peek at the beginning of a large file to see what sort of records it contains: $ head < file will print the first 10 lines to your terminal. If the entire file you’re dealing with is a single 1.3 gigabyte line, this is less than helpful. https://www.lambdafunctions.com/articles/racing-sed-with-rust
* goofy semantics
> These identifiers, ISA and GS, likely follow a convention used when the ANSI X12 standards were first developed in the late 1970s and 1980s. The X12 committee aimed to make EDI transactions compact and machine-readable. Short, non-ambiguous codes like ISA, GS, and others (e.g., ST, BEG, REF) were chosen as simple identifiers, often favoring brevity over human readability. - GPT

POINT TO POINT IS INHERENTLY COMPLEX https://www.stedi.com/blog/what-makes-edi-so-hard
> Since each business has multiple trading partners, and each of its trading partner operates on different business systems, “point to point” integration of these transactions (that is, mapping Walmart’s internal database format directly to the QuickBooks JSON API) would require the recipient to have detailed knowledge of many different transaction formats – for example, a company selling to three customers running on NetSuite, SAP, and QuickBooks, respectively, would need to understand NetSuite XML, SAP IDoc, and QuickBooks JSON. Maintaining familiarity with so many systems isn’t practical; to avoid this explosion of complexity, businesses instead use commonly-accepted intermediary formats, which are broadly known as Electronic Data Interchange - EDI.
> It is designed to eliminate only the unrealistic requirement that a trading partner be able to understand each of its trading partner’s internal syntax and vocabulary.  Instead of businesses having to work with many different syntaxes (e.g., JSON, XML, CSV) and vocabularies (e.g., PO No. and Purchase Order #), frameworks like X12 and EDIFACT provide highly structured, opinionated alternatives intended to reduce the surface area of knowledge required to successfully integrate with trading partners.
> The vast majority of fields cannot be standardized to this degree. Take, for example, the product identifier of a line item on a Purchase Order - while X12 specifies that the 850 Purchase Order's PO107 element should be used to specify the product identifier value, the standard cannot possibly mandate which type of product identifier should be used. Some companies use SKUs (Stock Keeping Units), while others use Part Numbers, UPCs (Universal Product Codes), or GTINs (Global Trade Item Numbers); all in all, the X12 standard specifies a dictionary of 544 different possible product identifier values that can be populated in the PO106 element
> What we’re seeing here is that while a standard can be opinionated about the structure of a document and the naming of fields, it cannot be opinionated about the contents of a business transaction – the contents of a business transaction are dictated by the idiosyncrasies of the business itself.

ATTEMPTS AT REPLACEMENT https://chatgpt.com/c/670d82d9-c488-8004-967f-2a987b16c9e9
* XML, s-expressions https://en.wikipedia.org/wiki/S-expression#Parsing https://news.ycombinator.com/item?id=31840852
* JSON Schema https://www.stedi.com/blog/getting-started-with-the-x12-file-format
> In the healthcare sector, the Health Insurance Portability and Accountability Act of 1996 (HIPAA) requires that all insurance carriers exchange transactions such as claims, eligibility checks, prior authorizations, and enrollments using a standardized EDI format called X12 HIPAA. A small group of legacy clearinghouses process the majority of these transactions, offering consolidated connectivity to carriers and providers. Stedi is building the world's only API-first clearinghouse. By offering modern API interfaces alongside traditional real-time and batch EDI processes, we enable both healthcare technology businesses and established players to exchange mission-critical transactions...by offering a modern API interface for running eligibility checks, processing claims, and ingesting ERAs, healthcare technology businesses can exchange transactions with payers without dealing with the EDI protocol or carrier-specific connectivity. - Stedi job posting
