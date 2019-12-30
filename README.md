# Graphs for Similar Entity Search 

#### Code accompanying the medium [article](https://medium.com/coreview-systems/graphs-for-similarity-search-23a23364d08f)
## Create Graph

Using the [neo4j-admin](https://neo4j.com/docs/operations-manual/current/tools/import/syntax/) import 
1. Download data from [here](https://www.kaggle.com/himanshupoddar/zomato-bangalore-restaurants) 
2. neo4j-admin import option requires the csv to be in a specific format to create nodes and relationships.
3. The logic of creating these csv's can be found in this [notebook](https://github.com/deepam8155/SimNode/blob/master/Food_graph_logic.ipynb)
4. Run the notebook and create required csv's
5. Copy all the csv's to import folder of neo4j database
6. Run the below command 
```bash
sudo ./bin/neo4j-admin import --database zomato.db  --mode csv --ignore-missing-nodes --multiline-fields=True --ignore-duplicate-nodes --nodes:Location=import/locations.csv --nodes:Restaurant=import/restaurant.csv --nodes:Dish=import/dishes.csv --nodes:Type=import/type.csv --nodes:Cuisine=import/cuisine.csv --relationships:SERVES_CUISINE=import/cuisine_restaurant.csv --relationships:SERVES_DISH=import/restaurant_dish.csv --relationships:FALL_UNDER import/type_restaurant.csv --relationships:FAMOUS_FOR=import/liked_dishes_restaurant.csv --relationships:IN_AREA=import/restaurant_location.csv
```

### TL;DR

Import graph using [cypher-shell](https://neo4j.com/developer/kb/export-sub-graph-to-cypher-and-import/)

```bash
cat zomato_food_graph.cypher | ./bin/cypher-shell -u neo4j -p password
```
