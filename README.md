# TJcop
TJBot project
Dit is een voorbeeld project voor wat je met de TJBot kan doen.
## Doel
Het doel van de TJBot is om met behulp van zijn camera mensen te detecteren die zitten te bellen of appen op de fiets.
## setup
Het project gebruikt Node Red. De Node RED services draaien lokaal in een docker, zie: https://nodered.org/docs/getting-started/docker hoe je dat kan installeren.
## De flow
De flow ziet er als volgt uit:
![TJcop flow](https://raw.githubusercontent.com/Vic-s/TJcop/master/Screenshot.png)

Elke 5 seconden wordt er een foto genomen door de TJBot. 
Deze foto wordt door de object detector geanalyseerd. Vervolgens wroen 3 type objecten gefilterd elk met een eigen minimale threshold. Dit omdat het detecteren van mobieltjes veel moeilijker is en dus een lagere threshold nodig heeft dan bijvoorbeeld personen. In het filter wordt het object met de beste minimale threshold doorgestuurd naar de overlap image. 
In de overlap image word gekeken of de objecten wel bij elkaar in de buurt staan en er geen lossen personen, fietsen en mobieltjes zijn. Als er overlap in de objecten zit wordt er een message doorgezet. Deze message triggert de LED en de arm van de TJBot en speelt een sirene geluid af.


Mogelijke verbeteringen zijn er nog in bijvoorbeeld het detecteren van mobieltjes.
