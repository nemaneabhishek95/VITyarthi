# 🚌 College Bus Route Optimizer

This project implements a simple **Bus Route Optimization** solution using Python, focusing on clustering student pickup locations and generating routes based on the **Nearest Neighbor** heuristic. The goal is to efficiently transport students from their scattered pickup points to a central college location using a limited number of buses, each with a maximum capacity.

## ⚙️ How It Works

The core logic is encapsulated in the `BusRouteOptimizer` class.

### 1. Nearest Neighbor Clustering

The `nearest_neighbor_clustering` method is the heart of the optimization. It works as follows:

1.  **Initialization:** Starts at the **College Location**.
2.  **Iterative Selection:** For the current bus, it repeatedly selects the unassigned student pickup point that is **closest (nearest neighbor)** to the bus's **current location** (initially the college, then the last student picked up).
3.  **Route Building:** The selected student is added to the bus's route, and the student's location becomes the new current location for the bus.
4.  **Capacity Check:** This process continues until the bus reaches its `bus_capacity` or there are no remaining students.
5.  **New Bus:** Once a bus is full or all remaining students are assigned, the process repeats for the next available bus, starting again from the **College Location** to find the nearest unassigned student.



### 2. Route Distance Calculation

The `calculate_route_distance` method calculates the total Euclidean distance for a complete bus route, which includes:

* **College** $\rightarrow$ **First Student**
* **Student** $\rightarrow$ **Next Student** (for all intermediate stops)
* **Last Student** $\rightarrow$ **College** (return trip)

## 🧰 Requirements

This script requires the following standard Python libraries:

* `matplotlib` (for visualization)
* `numpy` (for distance calculation)

You can install them using pip:

```bash
pip install matplotlib numpy
🚀 UsageThe main block of the script (if __name__ == "__main__":) demonstrates how to initialize the optimizer, run the clustering, and visualize the results.Example 1: Random Data (45 students, 3 buses)Python# Initialize with random student locations
college = (50, 50)
num_students = 45
student_locations = [(random.uniform(10, 90), random.uniform(10, 90)) for _ in range(num_students)]

optimizer = BusRouteOptimizer(
    college_location=college,
    student_locations=student_locations,
    num_buses=3,
    bus_capacity=20
)

# Run optimization
optimizer.nearest_neighbor_clustering()
optimizer.print_route_details()
optimizer.visualize_routes()
Example 2: Custom Data (12 students, 2 buses)Python# Initialize with specific, clustered student locations
custom_students = [
    (20, 30), (25, 35), (22, 28),  # Cluster 1
    (70, 70), (75, 68), (72, 73),  # Cluster 2
    (40, 80), (38, 82), (42, 78),  # Cluster 3
    (80, 20), (82, 18), (78, 22),  # Cluster 4
]

optimizer2 = BusRouteOptimizer(
    college_location=(50, 50),
    student_locations=custom_students,
    num_buses=2,
    bus_capacity=8
)

# Run optimization
optimizer2.nearest_neighbor_clustering()
optimizer2.print_route_details()
optimizer2.visualize_routes(figsize=(10, 8))
📊 OutputRoute DetailsThe print_route_details method prints a summary of the optimized routes, including:The number of students assigned to each bus.The total distance covered by each bus's round trip.The overall total distance covered by all buses.VisualizationThe visualize_routes method generates a scatter plot map showing:The College Location (Red Star $\star$).Student Pickup Points grouped by their assigned bus (colored circles).The Bus Routes themselves, showing the sequence of pickups and the return trip to the college.
