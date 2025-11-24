# College Bus Route Optimizer

A Python-based solution for optimizing college bus routes using a nearest neighbor clustering algorithm. It minimizes total travel distance while respecting bus capacity constraints.

---

## Features

- Route optimization using nearest neighbor algorithm  
- Visual representation of optimized routes  
- Detailed route statistics and analytics  
- Configurable number of buses and capacities  
- Works with coordinate-based locations (latitude/longitude)

---

## Installation

git clone https://github.com/yourusername/college-bus-route-optimizer.git
cd college-bus-route-optimizer
pip install matplotlib numpy




Usage

from bus_optimizer import BusRouteOptimizer

# Define locations
college = (50, 50)
students = [
    (20, 30),
    (25, 35),
    (70, 70),
    (75, 68),
    (40, 80)
]

# Create and run optimizer
optimizer = BusRouteOptimizer(
    college_location=college,
    student_locations=students,
    num_buses=2,
    bus_capacity=30
)

To run the example directly:

python bus_optimizer.py


---

Configuration

Parameter	Type	Description

college_location	tuple	(x, y) coordinates of the college
student_locations	list	List of (x, y) coordinates of students
num_buses	int	Number of available buses
bus_capacity	int	Maximum students per bus



---

Algorithm

Nearest Neighbor Clustering

1. Start at the college location.


2. For each bus, repeatedly pick the nearest unassigned student.


3. Continue until the bus is full or no students remain.


4. Return the bus to the college.



Distance Calculation (Euclidean):

d = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}


---

Example with CSV Data

import pandas as pd
from bus_optimizer import BusRouteOptimizer

df = pd.read_csv("student_locations.csv")

students = list(zip(df["latitude"], df["longitude"]))
college = (df["college_lat"].iloc[0], df["college_long"].iloc[0])

optimizer = BusRouteOptimizer(
    college_location=college,
    student_locations=students,
    num_buses=3,
    bus_capacity=40
)

optimizer.nearest_neighbor_clustering()
optimizer.visualize_routes()


---

Sample Output

BUS ROUTE OPTIMIZATION RESULTS
Bus 1: Students: 15/20  Route Distance: 245.73 km
Bus 2: Students: 15/20  Route Distance: 238.91 km
==================================================
Total Distance (All Buses): 484.64 km
Total Students: 30


---

Requirements

Python 3.7+

matplotlib

numpy



---

Future Enhancements

Genetic algorithm optimization

Time window constraints

Real map integration with Folium

Traffic pattern consideration

Web-based interface
