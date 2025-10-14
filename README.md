# ✨ Exercise 4 – Refactor + Decorator Pattern with Full Test Coverage

## 📌 What’s Included
### **Step 1 – Refactor `Product`**
- Converted `Product` from a `record` to a standard Java class.
- Implemented the **Builder Pattern** for flexible and safe object creation.
- Added a new `price` field to `Product`.
- Updated all code and tests to use `Product.Builder` instead of direct constructors.

### **Step 2 – Introduce Repository & Service Layers**
- Created `ProductRepository` interface.
- Implemented `InMemoryProductRepository` for in‑memory storage.
- Introduced `ProductService` with **dependency injection** of `ProductRepository`.
- Updated all tests to pass either a real `InMemoryProductRepository` or a mock to `ProductService`.

### **Step 3 – Implement Decorator Pattern**
- Created `Sellable` interface for price‑retrievable entities.
- Added abstract `ProductDecorator` implementing `Sellable` and delegating calls.
- Implemented `DiscountDecorator`:
  - Applies a percentage discount to the product price.
  - Validates discount range (0–100%).
- Added **`DiscountDecoratorTest`** covering:
  - ✅ Happy path (e.g., 1.5% discount)  
  - ✅ 0% discount (no change)  
  - ✅ 100% discount (price becomes 0)  
  - ✅ Invalid discounts (<0 or >100) throw `IllegalArgumentException`

---

## 🎯 Why These Changes
- **Builder Pattern** → Improves readability, maintainability, and reduces constructor overload complexity.
- **Repository + Service Layers** → Separates concerns, improves testability, and follows clean architecture principles.
- **Decorator Pattern** → Adds flexible, runtime‑configurable behavior without modifying existing classes.
- **Full Test Coverage** → Ensures correctness, prevents regressions, and validates edge cases.

---

## 🛠 How It Was Done
- Replaced all direct `Product` instantiations with `Product.Builder`.
- Injected `ProductRepository` into `ProductService` for better flexibility.
- Implemented `DiscountDecorator` to override `getPrice()` while preserving other `Sellable` properties.
- Wrote comprehensive unit tests for all new and modified public methods.

---

## ✅ Testing
- All existing tests updated to work with the new `ProductService` and `Product.Builder`.
- All tests pass (`mvn test` → green).
- **New tests** in `DiscountDecoratorTest` verify:
  - Correct discount calculation.
  - No change for 0% discount.
  - Price becomes 0 for 100% discount.
  - Exceptions thrown for invalid discount values.

---
## Linked School Issue 
 [Exercise 4 - Design Patterns](https://github.com/fungover/exercise2025/issues/71)
