# Requisições GET com JavaScript - Exemplo de consumo de API de países

Este é um simples exemplo de uma página HTML que utiliza JavaScript para fazer requisições GET a uma API de países e exibe as informações dos países retornados em forma de cartões. A página também possui um arquivo CSS para estilização dos elementos.

## Pré-requisitos

Antes de executar o código, você precisará de acesso à internet para fazer requisições à API de países.

## Arquivos do projeto

Certifique-se de que os seguintes arquivos estejam presentes no seu projeto:

1. **index.html**: Contém a estrutura HTML da página e faz referência aos arquivos JavaScript e CSS necessários.

2. **index.js**: Contém o código JavaScript responsável por fazer a requisição à API e criar os cartões de país.

3. **index.css**: Contém o código CSS para estilização dos elementos da página.

## Estrutura do arquivo index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Requisições GET com JavaScript</title>
  <link rel="stylesheet" href="index.css">
</head>
<body>
  <h1>Requisições Get com JavaScript</h1>
  <main id="countries">

  </main>

  <script src="index.js"></script>
</body>
</html>
```

## Estilo (CSS) - index.css

```css
* {
  box-sizing: border-box;
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  margin: 0;
  padding: 0;
}

#countries {
  display: flex;
  flex-wrap: wrap;
  padding: 2rem;
}

.country {
  background-color: #eaeaea;
  margin: 1rem;
  padding: 1rem 1.5rem;
  width: 11rem;
}

.country h2 {
  margin-bottom: .75rem;
}

.country img {
  width: 8rem;
  height: auto;
}
```

## Código JavaScript - index.js

```javascript
function createCountryCard(country) {
  const card = document.createElement('div');
  card.classList.add('country');

  const countryName = country.name.common;
  const name = document.createElement('h2');
  name.textContent = countryName;

  const flag = document.createElement('img');
  flag.src = country.flags.svg;
  flag.alt = countryName;

  card.append(name, flag);
  document.querySelector('#countries').append(card);
}

async function getCountries() {
  const response = await fetch('https://restcountries.com/v3.1/all');
  const countries = await response.json();

  countries.forEach(createCountryCard);
}

getCountries();
```

## Como funciona

1. A página HTML possui um cabeçalho com o título "Requisições GET com JavaScript" e uma estrutura para exibir os cartões dos países.

2. No arquivo CSS, definimos estilos básicos para os elementos da página, como o layout dos cartões dos países.

3. O JavaScript é responsável por fazer a requisição GET à API de países, através da função `getCountries`. Essa função utiliza a função `fetch` para obter os dados da API e a função `json()` para converter a resposta em formato JSON.

4. A função `createCountryCard` é chamada para cada país retornado pela API, e ela cria um novo elemento `div` com a classe `country` para representar o cartão do país. Dentro desse elemento, são adicionados um `h2` com o nome do país e uma `img` com a bandeira do país.

5. Os cartões de país são então adicionados à página dentro do elemento com o id `countries`, que é o local onde os cartões são exibidos.

## Executando o projeto

Para executar o projeto, basta abrir o arquivo `index.html` em um navegador web que suporte JavaScript e fazer requisições à internet. A página será carregada e os cartões dos países serão exibidos conforme as informações retornadas pela API.

## Notas adicionais

Este exemplo utiliza a API "restcountries.com" para obter informações dos países. Certifique-se de que a API está online e acessível. Caso a API não esteja mais disponível ou tenha sofrido alterações, é possível que o código precise ser adaptado para uma nova fonte de dados.

Além disso, lembre-se de que fazer requisições a APIs públicas requer atenção aos limites de uso impostos pela API. Alguns serviços podem ter limites de requisições por hora ou por dia para cada usuário.

Esse projeto é apenas um exemplo didático e pode ser expandido ou adaptado para atender a diferentes necessidades.