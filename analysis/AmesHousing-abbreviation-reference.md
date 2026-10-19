# Ames Housing abbreviation and code reference

This reference accompanies `AmesHousing-working.csv`. It explains category codes and shortened column names. Category spellings now follow the cited source dictionary, except for the previously approved spelled-out quality labels. Column names retain their original CSV spelling.

Current working dataset: **2,884 records and 82 columns**. The original `../AmesHousing-1.csv` remains intact.

## Current notation and missing values

- The working CSV retains the earlier quality replacements: `Po` = `Poor`, `Fa` = `Fair`, `TA` = `Typical/Average`, `Gd` = `Good`, and `Ex` = `Excellent` in quality/condition rating columns.
- `Bsmt Exposure` uses the original `Gd` code, meaning **good exposure**, rather than a general quality rating.
- `NA` is context dependent. In feature categories it can mean no alley, basement, fireplace, garage, pool, fence, or miscellaneous feature, according to the dictionary. An individual record can still contain an inconsistent or genuinely missing entry; do not infer absence from the token alone.
- In this working file, 490 blank `Lot Frontage` values were changed to `NA`, meaning unknown frontage. `Garage Yr Blt = NA` was explicitly assigned to 157 records with `Garage Type = NA`.
- Other blanks have not been globally converted to `NA`. `None` in masonry veneer type is an explicit category for no veneer.
- Two detached-garage records with missing garage years (Order 1357 and 2237) were initially excluded from the working file, leaving 2,928 records at that stage. They remain in the original CSV.
- For Order 2261 (PID `0916384070`), `Garage Yr Blt` was corrected from `2207` to `2007`. This is an agreed assumption based on the apparent typing error, house construction in 2006, and remodeling in 2007; the intended year has not been independently confirmed. That record was later excluded because its veneer information was missing.

## Additional record exclusions

The following nine records were subsequently omitted at the user's direction because the identified anomalies could not be reliably resolved. Identifiers refer to the original `Order` column, not spreadsheet row numbers. This reduced the working dataset from 2,928 to 2,919 records; all excluded records remain available in the original CSV.

| Order | Issue prompting exclusion |
|---|---|
| 851 | Remodeling year precedes house construction year |
| 1703 | Remodeling year follows sale year |
| 2181 | House/garage construction and remodeling years follow sale year |
| 2182 | Remodeling year follows sale year |
| 67 | Missing basement exposure despite positive basement area |
| 1797 | Missing basement exposure despite positive basement area |
| 2780 | Missing basement exposure despite positive basement area |
| 445 | Missing second basement finishing type |
| 1578 | Missing electrical system category |

### Veneer and basement exclusions

An additional 35 records were omitted at the user's direction, reducing the working dataset from 2,919 to 2,884 records. All identifiers below are original `Order` values, and the records remain available in the original CSV.

| Reason | Count | Order values |
|---|---:|---|
| Missing masonry veneer type and area | 23 | 56, 485, 518, 539, 868, 1096, 1120, 1123, 1128, 1185, 1455, 1728, 1752, 1784, 1800, 1840, 1841, 2230, 2261, 2383, 2393, 2456, 2824 |
| Veneer type None with positive veneer area | 7 | 364, 404, 442, 1862, 1914, 2004, 2529 |
| Veneer type present with zero veneer area | 3 | 1641, 1741, 1786 |
| Missing basement descriptors, areas, and bathroom counts | 1 | 1342 |
| Missing basement bathroom counts | 1 | 1498 |

The user chose to retain very large homes because size alone does not establish an error. Orders 1499, 1761, and 1768 remain in the working file and each has more than 4,000 square feet of above-ground living area.

## Category spelling changes

The following changes align category codes with the source dictionary. Counts refer to changed cells in the 2,928-record working file at the time of standardization, before the subsequent exclusions above. They are historical change counts, not current category frequencies. Existing spelled-out quality ratings are retained as an intentional project convention.

| Column | Previous value | Current value | Changed cells |
|---|---|---|---:|
| Exterior 2nd | Brk Cmn | BrkComm | 22 |
| Exterior 2nd | CmentBd | CemntBd | 126 |
| Exterior 2nd | Wd Shng | WdShing | 81 |
| Bldg Type | 2fmCon | 2FmCon | 61 |
| Bldg Type | Duplex | Duplx | 109 |
| Bldg Type | Twnhs | TwnhsI | 101 |
| MS Zoning | A (agr) | A | 2 |
| MS Zoning | C (all) | C | 25 |
| MS Zoning | I (all) | I | 2 |
| Neighborhood | NAmes | Names | 443 |
| Sale Type | Codes with surrounding whitespace | Same codes, trimmed | 2,534 |

`Names` is the source dictionary's exact spelling for North Ames, formerly `NAmes` in this CSV. `TwnhsI` denotes an interior townhouse unit; the final character is a capital letter I. The source uses `BrkComm` for common brick in exterior coverings and `BrkCmn` for masonry veneer; these remain distinct column-specific codes.

## Abbreviated column names and units

| Column name(s) | Meaning |
|---|---|
| PID | Parcel identification number; preserve leading zeros |
| MS SubClass | Dwelling classification code; use the code table below |
| MS Zoning | General zoning classification |
| Lot Config | Lot configuration |
| Bldg Type | Building/dwelling type |
| Overall Qual / Overall Cond | Overall material and finish quality / overall condition |
| Year Remod/Add | Remodeling or addition year; dictionary specifies construction year if neither occurred |
| Roof Matl | Roof material |
| Exterior 1st / Exterior 2nd | Primary / secondary exterior covering |
| Mas Vnr Type / Mas Vnr Area | Masonry veneer type / area |
| Exter Qual / Exter Cond | Exterior material quality / condition |
| Bsmt Qual / Bsmt Cond | Basement height rating / basement condition |
| Bsmt Exposure | Exposure of walkout or garden-level basement walls |
| BsmtFin Type 1 / BsmtFin Type 2 | First / second basement finished-area classification |
| BsmtFin SF 1 / BsmtFin SF 2 | Area associated with each basement finishing classification |
| Bsmt Unf SF / Total Bsmt SF | Unfinished / total basement area |
| Heating QC | Heating quality and condition |
| 1st Flr SF / 2nd Flr SF | First / second floor area |
| Low Qual Fin SF | Low-quality finished area across all floors |
| Gr Liv Area | Above-grade (above ground) living area |
| Bsmt Full Bath / Bsmt Half Bath | Number of basement full / half bathrooms |
| Full Bath / Half Bath | Number of above-grade full / half bathrooms |
| Bedroom AbvGr / Kitchen AbvGr | Number of above-grade bedrooms / kitchens |
| Kitchen Qual | Kitchen quality |
| TotRms AbvGrd | Total above-grade rooms, excluding bathrooms |
| Fireplace Qu | Fireplace quality |
| Garage Yr Blt | Garage construction year |
| Garage Cars | Garage capacity measured in cars |
| Garage Qual / Garage Cond | Garage quality / condition |
| Wood Deck SF / Open Porch SF | Wood deck / open porch area |
| Enclosed Porch / Screen Porch | Enclosed / screened porch area |
| 3Ssn Porch | Three-season porch area |
| Pool QC | Pool quality |
| Misc Feature / Misc Val | Miscellaneous feature / its dollar value |
| Mo Sold / Yr Sold | Sale month (1–12) / sale year |
| SalePrice | Sale price in US dollars |

`SF` means square feet; `Qual`, `Qu`, and `QC` indicate quality (QC can include condition); `Cond` means condition; `Fin` means finished; `Unf` means unfinished. Lot frontage is measured in linear feet. All area fields, including those without `SF` in their names, are measured in square feet. `Order` is the original observation number, not a housing characteristic.

## Quality and condition scales

### Letter ratings

Applies to `Exter Qual`, `Exter Cond`, `Bsmt Qual`, `Bsmt Cond`, `Heating QC`, `Kitchen Qual`, `Fireplace Qu`, `Garage Qual`, `Garage Cond`, and `Pool QC`. Not every column contains all five levels.

| Original code | Current working label | Relative order |
|---|---|---:|
| Po | Poor | 1 |
| Fa | Fair | 2 |
| TA | Typical/Average | 3 |
| Gd | Good | 4 |
| Ex | Excellent | 5 |

These are ordered categories; the gaps between levels are not necessarily equal.

Specific dictionary interpretations:

- **Bsmt Qual** describes basement height: Poor below 70 inches; Fair 70–79; Typical 80–89; Good 90–99; Excellent 100 or more.
- **Bsmt Cond**: Typical permits slight dampness; Fair includes dampness or some cracking/settling; Poor includes severe cracking, settling, or wetness.
- **Fireplace Qu**: Excellent describes exceptional masonry; Good describes a main-level masonry fireplace; Typical describes a prefabricated fireplace in the main living area or basement masonry fireplace; Fair describes a basement prefabricated fireplace; Poor describes a Ben Franklin stove.

### Overall Qual and Overall Cond

| Code | Meaning |
|---|---|
| 1 | Very poor |
| 2 | Poor |
| 3 | Fair |
| 4 | Below average |
| 5 | Average |
| 6 | Above average |
| 7 | Good |
| 8 | Very good |
| 9 | Excellent |
| 10 | Very excellent |

The dictionary defines 1–10 for both variables; this project's observed `Overall Cond` levels stop at 9.

## Dwelling classification: MS SubClass

These numbers are category codes, not quantities. PUD means planned unit development.

| Code | Meaning |
|---|---|
| 020 | One story, built 1946 or later, all styles |
| 030 | One story, built 1945 or earlier |
| 040 | One story with finished attic, any age |
| 045 | One and a half stories, unfinished, any age |
| 050 | One and a half stories, finished, any age |
| 060 | Two stories, built 1946 or later |
| 070 | Two stories, built 1945 or earlier |
| 075 | Two and a half stories, any age |
| 080 | Split or multiple levels |
| 085 | Split foyer |
| 090 | Duplex, any style or age |
| 120 | One-story PUD, built 1946 or later |
| 150 | One-and-a-half-story PUD, any age |
| 160 | Two-story PUD, built 1946 or later |
| 180 | Multilevel PUD, including split level or foyer |
| 190 | Conversion to two-family dwelling, any style or age |

## Location and lot codes

### MS Zoning

| Code in CSV | Meaning |
|---|---|
| A | Agricultural |
| C | Commercial |
| FV | Floating Village Residential (dictionary terminology) |
| I | Industrial |
| RH | Residential, high density |
| RL | Residential, low density |
| RM | Residential, medium density |

The dictionary also defines `RP` as residential low-density park; that code is not observed in this CSV.

### Street and Alley

| Code | Meaning |
|---|---|
| Grvl | Gravel |
| Pave | Paved |
| NA | No alley access, for Alley |

### Lot Shape

| Code | Meaning |
|---|---|
| Reg | Regular |
| IR1 | Slightly irregular |
| IR2 | Moderately irregular |
| IR3 | Irregular |

### Land Contour

| Code | Meaning |
|---|---|
| Lvl | Nearly flat or level |
| Bnk | Banked: substantial rise from street to building |
| HLS | Hillside: substantial slope from side to side |
| Low | Depression |

### Utilities

| Code | Meaning |
|---|---|
| AllPub | Public electricity, gas, water, and sewer |
| NoSewr | Electricity, gas, and water; septic tank instead of sewer |
| NoSeWa | Electricity and gas only |

The dictionary also defines `ELO` as electricity only; it is not observed here.

### Lot Config

| Code | Meaning |
|---|---|
| Inside | Interior lot |
| Corner | Corner lot |
| CulDSac | Cul-de-sac lot |
| FR2 | Frontage along two property sides |
| FR3 | Frontage along three property sides |

### Land Slope

| Code | Meaning |
|---|---|
| Gtl | Gentle slope |
| Mod | Moderate slope |
| Sev | Severe slope |

### Neighborhood

| Code | Name |
|---|---|
| Blmngtn | Bloomington Heights |
| Blueste | Bluestem |
| BrDale | Briardale |
| BrkSide | Brookside |
| ClearCr | Clear Creek |
| CollgCr | College Creek |
| Crawfor | Crawford |
| Edwards | Edwards |
| Gilbert | Gilbert |
| Greens | Greens |
| GrnHill | Green Hills |
| IDOTRR | Iowa Department of Transportation and Railroad |
| Landmrk | Landmark |
| MeadowV | Meadow Village |
| Mitchel | Mitchell |
| Names | North Ames |
| NoRidge | Northridge |
| NPkVill | Northpark Villa |
| NridgHt | Northridge Heights |
| NWAmes | Northwest Ames |
| OldTown | Old Town |
| Sawyer | Sawyer |
| SawyerW | Sawyer West |
| Somerst | Somerset |
| StoneBr | Stone Brook |
| SWISU | South and West of Iowa State University |
| Timber | Timberland |
| Veenker | Veenker |

### Condition 1 and Condition 2

These describe nearby features, rather than building condition. The second column records an additional condition when applicable.

| Code | Meaning |
|---|---|
| Artery | Beside an arterial street |
| Feedr | Beside a feeder street |
| Norm | Normal |
| PosN | Near a beneficial off-site feature, such as a park or greenbelt |
| PosA | Adjacent to a beneficial off-site feature |
| RRNn | Within 200 feet of a north–south railroad |
| RRAn | Adjacent to a north–south railroad |
| RRNe | Within 200 feet of an east–west railroad |
| RRAe | Adjacent to an east–west railroad |

## Building and construction codes

### Bldg Type

| Code in CSV | Meaning |
|---|---|
| 1Fam | Detached single-family dwelling |
| 2FmCon | Two-family conversion, originally a single-family dwelling |
| Duplx | Duplex |
| TwnhsI | Interior townhouse unit |
| TwnhsE | End townhouse unit |

These codes now match the source dictionary; prior CSV variants are recorded in the spelling-change table above.

### House Style

| Code | Meaning |
|---|---|
| 1Story | One story |
| 1.5Fin | One and a half stories, upper level finished |
| 1.5Unf | One and a half stories, upper level unfinished |
| 2Story | Two stories |
| 2.5Fin | Two and a half stories, upper level finished |
| 2.5Unf | Two and a half stories, upper level unfinished |
| SFoyer | Split foyer |
| SLvl | Split level |

### Roof Style

`Flat`, `Gable`, `Gambrel`, `Hip`, `Mansard`, and `Shed` are roof-shape names rather than abbreviations. A gambrel is the familiar barn-style roof; a hip roof slopes down on all sides.

### Roof Matl

| Code | Meaning |
|---|---|
| ClyTile | Clay or tile |
| CompShg | Standard composite shingles |
| Membran | Membrane roofing |
| Metal | Metal roofing |
| Roll | Roll roofing |
| Tar&Grv | Tar and gravel |
| WdShake | Wood shakes |
| WdShngl | Wood shingles |

### Exterior 1st and Exterior 2nd

Both exterior columns now use the source dictionary's material codes. Prior CSV variants are recorded in the spelling-change table above.

| Code(s) | Meaning |
|---|---|
| AsbShng | Asbestos shingles |
| AsphShn | Asphalt shingles |
| BrkComm | Common brick |
| BrkFace | Face brick |
| CBlock | Cinder block |
| CemntBd | Cement board |
| HdBoard | Hardboard |
| ImStucc | Imitation stucco |
| MetalSd | Metal siding |
| Other | Other exterior covering |
| Plywood | Plywood |
| PreCast | Precast; source dictionary does not specify the material further |
| Stone | Stone |
| Stucco | Stucco |
| VinylSd | Vinyl siding |
| Wd Sdng | Wood siding |
| WdShing | Wood shingles |

### Mas Vnr Type

| Code | Meaning |
|---|---|
| BrkCmn | Common brick veneer |
| BrkFace | Face brick veneer |
| CBlock | Cinder block |
| None | No masonry veneer |
| Stone | Stone veneer |

### Foundation

| Code | Meaning |
|---|---|
| BrkTil | Brick and tile |
| CBlock | Cinder block |
| PConc | Poured concrete |
| Slab | Slab |
| Stone | Stone |
| Wood | Wood |

## Basement and interior codes

### Bsmt Exposure

| Code | Meaning |
|---|---|
| Gd | Good exposure |
| Av | Average exposure |
| Mn | Minimal exposure |
| No | No exposure |
| NA | No basement, per dictionary; check record consistency |

`No` and `NA` have different meanings: a basement can exist without exposed walls.

### BsmtFin Type 1 and BsmtFin Type 2

| Code | Meaning |
|---|---|
| GLQ | Good living quarters |
| ALQ | Average living quarters |
| BLQ | Below-average living quarters |
| Rec | Average recreation room |
| LwQ | Low quality |
| Unf | Unfinished |
| NA | No basement, per dictionary |

### Heating

| Code | Meaning |
|---|---|
| Floor | Floor furnace |
| GasA | Gas furnace supplying forced warm air |
| GasW | Gas hot-water or steam heating |
| Grav | Gravity furnace |
| OthW | Hot-water or steam heating using fuel other than gas |
| Wall | Wall furnace |

### Central Air

`Y` = yes; `N` = no.

### Electrical

| Code | Meaning |
|---|---|
| SBrkr | Standard circuit breakers with Romex wiring |
| FuseA | Fuse box above 60 amps, all Romex wiring; average rating |
| FuseF | 60-amp fuse box, mostly Romex wiring; fair rating |
| FuseP | 60-amp fuse box, mostly knob-and-tube wiring; poor rating |
| Mix | Mixed electrical system |

### Functional

| Code | Meaning |
|---|---|
| Typ | Typical functionality |
| Min1 | Minor deductions, category 1 |
| Min2 | Minor deductions, category 2 |
| Mod | Moderate deductions |
| Maj1 | Major deductions, category 1 |
| Maj2 | Major deductions, category 2 |
| Sev | Severely damaged |
| Sal | Salvage only |

The source dictionary does not further define the distinction between deduction categories 1 and 2.

## Garages and amenities

### Garage Type

| Code | Meaning |
|---|---|
| 2Types | More than one garage type |
| Attchd | Attached to the home |
| Basment | Basement garage |
| BuiltIn | Garage incorporated into the house, typically with a room above |
| CarPort | Carport |
| Detchd | Detached from the home |
| NA | No garage |

### Garage Finish

| Code | Meaning |
|---|---|
| Fin | Finished |
| RFn | Rough finished |
| Unf | Unfinished |
| NA | No garage, per dictionary |

### Paved Drive

| Code | Meaning |
|---|---|
| Y | Paved |
| P | Partially paved |
| N | Dirt or gravel |

### Fence

| Code | Meaning |
|---|---|
| GdPrv | Good privacy |
| MnPrv | Minimum privacy |
| GdWo | Good wood |
| MnWw | Minimum wood/wire |
| NA | No fence |

### Misc Feature

| Code | Meaning |
|---|---|
| Elev | Elevator |
| Gar2 | Second garage, if not described in the garage fields |
| Othr | Other feature |
| Shed | Shed over 100 square feet |
| TenC | Tennis court |
| NA | No miscellaneous feature |

## Sale codes

### Sale Type

| Code | Meaning |
|---|---|
| WD | Conventional warranty deed |
| CWD | Cash warranty deed |
| VWD | Warranty deed with a Veterans Affairs (VA) loan |
| New | Newly constructed home sold |
| COD | Court officer deed or estate sale |
| Con | Contract with 15% down payment and regular terms |
| ConLw | Contract with low down payment and low interest |
| ConLI | Contract with low interest |
| ConLD | Contract with low down payment |
| Oth | Other sale type |

### Sale Condition

| Code | Meaning |
|---|---|
| Normal | Normal sale |
| Abnorml | Abnormal sale, such as a trade, foreclosure, or short sale |
| AdjLand | Adjoining-land purchase |
| Alloca | Allocation involving linked properties with separate deeds, such as a condo and garage |
| Family | Sale between family members |
| Partial | Home incomplete at its last assessment; associated with new homes |

## Sources and interpretation

Code meanings are factual mappings adapted from Dean De Cock's documentation for the Ames Housing dataset, based on Ames Assessor's Office records. Category spelling changes are documented above; earlier spelled-out quality labels remain a project convention. Source descriptions with typographical errors have been clarified in the explanations without changing their category codes.

- [Original Ames Housing data documentation, Journal of Statistics Education](https://jse.amstat.org/v19n3/decock/DataDocumentation.txt).
- [Readable mirror of De Cock's data documentation](https://raw.githubusercontent.com/webartifex/ames-housing/main/data/data_documentation.txt), consulted October 18, 2026; reproduces the source dictionary.
- [Original paper: Ames, Iowa: Alternative to the Boston Housing Data as an End of Semester Regression Project (2011)](https://jse.amstat.org/v19n3/decock.pdf).

Names such as `Hip` are terms rather than shortened labels. Definitions are specific to their column: for example, `Mod` describes slope in `Land Slope` but functionality deductions in `Functional`.
