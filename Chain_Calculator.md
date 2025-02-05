Key Requirements
- ✅ Chaining operations (e.g., calc.add(5).subtract(2).multiply(3).value() → 9)
- ✅ Supports addition, subtraction, multiplication, division
- ✅ Maintains immutability (creates a new instance to avoid modifying the existing state)
- ✅ Handles edge cases (e.g., division by zero)
- ✅ Follows design patterns
- ✅ System design best practices

```
class ChainCalculator {
  constructor(value = 0) {
    this._value = value; // Renamed the property to avoid conflict
  }

  add(number) {
    return new ChainCalculator(this._value + number);
  }

  subtract(number) {
    return new ChainCalculator(this._value - number);
  }

  multiply(number) {
    return new ChainCalculator(this._value * number);
  }

  divide(number) {
    if (number === 0) {
      throw new Error("Division by zero is not allowed.");
    }
    return new ChainCalculator(this._value / number);
  }

  value() {
    return this._value; // Return the renamed property
  }
}

const calc = new ChainCalculator();
console.log(calc.add(5).subtract(2).multiply(3).value()); // 9
```
