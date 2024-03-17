Skapa en matleveranstjänst där kunder kan registera nya matordrar och leverantörer kan uppdatera motsvarande matorder som levererad. Senare kan tjänsten även uppdateras med administratörvy med hjälp av authorization (jwt roller).

*Förslag* på endpoints
POST /auth/login
POST /auth/register
 
(endast authentiserad användare)
GET /order - lista på alla pågående ordrar
GET /order/:id - Hämta en specifik order
POST /order - skapa en ny order
PATCH /order/:id - Uppdatera en order med :id, ex. ny leveranstid, status m.m.
DELETE /order/:id - Ta bort en pågående order

I designen föreslås det att du skapar två olika roller, en för matkunder och en för matleverantörer. Börja med att fokusera på matkunden, utveckla med leverantör i första level-up:en.

Varje order består av egenskaperna:
1. Klockslag vid beställning
2. Datum vid beställning
3. kundens telefonnummer
4. kundens email
5. varor (helt ok att spara om en text sträng ["Vesuvio", "Kebabtalrik", ...])


### Level up 1
För en mer visuell upplevelse **föreslås** en mock design i [images/](images/) design, med betoning på föreslås. Ifall du hellre skapar en egen så är det helt ok. I samma mapp finns det även bifogat bakgrunds svg ifall du vill spinna vidare på samma tema i leverans och administratör vy (se level ups). 

### Level up 2 (authentiserade vanliga användare)
Skapa en vy för levenratörerna där de kan uppdatera statusen på leveranser.

Modeltyp som motsvarar statusen på en leverans bör innehålla följande data
1. beräknad leveranstid (helt ok att sätta 30 minuter från "nu")
2. levererad (true/false beroende om varorna är levererade)
3. leverantörs uid (unik identiferbar, e.g. id)

### Level up 3 (authentiserade personal, e.g. roll "admin" elr. "staff")
Lägg till en administratörvy där administratören kan få tillgång till samtliga leveranser, pågående samt avslutade. Börja med att svara på frågan, vilka endpoints behöver läggas till?

