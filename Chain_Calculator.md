Key Requirements
✅ Chaining operations (e.g., calc.add(5).subtract(2).multiply(3).value() → 9)
✅ Supports addition, subtraction, multiplication, division
✅ Maintains immutability (creates a new instance to avoid modifying the existing state)
✅ Handles edge cases (e.g., division by zero)
✅ Follows design patterns
✅ System design best practices

```
class ChainCalculator {
  constructor(value = 0) {
    this.value = value;
  }

  add(number) {
    return new ChainCalculator(this.value + number);
  }

  subtract(number) {
    return new ChainCalculator(this.value - number);
  }

  multiply(number) {
    return new ChainCalculator(this.value * number);
  }

  divide(number) {
    if (number === 0) {
      throw new Error("Division by zero is not allowed.");
    }
    return new ChainCalculator(this.value / number);
  }

  value() {
    return this.value;
  }
}

// Example Usage
const calc = new ChainCalculator();
console.log(calc.add(5).subtract(2).multiply(3).value()); // 9

```
