# Integrated-Modeling
In this repository, multiple free programing tools will be integrated to summarize and demonstrate the 4 steps of small and mid-sized city planning.

1. Subarea Analysis
- Creating General Multi model specifications (GMNS) format network for the area and specify point of intrests (POIs).
- Metohd: osm2gmns https://osm2gmns.readthedocs.io/en/latest/
Step	Process	Input file	Method	Output
1	Network files preparation	map.osm (from OpenStreetMap)	OSM2GMNS (Python package)	link.csv
				node.csv
				poi.csv
![image](https://user-images.githubusercontent.com/117876335/214445873-51ce8409-f594-412b-8aad-aedcc697f6a3.png)

2. Trip Generation
- Generate the number of production and attraction trips (the number of trips entering and leaving each zone)for each trip purpose (HBw, HBO, and NHB) >> person trips per day.
- Method: grid2demand https://github.com/asu-trans-ai-lab/grid2demand
	Steps	Process 	Input file	Method	Output
1	- Zone generation.
- Partition network into grid cells	poi.csv
link.csv
node.csv	Grid2demand	Zone.csv
2	- production/attraction rates of each land use ((optional))	poi.csv, trip purpose set as 1	Grid2demand	poi_trip_rate.csv
3	- production/attraction value of each node according to POI type	poi.csv 
or
poi_trip_rate.csv	Grid2demand	Updated: node.csv
Which contains # of production and attraction trips
4	- zone-to-zone accessibility matrix.
- Change the latitude of the area of interest (optional). Default value asigned
	Zone.csv
Updated: node.csv
	Grid2demand	accessibility.csv (optional, however, it is needed if you preceding to next step, trip Distribution)
![image](https://user-images.githubusercontent.com/117876335/214445478-f0766d94-4633-4179-8fe3-6c1db411bfa8.png)

3. Trip Distriputaion
- Estimate the number of trips made between each zone.
- Trip distribution classification is considered.
	. Classification of trip distribution
		- internal > internal 
		- internal > external
		- external > internal
		- external > external 
- Method: grid2demand https://github.com/asu-trans-ai-lab/grid2demand
Step	Process	Input file	Method	Output
1	Apply gravity model to perform trip distribution	zone.csv 
od_accessibility.csv
	Grid2demand (Python package)	demend.csv
	Generate agent-based demand	demend.csv	Grid2demand 	input_agent.csv
![image](https://user-images.githubusercontent.com/117876335/214452374-316789be-ba1e-4eb6-89c2-4501f8cb474f.png)

4. Traffic Assignment
- Path4GMNS supports, in short,
	. finding (static) shortest path between two nodes,
	. constructing shortest paths for all individual agents,
	. performing path-based User-Equilibrium (UE) traffic assignment,
	. evaluating multimodal accessibility and equity,
	. synthesizing zones and Origin-Destination (OD) demand for a given network.
- Method: path4gmns https://path4gmns.readthedocs.io/en/latest/
Steps	Process 	Input file	Method	Output
1	-Finding (static) shortest path between two nodes,	node.csv
link.csv
demand.csv
settings.yml (for multimodal analyses)
	Path4gmns (Python package)	agent.csv
2		node.csv
link.csv
demand.csv
settings.csv (for DTALite)
	DTALite (C++ package)	link_performence.csv
(volume, v/c, Speed, travel time)
route_assignment.csv
(OD pair, path volume)

![image](https://user-images.githubusercontent.com/117876335/214459961-653925b5-04b1-4486-aac8-3880a1fa1dad.png)

Flowchart shows the different 4-steps small&mid-sized city planning:

![4-steps_mid-sized_city_planning_v2](https://user-images.githubusercontent.com/117876335/214474319-9848913d-c704-41a8-b91a-e555f5ee957b.jpeg)
