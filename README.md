# ODGR - Open Data GEO Registry

Seznam otevřených datových zdrojů, které lze využít při zpracovávání územních ploch ČR. Seznam obsahuje údaje o provozovateli, 
způsobu získání dat, jejich povaze a zpracování.

Téměř všechny zdroje pracují se souřadnicovým systémem JTSK.


## KN - Katastr nemovitostí

https://www.cuzk.cz

**Provozuje:** ČÚZK - Český úřad zeměměřičský a katastrální

**Popis:** ČÚZK shromažďuje údaje o parcelách, budovách, LV, vlastnících, ... Ty poskytuje několika způsoby:

https://cuzk.cz/Katastr-nemovitosti/Poskytovani-udaju-z-KN/Poskytovani-udaju-z-KN.aspx

- **Dálkový přístup do KN** - webová aplikace + webová složba - **placené**
- **Nahlížení do KN** - webová aplikace, není dovoleno strojové zpracování
- **Katastrální mapy** - a WMS služby
- **Výměnný formát (VFK)** - vlastní textový formát pro výměnu dat (https://github.com/jirikyncl/vfk-importer)
  - https://services.cuzk.cz/vfk/ku/ - Katastrální mapa - Parcely, stavební objekty, katastrální území, města, popisné informace, věcná břemena ... (existuje placená podoba VFK, kde jsou další údaje o LV, vlastnících, ...)
  - https://services.cuzk.cz/vfk-gmpl/ku/ - Geometrické plány
- **INSPIRE** - Infrastruktura pro společné informace EU. Data jsou podmnožinou VFK.
  - https://services.cuzk.cz/gml/inspire/cpx/epsg-5514/ (https://geoportal.cuzk.cz/(S(aifbxjppyy2ext15bcxt3sqg))/Default.aspx?mode=TextMeta&side=INSPIRE_PAR&metadataID=CZ-00025712-CUZK_SERIES-MD_CPX&menu=21501) 
    rozšířené parcely (obsahuje parcely a VB).
- **Další výstupy** - Pak mají různé typy dat (VKM, DXF, DGN), ale je to vždy podmnožina RUIAN
 
Kromě mapových vrstev zde nic zajímavého ke zpracování zdarma vlastně není (na to stačí RUIAN). VFK je těžkopádný formát, 
který v neplacené podobě (https://services.cuzk.cz/vfk/ku/) obsahuje základní data, v placené pak přidává například osobní 
údaje. RUIAN ale neobsahuje např. věcná břemena.

### Katalogy

https://data.gov.cz/datov%C3%A9-sady?poskytovatel=%C4%8Cesk%C3%BD%20%C3%BA%C5%99ad%20zem%C4%9Bm%C4%9B%C5%99ick%C3%BD%20a%20katastr%C3%A1ln%C3%AD


## RUIAN - Registr územní identifikace adres a nemovitostí

https://www.cuzk.cz/ruian/

**Provozuje:** ČÚZK - Český úřad zeměměřičský a katastrální


### Adresní místa

https://nahlizenidokn.cuzk.cz/StahniAdresniMistaRUIAN.aspx

**Popis:** Varianta buď pro celou ČR nebo po obcích. Výstup je **CSV** s definicí adresního místa a jeho souřadnicovým bodem.


### Územní celky

https://vdp.cuzk.cz/vdp/ruian/vymennyformat/vyhledej

**Popis:** Pomocí VDP (veřejný dálkový přístup) je možné získat data k základním územním celkům (stát, kraje, obce, 
městské části, parcely, stavební objekty, volební okrsky). Výstup je **XML**, které se dá zpracovat např. pomocí GDAL ogr2ogr.


## Výškopis

https://geoportal.cuzk.cz/(S(qrqwp2s1a2jpbggyphry5zpy))/Default.aspx?mode=TextMeta&metadataXSL=full&side=vyskopis&metadataID=CZ-CUZK-EL

**Provozuje:** ČÚZK - Český úřad zeměměřičský a katastrální

**Popis** Výškopisů je více (ZABAGED, INSPIRE) v různých přesnostech. Nenašel jsem ale žádný zdarma a ceny jsou astronimické.


## LPIS - Veřejný registr půdy

http://eagri.cz/public/app/lpisext/lpis/verejny2/plpis/

**Provozuje:** MZ - Ministerstvo zemědlství


### DPB - Díl půdního bloku

http://eagri.cz/public/app/eagriapp/lpisdata/

**Popis:** Data ve dvou formátech s rozdílným obsahem (!) XML a SHP, opět možno zpracovat pomocí GDAL.

#### Slovník
- LFA - Less Favoured Areas (méně příznivé oblasti)
- ECP - env. citlivé plochy
- EZ - ekologické zemědělství, (parametr EKO - Režim ekologického hospodářství), jinak se to jmenuje režim EZ/PO

#### Zdroje
- http://docplayer.cz/162982894-Dpb-shp-verejny-export-dpb-atributy-popis-atributu.html
- http://eagri.cz/public/web/file/2091/Uzivatelska_prirucka_pLPIS.pdf
- http://eagri.cz/public/web/file/626973/Popis_atributu_ve_verejnych_exportech_dat_LPIS.pdf
- http://eagri.cz/public/web/file/523757/Uzivatelska_prirucka__Pouziti_WMS_WFS_v1_24_20200311.pdf


### Uživatelé DPB

http://eagri.cz/public/app/lpisext/lpis/verejny/getUzivatelZakladni.jsp?idUz=1

**Popis:** Ke každému půdnímu bloku je evidován uživatel, jeho detail je k dispozici přes uvedené rozhraní. Data jsou ve formátu JSON.


### Dotace uživatelům (neptří tak docela pod LPIS)

https://www.szif.cz/cs/seznam-prijemcu-dotaci

**Provozuje:** SZIF - Státní zemědělský intervenční fond

**Popis:** Uživatelé půdních bloků mohou pobírat dotace, v dolní části jsou dotace k uživatelům ke stažení. Data ve formátu XML.


### OVP - Ochrana vody a půdy

http://eagri.cz/public/app/eagriapp/lpisdata/

@TODO


### EVP - Ekologicky významný prvek

http://eagri.cz/public/app/eagriapp/lpisdata/

@TODO


### BPEJ - Celostátní databáze BPEJ (Bonitovaná půdně ekologická jednotka)

https://www.spucr.cz/bpej/celostatni-databaze-bpej

**Provozuje:** SPÚ - Státní pozemkový úřad

**Popis:**

- Ke stažení je **SHP** file pro celou ČR, ten obsahuje geometrie, kód a cenu za m2. 
- Klasifikaci určuje VUMOP: Výzkumný ústav meliorací a ochrany půdy
- Tabulka s kódy (https://bpej.vumop.cz) se dá stáhnout a BPEJ kód extrahovat a doplnit o metadata.

#### Zdroje
- https://www.spucr.cz/bpej/definice-a-vyznam-bpej
- https://statistiky.vumop.cz/?core=popis


## ZCHÚ - Zvláště chráněná území

https://opendata.mzp.cz/organization/agentura-ochrany-prirody-a-krajiny-cr

**Provozuje:** MZP: Ministerstvo životního prostředí

Dá se stáhnout několik datových sad - **XML** (podle typu chráněného území), opět lze využít GDAL.

### Slovník
- **VZCHÚ** - Velkoplošné zvláště chráněné území
  - **NP** - Národní park
  - **CHKO** - Chráněná krajiná oblast
- **MZCHÚ** - Maloplošné zvláště chráněné území
  - **NPR** - Národní přírodní rezervace
  - **NPP** - Národní přírodní prark
  - **PR** - Přírodní rezervace
  - **PP** - Přírodní park
- **Natura 2000**
  - **EVL** - Evropsky významná lokalita
  - **PO** - Ptačí oblast
  - **SCHÚ** - Smluvně chráněná území

**(IUCN) definuje 6 typů chráněných území:**

- **Ia.** – Přísná přírodní rezervace (Natural Reserve)
- **Ib.** – Divočina (Wilderness)
- **II.** – Národní park (National Park) – Seznam národních parků ve světě
- **III.** – Přírodní památka (National Monument)
- **IV.** – Místo výskytu druhu (Habitat)
- **V.** – Chráněná krajinná oblast (Protected Landscape/Seascape)
- **VI.** – Oblast ochrany přírodních zdrojů (Managed Resource Protected Area)



## Registry ekonomických subjektů (IČO)

### OR / VR / VREO - Obchodní rejstřík / Veřejný rejstřík / Veřejný rejstřík ekonomických objektů / Veřejný rejstřík a sbírka listin

Více názvů pro jedno a totéž.

https://or.justice.cz/ias/ui/rejstrik

**Provozuje:** MS - Ministerstvo spravedlnosti

**Popis:** Nejsou zde živnostníci..., jen společnosti. Datove sady, jako např. https://dataor.justice.cz/vos-actual-praha-2019 obsahují i údaje o exekucích a insolvencích.
a jsou ve formátech **XML** a **CSV**. ARES bulk export je právě pro tento rejstřík.


### RŽP - Registr živnostenského podnikání

http://www.rzp.cz/

@TODO


### RES - Registr ekonomických subjektů

http://apl.czso.cz/irsw/

https://www.czso.cz/csu/res/poskytovani_udaju_z_res

**Provozuje:** ČSÚ - Český statistický úřad

Popis: Cena **6000 Kč** za databázi (https://www.czso.cz/csu/res/poskytovani_udaju_z_res). Obdobná data nabízejí https://www.inisoft.cz/software/res-plus za poloviční cenu.


### ROS - Registr osob 

https://www.czso.cz/csu/czso/registr_osob

**Provozuje:** ČSÚ - Český statistický úřad

**Popis:** Prvánické a podnikající osoby, přijde mi to podobné jako RES.


### ARES - Administrativní registr ekonomických subjektů

https://wwwinfo.mfcr.cz/ares/ares_es.html.cz

**Provozuje:** MF - Ministerstvo financí

**Popis:** ARES čerpá data z VR, RŽP, RES. Obsahuje limitované API, které hledá nad všemi dílčími registry, 
ale výsledná data jsou v různých formátech. Zřejmě podle typu zdrojového registru.
Poskytuje i bulk soubor, kde jsou jen údaje z VR. Ten je formátu XML (pro každé IČO zvlášť!).


## Registry obyvatel


### ROB - Registr obyatel

**Provozuje:** MV - Ministerstvo vnitra

**Popis:** Obsahuje adresy, data narození osob na našem území. Není veřejné to vypadá, mohu se ptát jen sám na sebe nebo na nějakou osobu blízkou.
Bez poplatku.


### EO - Evidence obyvatel

**Provozuje:** MV - Ministerstvo vnitra

**Popis:** Obsahuje adresy, data narození osob na našem území, jen státních občanů. Není veřejné to vypadá, mohu se ptát jen sám na sebe nebo na nějakou osobu blízkou.
Evidence obyvatel je asi jedním ze zdrojů pro ROB. Správní poplatek 50 Kč.


## Registry dlužníků


### BRKI - Bankovní registr klientských informací

@TODO


### NRKI - Nebankovní registr klientských informací 

@TODO


### Solus - Sdružení na Ochranu Leasingu a Úvěrů Spotřebitelům

Soukromý registr (některé pojišťovny atp.).


### CERD - Centrální registr dlužníků ČR

**Celé je to nějaký podvod.**


### IR - Insolvenční rejstřík

https://isir.justice.cz/isir/common/stat.do?kodStranky=SLEDOVANIWS

**Provozuje:** MS - Ministerstvo spravedlnosti

**Popis:** Poskytuje webovou službu IRIS_CUZK_WS2 pomocí které se dá dotazovat na subjekty v insolvenci pomocí SOAP.


### EÚ - Evidence úpadců

http://upadci.justice.cz/cgi-bin/sqw1250.cgi/upkuk/s_i8.sqw

**Provozuje:** MS - Ministerstvo spravedlnosti

**Popis:** Webová stránka pro nalezení úpadce. O limitech nevím.


## Registr exekucí

### CEE - Centrální evidence exekucí

https://www.ceecr.cz/

**Provozuje:** Exekutorská komora

**Popis:** Vyhladávání v Centrální evidenci exekucí je **zpoplatněno** ze zákona 329/2008 Sb. (30 - 60 Kč).


## Dražby 

### UZSVM - Úřad pro zastupování státu ve věcech majetkových

https://www.nabidkamajetku.cz

**Provozuje:** MF - Ministerstvo financí

**Popis:** Otevřená data vysloveně nemají, ale dá se použít jejich API, které používá FE tohohoto webu. Formát **JSON**.


## Lokální zdroje

http://www.geoportalpraha.cz/cs/opendata

http://opendata.praha.eu/dataset


# Katalogy

https://data.gov.cz/datov%C3%A9-sady

https://data.mfcr.cz/en/dataset?query=&sort_by=changed&sort_order=ASC

https://opendata.gov.cz/nastroj:narodni-katalog-otevrenych-dat

https://www.europeandataportal.eu

# Prozkoumat

NR Nadační rejstřík

OR Obchodní rejstřík

ROPS Rejstřík obecně prospěšných společností

RSVJ Rejstřík společenství vlastníků jednotek

RU Rejstřík ústavů

SR Spolkový rejstřík




