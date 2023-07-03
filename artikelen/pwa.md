# Progressive Webapps: De toekomst van gebruiksvriendelijke mobiele applicaties
Tijdens deze minor heb ik het vak Progressive Web Apps gevolgd, waarbij ik kennis heb gemaakt met PWA's. Er ging een wereld voor mij open, want ineens waren de websites die ik maakte ook echt downloadbaar! Waar ik voorheen dacht dat dit alleen via appstores mogelijk was, weet ik nu dat dit door middel van een paar handige truckjes ook kan met een progressive web app. Ik weet zeker dat ook veel bedrijven baat zouden hebben bij het maken van PWA's in plaats van mobiele applicaties. In dit artikel zal ik uitleggen wat PWA's zijn, wat de voordelen zijn en hoe je ze maakt.


## Wat zijn Progressive Web Apps?
Progressive Web Apps (PWA) zijn webapplicaties die zich gedragen als een mobiele app. Ze zijn te installeren op je telefoon en kunnen gebruik maken van de hardware van je telefoon, zoals bijvoorbeeld de camera, GPS, Bluetooth en NFC. Ook kunnen ze push notificaties sturen naar je telefoon en daarmee de gebruiker op de hoogte brengen van nieuwe informatie. Dit alles zonder dat je de applicatie hoeft te downloaden uit de App Store of Google Play Store. Je kunt de website gewoon openen in je browser en vervolgens installeren op je telefoon, waar het ook echt een icoon als snelkoppeling zal krijgen.

Dat dit allemaal mogelijk is komt door Service Workers. Deze Service Workers zijn scripts die op de achtergrond draaien en de communicatie tussen de applicatie en de server regelen. Niet alleen kun je hierdoor de apps installeren op je mobiel, maar is het ook mogelijk om de applicatie te gebruiken als je geen internetverbinding hebt. Op het moment dat je de app voor de eerste keer gebruikt, worden namelijk de bezochte pagina's opgeslagen in de cache van je telefoon. Mocht je dan een keer zonder internet komen te zitten, zal de Service Worker kijken of er data over de webpagina is opgeslagen in de cache en wanneer dit het geval is wordt deze geserveerd. Op deze manier kun je de applicatie dus ook offline gebruiken.

Zoals eerder al genoemd is het door de Service Worker mogelijk om de app te downloaden op je apparaat, zonder dat je deze hoeft te downloaden uit de App Store of Google Play Store. Dit scheelt veel tijd in de ontwikkelingsfase en voor de gebruiker scheelt het opslagruimte op hun telefoon. Ook is het mogelijk om een PWA te gebruiken op een desktop computer, door het Progressive Web App Manifest. Dit is een JSON bestand waarin je de naam van de applicatie, de kleur van de applicatie en het icoon van de applicatie kunt instellen. Ook kun je in dit bestand instellen of de applicatie op een desktop computer geopend kan worden. Als je dit instelt, wordt er een snelkoppeling van de applicatie op het bureaublad van de computer geplaatst. Als je vervolgens op deze snelkoppeling klikt, wordt de applicatie geopend in een apart venster.

Kort samengevat rustten PWA's op drie pijlers:
* **Capable**: PWA's zijn in staat om gebruik te maken van de hardware van je telefoon en het is mogelijk om push notificaties te sturen
* **Reliable**: PWA's zijn betrouwbaar en kunnen ook offline gebruikt worden
* **Installable**: PWA's zijn te installeren op je telefoon en op je computer


## Wat zijn de voordelen van Progressive Web Apps? 
Progressive Web Apps hebben veel voordelen ten opzichte van normale webapplicaties en mobiele applicaties. Hieronder staan de belangrijkste voordelen van Progressive Web Apps op een rijtje:

1. **Gemakkelijke te gebruiken**: PWA's kunnen direct geopend worden via een browser zonder dat het nodig is om eerst een app te installeren. Hierdoor is het laagdrempeliger voor de gebruikers om de app uit te testen en zullen ze sneller geneigd zijn om de app te gebruiken.

2. **Snellere laadtijden**: PWA's maken gebruik van caching en andere technieken om snel te laden, waardoor zelfs bij een trage of onstabiele internetverbinding de gebruiker kan genieten van je web app. Dit verbeterd dus de gebruikerservaring en zorgt ook voor minder frustratie bij de gebruiker dan wanneer hij moet wachten op een pagina die laadt.

3. **Offline beschikbaar**: Een ander voordeel van een Progressive Web App is dat deze vrijwel altijd offline beschikbaar zijn. Door middel van caching worden de eerder bezochte pagina's opgeslagen, en wanneer de gebruiker dus geen internet heeft kan hij alsnog de pagina's bekijken die hij eerder heeft bezocht. Zodra de gebruiker weer internet heeft, worden de gegevens gesynchroniseerd met de server.

4. **Lagere ontwikkelingskosten**: Als je een native app beschikbaar wil maken voor download, moet je bepalen of je de app voor iOS, Android of voor beide besturingssystemen wil ontwikkelen. Dit betekent vaak dat je twee verschillende apps moet ontwikkelen, wat veel tijd en geld kost. Met een PWA hoef je maar één app te ontwikkelen die op beide platformen werkt door middel van de Service Worker, waardoor je dus veel tijd en geld bespaart. Ook is het hierdoor makkelijker om de app te onderhouden en updates door te voeren, omdat je maar één codebase hebt.

5. **Automatische updates**: PWA's worden automatisch bijgewerkt wanneer gebruikers ze openen via een webbrowser. Dit zorgt ervoor dat gebruikers altijd de nieuwste versie van de app hebben, zonder dat ze handmatig updates hoeven te downloaden en te installeren. Mocht de user gebruik maken van de offline versie van de app, zal deze weer worden bijgewerkt wanneer de gebruiker weer verbinding maakt met het internet.

## Hoe maak je een Progressive Web App?
Nu je weet wat een Progressive Web App is en wat de voordelen zijn, wil je natuurlijk ook weten hoe je een Progressive Web App maakt. Hieronder zal ik uitleggen hoe je dit het beste kan aanpakken.

### Stap 1: Maak een webapplicatie
De eerste stap is het maken van een webapplicatie. Dit kan in elke programmeertaal die je wil, zolang het maar een webapplicatie is. Je kan dus bijvoorbeeld een webapplicatie maken met behulp van HTML, CSS en JavaScript, maar je kan ook een webapplicatie maken met behulp van een framework zoals React, Angular of Vue.

### Stap 2: Maak een Service Worker
De tweede stap is het aanmaken van een Service Worker. Dit is een script dat op de achtergrond draait en de communicatie tussen de applicatie en de server regelt. Dit is dus een belangrijk onderdeel van de Progressive Web App. Let op dat je dit JavaScript bestand in de root van je project zet en vervolgens kun je de functionaliteiten van de Service Worker schrijven. Hieronder staat een voorbeeld van een Service Worker die de pagina's die je bezoekt opslaat in de cache van je telefoon, zodat je deze pagina's ook offline kan bekijken.

```javascript
// Define constants
const CORE_CACHE = 1
const CORE_CACHE_NAME = `core-v${CORE_CACHE}`
// Array of core assets to be cached
const CORE_ASSETS = [
    "/manifest.json",
    "/offline",
    "/css/style.css",
]

// Install event that is triggered when the service worker is first installed
self.addEventListener('install', (event) => {
    console.log("Installed service worker")

    event.waitUntil(
        // Open the cache and add all the core assets to it
        caches.open(CORE_CACHE_NAME)
            .then(cache => cache.addAll(CORE_ASSETS))
            // Activate the service worker immediately once the core assets have been cached
            .then(() => self.skipWaiting())
    )
})

//Activate event that is triggered when the service worker is activated
self.addEventListener("activate", (event) => {
    console.log("Activating service worker")
    // Ensure that the service worker takes control of all pages within its scope
    event.waitUntil(clients.claim())
})

// Fetch event that is triggered when a resource/url is fetched
self.addEventListener("fetch", (event) => {
    const req = event.request;
    console.log("Fetch event:" + req.url);

    // Check if the request is a GET request
    if (isCoreGetRequest(req)) {
        console.log('Core get request: ', req.url);

        event.respondWith(
            caches.open(CORE_CACHE_NAME)
                .then(cache => cache.match(req.url)) // Check if the request is already cached
        );
    } else if (isHtmlGetRequest(req)) { // Check if the request is a GET request for HTML
        console.log('Html get request', req.url);

        event.respondWith(
            caches.open('html-cache')
                .then(cache => cache.match(req.url))
                .then(response => response ? response : fetchAndCache(req, 'html-cache'))
                .catch(e => {
                    return caches.open(CORE_CACHE_NAME)
                        .then(cache => cache.match('/offline'))
                })
        )
    }
});

function fetchAndCache(request, cacheName) {
    return fetch(request)
        .then(response => {
            if (!response.ok) {
                throw new TypeError('Bad response status');
            }

            const clone = response.clone()
            caches.open(cacheName).then((cache) => cache.put(request, clone))
            return response
        })
}

// Checks if a request is a GET request for HTML and if the URL is in the CORE_ASSETS array
function isHtmlGetRequest(request) {
    return request.method === 'GET' && (request.headers.get('accept') !== null && request.headers.get('accept').indexOf('text/html') > -1);
}

// Checks if a request is a GET request and if the URL is in the CORE_ASSETS array
function isCoreGetRequest(request) {
    return request.method === 'GET' && CORE_ASSETS.includes(getPathName(request.url));
}

function getPathName(requestUrl) {
    const url = new URL(requestUrl);
    return url.pathname;
}

```

### Stap 3: Maak een manifest
De derde stap is het maken van een manifest. Dit is een JSON bestand waarin je de naam van de applicatie, de kleur van de applicatie en het icoon van de applicatie kunt instellen. Ook kun je in dit bestand instellen of de app op een desktop geopend kan worden. Als je dit instelt, wordt er een snelkoppeling van de applicatie op het bureaublad van de computer geplaatst. Als je vervolgens op deze snelkoppeling klikt, wordt de applicatie geopend in een apart venster. Hieronder staat een voorbeeld van een manifest.

```json
{
  "name": "Example App",
  "short_name": "Example",
  "start_url": "/index.html",
  "display": "standalone",
  "background_color": "#3E4EB8",
  "description": "An example app",
  "icons": [
    {
      "src": "images/icons-192.png",
      "type": "image/png",
      "sizes": "192x192"
    },
    {
      "src": "images/icons-512.png",
      "type": "image/png",
      "sizes": "512x512"
    }
  ]
}
```

### Stap 4: Test je PWA!
Yes, als het goed is heb je je website nu omgezet naar een Progressive Web App! Uit ervaring weet ik dat het niet altijd in één keer goed gaat, dus is het belangrijk om te testen of je app werkt zoals je verwacht. Dit testen kun je doen door via je browser de websote te bezoeken en te kijken of het installable is. Mocht dit niet het geval zijn, open dan de console om te kijken naar eventuele foutmeldingen. Mocht dit wel het geval zijn, installeer dan de app en klik er eens doorheen om te kijken of alles goed werkt. Zet daarna ook je internet uit om te kijken of de offline functionaliteit goed werkt en of de offline pagina wordt getoond. Als dit allemaal goed werkt, dan heb je een werkende PWA gemaakt!


## Voorbeeld
Mocht je het leuk vinden om een voorbeeld te zien van een PWA en hoe deze eruit ziet nadat je hem geïnstalleerd hebt, kun je [RijksKunst bekijken](https://rijkskunst.up.railway.app/). Dit is een PWA die ik gemaakt heb tijdens mijn minor en waarbij je alle kunst van het Rijksmuseum kunt bekijken vanuit je luie stoel!



## Bronnen
* [What is a Progressive Web App](https://www.techtarget.com/whatis/definition/progressive-web-app-PWA)
* [What is PWA? Progressive Web Apps in eCommerce Explained](https://vuestorefront.io/pwa)
* [What are PWA's](https://web.dev/what-are-pwas/)