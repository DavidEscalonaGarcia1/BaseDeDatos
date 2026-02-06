# Nivell 1: Unions directes (2 taules)

## 1) Pel·lícules i Idiomes:

- Selecciona el títol de la pel·lícula (film.title) i el nom de l'idioma (language.name).

```
Select f.title as “Titol”, l.name as “Idioma”
```
```
From film f join language l on f.language_id = l.language_id;
```

-------------------------------------------------------------------------------------------

## 2) Ciutats i Països:

- Selecciona el nom de la ciutat (city.city) i el nom del país al qual pertany (country.country).

```
Select city.city, country.country
```
```
From city 
```
```
Join country on city.country id = country.country_id;
```

-------------------------------------------------------------------------------------------

## 3) Adreces i Ciutats:

- Selecciona l'adreça (address.address) i el nom de la ciutat (city.city) de la taula address.

```
Select a.address, c.city
```
```
From a.address as “Adreça”, c.city as “Ciutat”
```
```
From address a join city c on a.city_id = c.city_id;
```

-------------------------------------------------------------------------------------------

## 4) Clients i Adreces:

- Selecciona el nom i cognom del client (customer) i la seva adreça (address).

```
Select c.first_name, c.last_name, a.address
```
```
From customer c
```
```
Join address a ON c.address_id = a.address_id;
```

-------------------------------------------------------------------------------------------

## 5) Empleats i Adreces:

- Selecciona el nom de l'empleat (staff) i la seva adreça.

```
Select first name, address
```
```
From staff join address on staff.address_id = address.address_id;
```

-------------------------------------------------------------------------------------------

## 6) Pel·lícules en anglès:

- Mostra els títols de les pel·lícules, però només aquelles on l'idioma sigui 'English'.

```
Select film.title
```
```
From file inner join language on film.language_id = language.language_id;
```

-------------------------------------------------------------------------------------------

## 7) Pagaments i Clients:

- Mostra la data del pagament (payment_date) i l'import (amount), juntament amb el nom complet del client que l'ha fet.

```
Select payment.payment_date, payment.amount, customer.first_name, customer.last_name
```
```
From payment join customer on payment.customer_id = customer.customer_id;
```

-------------------------------------------------------------------------------------------

## 8) Inventari i Pel·lícules:

- Mostra l'ID de l'inventari (inventory_id) i el títol de la pel·lícula que correspon a aquest ítem.

```
Select inventory_id, film.title
```
```
From inventory join film on film.film_id = inventory.film_id;
```

-------------------------------------------------------------------------------------------

## 9) Lloguers i Empleats:

- Mostra l'ID del lloguer (rental_id) i el nom de l'empleat (staff) que va processar el lloguer.

```
Se`ect rental.rental_id,staff.first_name
```
```
From rental join staff on rental.staff_id = staff.staff_id;
```

-------------------------------------------------------------------------------------------

## 10) Clients i Botigues:

- Mostra el nom del client i l'ID de la botiga (store_id) a la qual està assignat, però assegura't de mostrar l'adreça de la botiga (necessitaràs unir customer i store, i després store i address).
###### Versió 1: Mostra només la relació del client amb la botiga
###### Versió 2: Mostra client, botiga i adreça
###### Versió 3: Mostra client, botiga, adreça del client i adreça de la botiga

- Versió 10.1

```
Select first_name, store_id
```
```
From customer;
```

- Versió 10.2

```
Select customer.first_name, customer.ast_name, store_id, address
```
```
From customer
```
```
Join store on customer.store_id = store.store_id
```
```
Join address on store.address_id = address.address_id;
```

- Versió 10.3

```
Select cu.first_name, cu.last_name, st.store_id, adreca_cliente.address, adreca_botiga.address 
```
```
From customer cu
```
```
Joon store st on cu.store_id = st.store_id
```
```
Join address adreca_client on cu.address_id = adreca_client.address_id
```
```
Join address adreca_botiga on st.address_id = adreca.address_id;
```

-------------------------------------------------------------------------------------------

# Nivell 2: Camins de 3 taules o taules intermèdies

## 11) Pel·lícules i Categories:

- Mostra el títol de la pel·lícula i el nom de la seva categoria (category.name). Pista: film -> film_category -> category.

```
Select film.title, category.name
```
```
From film
```
```
Join film_category on film.film_id = film.category. film_id
```
```
Join category on film_category.category_id = category.category_id;
```

-------------------------------------------------------------------------------------------

## 12) Pel·lícules i Actors:

- Mostra el títol de la pel·lícula i el nom i cognom dels actors que hi surten. Pista: film -> film_actor -> actor.

```
Select f.title, a.first_name, a.last_name
```
```
From film f
```
```
Join film_actor fa on f.film_id = fa.film_id
```
```
Join actor a on fa.actor_id = a.actor_id;
```

-------------------------------------------------------------------------------------------

## 13) Clients i Ciutats:

- Volem saber de quina ciutat és cada client. Mostra el nom del client i la ciutat. Pista: customer -> address -> city.

```
Select c.first_name, ci.city
```
```
From customer c
```
```
Join address a ON c.address_id = a.address_id
```
```
Join city.ci ON a.city_id = ci.city_id;
```

-------------------------------------------------------------------------------------------

## 14) Inventari, Pel·lícula i Botiga:

- Mostra l'ID de l'inventari, el títol de la pel·lícula i l'ID de la botiga on es troba.

```
Select i.inventory_id, f.title, i.store_id
```
```
From inventory i
```
```
Join film f ON i.film_id = f.film_id;
```

-------------------------------------------------------------------------------------------

## 15) Lloguers detallats (Client):

- Mostra la data de lloguer, el títol de la pel·lícula llogada i el nom del client. Pista: rental -> inventory -> film (per al títol) i rental -> customer (per al client).

```
Select rental.rental_date, film.title, customer.first_name, customer.last_name
```
```
From rental
```
```
Join inventory on rental.inventory_id = inventory.inventory_id
```
```
Join film on inventory.film id = film.film=id
```
```
Join customer on rental.customer_id = customer.customer_id;
```

-------------------------------------------------------------------------------------------

# Nivell 3: Múltiples Joins i Lògica de Negoci

## 16) Clients i Països:

- Volem un llistat dels clients indicant el seu país de residència. Mostra: Nom Client, País.

```
Select customer.firat_name, customer.last_name, country .country
```
```
From customer
```
```
Join address on customer.address_id = address_id = address.address_id
```
```
Join city on addres.city_id = city.city_id
```
```
Join country on city.country_id = country.country_id;
```

-------------------------------------------------------------------------------------------

## 17) Actors de "ACADEMY DINOSAUR":

- Mostra només els noms dels actors que han actuat a la pel·lícula titulada "ACADEMY DINOSAUR".

```
Select actor.firt_name, actor.last_name, film.title
```
```
From actor
```
```
Join film_actor on actor.actor_id = film_actor.actor_id
```
```
Join film on film_actor.film_id =film.film_id;
```
```
Where film.title='ACADEMY DINOSAUR';
```

-------------------------------------------------------------------------------------------

## 18) Qui ha llogat què? (Filtre per nom):

- Mostra els títols de les pel·lícules que ha llogat la clienta 'MARY SMITH'.

```
Select f.title, cu.first_name, cu.last_name
```
```
From rental r 
```
```
Join inventory inv on r.inventory_id = inv.inventory_id 
```
```
Join film on inv.film_id = f.film_id
```
```
Join customer cu on rental.customer_id = cu.customer_id
```
```
Where cu.first_name='MARY' and cu.last_name='SMITH';
```

-------------------------------------------------------------------------------------------

## 19) Pagaments detallats:

- Mostra la data del pagament, l'import, el nom del client i el nom de l'empleat que ha cobrat.

```
Select payment.payment_date, payment-amount, customer.first_name, customer.last_name, staff.first_name, staff_name
```
```
From payment
```
```
Join customer on payment.customer_id = customer.customer_id
```
```
Join staff on payment.staff_id = staff.staff_id;
```

-------------------------------------------------------------------------------------------

## 20) Informació completa de la Botiga:

- Mostra l'ID de la botiga, la ciutat on està i el país.

```
Select store.store_id, city.city, country.country
```
```
From store
```
```
Join address on store.address_id = address.address_id
```
```
Join city ci on city.city_id = address.address_id
```
```
Join country co on ci.country_id = co.country_id;
```

-------------------------------------------------------------------------------------------

# Nivell 4: LEFT JOIN i RIGHT JOIN

## 21) Totes les películes i si son a l'inventari (LEFT JOIN)

- Volem una llista de totes les pel·lícules i, si en tenim còpies, el seu ID d'inventari. Si no en tenim, volem que surti la pel·lícula igualment amb un NULL.

```
Select f.title, i.inventory_id
```
```
From film f
```
```
Left Join inventory i on f.film_id = i.film_id;
```

-------------------------------------------------------------------------------------------

## 22) Tots els idiomes i les seves pel·lícules (RIGHT JOIN).

- Volem llistar tots els idiomes disponibles a la base de dades i el títol de les pel·lícules associades. Fes servir RIGHT JOIN amb la taula d'idiomes a la dreta. Si per un idioma no hi han pel.lícules, s'ha de mostrar l'idioma i un NULL

```
Select f.title, l.name as language
```
```
From films f
```
```
Right Join language l on f.language_id = l.language_id; 
```

-------------------------------------------------------------------------------------------

## 23) Actors i les seves pel·lícules (LEFT JOIN).

- Llista tots els actors i l'ID de les pel·lícules que han fet. Encara que a Pagila tots els actors han treballat, aquesta consulta és la manera correcta de verificar si tenim algun actor "a l'atur".

```
Select a.actor_id, a.first_name, a.last_name, fpa.film_id
```
```
From actor a
```
```
Left Join film_actor fpa ON a.actor_id = fpa.actor_id;
```

-------------------------------------------------------------------------------------------

## 24) Inventari i Lloguers (LEFT JOIN).

- Mostra tot l'inventari (cintes físiques) i l'ID del lloguer si està llogada. Volem veure totes les cintes, fins i tot les que mai s'han llogat (o l'historial de lloguer).

```
Select i.inventory_id, r.rental_id
```
```
From inventory i
```
```
Left Join rental r ON i.inventory_id = r.inventory_id;
```

-------------------------------------------------------------------------------------------

## 25) Comparativa: Pel·lícules sense inventari (RIGHT JOIN).

- Repeteix l'exercici 1 (pel·lícules i inventari) però utilitzant RIGHT JOIN. Posa inventory a l'esquerra i film a la dreta.

-------------------------------------------------------------------------------------------

## 26) Troba les pel·lícules que NO tenim a l'inventari.

- Utilitza un LEFT JOIN i filtra amb WHERE per mostrar només els títols que tenen l'ID d'inventari a NULL.

-------------------------------------------------------------------------------------------

## 27) Compta quantes pel·lícules ens falten a l'inventari.

- En lloc de llistar els títols, volem saber la xifra total de pel·lícules que consten a la base de dades però no tenim físicament.

-------------------------------------------------------------------------------------------

## 28) Troba idiomes sense pel·lícules (RIGHT JOIN + WHERE).

- Mostra els noms dels idiomes que no tenen cap pel·lícula associada a la base de dades.

-------------------------------------------------------------------------------------------

## 29) Suma del cost de reemplaçament de les pel·lícules "perdudes".

- Volem saber quants diners representaria (segons replacement_cost) si haguéssim de comprar una còpia de totes les pel·lícules que actualment no tenim a l'inventari.

-------------------------------------------------------------------------------------------

## 30) Llistar pel·lícules 'G' que NO estan a l'inventari (Filtre compost).

- Volem títols de pel·lícules que siguin aptes per a tots els públics (rating = 'G') I que, a més a més, no tinguem a l'inventari.

-------------------------------------------------------------------------------------------