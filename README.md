# PP-W162-Domoticz
Integracja gniazdek z biedronki DGM PP-W162 z Domoticz

Narzędzia:
1. Ze sklepu play instalujemy na androdzie Packet Capture https://play.google.com/store/apps/details?id=app.greyshirts.sslcapture&hl=pl
2. Oryginalna aplikacja SmartDGM stąd: https://play.google.com/store/apps/details?id=com.dgm.smart&hl=pl
3. Instalacja oryginalnego pluginu sincze wg instrukcji: https://github.com/sincze/Domoticz-Tuya-SmartPlug-Plugin
4. Podmieniamy przerobione przeze mnie pliki "plugin.py" i "__init__.py"
5. Restartujemy domoticz: sudo service domoticz restart
Gdyby jednak coś nie zadziałało, to usuwamy folder z pluginem z katalogu domoticz i wykonujemy ponowny restart domoticza (usunięcie pluginu)


DevKey i localkey uzyskamy poprzez wejście do oryginalnej aplikacji ze sparowanym gniazdkiem, a nastepnie uruchomienie programu Packet Capture i właczenie ściąganie pakietów. Przechodzimy do aplikacji SmartDGM nie wychodząc z Packet Capture i przeciągamy palcem w dół aby oświeżyć. Następnie wyłaczamy snifowanie w Packet Capture i szukamy pakietu SmartDGM zawierającego wpis na czerwono (tam powinny byc nasze klucze. Pakietów będzie kilka, przeglądamy wszystkie, aż znajdziemy. Format to json (jawny tekst, więc nie będzie problemu znaleźć)

Ustawienia Sprzętu w domoticz:
IP address - adres ip gniazdka (najlepiej dodać w routerze jako stały)
DevID - ściągnięty z Packet Capture (20 znaków)
Local Key - ściągnięty z Packet Capture 16 znaków)
DPS: 1
DPS group: None
ID Amp, Watt, Volt: 18;19;20


Uwagi:
1. Gniazdko może mieć jednocześnie podłączonego jednego klienta Jak jest uruchomiona aplikacja SmartDGM to nie będzie działać w tej chwili w Domotiiczu (będzie sypać błędami w logu)
2. Każdorazowe nowe sparowanie (po usunięciu z aplikacji SmartDGM) wcześniej sparowanego gniazdka w SmartDGM wymaga aktualizacji klucza local_key i użycia Packet Capture
3. Przy przekładaniu gniazdka w inne miejsce lub lub ponownym wpięciu go pod zasilanie, najlepiej wyłączyć w Domoticz urządzenie, włączyć oryginalną aplikację SmartDGM i poczekać aż aplikacja zauważy gniazdko). Czasami gniazdko nie chce uzyskać adresu ip (ale tego nie sprawdziłem dokładnie)
