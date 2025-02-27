```javascript
// Polyfill for Array.prototype.map()
Array.prototype.myMap = function (callback) {
  let result = [];
  for (let i = 0; i < this.length; i++) {
    if (this.hasOwnProperty(i)) {
      result.push(callback(this[i], i, this));
    }
  }
  return result;
};

// Polyfill for Array.prototype.filter()
Array.prototype.myFilter = function (callback) {
  let result = [];
  for (let i = 0; i < this.length; i++) {
    if (this.hasOwnProperty(i) && callback(this[i], i, this)) {
      result.push(this[i]);
    }
  }
  return result;
};

// Polyfill for Array.prototype.reduce()
Array.prototype.myReduce = function (callback, initialValue) {
  let accumulator = initialValue !== undefined ? initialValue : this[0];
  let startIndex = initialValue !== undefined ? 0 : 1;

  for (let i = startIndex; i < this.length; i++) {
    if (this.hasOwnProperty(i)) {
      accumulator = callback(accumulator, this[i], i, this);
    }
  }
  return accumulator;
};

// Polyfill for Array.prototype.forEach()
Array.prototype.myForEach = function (callback) {
  for (let i = 0; i < this.length; i++) {
    if (this.hasOwnProperty(i)) {
      callback(this[i], i, this);
    }
  }
};

// Polyfill for Array.prototype.find()
Array.prototype.myFind = function (callback) {
  for (let i = 0; i < this.length; i++) {
    if (this.hasOwnProperty(i) && callback(this[i], i, this)) {
      return this[i];
    }
  }
  return undefined;
};

// Polyfill for Array.prototype.some()
Array.prototype.mySome = function (callback) {
  for (let i = 0; i < this.length; i++) {
    if (this.hasOwnProperty(i) && callback(this[i], i, this)) {
      return true;
    }
  }
  return false;
};

// Polyfill for Array.prototype.every()
Array.prototype.myEvery = function (callback) {
  for (let i = 0; i < this.length; i++) {
    if (this.hasOwnProperty(i) && !callback(this[i], i, this)) {
      return false;
    }
  }
  return true;
};

// Example Usage
const arr = [1, 2, 3, 4, 5];

console.log(arr.myMap(num => num * 2)); // [2, 4, 6, 8, 10]
console.log(arr.myFilter(num => num % 2 === 0)); // [2, 4]
console.log(arr.myReduce((acc, num) => acc + num, 0)); // 15
arr.myForEach(num => console.log(num * 2)); // 2, 4, 6, 8, 10
console.log(arr.myFind(num => num > 3)); // 4
console.log(arr.mySome(num => num > 3)); // true
console.log(arr.myEvery(num => num > 0)); // true
