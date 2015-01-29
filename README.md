<h4>Requisitos</h4>
Se necesita instalar <b>cURL</b> para utilizar la API propia de filmdate.

- <h6>Instalar cURL para la API:</h6>
  >*sudo apt-get install php5-curl*

- <h6>Reiniciar apache:</h6>
  >*sudo /etc/init.d/apache2 restart*
<br>

<h4>Código</h4>
```js

<?php

// URL para obtener todas las películas
$peliculas="http://filmdate-filmdate.rhcloud.com/api/api.php/getPeliculas";

// Se obtiene los resultados en un array
$resultaPelis=obtenerUrl($peliculas);

// Se muestra el array
var_dump($resultaPelis);

echo "<br><br>";

// Ejemplo de URL para los datos de una sola película
$pelicula="http://filmdate-filmdate.rhcloud.com/api/api.php/getPelicula/Big%20Hero%206";

// Se obtiene los resultados en un array
$resultaPelicula=obtenerUrl($pelicula);

// Se muestra el array
var_dump($resultaPelicula);

function obtenerUrl($url){

    // Inicia sesión cURL
    $curl=curl_init($url);

    // Configura una opción para una transferencia cURL    
    curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);

    // Establece una sesión cURL
    $data=curl_exec($curl);

    // Cierra una sesión cURL
    curl_close($curl);

    // Decodifica un string de JSON
    $search_results=json_decode($data);

    // Devuelve un array de resultados
    return $search_results;

} // Cierre de la función obtenerUrl
?>
```
