### Criando um Test Unitários com Jest

#### Inicio

        npm init

        npm install --save-dev jest

#### comoando para testa

        npm test

#### Criar um file com o final .test.js

<br>

<p>Sempre que voce for testa va ao package.json e mude para esse scripts test:</p>

```
"scripts": {
    "test": "jest"
  },
```

#### Codigo do para fazer o test funcionar :

```
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

```
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
