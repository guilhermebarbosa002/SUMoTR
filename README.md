# 🌍 SUMoTR — Sustainable Urban Multimodal Transport Routing

**SUMoTR (Sustainable Urban Multimodal Transport Routing)** is an open research repository providing **datasets, multimodal graph representations, and solution outputs** for sustainable urban transport routing problems.

The repository is designed to support **reproducible research**, **transparent experimentation**, and **method-independent benchmarking** of routing and optimization approaches in large-scale public transport networks.

SUMoTR focuses on **user-centric multimodal routing** within the **Mobility as a Service (MaaS)** paradigm, integrating realistic public transport schedules, pedestrian connectivity, and sustainability-oriented performance indicators.

---

## 🎯 Scope and Objectives

The main goals of this repository are to:

- Provide **realistic multimodal transport instances** for large urban environments
- Enable the analysis of **trade-offs between travel efficiency and sustainability**
- Support **fair and method-independent benchmarking** of routing and optimization algorithms
- Promote **reproducibility, transparency, and reuse** in urban transport research

The repository is **not tied to a specific optimization method**. While algorithms may evolve, the problem instances and evaluation context remain consistent over time.

---

## 🏙️ Covered Cities

SUMoTR currently includes data for the following cities:

- **Lisbon, Portugal**
- **Oporto, Portugal**

Each city is modeled as a **large-scale multimodal transport network**, combining public transport services and pedestrian connections.

---

## 🗂️ Repository Structure

For each city, the repository is organized into the following components:

### 📌 Instances
Origin–destination routing instances defined by geographic coordinates and contextual information used during optimization.

Each instance includes:
- `po_lat`, `po_lon` — origin coordinates  
- `pd_lat`, `pd_lon` — destination coordinates  
- `number_of_stops` — number of stops in the reference path  
- `instance_type` — difficulty or category label  
- `dateTime` — departure date and time  

These instances allow evaluation under different spatial configurations and levels of difficulty.

---

### 🧩 Graphs


#### 🚦 Transport mode nomenclature

Transport modes stored in the `transport` edge attribute use **Portuguese labels**.  
For clarity and international reuse, their English equivalents are:

- **Autocarro** → *Bus*
- **Barco** → *Ferry*
- **Bicicleta** → *Bicycle*
- **Caminhar** → *Walking*
- **Comboio** → *Train*
- **Metro** → *Metro / Subway*

Multimodal transport graphs representing:
- Public transport stops and stations  
- Scheduled services (time-dependent edges)  
- Pedestrian connections subject to distance constraints  

Graphs were built using **NetworkX** and are stored in **pickle format**, **compressed as ZIP files** to reduce storage requirements.  
**NetworkX is required** to load and manipulate these graph structures.

Each graph contains:
- **Nodes** representing public transport stops, stations, or pedestrian access points
- **Edges** representing multimodal connections, including scheduled public transport services and non-scheduled active modes

#### 🔹 Node attributes
Each node stores geographic and contextual information, such as:
- `name` — stop or street name
- `lat`, `lon` — geographic coordinates
- `zone` — fare or operational zone (when available)

#### 🔹 Edge attributes
Edges encode both physical and operational characteristics. Multiple edges may exist between the same nodes, each corresponding to a different transport option.

Common edge attributes include:
- `distance` — length of the connection (in kilometers)
- `transport` — transport mode (e.g., *Autocarro*, *Metro*, *Caminhar*, *Bicicleta*)
- `time` — travel time representation (mode-dependent)
- `co2` — estimated CO₂ emissions
- `energy` — estimated energy consumption


#### ⏱️ Time-dependent vs. fixed-time edges

The representation of the `time` attribute depends on the transport mode:


These labels are used consistently across all graphs and solution outputs.
- **Public transport modes** (e.g., *Autocarro*, *Metro*):  
  The `time` attribute is stored as a **tabular structure (DataFrame)** containing all available scheduled services between the two nodes.  
  This includes:
  - `route_id`
  - `departure_time`
  - `arrival_time`
  - `travel_time`
  - `days` of operation  

  This enables accurate **time-dependent routing**, accounting for service availability and departure times.

- **Active modes — *Caminhar* (Walking) and *Bicicleta* (Cycling)**:  
  These modes do **not** depend on schedules.  
  Therefore, the `time` attribute is stored as a **single fixed scalar value**, representing the deterministic travel time required to traverse the edge.  

  For these edges:
  - No timetable is required
  - Travel time is constant
  - CO₂ emissions are zero
  - Energy expenditure may be included (e.g., for walking)

---

### 📊 Pareto Fronts
Sets of **non-dominated solutions** obtained for each routing instance, capturing trade-offs between conflicting objectives such as:
- Total travel time
- Co2 emissions 

---

### 🗺️ Maps and Visualizations
Geographic visualizations of selected routing solutions projected onto city maps.

These visualizations:
- Correspond to solutions obtained by the algorithm proposed in the associated paper
- Illustrate representative points from the Pareto fronts
- Provide intuitive insight into multimodal routing behavior

---

## 🔁 Reproducibility and Reuse

SUMoTR is intended for:

- Academic research
- Algorithm benchmarking
- Comparative studies in multimodal and sustainable transport routing
- Development of intelligent decision-support systems

Researchers are encouraged to **reuse, extend, and compare** against this data, provided appropriate citation is given.

---

## 📂 Data Availability

All datasets, graphs, and solution outputs required to reproduce the experimental analysis are **publicly available in this repository**.

The repository is maintained to ensure **long-term accessibility**, **traceability**, and **research transparency**.

---

## 📝 Citation

<!-- If you use this repository in your work, please cite the corresponding publication:

> *Sustainable Urban Multimodal Transport Routing: Data and Experimental Resources*  
> **Swarm and Evolutionary Computation**, Elsevier -->

(citation details will be added upon publication.)

---

## 📬 Contact

For questions, issues, or suggestions, please open an issue in this repository.