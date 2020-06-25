# Toegankelijke SVG iconen
Naar aanleiding van een gesprek wat ik heb gehad met een medestudent en na wat sturing van Vitaly Friedman heb ik besloten om wat onderzoek te doen naar goede toegankelijke iconen op het web.    
Het gesprek startte met het inladen van Font Awesome iconen, verplaatstte toen naar SVGs en ging daarna verder naar accesibility.      
Op deze manier zal ik het hier ook proberen te vertellen.  

## Font Awesome
Font Awesome is een font en iconen toolkit uitgebracht in 2012.    
Het is een makkelijke manier om iconen toe te voegen aan pagina’s zonder moeilijk te doen.    
Dit is de reden waarom het op vrijwel 20% van de pagina’s met third-party typefaces aanwezig is.   
Op Google Fonts na word Font Awesome het meest gebruikt.   
Er zijn meerdere negatieve zaken aan Font Awesome.    
Waaronder het feit dat je het volledige font moet inladen ook al gebruik je er waarschijnlijk maar een paar: de social iconen, het hamburger menu en het zoekicoon.   
Voor de volledige grootte van Font Awesome zou je wel meer dan 50 kleine icoon .png’tjes kunnen inladen.    
Het is dus niet alleen groot als bestand waardoor er een lange laadtijd nodig is wat het laden van de pagina ophoud, het is ook nog een onnodig aangezien je niet alles gebruikt.    
De iconen van Font Awesome zijn ook niet aanpasbaar en je zult dus vastzitten aan de standaarden die zij maken voor hun iconen.   
Als je opzoek bent naar een icoon van bijvoorbeeld een ovaal moet je dit dus alsnog anders oplossen.   
Font Awesome heeft ook geen fallbacks die iets anders laten zien wanneer het niet laad wat voor verwarring kan zorgen als een plek ineens leeg is of een `` laat zien.    
Tevens zou je ook de tijd moeten nemen om Font Awesome iconen toegankelijk te maken aangezien ze alleen bedoeld zijn als decoratieve elementen.   
Zo zou je op elk icoon nog steeds een title of een aria-label moeten zetten.   
Verder zullen fonts zich door anti-aliasing zich mogelijk op een andere plek laten zien op verschillende schermen en devices wanneer deze niet goed geplaatst worden.   
Tot slot kan ik ook nog mijn ongenoegen uiten over het gebruik van het `<i>` element wat voor italic tekst is en niet voor iconen.   
Het toevoegen van een klasse aan dit element maakt het semantisch gezien niet veel beter. 

## Scalable Vector Graphics (SVG)
Een SVG definieert vector afbeeldingen in XML formaat.   
In normaal Nederlands betekend het dat dit met behulp van formules lijnen, paden, cirkels en meer een afbeelding tekent.   
Bij normale afbeeldingen krijg je een korrelig beeld wanneer je inzoomt of de afbeelding vergroot omdat de afbeeldingen in kleine puntjes worden opgeslagen.   
Door vector afbeeldingen zoals de SVG worden er juist lijnen getrokken tussen verschillende punten.   
Op deze manier blijft zo’n afbeelding hetzelfde hoe klein of groot je deze precies laat inkrimpen of uitrekt, dit werkt ook erg goed voor print.   
Het antwoord op veel van de problemen die Font Awesome met zich mee neemt is het gebruik van SVGs.   
Het inladen van een SVG gaat gigantisch snel en kan zelfs in de HTML zelf gedaan worden.    
Het gewicht van een SVG is omdat het vector is niet anders voor kleine of voor grote iconen en is omdat het een vector formule is klein van bestandsgrootte.   
Het andere voordeel is dat je natuurlijk geen afbeeldingen hoeft in te laden die je niet gebruikt zoals bij Font Awesome.    
Tevens is het mogelijk om een SVG aan te passen en weer te exporteren met behulp van programma’s zoals Adobe Illustrator.   
Zelf gebruik ik steeds vaker een teksteditor om de XML van een SVG aan te passen. Een SVG kan je sterke fallbacks meegeven waaronder alt-tekst.   
Dit helpt ook de toegankelijkheid van dit soort elementen door het titels aan te geven. Een SVG zal er ook op elk device er hetzelfde uitzien.    
Tot slot gebruik je met een SVG het daarvoor bedoelde <svg> element en blijft de HTML semantisch correct.

## Accesibility
Een afbeelding kan natuurlijk puur voor decoratie zijn.   
Dit is af en toe omdat er al een stuk beschrijvende tekst aanwezig is of omdat de afbeelding geen toevoeging is aan de inhoud van de content.   
Wanneer er een afbeelding niet geladen kan worden of als iemand afhankelijk is van een screenreader dan is er altijd de bekende `alt=””` tag op afbeeldingen om de gebruiker te vertellen wat er had moeten staan.     
Hierbij is het belangrijk dat deze alt-tag beschrijvend is en niet hergebruikt word zowel als een inhoudelijke beschrijving is van de afbeelding en niet enkel stelt dat het een ‘afbeelding is van …’. Tevens is het ook belangrijk dat als een afbeelding decoratief is de alt-tekst leeggelaten word.    
Dit betekend dat je deze declareert als `alt=””`. Door de alt-tekst op deze manier te declareren zal een screenreader geen poging wagen om de bestandsnaam van de afbeelding op te lezen.   
Wanneer een SVG is opgeslagen is als afbeelding `bestandsnaam.svg` kan deze zoals een afbeelding in de html worden met de `<img>` tag.    
Naar mijn mening kan de SVG pas echt stralen op het moment dat je deze inline toevoegt. Op dat moment kan je deze namelijk aanspreken met CSS en Javascript om de SVG te stylen of te animeren.    
Een inline SVG element kan meerdere attributen hebben. Voor zover ik weet is het altijd netjes om na de openings tag: `<svg ` een `role=img` te plaatsen zowel als  `xmlns="http://www.w3.org/2000/svg"` om aan te geven dat het om een xml formaat SVG gaat.    
Na het sluiten van deze tag komt het `<title>` element wat binnen de SVG functioneert zoals de alttekst dat deed in de `<img>`.    

Om extra lief te zijn voor de screenreader is het wijs om de het `<title>` element een id-attribuut mee te geven en om op de `<svg>` een `aria-labelledby` attribuut neer te zetten. Op deze manier verbind je de SVG element met het title element wat er in zit.   
Ik heb mij laten vertellen dat dit voor sommige screenreaders nodig is en dit kan zeker geen kwaad.  
Zowel bij het alt-tekst attribuut en het title-element zit een maximum van 250 karakters.     
Wanneer het nodig is om meer te vertellen over de afbeelding is er een omschrijving element.    
Bij een afbeelding is dit het attribuut `longdesc=””` en voor de SVG is dit het `<desc>` element.    

Als wij dit allemaal combineren dan hebben wij een inline SVG die er zo uit ziet:  
```html
<svg 
  role=”img” 
  aria-labelledby=”coolimage description” 
  xmlns=”http://www.w3.org/2000/svg” 
  width=”500” 
  height=”500”>
  
  <title id=”coolimage”>
    Mooie afbeelding
  </title>

   <desc id=”description”>
    Dit is een mooie en langere uitleg over wat je afbeelding precies is en wilt laten zien aangezien je hier meer dan 250 karakters voor kan gebruiken.
  </desc>

   <!—Hier komen de svg onderdelen -->

</svg>
```

Deze SVG kunnen we verder nog attributen meegeven zoals: `focusable="false"` zodat er geen focus op gelegd kan worden.   
De screenreader kan ook uitgezet worden door `aria-hidden=”true”` aan het de SVG toe te voegen.   
Verder kan het `role` attribuut ook een meer beschrijvende en semantische waarde krijgen in plaats van alleen image.   
Dit is ideaal als je deze SVG in bijvoorbeeld een button doet.    
Vervolgens hebben we een afbeelding die schaalbaar is en een stuk toegankelijker is voor alle gebruikers, waaronder degene met een screenreader.   
