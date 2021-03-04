---
layout: post
title:  "Directed Graphs and Dijkstra's Algorithm"
date:   2021-02-28 12:00:00 +0900
categories: C C++
---

<div style="text-align: center"><i><b>Last Updated on February 28th, 2021</b></i></div>

<!-- ## WHY?
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black"> -->

<!-- When I got this assignment from a superior who had taken the course "Data Structure", I was done implementing Dijkstra's Algorithm and very close to finishing it.
However, an error "Cannot dereference value-initialized list iterator." occurred when I finnally
 because of an error, "Cannot dereference value-initialized list iterator." which is 
I modified some parts of the skeleton and commented them right after the code -->

## AdjacencyListDirectedGraph.h
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

```cpp
#ifndef ASSIGNMENT6_ADJACENCYLISTDIRECTEDGRAPH_H
#define ASSIGNMENT6_ADJACENCYLISTDIRECTEDGRAPH_H

#include <iostream>
#include <list>
#include <stdexcept>

using namespace std;

template<typename V, typename E>
class AdjacencyListDirectedGraph {

public:
    class Vertex;
    class Edge;

    typedef list<Vertex> VertexList;
    typedef list<Edge> EdgeList;
    typedef typename VertexList::iterator VertexItor;
    typedef typename EdgeList::iterator EdgeItor;
    typedef typename VertexList::const_iterator VertexConstItor;
    typedef typename EdgeList::const_iterator EdgeConstItor;


private:
    struct VertexObject;
    struct EdgeObject;

    typedef list<VertexObject> VertexObjectList;
    typedef list<EdgeObject> EdgeObjectList;
    typedef list<EdgeList> IncidenceEdgesList;

    typedef typename VertexObjectList::iterator VertexObjectItor;
    typedef typename EdgeObjectList::iterator EdgeObjectItor;
    typedef typename IncidenceEdgesList::iterator IncidenceEdgesItor;

    struct VertexObject {
        V elt;                             
        VertexItor pos;  // VertexObjectItor pos;
        IncidenceEdgesItor inc_edges_pos;  

        VertexObject(V _elt) : elt(_elt) {
        }
    };

    struct EdgeObject {
        E elt;                          
        Vertex origin_vertex;        
        Vertex dest_vertex;                
        EdgeItor pos;  //EdgeObjectItor pos;
        EdgeItor origin_inc_edges_pos;
        EdgeItor dest_inc_edges_pos;

        EdgeObject(const Vertex& v, const Vertex& w, E _elt) : origin_vertex(v), dest_vertex(w), elt(_elt) {
        }
    };

    VertexList vertex_collection;  //VertexObjectList vertex_collection;
    EdgeList edge_collection;  //EdgeObjectList edge_collection;
    IncidenceEdgesList inc_edges_collection;


public:
    class Vertex {
        VertexObject *v_obj;

    public:
        Vertex(VertexObject* v = NULL) : v_obj(v) {}

        VertexObject* checkloc() {
            return this->v_obj;
        }

        V& operator*() const {
            return this->v_obj->elt;
        }

        EdgeList& incidentEdges() const { // EdgeList incidentEdges() const {
            return *(this->v_obj->inc_edges_pos);
        }

        bool isAdjacentTo(const Vertex& v) const {
            EdgeList EL = this->incidentEdges();
            for (EdgeItor EI = EL.begin(); EI != EL.end(); EI++) {
                if (EI->origin() == *this && EI->dest() == v) {
                    return true;
                }
                else if (EI->origin() == v && EI->dest() == *this) {
                    return true;
            }
            return false;
        }

        bool isOutgoingTo(const Vertex& v) const {
            EdgeList EL = this->incidentEdges();
            for (EdgeItor EI = EL.begin(); EI != EL.end(); EI++) {
                if (EI->origin() == *this && EI->dest() == v) {
                    return true;
                }
            }
            return false;
        }

        Edge outgoingEdge(const Vertex& v) const {
            EdgeList EL = this->incidentEdges();
            for (EdgeItor EI = EL.begin(); EI != EL.end(); EI++) {
                if (EI->origin() == *this && EI->dest() == v) {
                    return *EI;
                }
            }
            throw runtime_error("The directed edge does not exist.");
        }

        EdgeList outgoingEdges() const {
            EdgeList EL = this->incidentEdges(),
                NEW_EL;
            for (EdgeItor EI = EL.begin(); EI != EL.end(); EI++) {
                if (EI->origin() == *this) {
                    NEW_EL.push_back(*EI);
                }
            }
            return NEW_EL;
        }

        bool operator==(const Vertex& v) const {
            return (**this == *v);
        }

        friend class AdjacencyListDirectedGraph<V,E>;
    };

    class Edge {
        EdgeObject *e_obj;

    public:
        Edge(EdgeObject* e = NULL) : e_obj(e) {}

        E& operator*() const {
            return this->e_obj->elt;
        }

        VertexList endVertices() const {
            VertexList VL;
            VL.push_back(this->origin());
            VL.push_back(this->dest());
            return VL;
        }

        Vertex opposite(const Vertex& v) const {
            if (this->origin() == v) return this->dest();
            else if (this->dest() == v) return this->origin();
            else throw runtime_error("The given vertex is neither origin nor destination");
        }

        bool isAdjacentTo(const Edge& edge) const {
            return this->origin() == edge.origin()
                || this->origin() == edge.dest()
                || this->dest() == edge.origin()
                || this->dest() == edge.dest();
        }

        bool isIncidentOn(const Vertex& v) const {
            return ((this->origin() == v || this->dest() == v) ? true : false);
        }

        Vertex origin() const {
            return this->e_obj->origin_vertex;
        }

        Vertex dest() const {
            return this->e_obj->dest_vertex;
        }

        bool isDirected() const {
            return true;
        }

        bool operator==(const Edge& edge) const {
            return (**this == *edge);
        }

        friend class AdjacencyListDirectedGraph<V,E>;
    };


public:
    VertexList vertices() {
        return vertex_collection;
    }

    EdgeList edges() {
        return edge_collection;
    }

    Vertex insertVertex(const V& x) {
        VertexObject* VO = new VertexObject(x);
        EdgeList* EL = new EdgeList;

        Vertex VTX(VO);
        VO->pos = vertex_collection.insert(vertex_collection.end(), VTX);
        VO->inc_edges_pos = inc_edges_collection.insert(inc_edges_collection.end(), *EL);

        return VTX;
    }

    Edge insertDirectedEdge(const Vertex& v, const Vertex& w, E x) {
        EdgeObject* EO = new EdgeObject(v, w, x);
        Edge EDG(EO);

        EO->pos = edge_collection.insert(edge_collection.end(), EDG);
        EO->origin_inc_edges_pos = v.incidentEdges().insert(v.incidentEdges().end(), EDG);
        EO->dest_inc_edges_pos = w.incidentEdges().insert(w.incidentEdges().end(), EDG);

        return EDG;
    }

    void eraseVertex(const Vertex& v) {
        //TODO
    }

    void eraseEdge(const Edge& e) {
        //TODO
    }

};
#endif //ASSIGNMENT6_ADJACENCYLISTDIRECTEDGRAPH_H
```

## assignment6.cpp
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

```cpp
#include <iostream>
#include <string>
#include <stdexcept>
#include <queue>
#include <list>
#include <vector>
#include <map>
#include <limits>
#include "AdjacencyListDirectedGraph.h"
#include "FlightMap.h"

double FlightMap::calcRouteDistance(const list<string> route) {
	double sum = 0;
	int numofAirport = route.size();

	list<string>::const_iterator LCiter = route.begin();
	for (int i = 0; i < numofAirport - 1; i++, LCiter++) {
		string str1 = *LCiter,
			str2 = *(++LCiter);
		FlightGraph::Vertex v1, v2;
		if (!findAirport(v1, str1) || !findAirport(v2, str2)) {
			throw runtime_error("Any airport in the route does not exist.");
		}
		if (!isConnectionExist(str1, str2)) {
			throw runtime_error("some edges on the route do not exist.");
		}
		FlightGraph::EdgeList elist = v1.outgoingEdges();
		for (FlightGraph::EdgeItor iter = elist.begin(); iter != elist.end(); iter++) {
			if (iter->dest() == v2) {
				sum += **iter;
			}
		}
		LCiter--;
	}
	return sum;
}

list<string> FlightMap::findShortestRoute(const string& airport1, const string& airport2) {
	// dist_DB and backtracking_DB
	const int INF = 2147483647;
	map<string, double> dist_DB;
	map<string, string> backtracking_DB;

	FlightGraph::VertexList vtx_list = flight_graph.vertices();
	for (FlightGraph::VertexItor vtx_iter = vtx_list.begin(); vtx_iter != vtx_list.end(); vtx_iter++) {
		dist_DB.insert({ **vtx_iter, INF });
		backtracking_DB.insert({ **vtx_iter, "EMPTY" });
	}

	// Starting, Ending airports check
	FlightGraph::Vertex v1, v2;
	if (!findAirport(v1, airport1) || !findAirport(v2, airport2)) {
		throw runtime_error("some of the given airports does not exist.");
	}

	// Dijkstra with priority_queue
	priority_queue<pair<double, string>> pq;
	pq.push({ 0, airport1 });
	dist_DB.find(airport1)->second = 0;

	while (!pq.empty()) {
		string now = pq.top().second;
		double cost = -pq.top().first;
		pq.pop();

		FlightGraph::Vertex now_vtx;
		if (!findAirport(now_vtx, now)) {
			throw runtime_error("some of the given airports does not exist.");
		}

		if (cost > dist_DB.find(now)->second) continue;

		FlightGraph::EdgeList edg_list = now_vtx.outgoingEdges();
		for (FlightGraph::EdgeItor edg_iter = edg_list.begin(); edg_iter != edg_list.end(); edg_iter++) {
			FlightGraph::Vertex nxt_vtx = edg_iter->dest();
			double nxtCost = cost + **edg_iter;
			if (nxtCost < dist_DB.find(*nxt_vtx)->second) {
				dist_DB.find(*nxt_vtx)->second = nxtCost;
				pq.push({ -nxtCost, *nxt_vtx });
				backtracking_DB.find(*nxt_vtx)->second = now;
			}
		}
	}
	list<string> return_list;

	// Route check
	if (backtracking_DB.find(airport2)->second == "EMPTY") {
		throw runtime_error("no route exists.");
		return return_list;
	}

	// Backtracking
	string endPoint = airport2;
	while (true) {
		return_list.push_front(endPoint);
		endPoint = backtracking_DB.find(endPoint)->second;
		if (endPoint == "EMPTY") {
			break;
		}
	}
	return return_list;
}

void FlightMap::printAllShortestRoutes(const string &airport) {
	FlightGraph::Vertex vtx;

	if (!findAirport(vtx, airport)) {
		throw runtime_error("The given airport do not exist");
	}

	FlightGraph::VertexList vtx_list = flight_graph.vertices();
	for (FlightGraph::VertexItor vtx_iter = vtx_list.begin(); vtx_iter != vtx_list.end(); vtx_iter++) {
		if(*vtx_iter == vtx) continue;
		list<string> return_list = findShortestRoute(airport, **vtx_iter);
		if (return_list.size() > 0) {
			printRoute(return_list);
			cout << " (Distance = " << calcRouteDistance(return_list) << ")" << endl;
		}
	}

}

``` 

## Result
<hr style="height: 2px; border:none; margin-top: -1em; margin-bottom:0.5em; padding: 0; background:black">

Left: ./flight_map_sample   
Right: g++ -o output assignment6.cpp FlightMap.cpp main.cpp -std=c++11, ./output   
<img src="/img/flightmap_01.png">
<img src="/img/flightmap_02.png">
<img src="/img/flightmap_03.png">
<img src="/img/flightmap_04.png">