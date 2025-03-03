# JavaScript Expert - Spies

This project is part of the **JavaScript Expert** series, focusing on testing with Spies using [Sinon.js](https://sinonjs.org/). The goal is to understand how Spies work in JavaScript, monitor function calls, and validate their behavior.

## 📂 Project Structure
```
javascript-expert--spies/
│-- src/
│   │-- fibonacci.js
│   └-- fibonacci.test.js
│-- package.json
│-- README.md
```

## 📌 What are Spies?
A **Spy** is a type of test double that allows you to monitor function calls, including:
- How many times a function was called (`callCount`)
- With what arguments it was called (`args`)
- What values it returned
- If it threw an error

Unlike **Stubs** (which replace function behavior), Spies do not modify the function’s logic; they only observe it.

## 🛠️ Setup
Make sure you have [Node.js](https://nodejs.org/) installed.

```sh
# Clone the repository
git clone https://github.com/yourusername/javascript-expert--spies.git
cd javascript-expert--spies

# Install dependencies
npm install
```

## 🚀 Running Tests
To run the test suite, execute:
```sh
npm test
```

## 📝 Implementation Details
The **`fibonacci.js`** file contains a generator function that calculates Fibonacci numbers recursively.
The **`fibonacci.test.js`** file uses `sinon.spy()` to:
- Track the number of function calls
- Validate input parameters
- Ensure correct Fibonacci sequence generation

### Example Test Case
```javascript
const spy = sinon.spy(fibonacci, fibonacci.execute.name);

const results = [...fibonacci.execute(5)];

// Check if the function was called 6 times
assert.strictEqual(spy.callCount, 6);

// Check if the 3rd call received the correct parameters
const { args } = spy.getCall(2);
const expectedParams = [3, 1, 2];
assert.deepStrictEqual(args, expectedParams);
```