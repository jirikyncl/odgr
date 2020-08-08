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
- **Výměnný formát (VFK)** - vlastní textový formát pro výměnu dat
 
Kromě mapových vrstev zde nic zajímavého ke zpracování zdarma vlastně není (na to stačí RUIAN). VFK je těžkopádný formát, 
který v neplacené podobě (https://services.cuzk.cz/vfk/ku/) obsahuje základní data, v placené pak přidává například osobní 
údaje.


## RUIAN - Registr územní identifikace adres a nemovitostí

https://www.cuzk.cz/ruian/

**Provozuje:** ČÚZK - Český úřad zeměměřičský a katastrální


### Adresní místa

https://nahlizenidokn.cuzk.cz/StahniAdresniMistaRUIAN.aspx

**Popis:** Varianta buď pro celou ČR nebo po obcích. Výstup je **CSV** s definicí adresního místa a jeho souřadnicovým bodem.


### Nemovitosti

https://vdp.cuzk.cz/vdp/ruian/vymennyformat/vyhledej

**Popis:** Pomocí VDP (veřejný dálkový přístup) je možné získat data k základním územním celkům (stát, kraje, obce, 
městské části, parcely, stavební objekty). Výstup je **XML**, které se dá zpracovat např. pomocí GDAL ogr2ogr.


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


@TODO - dale

## Registry ekonomických subjektů (IČO)

### OR / VR / VREO - Obchodní rejstřík / Veřejný rejstřík / Veřejný rejstřík ekonomických objektů / Veřejný rejstřík a sbírka listin

https://or.justice.cz/ias/ui/rejstrik

Více názvů pro jedno a totéž.

Provozuje MS: Ministerstvo spravedlnosti

ARES obsahuje bulk export pro tento rejstřík. Ten zahrnuje subjekty a k nim přiřazené strukturální vazby. Je vidět, kdo je jednatelem atp.

Nejsou zde živnostníci..., jen společnosti.

Datove sady, jako např. https://dataor.justice.cz/vos-actual-praha-2019 obsahují i údaje o exekucích a insolvencích.


### RŽP - Registr živnostenského podnikání

http://www.rzp.cz/

### RES - Registr ekonomických subjektů

http://apl.czso.cz/irsw/

Provozuje ČSÚ: Český statistický úřad

Získání dat: https://www.czso.cz/csu/res/poskytovani_udaju_z_res

Cena 6000 Kč za databázi

Obdobná data nabízejí https://www.inisoft.cz/software/res-plus za poloviční cenu

### ROS - Registr osob 

Pránické a podnikající osoby, přijde mi to podobné jako RES.

Provozuje ČSÚ: Český statistický úřad

https://www.czso.cz/csu/czso/registr_osob

### ARES

Provozuje MF: Ministerstvo financí

ARES čerpá data z VR, RŽP, RES

obsahuje limitované API, které hledá nad všemi dílčími registry

obsahuje bulk soubor, kde jsou jen údaje z VR

## Registry obyvatel

### ROB - Registr obyatel

Provozuje MV: Ministerstvo vnitra

Obsahuje adresy, data narození osob na našem úazemí

Není veřejné to vypadá, mohu se ptát jen sám na sebe nebo na nějakou osobu blízkou.

Bez poplatku

### EO - Evidence obyvatel

Provozuje: Ministerstvo vnitra

Obsahuje adresy, data narození osob na našem úazemí, jen státních občanů

Není veřejné to vypadá, mohu se ptát jen sám na sebe nebo na nějakou osobu blízkou.

Evidence obyvatel je asi jedním ze zdrojů pro ROB

Správní poplatek 50 Kč


## Registry dlužníků

### BRKI - Bankovní registr klientských informací

### NRKI - Nebankovní registr klientských informací 

### Solus - Sdružení na Ochranu Leasingu a Úvěrů Spotřebitelům

Soukromý registr (některé pojišťovny atp.)

### CERD - Centrální registr dlužníků ČR

Podvod

### IR - Insolvenční rejstřík

https://isir.justice.cz/isir/common/stat.do?kodStranky=SLEDOVANIWS

Provozuje MS: Ministerstvo spravedlnosti

Poskytuje webovou službu IRIS_CUZK_WS2 pomocí které se dá dotazovat na subjekty v insolvenci pomocí SOAP.

### EÚ - Evidence úpadců

http://upadci.justice.cz/cgi-bin/sqw1250.cgi/upkuk/s_i8.sqw

Provozuje MS: Ministerstvo spravedlnosti

Webová stránka pro nalezení úpadce.

## Registr exekucí

### CEE - Centrální evidence exekucí

https://www.ceecr.cz/

Provozuje exekutorská komora

Vyhladávání v Centrální evidenci exekucí je zpoplatněno ze zákona 329/2008 Sb. (30 - 60 Kč)


## Dražby 

### UZSVM - Úřad pro zastupování státu ve věcech majetkových

https://www.nabidkamajetku.cz - jejich portál s dražbami majetku ve správě státu.

Otevřená data nemají, ale dá se použít jejich API, které používá FE tohohoto webu.


## Zdroje

http://www.geoportalpraha.cz/cs/opendata

https://data.gov.cz/datov%C3%A9-sady

https://data.mfcr.cz/en/dataset?query=&sort_by=changed&sort_order=ASC

http://opendata.praha.eu/dataset

https://www.hlidacstatu.cz/data

https://opendata.gov.cz/nastroj:narodni-katalog-otevrenych-dat

kokes/od

kokes/knod


## Zpracovat

NR Nadační rejstřík
OR Obchodní rejstřík
ROPS Rejstřík obecně prospěšných společností
RSVJ Rejstřík společenství vlastníků jednotek
RU Rejstřík ústavů
SR Spolkový rejstřík




