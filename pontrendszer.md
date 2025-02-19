## Pontszerzési szabályok

* Egy jogcímen csak egyszer szerezhető pont (pl. nem lehet 3 külső osztálykönyvtárral 21 pontot összeszedni), kivéve ahol ezt külön jelezzük
* Részpontszám nem adható, kivéve, ahol intervallum van megadva
* Kliensoldali megoldásért nem adható pont
* A szoftvernek egységes funkcióhalmazt kell nyújtania, különálló, egymáshoz nem kapcsolódó funkciókból álló szoftver nem elfogadható. Azaz különálló tutorialok összefércelését nem díjazzuk.

## Még nincs véglegesítve 2023. tavaszi félévre!

Véglegesítés után csak a következő típusú változások lehetnek
  * hallgatóknak kedvező változások (pl. új jogcímek)
  * elírások, megfogalmazásbeli pontosítások javítása
  * ellentmondások feloldása
  
Változások: lásd git history

## Társadalmi munka
* a véglegesített pontrendszer vagy gyakorlatjegyzet javítása, bővítése, módosítása pull request-tel **\[0-2, max. 5\]**
    * Helyesírási hiba is lehet, de az oktatók döntenek, hogy hány pontot (0-2) ér a módosítás
    * Többször is megszerezhető!
    * A gyakorlatjegyzet repo-ja: https://github.com/bmeaut/aspnetcorebook

## ASP.NET Core Web API
*  [HATEOAS](https://en.wikipedia.org/wiki/HATEOAS) linkek generálása a válaszban **\[7\]**
*  Web API Core által alapból nem támogatott HTTP ige (verb) implementálása **\[5-7\]**
   * pl. GET-hez hasonló működés **5**
   * pl. PATCH ige részleges módosításhoz JSON Patch dokumentumok [felküldésével](https://docs.microsoft.com/en-us/aspnet/core/web-api/jsonpatch?view=aspnetcore-6.0) **7**
   * pl. OPTIONS ige az erőforrás által támogatott igék lekérdezéséhez **7**
* verziókezelt API. Szemléltetés két különböző verziós API egyidejű kiszolgálásával. A kívánt verziót HTTP fejléc vagy például URL szegmens alapján választhatja meg a kliens. **\[7\]**   
* API (egy részének) védése felhasználó által igényelhető API kulccsal **\[7\]**
* cache megvalósítása E-TAG használatával **\[3-8\]**
  * a kliens felüküldi az E-TAG-et, szerver összeveti az adatbázisból felolvasott verzióval **3**
  * a szerver is cache-ből olvassa ki az aktuális verziót **+5**
* Szerver oldali autentikáció. Saját token provider készítése, használata esetén nem jár pont. **\[7-15\]**
  * ASP.NET Core Identity middleware-rel, süti alapú - csak böngészős/Postman kliens esetén! **7**
  * token alapú, ASP.NET Core Identity + Duende Server/IdentityServer5/OpenIddict middleware-rel, interaktív flow
    * angular, react kliens esetén **7**
    * Blazor WebAssembly kliens esetén **10**
    * egyéb kliens esetén **12**
  * Azure AD B2C-re (ingyenes szint) építve **10**
  * normál Azure AD (nem B2C) **7**
  * LDAP alapú szolgáltatásra építve **10**
  * más Identity-as-a-Service szolgáltatással (pl. Auth0) **7**
  * legalább egy külső identity provider integrálása (Google login, Windows login, stb.)  **+3**
* szerver oldali hozzáférés-szabályozás, az előbbi authentikációra építve  **\[2-5\]**
    * szerepkör alapú hozzáférés-szabályozás **2**
    * policy alapú hozzáférés-szabályozás (pl.: Claim alapon) **5**
* külső online szolgáltatás (Twitter, Facebook, Google Maps, Bing Maps, stb.) integrálása a szerveroldali alkalmazásba klienskönyvtárral (pl. HttpClient) vagy SDK-val **\[7-10\]**
  * egyszerű REST API, SDK használat nélkül, egyszerű API kulcs alapú authentikáció **7**
  * SDK-val / REST API-val, authentikációt (pl. OIDC) végrehajtva **10**
* SignalR Core alkalmazása valós idejű, szerver felől érkező push jellegű kommunikációra **\[7\]**
* teljes szerveroldal hosztolása külső szolgáltatónál **\[5-7\]**
  * Azure (ingyenes [App Services - WebApp szolgáltatás](https://docs.microsoft.com/en-us/azure/app-service/quickstart-dotnetcore)) **7**
  * egyéb szolgáltató **5**
* hosztolás service-ben (Windows Service, Linux systemd) **\[7-10\]**
  * Windows service **7**
  * Linux systemd **10**
* Publikálás docker konténerbe és futtatás konténerből **\[7\]**
* OpenAPI leíró (swagger) alapú dokumentáció **\[3-5\]**
  * minden végpont kliens szempontjából releváns működése dokumentált, minden lehetséges válaszkóddal együtt **3**
  * az API-nak egyidejűleg több támogatott verziója van, mindegyik dokumentált és mindegyik támogatott verzió dokumentációja elérhető  **+2**
* Adatbázis entitás elsődleges kulcs elrejtése a kliens elől véletlenszerűen generált, nem növekvő sorrendben kiosztott kulcsokkal. A kliens nem ismeri az adatbázis entitás kulcs értékét, helyette egy generált kulcsot lát csak. Az adatbázis **nem** tárolja a generált kulcsot. Megvalósítható kétirányú szám <-> generált azonosító függvények [segítségével](https://hashids.org/net/). **\[7\]**
* ~~WebHook-ok használata külső szolgáltatással (pl. github, slack) **\[7\]**~~  **(egyelőre nincs hivatalos támogatás, csak Lab projekt)**

## Kommunikáció, hálózatkezelés
* alacsony szintű kommunikáció (soros port, HTTP alatti OSI réteg, pl. kétirányú TCP) **\[10\]**
* HTTPS kommunikáció (self-signed tanúsítvánnyal) az ASP.NET Web API és a kliens között, hosztolás normál, nem fejlesztői webszerverben (pl. Apache, nginx, nem IIS Express) és nem Kestrel-en, szemléltetés Fiddler-rel/Postman-nel **\[5-10\]**
  * csak szerver oldali tanúsítvány **5**
  * kliens is azonosítja magát tanúsítvánnyal a szerver felé **+5**
* az API funkciók egy részének elérhetővé tétele GraphQL hívásokon keresztül, ASP.NET Core middleware segítségével (pl. [GraphQL.NET](https://graphql-dotnet.github.io/) vagy [Hot Chocolate](https://chillicream.com/docs/hotchocolate)) az EF entitásmodellre építve. Szemléltetés példahívásokkal a kliensből. **\[7-10\]**
  * csak lekérdezés **7**
  * módosítás vagy hozzáadás is (mutáció) **+3**
* az API funkciók egy részének elérhetővé tétele gRPC HTTP/2 vagy gRPC-Web hívásokon keresztül. Szemléltetés példahívásokkal kliensből vagy gRPC teszteszközből (pl. [bloomrpc](https://github.com/uw-labs/bloomrpc)) ***Azure App Service-szel, IIS-sel, böngészős klienssel korlátozottan [kompatibilis](https://docs.microsoft.com/en-us/aspnet/core/grpc/supported-platforms)!*** **\[7\]**
* az EF adatmodell kiajánlása OData szolgáltatás segítségével (*Microsoft.AspNetCore.OData* csomag). Példahívás bemutatása a kliensből OData v4 protokollt használva.  **\[7-10\]**
  * csak lekérdezés **7**
  * módosítás vagy hozzáadás vagy törlés is **+3**

## Entity Framework Core
* leszármazási hierarchia leképezése Entity Framework-kel (legalább kétszintű, legalább 3 tagú hierarchia) **\[3-7\]**
  * TPH, a diszkriminátor mező testreszabásával (saját mezőnév vagy saját értékek) **3**
  * TPT-vel **5**
  * ~~TPC-vel **7**~~ **(EF Core v6 még [nem támogatja](https://github.com/dotnet/efcore/issues/3170))**
* MS SQL/Azure SQL/LocalDB-től eltérő adatbáziskiszolgáló használata EF Core-ral (kivéve még: sqlite) **\[10-12\]**
  * Azure Cosmos DB (**NoSQL!**) **10**
  * egyéb, EF Core v6 támogatott adatbázis **5**  
* ~~saját Code-First konvenció készítése **\[5\]**~~  **(EF Core v6 még [nem támogatja](https://github.com/dotnet/efcore/issues/214))**
* saját szabályszerűség (konvenció) implementálása vagy meglevő felülbírálása reflexióval és/vagy Model API-val **\[5\]**
* saját többesszámosító (`IPluralizer`) - nem kell nyelvtanilag helyesnek lennie **\[7\]**
* automatikus újrapróbálkozás beállítása tranziens adatbázishibák (pl. connection timeout) ellen **\[2\]**
* Table splitting **\[5\]**
* ~~Entity splitting **\[5\]**~~  **(EF Core v6 még [nem támogatja](https://github.com/dotnet/efcore/issues/620))**
* alternatív kulcs **\[3-5\]**
  * alternatív kulcs bevezetése valamelyik entitásban **3**      
  * más entitás kapcsolattal hivatkozik az alternatív kulcsra **+2**
* adatbázis index konfigurációja az EF modellben **\[3\]**
* HiLo elsődleges kulcs alkalmazása **\[3\]**
* birtokolt típus (owned type) használata **\[3\]**
* adatbetöltés (seeding) migráció segítségével (`HasData`) **\[3\]**
* értékkonverter (value converter) alkalmazása EF Core leképezésben **\[3-5\]**
  * beépített, vagy külső komponensből származó value converter **3**
  * saját value converter **5**
* térbeli (_spatial_) adatok kezelése EF Core és **NetTopologySuite** segítségével. Legalább egy spatial oszlop kezelése és legalább egy spatial művelet (pl. `Contains`) alkalmazása. Nem minden provider támogaja!  **\[7\]**
* időkezelt (_temporal_) táblák kezelése EF Core segítségével. Legalább egy időkezelt tábla használata és historikus adatának felhasználása. Csak SQL Server/LocalDB/Azure SQL provider támogatja! **\[7\]**
  
## .NET Core részfunkciók alkalmazása
* az EF Core működőképességét, az adatbázis elérhetőségét jelző health check végpont publikálása a *Microsoft.Extensions.Diagnostics.HealthChecks.EntityFrameworkCore* NuGet csomag használatával **\[3\]**
* kifejezésfa (ExpressionTree) értelmezése/ksézítése/módosítása az [Expression API](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/expression-trees/#creating-expression-trees-by-using-the-api) használatával **\[5-20\]**
    * pl. szűrés dinamikusan, paraméterből érkező property neve alapján (pl. `o => o.Prop == propNev`) **5**
    * pl. keresés kapcsolódó kollekcióban dinamikusan (pl. `o => o.Coll.Any(e => e.Prop == propNev)`) **10**
    * saját LINQ provider - **előzetes egyeztetés szükséges!** **20**
* explicit kölcsönös kizárás helyett _ConcurretBag/ConcurrentQueue/ConcurrentStack/ConcurrentDictionary_ használata olyan rétegben, ahol párhuzamos hozzáférés valóban előfordul **\[5\]**
* lock-free algoritmus implementálása és használata (könyvtári implementáció felhasználása nélkül, `Interlocked` függvények használatával) **\[10\]**
* automatizált (unit vagy integrációs) tesztek készítése  **\[7-14\]**
  * minimum 10 függvényhez/végponthoz **7**
  * a unit tesztekben a mock objektumok injektálása **+3**
  * EF Core memória-adatbázis vagy sqlite (vagy in-memory sqlite) használata teszteléshez **+4**
* XML validálás, alkalmazkodás meglévő XML formátumhoz pl. publikus webes sémához (RSS, opml) **\[7\]**
* Optimista konkurenciakezelés **\[5-15\]**
  * ütközésdetektálás és automatikus ütközésfeloldás **5**
  * ütközésfeloldás a felhasználó döntése alapján: _client wins_ vagy _store wins_ feloldással. Ütközés esetén a felhasználótól megkérdezzük, hogy a két adatverzió közül melyik legyen mentve az adatbázisba: az aktuális felhasználóé, a másik felhasználóé. Bemutatáskor szemléltetés egy példán keresztül. **10**
  * a felhasználó az eredeti értéket is választhatja (a módosítások előtti érték visszaállítása) **+5**
* pesszimista konkurenciakezelés (adatbázisobjektumok zárolása) bizonyos entitások/funkciók esetén, nem kell a teljes alkalmazásban alkalmazni. Bemutatáskor szemléltetés egy példán keresztül. **\[10\]**
* diagnosztika beépített vagy külső komponens segítségével **\[5-9\]**
  * legalább két célba, amiből legalább egy perzisztens (pl. fájl vagy adatbázis vagy külső szolgáltatás) **5**
  * struktúrált naplózás (structured logging) **+2**
  * fájl cél esetén rolling log (minden napon/héten/10 MB-onként új naplófájl) **+2**
  * az egyik cél egy külső naplózó szolgáltatás (pl. Azure Application Insights) **+2**
* áthívás nem felügyelt környezetbe (pl. natív Win32, natív linux) **\[7-12\]**
    * legalább egy nem egyszerű típus átadása/átvétele paraméterként **7**
    * saját natív kód használata, összetett típus átadásával **12**
* külső komponens használata DTO-k inicializálására **\[3\]**
   * Object mapper, pl. [AutoMapper](http://automapper.org/), [QueryMutator](https://github.com/yugabe/QueryMutator) **3**
   * Explicit kódgeneráló, pl. [MappingGenerator (ingyenes változat)](https://marketplace.visualstudio.com/items?itemName=54748ff9-45fc-43c2-8ec5-cf7912bc3b84.mappinggenerator) **3**
* logikai törlés (soft delete) megvalósítása. A logikailag törölt elemek alapértelmezésben nem lekérdezhetőek - ezen szűrés megvalósítása globális szűrőkkel (Global Query Filter) **\[5\]**
* háttérművelet(ek) megvalósítása **\[5-7\]**
  * `IHostedService` / `BackgroundService` használatával **\[5\]**
  * nem beépített, külső háttérfolyamat komponenssel, pl. Quartz.NET, Hangfire **\[7\]**
* nem nullozható referencia típusok (NRT) kényszerítése a _nullable context_ bekapcsolásával minden szerveroldali projektre **és** minden nullable context sértés figyelmeztetés hibaként kezelése. Nullable context kikapcsolása projekten belül csak indokolt esetekben. **\[3\]**
* Entitás specifikus elsődleges kulcs típusok használata (`entityA.Id = entityB.Id` fordítási hiba, ha a két entiás típusa eltér). A kliens oldalon, illetve a kontroller függvények fejlécében (pl. bemenetként) nem kell, hogy megjelenjenek ezek a típusok, csak a kontroller rétegtől lefelé (EF szinten is). [Segédkönyvtár](https://github.com/andrewlock/StronglyTypedId). **\[10\]**

## Kiegészítő, kapcsolódó technológiák alkalmazása
* [Rx.NET](https://github.com/dotnet/reactive) használata ([dokumentáció](http://reactivex.io/)) **\[7-10\]**
    * néhány alap Rx operátor használata **7**
    * két külső adatforrás integrálása **10**
* F# modul készítése és meghívása. Legalább az egyik legyen benne ezek közül: pattern matching, async, magasabb rendű függvény **\[7\]**
* külső osztálykönyvtár használata szerver oldalon. A külső komponens által megvalósított funkcionalitásért, képességért további pontszám nem adható. Nem számít ide a projekt generálásakor automatikusan bekerülő, illetve a Microsoft által készített, az alaptechnológiák függőségeit jelentő NuGet csomagok **\[7\]**
* platformfüggetlen kódbázisú szerveralkalmazás készítése és bemutatása legalább 2 operációs rendszeren az alábbiak közül: Windows, Linux, Mac, ARM alapú OS (pl. Raspberry Pi OS). Közvetlen futtatás fogadható csak el, pl. konténerből való futtatás nem (arra van külön jogcím). **\[7\]**
* NET Compiler platform (Roslyn) Diagnostic Analyzer **\[3-7\]**
  * egyszerű analyzer, pl. property név konvenciók ellenőrzése **3**
  * bonyolultabb analyzer és kód fix is, pl. kiemelés metódusba **7**
* CQRS és Mediátor tervezési minta használata a teljes alkalmazásban (MediatR) **\[5-11\]**
  * Commandok és Queryk szétválasztása és lazán csatolása mediátorral **5**
  * Domain események használata **+3**
  * MediatR behavior pipeline kiterjesztése  **+3**
