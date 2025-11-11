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


## Kapitel 8 – Specifikationsbaserade testtekniker

Tester ska baseras på specifikationen — vad koden ska göra, inte hur den är implementerad.

### Vanliga tekniker:

* **Ekvivalensklasser:** Dela in indata i grupper som ska ge samma resultat
* **Gränsvärdestestning:** Testa precis vid och strax utanför gränser
* **Tillstånds- och beslutstabeller:** För att säkerställa alla kombinationer av indata

Exempel(Jest)
```js 
// discount.js
export function discount(ålder) {
  if (ålder < 0) throw new Error('Age must be positive');
  if (ålder < 18) return true;
  if (ålder >= 65) return true;
  return false;
}
```

```js 
// rabatt.test.js
import { discount } from './discount'

test('give descount for people under 18', () => {
  expect(discount(10)).toBe(true);
});

test('give discount for elders (65+)', () => {
  expect(discount(70)).toBe(true);
});

test('no discout for people between 18–64', () => {
  expect(discount(30)).toBe(false);
});

test('Throw error if age > 0', () => {
  expect(() => discount(-5)).toThrow('Age must be positive');
});
```
