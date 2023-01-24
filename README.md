# Integrated-Modeling
In this repository, multiple free programing tools will be integrated to summarize and demonstrate the 4 steps of small and mid-sized city planning.

1. Subarea Analysis
- Creating General Multi model specifications (GMNS) format network for the area and specify point of intrests (POIs)
- Metohd: osm2gmns https://osm2gmns.readthedocs.io/en/latest/
Input file	Method	Output
map.osm 	OSM2GMNS (Python package)	link.csv
		node.csv
		poi.csv
![image](https://user-images.githubusercontent.com/117876335/214426778-19e83a89-edc0-4e4d-8a2c-d24914073531.png)
- Visualization: NeXTA https://github.com/asu-trans-ai-lab/NeXTA4GMNS or QGIS https://qgis.org/en/site/

2. Trip Generation
- Generate the number of production and attraction trips for each trip purpose (HBw, HBO, and NHB) >> person trips per day.
- Method: grid2demand https://github.com/asu-trans-ai-lab/grid2demand
	Process 	Input file	Method	Output
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
![image](https://user-images.githubusercontent.com/117876335/214443163-bdb8cdec-9da7-426b-ab95-32becf88a516.png)

3. Trip Distriputaion
- Trip distribution classification is considered.
	. Classification of trip distribution
		- 	internal > internal 
