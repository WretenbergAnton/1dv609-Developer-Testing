# 1dv609-Developer-Testing

## Capter 7 - Enhetstester (Unit Testing)

En enhetstest testar en liten del av koden i isolering, t.ex. en funktion eller klass. Målet är att fånga fel tidigt och våga ändra kod (refakorisering) utan att bryta något.

### Arrange-Act-Assert är ett centralt mönster:

* **Arrange:** Förbered teste (skapa data, inställningar)
* **Act:** Kör funktionen
* **Assert:** Kontrollera resultatet


### Enhetstester ska vara:

* **Snabbt:** Ska gå att köra ofta
* **Isolerade:** Testa bara en sak i taget
* **Förutsägbara:** Alltid samma resultat för samma input


Exempel(Jest)
```js 
// sum
export function sum(a, b) {
  return a + b;
}
```

```js 
// sum.test.js
import { sum } from './summa'

test('return 5 when 2 + 3', () => {
  const result = sum(2, 3);
  expect(result).toBe(5);
});

test('hanterar negativa tal', () => {
  const result = sum(-2, 3);
  expect(result).toBe(1);
});

```
