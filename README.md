# Apie
Lietuvos teritorinio administracinio suskirstymo failai skirti naudoti **Microsoft Power BI** platformoje kuriant teritorinio užpildymo žemėlapį (angl. ***Choropleth Map***).

![image](/examples/LT_choropleth_map.png)

# Tikslas
Turėti galimybę **Microsoft Power BI** platformoje kurti Lietuvos teritorinio administracinio užpildymo žemėlapius panaudojant esamas ir laisvai prieinamas **Power BI** priemones bei atvirus duomenis.

# Uždavinys
Sukurti universalius trijų Lietuvos administracinių lygių TopoJSON failus pritaikytus atviro kodo ***Drilldown Choropleth*** žemėlapio vizualizacijos įskiepiui **Power BI Desktop** aplinkoje. Šių failų sukūrimui naudoti atvirų duomenų šaltinius.

# Duomenų šaltiniai
TopoJSON failų sukūrimui buvo panaudoti šie atvirų duomenų šaltiniai:
- [Registrų centro (RC) atviri duomenys](https://www.registrucentras.lt/p/1187)
- [Oficialaus statistikos portalo (OSP) gyventojų ir būstų surašymo 2021 duomenys](https://open-data-ls-osp-sdg.hub.arcgis.com/datasets/46a45e28ef384e69a92afedea49ee421_0)
- [Eurostat NUTS 2021 classification duomenys](https://ec.europa.eu/eurostat/web/nuts/background)

# Rezultatai
Sukurti trijų Lietuvos administracinių lygių TopoJSON failai:

| Failas                              | Raw nuoroda |
|-------------------------------------|:-----------:|
| LT-apskritys-districts.json         | [:link:](https://raw.githubusercontent.com/OfficeGovLT/powerbi-map-lt/main/topojson/LT-apskritys-districts.json) |
| LT-savivaldybes-municipalities.json | [:link:](https://raw.githubusercontent.com/OfficeGovLT/powerbi-map-lt/main/topojson/LT-savivaldybes-municipalities.json) |
| LT-seniunijos-wards.json            | [:link:](https://raw.githubusercontent.com/OfficeGovLT/powerbi-map-lt/main/topojson/LT-seniunijos-wards.json) |

Failuose saugomos teritorinio vieneto ribų geografinės koordinatės WGS-84 koordinačių sistemoje ir geografinį objektą aprašantys laukai:
### LT-apskritys-districts.json
| Laukas    | Aprašas                   | Šaltinis; pastabos |
|----------:|---------------------------|--------------------|
| OBJECTID  | Objekto indentifikatorius | Lokalus            |
| NUTS_2    | NUTS 2 kodas              | Eurostat           |
| NUTS_3    | NUTS 3 kodas              | Eurostat           |
| APS_KODAS | Apskrities kodas          | RC                 |
| APS_PAV   | Apskirties pavadinimas    | RC                 |

### LT-savivaldybes-municipalities.json
| Laukas    | Aprašas                   | Šaltinis; pastabos |
|----------:|---------------------------|--------------------|
| OBJECTID  | Objekto indentifikatorius | Lokalus            |
| NUTS_3    | NUTS 3 kodas              | Eurostat           |
| APS_KODAS | Apskrities kodas          | RC                 |
| APS_PAV   | Apskirties pavadinimas    | RC                 |
| LAU_1     | LAU 1 kodas               | Eurostat           |
| SAV_KODAS | Savivaldybės kodas        | RC                 |
| SAV_PAV   | Savivaldybės pavadinimas  | RC                 |

### LT-seniunijos-wards.json
| Laukas     | Aprašas                         | Šaltinis; pastabos |
|-----------:|---------------------------------|--------------------|
| OBJECTID   | Objekto indentifikatorius       | Lokalus            |
| LAU_1      | LAU 1 kodas                     | Eurostat           |
| SAV_KODAS  | Savivaldybės kodas              | RC                 |
| SEN_PAV_TR | Seniūnijos pavadinimas trumpas  | RC                 |
| SEN_UID    | Seniūnijos unikalus kodas       | Lokalus; savivaldybės kodo, vertikalaus brūkšnio ( \| ) ir seniūnijos trumpo pavadinimo junginys |
| SEN_PAV    | Seniūnijos unikalus pavadinimas | Lokalus; savivaldybės pavadinimo, vertikalaus brūkšnio ( \| ) ir seniūnijos pavadinimo junginys  |
| SEN_KODAS  | Seniūnijos kodas                | RC; papildytų miestų ir savivaldybės kodas yra neoficialus. Jį sudaro 4 simboliai: pirmi du – savivaldybės kodas, kiti du yra nuliai |
| OSP_ID     | OSP identifikatorius            | OSP                                                                                              |
| OSP_TIPAS  | OSP seniūnijos tipas            | OSP; SEN – oficialiai registruota seniūnija, GYV – miestai, SAV - savivaldybė                    |

Taip pat pateikti trys testiniai duomenų failai CSV formate:
- [LT-apskritys-districts.csv](https://raw.githubusercontent.com/OfficeGovLT/powerbi-map-lt/main/testdata/LT-apskritys-districts.csv)
- [LT-savivaldybes-municipalities.csv](https://raw.githubusercontent.com/OfficeGovLT/powerbi-map-lt/main/testdata/LT-savivaldybes-municipalities.csv)
- [LT-seniunijos-wards.csv](https://raw.githubusercontent.com/OfficeGovLT/powerbi-map-lt/main/testdata/LT-seniunijos-wards.csv)

Jie naudojami Lietuvos administracinio žemėlapio [Power BI pavyzdyje](https://github.com/OfficeGovLT/powerbi-map-lt/blob/main/examples/Lietuva%20Choropleth.pbix).

# Žinomi netikslumai ir apribojimai
Siekiant išlaikyti žemėlapio vizualinį vientisumą, seniūnijų lygmens failas buvo papildytas miestais ir viena savivaldybe, o kelių seniūnijų teritorijos buvo išplėstos tam, kad užpildyti gretimas tuščias žemėlapio vietas. Atsižvelgus į šiuos pakeitimus, nerekomenduojama teritorinių vienetų geometrinių plotų naudoti tiksliems skaičiavimams.
