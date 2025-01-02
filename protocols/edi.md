# ⛩️

## 参考

🔍 https://www.stedi.com/edi/x12/transaction-set/832

| BCT10 | G5310 | ERROR                                                                                                           |
|-------|-------|-----------------------------------------------------------------------------------------------------------------|
| 05    | 001   | LDT is required https://commerce.spscommerce.com/testing-and-certification/7625/partners/parcel/3029840908      |
| 05    | 003   | G5301 must be 001 https://commerce.spscommerce.com/testing-and-certification/7625/partners/parcel/3029840908    |
| 02    | 001   | https://commerce.spscommerce.com/testing-and-certification/7625/partners/parcel/3030275387/                     |
| 02    | 003   | https://commerce.spscommerce.com/testing-and-certification/7625/partners/parcel/3030273514/                     |

Here's my x12 doc:
```txt
```

I'm getting this error:
```sh
```

STEDI TEACHING
* https://www.stedi.com/blog/the-foundation-of-any-reliable-edi-system
* https://www.stedi.com/blog/getting-started-with-the-x12-file-format
* https://www.stedi.com/docs/edi-platform/edi-essentials/what-is-edi#what-is-edi
* https://www.stedi.com/blog/edi-for-developers-turn-edi-into-json
* https://www.stedi.com/blog/transaction-set-variants-in-the-amazon-850-purchase-order
* control numbers https://www.stedi.com/blog/control-numbers-in-x12-edi
* https://www.stedi.com/blog/date-and-time-in-edi
* standards at national level https://increment.com/apis/introduction-apis-egovernment/

## 进步

* _24_: Capp

# 🗺️ ECOSYSTEM

🗓️️ versions https://x12.org/news-and-events/release-schedule https://www.stedi.com/edi/x12-008050 https://www.stedi.com/blog/getting-started-with-the-x12-file-format

BIG PICTURE
* who uses: GSA, B2B (healthcare, manufacturing, railroad frieight) https://www.remedi.com/blog/edi-for-railway-freight
* who controls: corporate hacks https://x12.org/about/committees/subcommittee-x12-03-external-code-list-oversight-eco https://www.linkedin.com/in/tina-martinez-8511192/ https://cognosante.com/

## standards bodies

🗄️ `protocols.md` specs

* _EDI_: fmt for business transactions (purchases orders, sales) https://en.wikipedia.org/wiki/Electronic_data_interchange
* _ASC x12_: US standards body for x12, created by ANSI https://en.wikipedia.org/wiki/ASC_X12 https://www.nist.gov/
* _x12_: USA EDI spec
* _EDIFACT_: EU EDI spec https://en.wikipedia.org/wiki/EDIFACT

## middlemen

🧠 https://chatgpt.com/share/9b405f7d-4879-4985-be22-39fc267349f7

* new guys: https://www.stedi.com/edi/network https://www.orderful.com/
* _VAN_: middleman, alternative to P2P, provides message tracking
> To simplify the complexity of managing multiple EDI direct connections, a company can use a single connection to an EDI VAN, which provides partner connections.  The EDI VAN is simply a secure network where EDI documents can be exchanged between a network of business partners. An organization will be provided with a mailbox by the EDI VAN provider. Documents are sent and received from there and the organization checks the mailbox periodically to retrieve its documents. Most EDI VAN providers offer an alerting service that informs the sender when messages have been sent successfully and also notifies the recipient that a new message is waiting. https://www.edibasics.com/types-of-edi/edi-via-van/
* _AS2_: HTTPS for EDI, can just use SFTP
* _Conexiom_: PDF to EDI https://conexiom.com/
* _Kleinschmidt_: does EDI for Steersman
* _SPS_: does EDI for ERPs (Odoo) https://www.spscommerce.com/

## constraints

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

## replacement

```txt
Applicability Statement 2 (AS2) and Applicability Statement 4 (AS4) are internet-based protocols designed for secure and reliable data exchange between trading partners, often seen as successors to traditional EDI communication methods. While AS2 and AS4 are not a replacement for EDI itself, they modernize the way EDI messages are transmitted, offering enhanced security and efficiency over older methods like VAN (Value Added Networks).

Modern ERP (Enterprise Resource Planning) systems are increasingly offering built-in or plug-and-play B2B integration features that handle tasks traditionally done by EDI. These ERP systems use cloud-based platforms and provide real-time data exchange, which can often be easier to set up and maintain than traditional EDI systems.
```
```txt
Legacy Systems: EDI is deeply embedded in the systems of many industries, and its efficiency is tied to its machine-readable structure. Making it more human-readable would sacrifice some of this efficiency, particularly in terms of file size and processing speed.

Automation Focus: EDI was designed from the beginning to be machine-readable because it is intended for automated data exchange between systems, not for direct human interaction. Human readability has always been secondary to efficiency, accuracy, and consistency in business-to-business (B2B) communication.

Industry Adoption: Many industries that rely on EDI have invested heavily in infrastructure that supports X12. The cost and effort to completely transition to a more human-readable format are significant, so most updates have focused on compatibility and modernization without completely overhauling the format.
```

* more middlemen + better protocol
> Stedi’s native format for EDI transactions is called Guide JSON. It closely reflects the structure of an EDI transaction, but uses JSON instead of EDI syntax. https://www.stedi.com/docs/edi-platform/operate/transform-json/guide-json https://www.stedi.com/docs/edi-platform/operate/generate-edi/index
* JSON Schema https://www.stedi.com/blog/getting-started-with-the-x12-file-format
> In the healthcare sector, the Health Insurance Portability and Accountability Act of 1996 (HIPAA) requires that all insurance carriers exchange transactions such as claims, eligibility checks, prior authorizations, and enrollments using a standardized EDI format called X12 HIPAA. A small group of legacy clearinghouses process the majority of these transactions, offering consolidated connectivity to carriers and providers. Stedi is building the world's only API-first clearinghouse. By offering modern API interfaces alongside traditional real-time and batch EDI processes, we enable both healthcare technology businesses and established players to exchange mission-critical transactions...by offering a modern API interface for running eligibility checks, processing claims, and ingesting ERAs, healthcare technology businesses can exchange transactions with payers without dealing with the EDI protocol or carrier-specific connectivity. - Stedi job posting

# 🧬 SEGMENTS

* _transaction set purpose codes_: "why is document being sent?", only shows up in (typically) a single segment, can apply to multiple document lists (832, 850)
* `00` new `01` cancel previously sent doc `04` update `05` replace `06` ack receipt of sent doc `24` draft
* _qualifiers_: type for ID
* `ZZ` custom `01` DUNS `20` Health Industry Number (HIN) `30` U.S. Federal Tax Identification

## semantics

* _element_: segment subcomponent; `*` delimiter, `**` = blank
* data types: ID + NO (numeric) AN (alphanumeric) DT (date) TM (time)
* _segment_: ID + data; `~` terminal delimiter
* _loop_: list of common segments
* _envelope_: a single x12 document and its transmission; file extensions incl `.edi`, `.x12`, `.dat`, `.txt`
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

## sequence

```sh
├── ISA  # interchange header
│   └── GS  # functional header
│   └────── ST  # transaction set #1
│   └────── SE  # transaction set trailer
│   └────── ST  # transaction set #2
│   └────── SE  # transaction set trailer
│   └── GE  # functional trailer
├── IEA  # interchange trailer
```
```sh
ISA (Interchange Control Header)
  GS (Functional Group Header)
    ST (832 Transaction Set Header)
      BCT (Beginning Segment for Price/Sales Catalog)
      [Repeating group for each item]:
        LIN (Item Identification)
        G53 (Maintenance Type)
        DTM (Date/Time Reference)
        CTB (Restrictions/Conditions)
        PID (Product/Item Description)
        LDT (Lead Time)
        CTP (Pricing Information)
        DTM (Start Date)
        DTM (End Date)
      CTT (Transaction Totals)
    SE (Transaction Set Trailer)
  GE (Functional Group Trailer)
IEA (Interchange Control Trailer)
```
```sh
# issue where SPS parser referred to LDT as position 190 but it was listed as position 140 in the implementation guideline
* loop context misinterpretation: parser could expect segment to appear only under a specific context and assumes the issue is related to an incorrectly defined position
* tool-specific quirk: parsers sometimes report inaccurate segment positions when encountering unrecognized or misplaced segments
* unintended data in loop: unexpected data or improper sequence in loop might cause the tool to associate LDT with a different position
```
* high-level: ISA (initial), GSA (metadata) IEA (InterchangeEnvelope; terminal)
* LIN loop order found in position 010
* asterisks: don't grok contradictory examples to this
> No, you do not need to add an explicit * to indicate that CTB02 is not present in this context. In X12 EDI formatting, elements can be omitted from the segment without needing placeholders, as long as the subsequent elements maintain their proper positions.

```txt
The segment_count in the SE segment includes:

* All segments from ST to SE, including the ST and SE segments themselves.
* Excludes the envelope segments ISA, GS, GE, and IEA.

The ISA, GS, GE, and IEA segments form the envelope structure of the EDI document and are not part of any specific transaction set. Each transaction set (e.g., 832, 850, etc.) is encapsulated within the ST and SE segments, which define the boundary and count for the specific set.

ISA and IEA:

Represent the interchange envelope.
Used for overall document control across trading partners.
Not part of the transaction set count.
GS and GE:

Represent the functional group envelope.
Control a group of related transaction sets.
Not part of the transaction set count.
ST and SE:

Define the transaction set boundary.
SE counts all segments within this boundary, including itself and ST.
```

IMPL GUIDE
* _implementation guideline_: additional instructions from receiver re: how sender should impl 🧠 https://chatgpt.com/c/673d0121-f4d8-8004-b903-4d083157a552
* fmt of PDF is standard https://www.stedi.com/blog/transaction-set-variants-in-the-amazon-850-purchase-order
* doesn't align to actual document e.g. Fastenal
* _guideline position_: location of segment w/in implementation guideline e.g. CTP at position 170 in Fastenal 823 implementation guideline

## ☸️ meta

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

```sh
GS*SC*014654966*TST1FASTENAL*20241210*1255*1*X*004010~
```
* _GS01_: transaction set type; `SC` 832 `PO` 850
* _GS02_: sender code; `014654966`
* _GS03_: receiver code; `Fastenal`
* _GS04_: date
* _GS05_: time
* _GS06_: control number
* _GS07_: standards body; `X` for ASC x12
* _GS08_: version; `004010`

### ST / SE

HEADER
* _ST01_: transaction set type; `832`
> don't understand how this isn't duping GS01
* _ST02_: control number; matches SE02 (also matches GS06?)
* _ST03_: matches BCT10

TRAILER
* _SE01_: number of segments
* _SE02_: control number; matches ST02
```sh
SE*42*0001~
```

### BCT (purpose)

```sh
BCT*05*CAT123*V1*05~
```
* _BCT01_: catalog purpose code e.g. `SC` sales catalog `PS` price sheet `PC` catalog
* _BCT02_: catalog id
* _BCT03_: catalog version
* _BCT10_: transaction set purpose code e.g. `02` add `04` change `05` replace ("used for full updates, such as a monthly refresh")

### CTT / GE / IEA

* _CTT01_: sum of line items (e.g. `LIN`)
* _CTT02_: hash of total
* _GE01_: sum of transaction sets
* _GE02_: control number; matches GS06
* _IEA_: control number; matches GS06

## 🛰️ info

### LIN (ID)

* _LIN_: UUID e.g. UPC|SKU
* _LIN01_: internal line number for tracking
* _LIN02_: qualifier
* _LIN03_: ID itself
```sh
# UP = UPC, ID = 012345678905
LIN**UP*012345678905
```
* _DTM_: date range (for both LIN and CTP)

### G53 (op)

* _G5301_: CRUD ("maintenance operation")
* `001` update `002` delete `003` create
* if BCT10 is `05`, set to `003`

### DTM (date range)

* _DTM_: date range (for both LIN and CTP)
```sh
DTM*018*20241224~  # available date
DTM*196*20241224~  # start date
DTM*197*20241130~  # end date
```

### CTB (order quantity)

* _CTB01_: what restriction applies to
* _CTB02_: rarely used
* _CTB03_: restriction type; 57 = min order quantity
* _CTB04_: quantity
```sh
CTB*OR*57*10~
```

### PID (desc)

* _PID_: desc
* _PID01_: desc type e.g. `F` free-form `S` structured
* _PID05_: actual desc
```sh
# F = free-form
PID*F****Blue T-Shirt, Size Large
```

### LDT (lead time)

* _LDT_: lead time
```sh
# type * quantity * unit of time
# from date of purchase order to shipment * 10 * workdays
LDT*AE*10*DW~

# valid 2024.11.01-30
DTM*196*20241101~
DTM*197*20241130~
```

### CTP (price)

* _CTP_: price
* _CTP01_: price tier e.g. CN consumer WS wholesale RT retail IN industrial GO government HV healthcare
* _CTP02_: qualifier e.g. UCP (unit cost price)
* _CTP03_: unit price
* _CTP05_: unit type (composite unit of measure) e.g. each, dozen
```sh
CTP**UCP*10.50**1*EA
```

## G39 (physical characteristics)

* _G3917_: quantity
* _G3919_: unit e.g. each, set

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

* _pyedi_: parse (x12-JSON) https://github.com/freestream/pyedi
* your tmp fork for Capp https://github.com/zachvalenta/capp-pyedi
> don't forget to use you need to pull pyedi to same level as JSON generation scrip t
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
