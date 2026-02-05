#Pel·lícules i Idiomes:

- Selecciona el títol de la pel·lícula (film.title) i el nom de l'idioma (language.name).
```
Select f.title as “Titol”, l.name as “Idioma”
```
```
From film f join language l on f.language_id = l.language_id;
```
-------------------------------------------------------------------------------------------

2. #Ciutats i Països:

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

3. #Adreces i Ciutats:

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

#4. Clients i Adreces:

Selecciona el nom i cognom del client (customer) i la seva adreça (address).

Select c.first_name, c.last_name, a.address
From customer c
Join address a ON c.address_id = a.address_id;

-------------------------------------------------------------------------------------------

#5. Empleats i Adreces:
Selecciona el nom de l'empleat (staff) i la seva adreça.

Select first name, address
From staff join address on staff.address_id = address.address_id;

-------------------------------------------------------------------------------------------

#6. Pel·lícules en anglès:
Mostra els títols de les pel·lícules, però només aquelles on l'idioma sigui 'English'.

Select film.title
From file inner join language on film.language_id = language.language_id;

-------------------------------------------------------------------------------------------

#7. Pagaments i Clients:
Mostra la data del pagament (payment_date) i l'import (amount), juntament amb el nom complet del client que l'ha fet.

Select payment.payment_date, payment.amount, customer.first_name, customer.last_name
From payment join customer on payment.customer_id = customer.customer_id;

-------------------------------------------------------------------------------------------

#8. Inventari i Pel·lícules:
Mostra l'ID de l'inventari (inventory_id) i el títol de la pel·lícula que correspon a aquest ítem.

Select inventory_id, film.title
From inventory join film on film.film_id = inventory.film_id;

-------------------------------------------------------------------------------------------

#9. Lloguers i Empleats:
Mostra l'ID del lloguer (rental_id) i el nom de l'empleat (staff) que va processar el lloguer.

Select rental.rental_id,staff.first_name
From rental join staff on rental.staff_id = staff.staff_id;

-------------------------------------------------------------------------------------------

#10. Clients i Botigues:
Mostra el nom del client i l'ID de la botiga (store_id) a la qual està assignat, però assegura't de mostrar l'adreça de la botiga (necessitaràs unir customer i store, i després store i address).
Versió 1: Mostra només la relació del client amb la botiga
Versió 2: Mostra client, botiga i adreça
Versió 3: Mostra client, botiga, adreça del client i adreça de la botiga

Versió 10.1
Select first_name, store_id
From customer;

Versió 10.2
Select customer.first_name, customer.ast_name, store_id, address
From customer
Join store on customer.store_id = store.store_id
Join address on store.address_id = address.address_id;

Versió 10.3
Select cu.first_name, cu.last_name, st.store_id, adreca_cliente.address, adreca_botiga.address 
From customer cu
Join store st on cu.store_id = st.store_id
Join address adreca_client on cu.address_id = adreca_client.address_id
Join address adreca_botiga on st.address_id = adreca.address_id;

-------------------------------------------------------------------------------------------

#11. Pel·lícules i Categories:
Mostra el títol de la pel·lícula i el nom de la seva categoria (category.name). Pista: film -> film_category -> category.

Select film.title, category.name
From film
Join film_category on film.film_id = film.category. film_id
Join category on film_category.category_id = category.category_id;

-------------------------------------------------------------------------------------------

#12. Pel·lícules i Actors:
Mostra el títol de la pel·lícula i el nom i cognom dels actors que hi surten. Pista: film -> film_actor -> actor.

Select f.title, a.first_name, a.last_name
From film f
Join film_actor fa on f.film_id = fa.film_id
Join actor a on fa.actor_id = a.actor_id;

-------------------------------------------------------------------------------------------

#13. Clients i Ciutats:
Volem saber de quina ciutat és cada client. Mostra el nom del client i la ciutat. Pista: customer -> address -> city.

Select c.first_name, ci.city
From customer c
Join address a ON c.address_id = a.address_id
Join city.ci ON a.city_id = ci.city_id;

-------------------------------------------------------------------------------------------

#14. Inventari, Pel·lícula i Botiga:
Mostra l'ID de l'inventari, el títol de la pel·lícula i l'ID de la botiga on es troba.

Select i.inventory_id, f.title, i.store_id
From inventory i
Join film f ON i.film_id = f.film_id;

-------------------------------------------------------------------------------------------
