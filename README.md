/*https://github.com/afuu21/18CSL76-AIML-Programs/blob/main/4.%20ID3.ipynb*/
/2-https://github.com/afuu21/18CSL76-AIML-Programs/blob/main/2.%20S-AO-star.ipynb/
/1-https://github.com/afuu21/18CSL76-AIML-Programs/blob/main/1.%20A-star.ipynb/
//8-https://github.com/AshishVajpayee/VTU-AIML-Lab-Programs/blob/master/KNNLab8/KNN.ipynb//
//6-https://github.com/AshishVajpayee/VTU-AIML-Lab-Programs/blob/master/NaiveBayesianLab6/NaiveBayesian.ipynb//
//7-https://github.com/AshishVajpayee/VTU-AIML-Lab-Programs/blob/master/EMLab7/EM.ipynb//
//5-https://github.com/AshishVajpayee/VTU-AIML-Lab-Programs/blob/master/BackPropagationLab5/Backpropagation.ipynb//
//3-https://github.com/AshishVajpayee/VTU-AIML-Lab-Programs/blob/master/CandidateEliminationLab3/CandidateElimination.ipynb//
//9-https://github.com/AshishVajpayee/VTU-AIML-Lab-Programs/blob/master/RegressionLab9/Regression.ipynb//
///1st program 

import networkx as nx

def heuristic(n, goal):
    H_dist = {
        'A': 10,
        'B': 8,
        'C': 5,
        'D': 7,
        'E': 3,
        'F': 6,
        'G': 5,
        'H': 3,
        'I': 1,
        'J': 0
    }
    return H_dist[n]

def aStarAlgo(graph, start, goal):
    G = nx.Graph()
    G.add_weighted_edges_from([(node, neighbor, weight) for node, neighbors in graph.items() for neighbor, weight in neighbors])

    path = nx.astar_path(G, start, goal, heuristic=lambda n, goal_node: heuristic(n, goal), weight='weight')
    return path

# Describe your graph here
Graph_nodes = {
    'A': [('B', 6), ('F', 3)],
    'B': [('C', 3), ('D', 2)],
    'C': [('D', 1), ('E', 5)],
    'D': [('C', 1), ('E', 8)],
    'E': [('I', 5), ('J', 5)],
    'F': [('G', 1), ('H', 7)],
    'G': [('I', 3)],
    'H': [('I', 2)],
    'I': [('E', 5), ('J', 3)],
}

result = aStarAlgo(Graph_nodes, 'A', 'J')
print("Path found:", result)//
