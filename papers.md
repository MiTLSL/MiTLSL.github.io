---
### [Model based planning using The Dubins curve for gliding vehicles with multiple constraints](https://www.cnki.net)

**Authors**: Peinan Huang, Zongying Shi, Yisheng Zhong

**Keywords**: `Gliding Vehicles`, `Rendezvous`, `Path Planning`, `Dubins Curves`, `Hierarchical Planning`

#### Core Problem

This paper addresses the challenge of planning coordinated paths for multiple high-speed gliding vehicles. The goal is to enable them to arrive at designated rendezvous points simultaneously to form a specific formation, while respecting multiple complex constraints, including the vehicles' minimum turning radius and ensuring collision avoidance.

#### Proposed Method

The authors propose a **hierarchical planning framework** that decomposes the complex problem into manageable layers:

1.  **High-Level (Assignment)**: An optimization problem (integer programming) is solved to assign each vehicle to a target rendezvous point, minimizing the overall path cost.

2.  **Mid-Level (Path Generation & Synchronization)**:
    *   **Path Generation**: **Dubins curves** are used to generate the shortest, kinematically feasible horizontal paths between each vehicle's current state and its assigned target.
    *   **Time Synchronization**: To ensure simultaneous arrival, the framework first calculates the estimated time of arrival (ETA) for each vehicle along its shortest path. It then identifies the maximum ETA (`t_max`) and **elongates** the paths of all other vehicles (by adjusting their Dubins curve parameters, like turning radius) so that their flight times increase to match `t_max`.

3.  **Low-Level (Execution & Online Re-planning)**:
    *   An `l1` guidance law and PD controllers are used for accurate path and altitude tracking.
    *   Crucially, the system employs an **online planning** mechanism, continuously re-calculating paths based on the vehicles' current states. This allows for dynamic correction of deviations, significantly improving synchronization accuracy.

#### Key Contributions & Conclusions

*   The paper successfully develops and validates a **robust hierarchical framework** for multi-vehicle cooperative path planning under multiple constraints.
*   It demonstrates an effective method for **time synchronization** by intelligently adjusting and elongating Dubins paths, rather than just using them for shortest-path calculation.
*   The simulation results prove that the **online re-planning** approach is vastly superior to a static, one-time plan, reducing the final arrival time error by approximately **78%** (from 1.92s to 0.43s).
*   The framework effectively guarantees that the generated paths are flyable, collision-free (via height staggering), and perfectly synchronized.

---