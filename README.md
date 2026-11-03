# 🛗 Intelligent Elevator Control System Using Fuzzy Logic

An intelligent elevator allocation system developed using **Soft Computing and Fuzzy Logic** to select the most suitable elevator for a passenger request based on distance, direction compatibility, and passenger load.

## 📌 Project Overview

In multi-storey buildings with multiple elevators, selecting the most suitable elevator is an important optimization problem. Traditional elevator allocation methods may rely on fixed conditions or simple distance-based decisions.

This project implements a **Fuzzy Logic-Based Elevator Control System** that evaluates multiple parameters simultaneously and assigns a priority score to each available elevator.

The elevator with the highest priority score is selected to serve the passenger request.

The system is implemented in Python and demonstrates how fuzzy logic can be applied to real-world intelligent control and decision-making problems.

## 🎯 Objectives

- Develop an intelligent elevator selection mechanism using fuzzy logic.
- Evaluate elevators based on distance, direction, and passenger load.
- Implement triangular membership functions for fuzzy variables.
- Construct a fuzzy rule base using IF–THEN conditions.
- Calculate priority scores for multiple elevators.
- Select the most suitable elevator based on the highest priority score.

## ⚙️ System Configuration

| Parameter | Configuration |
|---|---|
| Building floors | 10 |
| Number of elevators | 4 |
| Maximum elevator capacity | 10 passengers |
| Programming language | Python |
| Decision-making technique | Fuzzy Logic |
| Membership function | Triangular (`trimf`) |

## 🧠 Fuzzy Logic Implementation

The system considers three input variables and one output variable.

### 1. Input Variables

**Distance**

Represents the number of floors between the elevator and the passenger.

- Near
- Medium
- Far

**Direction Compatibility**

Determines whether the elevator's current movement direction is suitable for the passenger request.

- Poor
- Moderate
- Good

**Passenger Load**

Represents the current occupancy of the elevator as a percentage of its maximum capacity.

- Low
- Medium
- High

### 2. Output Variable

**Priority Score (0–100)**

Represents the suitability of an elevator for serving the passenger request.

The output is classified into five fuzzy categories:

- Very Low
- Low
- Medium
- High
- Very High

## 📐 Membership Functions

Triangular membership functions are used to represent the fuzzy linguistic variables.

| Variable | Category | Parameters |
|---|---|---|
| Distance | Near | [0, 0, 3] |
| Distance | Medium | [1, 4.5, 8] |
| Distance | Far | [6, 9, 9.9] |
| Direction | Poor | [0, 0, 0.5] |
| Direction | Moderate | [0.25, 0.5, 0.75] |
| Direction | Good | [0.5, 1, 1] |
| Load | Low | [0, 0, 40] |
| Load | Medium | [20, 50, 80] |
| Load | High | [60, 100, 100] |

The priority output uses five triangular membership functions corresponding to Very Low, Low, Medium, High, and Very High.

## 📋 Fuzzy Rule Base

The fuzzy inference system uses **27 IF–THEN rules**, generated from all possible combinations of the three input variables.

Each linguistic category is assigned a relative contribution:

| Input | Category Contributions |
|---|---|
| Distance | Near = 2, Medium = 1, Far = 0 |
| Direction | Poor = 0, Moderate = 1, Good = 2 |
| Load | Low = 2, Medium = 1, High = 0 |

The total contribution determines the output category:

| Total Contribution | Priority Category |
|---|---|
| 0–1 | Very Low |
| 2 | Low |
| 3 | Medium |
| 4 | High |
| 5–6 | Very High |

**Example rule:**

IF distance is Near AND direction is Good AND load is Low, THEN priority is Very High.

## 🔄 System Workflow

1. Initialize the building with 10 floors and 4 elevators.
2. Receive a passenger request containing the requested floor and direction.
3. Retrieve the current state of each elevator.
4. Calculate the distance between each elevator and the requested floor.
5. Determine direction compatibility.
6. Calculate the passenger load percentage.
7. Pass the input values to the fuzzy inference system.
8. Apply the 27 fuzzy rules.
9. Calculate the priority score for each elevator.
10. Select the elevator with the highest priority score.

## 💻 Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core implementation |
| NumPy | Numerical computations and fuzzy universes |
| scikit-fuzzy | Fuzzy membership functions and inference |
| Pandas | Result processing and tabular representation |
| Matplotlib | Data visualization |
| Jupyter Notebook / Google Colab | Development and execution environment |

## 🚀 Installation and Execution

### Step 1: Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
```

### Step 2: Navigate to the project directory

```bash
cd YOUR_REPOSITORY
```

### Step 3: Install dependencies

```bash
pip install numpy pandas matplotlib scikit-fuzzy
```

### Step 4: Run the implementation

Open the Jupyter Notebook:

```bash
jupyter notebook
```

Alternatively, upload the notebook to Google Colab and execute the cells sequentially.

## 📊 Experimental Results

### Passenger Request

| Parameter | Value |
|---|---|
| Requested Floor | 5 |
| Requested Direction | UP |

### Elevator Evaluation

| Elevator | Floor | Direction | Load | Priority Score |
|---|---:|---|---:|---:|
| E1 | 1 | IDLE | 2 | 90.28 |
| E2 | 4 | UP | 5 | **90.97** |
| E3 | 7 | DOWN | 3 | 49.10 |
| E4 | 10 | IDLE | 8 | 50.00 |

### 🏆 Final Output

**SELECTED ELEVATOR: E2**

**Priority Score: 90.97**

Elevator E2 is selected because it is located at floor 4, is moving UP towards the requested floor 5, and currently carries 5 passengers.

The fuzzy inference system assigns E2 the highest priority score among the four elevators.

## 📈 Result Analysis

- E1 receives a high score because it has a low passenger load, although it is farther from the requested floor.
- E2 receives the highest score due to its proximity and compatible direction.
- E3 receives a lower score because it is moving DOWN while the passenger requests UP.
- E4 has a relatively high passenger load and is farther from the requested floor.

The results demonstrate how fuzzy logic combines multiple decision factors instead of relying only on physical distance.

*Note: Priority scores are relative outputs of the implemented fuzzy inference system and do not represent actual waiting times.*

## 🔮 Future Enhancements

- Support multiple simultaneous passenger requests.
- Introduce dynamic elevator movement simulation.
- Consider estimated waiting time and travel time.
- Include passenger destination information.
- Develop a graphical user interface for real-time visualization.
- Extend the system to larger buildings with more elevators.
- Optimize fuzzy membership functions and rules using simulation data.
