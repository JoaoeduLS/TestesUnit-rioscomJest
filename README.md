### Criando um Test Unitários com Jest

#### Inicio

        npm init

        npm install --save-dev jest

#### comoando para testa

        npm test

#### Criar um file com o final .test.js

<br>

<p>Sempre que voce for testa va ao package.json e mude para esse scripts test:</p>

```js
"scripts": {
    "test": "jest"
  },
```

#### Codigo do para fazer o test funcionar :

```js
function somar(a, b) {
  return a + b;
}
exports.somar = somar;

function multiplica(a, b) {
  return a * b;
}
exports.multiplica = multiplica;

function dividir(a, b) {
  return a / b;
}
exports.dividir = dividir;

function subtrair(a, b) {
  return a - b;
}
exports.subtrair = subtrair;
```

```js
const calculadora = require("./calculadora");

describe("testando a calculadora0", () => {
  test("1 + 2 = 3", () => {
    expect(calculadora.somar(1, 2)).toBe(3);
  });
  test("1 * 0 = 0", () => {
    expect(calculadora.multiplica(1, 0)).toEqual(0);
  });
  test("2 - 5 <> 3", () => {
    expect(calculadora.subtrair(2, 5)).not.toBe(3);
  });
  test("5 / 3 ≃ 1.7", () => {
    expect(calculadora.dividir(5, 3)).toBeCloseTo(1.7, 1);
  });
});
```

## Teste Assíncrono no Jest

#### teste para banco de dados

<p>Criar uma pasta db, e dentro dela criar um arquivo db.json,
inserir as seguintes informações:</p>

```json
{
  "alunos": [
    {
      "id": 1,
      "nome": "Maria"
    },
    {
      "id": 2,
      "nome": "Ana"
    }
  ]
}
```

<p>depois instale:</p>

    npm install json-server

<p>Abrir o arquivo existente package.json e incluir essa linha no script</p>

    "backend": "json-server --watch db/db.json"

<p>Depois use o comando:</p>

    npm run backend

#### para realiza o test de chamada

<p>instala o:</p>

    npm install --save-dev jest

<p>Criar um arquivo asyncawaiit.test.js e inserir:</p>

```js
describe("Testando uma requisição", () => {
  test("requisição com sucesso", async () => {
    const response = await fetch("http://localhost:3000/alunos/2");
    const aluno = await response.json();
    console.log("O aluno é: ", aluno.nome);
    expect(aluno.nome).toEqual("Ana");
  });
});
```

<p>lembre de usa o npm t para testa</p>

### Isolando uma função a testar

<p>Criar um arquivo soma.js e inserir:</p>

```js
function soma(a, b) {
  return a + b;
}
module.exports = soma;
```

<p>Criar um arquivo media.js e inserir:</p>

```js
const soma = require("./soma");
function media(a, b) {
  s = soma(a, b);
  m = s / 2;
  return m;
}
exports.media = media;
```

<p>Criar um arquivo media.test.js e inserir:</p>

```js
const calculo = require("./media");
test("Testando a media aritmética", () => {
  expect(calculo.media(7, 4)).toBe(5.5);
});
```
