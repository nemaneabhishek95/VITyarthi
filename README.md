** College Bus Route Optimizer**
A Python-based solution for optimizing college bus routes using nearest neighbor clustering algorithm. Minimizes travel distance while respecting bus capacity constraints.
Features

•	Route optimization using nearest neighbor algorithm

•	Visual representation of optimized routes

•	Detailed route statistics and analytics

•	Configurable number of buses and capacities

•	Works with coordinate-based locations (latitude/longitude)

**Installation**

git clone https://github.com/yourusername/college-bus-route-optimizer.git
cd college-bus-route-optimizer
pip install matplotlib numpy
Usage
from bus_optimizer import BusRouteOptimizer

# Define locations

college = (50, 50)
students = [(20, 30), (25, 35), (70, 70), (75, 68), (40, 80)]

# Create and run optimizer

optimizer = BusRouteOptimizer(
    college_location=college,
    student_locations=students,
    num_buses=2,
    bus_capacity=30
)

optimizer.nearest_neighbor_clustering()
optimizer.print_route_details()
optimizer.visualize_routes()
Run the example:
python bus_optimizer.py
Configuration
Parameter	Type	Description
college_location	tuple	(x, y) coordinates of college
student_locations	list	List of (x, y) student coordinates
num_buses	int	Number of available buses
bus_capacity	int	Maximum students per bus
Algorithm
Uses Nearest Neighbor Clustering:
1.	Start at college location
2.	For each bus, repeatedly pick nearest unassigned student
3.	Continue until bus is full or no students remain
4.	Return bus to college
Distance Calculation: Euclidean distance √[(x₂-x₁)² + (y₂-y₁)²]
Example with CSV Data
import pandas as pd

df = pd.read_csv('student_locations.csv')
students = list(zip(df['latitude'], df['longitude']))
college = (df['college_lat'].iloc[0], df['college_long'].iloc[0])

optimizer = BusRouteOptimizer(college, students, num_buses=3, bus_capacity=40)
optimizer.nearest_neighbor_clustering()
optimizer.visualize_routes()
Output
==================================================
BUS ROUTE OPTIMIZATION RESULTS
==================================================

Bus 1:
  Students: 15/20
  Route Distance: 245.73 km

Bus 2:
  Students: 15/20
  Route Distance: 238.91 km

==================================================
Total Distance (All Buses): 484.64 km
Total Students: 30
==================================================
**Requirements**

•	Python 3.7+

•	matplotlib

•	numpy

Future Enhancements

•	Genetic algorithm optimization

•	Time window constraints

•	Real map integration with Folium

•	Traffic pattern consideration

•	Web-based interface

Contributing

Pull requests are welcome. For major changes, please open an issue first.
