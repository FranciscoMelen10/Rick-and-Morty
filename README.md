# Rick-and-Morty

Practica Web con Astro usando una API de Rick y Morty

## API
[![jikan](https://img.shields.io/badge/Documentación-000?style=for-the-badge&logo=ko-fi&logoColor=white)](https://rickandmortyapi.com/documentation)

## Comando para ejecutar la página en un servidor local en Astro
#### npm
```http
npm run dev
```

#### pnpm
```http
pnpm run dev
```

#### yarn
```http
yarn run dev
```

# Rutas dinámicas

### Paginate() de Astro
[![jikan](https://img.shields.io/badge/Documentación-000?style=for-the-badge&logo=ko-fi&logoColor=white)](https://docs.astro.build/en/reference/api-reference/#paginate)

```javascript
//Ejemplo de paginación con astro

// Parametro que se obtendra de la url "/Character/{page}" para realizar la paginación de cada personaje
const { page } = Astro.props;

export async function getStaticPaths({ paginate }) {
  // Api de rick y morty (personajes)
  let api = "https://rickandmortyapi.com/api/character";

  // Almacenara intancias de objetos de los links del total de páginas que contendra la rutas dinamicas para que astro los se haga automaticamente
  let links_api = [];

  // variable temporal para almacenar de tipo objeto los links de cada página y agregarlo al arreglo "links_api"
  let links;

  for (let index = 1; index <= 42; index++) {
    links = { pagina: api.concat(`/?page=${index}`) };
    links_api.push(links);
  }

  // paginacion de todos los personajes de la api
  return paginate(links_api, { pageSize: 1 });
}

```


### Modo Estático (SSG) de Astro
[![jikan](https://img.shields.io/badge/Documentación-000?style=for-the-badge&logo=ko-fi&logoColor=white)](https://docs.astro.build/en/core-concepts/routing/#static-ssg-mode)

```javascript
// Ejemplo de Modo Estático (SSG) con astro

// Parametro que se obtendra de la url "/Character/{name}" para realizar las consultas
const { character } = Astro.params;

export async function getStaticPaths() {
  // Almacenara intancias de objetos de la información de todos los personajes donde contendra la rutas dinamicas para que astro los se haga automaticamente haciendo las consultas atravez del id de cada personaje
  let api_array = [];

  // variable temporal para almacenar de tipo objeto los links de cada página y agregarlo al arreglo "api_array"
  let tempo;

  // consulta a la api
  const data = await fetch("https://rickandmortyapi.com/api/character").then(
    (response) => response.json()
  );
  for (let index = 1; index < data.info.count + 1; index++) {
    tempo = { params: { character: "" + index } };
    api_array.push(tempo);
  }

  // retornara todos los links de las paginas de forma dinámica para mostrar todos los datos de los personajes de la api
  return api_array;
}

```

## Tecnologías
<p>
  <img src="https://astro.js.org/astro.png" alt="css3" width="100px" height="100px"/>
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original-wordmark.svg" alt="css3" width="100px" height="100px"/>
  <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original-wordmark.svg" alt="html5" width="100px" height="100px"/>
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/99/Unofficial_JavaScript_logo_2.svg/1024px-Unofficial_JavaScript_logo_2.svg.png" alt="html5" width="100px" height="100px"/>
</p>

## Autor

- [@Francisco Melendez](https://github.com/FranciscoMelen10)


