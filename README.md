# SUMoTR — Sustainable Urban Multimodal Transport Routing

SUMoTR (Sustainable Urban Multimodal Transport Routing) is an open research repository that provides datasets, graph representations, and solution outputs for sustainable multimodal urban transport routing problems.  
The repository is designed to support reproducible research and comparative evaluation of routing and optimization methods in large-scale public transport networks.

The focus is on user-centric multimodal routing under the Mobility as a Service (MaaS) paradigm, considering realistic public transport schedules, walking connections, and sustainability-related performance indicators.

---

## Scope and Objectives

This repository aims to:

- Provide **realistic multimodal transport instances** for urban environments.
- Support the study of **sustainable routing trade-offs**, such as travel time versus environmental impact.
- Enable **method-independent benchmarking**, allowing different algorithms and decision-support approaches to be evaluated on the same data.
- Promote **reproducibility and transparency** in urban transport optimization research.

The use cases are independent of specific optimization algorithms; therefore, methods may evolve over time while the problem instances and evaluation context remain consistent.

---

## Covered Cities

The repository currently includes data for the following cities:

- **Lisbon, Portugal**
- **Oporto, Portugal**

Each city is modeled as a large-scale multimodal transport network integrating public transport and pedestrian connectivity.

---

## Repository Structure

The repository is organized as follows (for each city):
 ---
- **Instances**  
  Origin–destination routing instances defined by the geographic coordinates of the selected origin and destination points, as well as contextual information used during optimization.  
  Each instance includes the following attributes:  
  `po_lat`, `po_lon`, `pd_lat`, `pd_lon`, `number_of_stops`, `instance_type`, and `dateTime`.  
  These instances are used to evaluate routing performance under different spatial configurations and levels of difficulty.

- **Graphs**  
  Multimodal transport graphs representing public transport stops, stations, and walking connections.  
  The graphs are stored in **pickle format** and have been **compressed into zip files** to reduce storage requirements.  
  They were created using the **NetworkX** package; NetworkX is therefore required to load, extract, and manipulate the graph structures.  
  Edges correspond to public transport services (including schedule information) and pedestrian links subject to distance constraints.

- **Pareto Fronts**  
  Sets of non-dominated solutions obtained for each routing instance, representing the trade-offs between conflicting objectives such as total travel time and environmental impact.

- **Maps and Visualizations**  
  Geographic visualizations of selected routing solutions projected onto city maps.  
  These visualizations correspond to solutions obtained by the algorithm proposed in the associated paper and illustrate representative points from the Pareto fronts.

---

## Data Characteristics

The data provided in this repository typically include:

- Multimodal network representations derived from public transport feeds
- Walking connections subject to maximum distance constraints
- Time-dependent information (e.g., service schedules)
- Objective values such as travel time and environmental indicators
- Solution paths and corresponding Pareto-optimal sets

Exact formats and contents may vary slightly between cities but follow a consistent conceptual structure.

---

## Reproducibility and Reuse

The repository is intended for:

- Academic research
- Algorithm benchmarking
- Comparative studies in multimodal and sustainable transport routing
- Decision-support system development

Researchers are encouraged to reuse and extend the data, provided appropriate citation is given.

---

## Data Availability

All datasets, graphs, and solution outputs required to reproduce the experimental analysis are publicly available in this repository.  
The repository is maintained to ensure long-term accessibility and traceability of research artifacts.

---

<!-- ## License

The contents of this repository are released for research and academic use.  
Please refer to the LICENSE file for detailed terms and conditions. -->

---

## Citation

If you use this repository in your work, please cite the corresponding publication:

> *Sustainable Urban Multimodal Transport Routing: Data and Experimental Resources*,  
> Swarm and Evolutionary Computation, Elsevier.

(Full citation details will be updated upon publication.)

---

## Contact

For questions, issues, or suggestions related to this repository, please open an issue or contact the authors via the associated publication.
