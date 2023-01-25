# Integrated-Modeling
In this repository, multiple free programing tools will be integrated to summarize and demonstrate the 4 steps of small and mid-sized city planning.

1. Subarea Analysis
- Creating General Multi model specifications (GMNS) format network for the area and specify point of intrests (POIs).
- Metohd: osm2gmns https://osm2gmns.readthedocs.io/en/latest/
<img width="502" alt="Screenshot 2023-01-24 at 8 36 57 PM" src="https://user-images.githubusercontent.com/117876335/214474562-b9f9de6f-5c69-4033-8dbf-2bfd99c5779f.png">

2. Trip Generation
- Generate the number of production and attraction trips (the number of trips entering and leaving each zone)for each trip purpose (HBw, HBO, and NHB) >> person trips per day.
- Method: grid2demand https://github.com/asu-trans-ai-lab/grid2demand
<img width="487" alt="Screenshot 2023-01-24 at 8 38 46 PM" src="https://user-images.githubusercontent.com/117876335/214474747-505ea644-5021-42e2-af5a-01347f42695a.png">

3. Trip Distriputaion
- Estimate the number of trips made between each zone.
- Trip distribution classification is considered.
	. Classification of trip distribution
		- internal > internal 
		- internal > external
		- external > internal
		- external > external 
- Method: grid2demand https://github.com/asu-trans-ai-lab/grid2demand
<img width="471" alt="Screenshot 2023-01-24 at 8 41 01 PM" src="https://user-images.githubusercontent.com/117876335/214474993-d92fdc1f-84ce-472e-918f-7c4f99b464bd.png">

4. Traffic Assignment
- Path4GMNS supports, in short,
	. finding (static) shortest path between two nodes,
	. constructing shortest paths for all individual agents,
	. performing path-based User-Equilibrium (UE) traffic assignment,
	. evaluating multimodal accessibility and equity,
	. synthesizing zones and Origin-Destination (OD) demand for a given network.
- Method: path4gmns https://path4gmns.readthedocs.io/en/latest/
<img width="492" alt="Screenshot 2023-01-24 at 8 49 55 PM" src="https://user-images.githubusercontent.com/117876335/214475798-6d9718e5-501d-48a0-b748-528de1c7cce4.png">

Flowchart shows the different 4-steps small&mid-sized city planning:

![4-steps_mid-sized_city_planning_v2](https://user-images.githubusercontent.com/117876335/214474319-9848913d-c704-41a8-b91a-e555f5ee957b.jpeg)
