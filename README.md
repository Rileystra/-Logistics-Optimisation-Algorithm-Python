


# 📦 Logistics Optimisation Algorithm – Python

A constraint-based **Python optimisation algorithm** that solves the van loading problem — maximising delivery efficiency by intelligently packing items based on weight distribution, stacking rules and retrieval order.

---

## 📌 What It Does

Manual van loading is error-prone and inefficient. This algorithm automates the decision-making by:

- Evaluating which items can be stacked based on weight and fragility constraints
- Distributing load evenly across the van to maintain safe weight balance
- Ordering items so the last delivery is loaded last (LIFO — Last In, First Out)
- Flagging constraint violations before a route begins

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Language | Python 3 |
| Algorithm | Constraint-based optimisation |
| Data Format | JSON / CSV input |
| Testing | Python unittest |

---

## 🧠 How the Algorithm Works

The problem is modelled as a **constraint satisfaction problem (CSP)**:

```
Input: List of items (weight, dimensions, fragility, delivery stop)
         └── Constraints: max weight, stack rules, balance threshold

Algorithm:
  1. Sort items by delivery stop (reverse order — last stop loads first)
  2. Apply stacking rules (fragile items on top, heavy items on base)
  3. Check cumulative weight against van capacity
  4. Validate left/right balance distribution
  5. Output: ordered loading plan + constraint report

Output: Optimised loading sequence + any violations flagged
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- No external libraries required (pure Python)

### Installation

```bash
git clone https://github.com/rylee stra/logistics-optimisation.git
cd logistics-optimisation
```

### Usage

**1. Define your items in `items.json`:**
```json
[
  { "id": "PKG001", "weight_kg": 12, "fragile": false, "stop": 3 },
  { "id": "PKG002", "weight_kg": 4,  "fragile": true,  "stop": 1 },
  { "id": "PKG003", "weight_kg": 8,  "fragile": false, "stop": 2 }
]
```

**2. Run the optimiser:**
```bash
python optimise.py --input items.json --capacity 500
```

**3. View the loading plan:**
```
Loading Plan (load in this order):
  1. PKG001 — 12kg — Stop 3  [BASE]
  2. PKG003 — 8kg  — Stop 2  [MID]
  3. PKG002 — 4kg  — Stop 1  [TOP — fragile]

Total weight: 24kg / 500kg capacity
Balance: OK
Constraint violations: None
```

---

## 📂 Project Structure

```
logistics-optimisation/
│
├── optimise.py         # Main algorithm entry point
├── constraints.py      # Constraint definitions and validation logic
├── loader.py           # Item sorting and stacking logic
├── items.json          # Sample input data
├── tests/
│   └── test_optimise.py  # Unit tests for constraint validation
└── README.md
```

---

## ✅ Constraints Modelled

| Constraint | Rule |
|---|---|
| Max capacity | Total weight must not exceed van limit |
| Stack safety | Fragile items always loaded on top |
| Weight balance | Left/right distribution within ±15% threshold |
| Retrieval order | Stop 1 items loaded last (LIFO) |
| Base stability | Heaviest items always form the base layer |

---

## 🧪 Running Tests

```bash
python -m unittest tests/test_optimise.py -v
```

Tests cover constraint validation, edge cases (overloaded van, all-fragile loads, single-item input) and correct LIFO ordering.

---

## 📈 Future Improvements

- [ ] Multi-van routing — assign items across a fleet optimally
- [ ] GUI visualisation of the loading plan
- [ ] Integration with Google Maps API for route-aware loading
- [ ] Genetic algorithm approach for larger item sets

---

## 💡 Why This Project

This was built to explore how software can solve real operational problems that businesses deal with every day. The goal was not just to write code, but to model a problem correctly from first principles — defining the constraints before writing a single line of solution logic.

---

## 👤 Author

**Uriel Djantou Fanja**
📧 urieldjantou@gmail.com
🔗 [GitHub](https://github.com/YOUR-USERNAME)

---

## 📄 Licence

MIT — free to use, modify and distribute.
