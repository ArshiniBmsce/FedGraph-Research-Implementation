# Federated Learning with Graph Convolutional Networks (GCNs)

This project demonstrates a federated learning setup using **Graph Convolutional Networks (GCNs)** across multiple clients (2 in this case) on graph datasets such as **Cora**, **CiteSeer**, and **KarateClub**. The clients train their models on local datasets and send the learned parameters to a central server for aggregation and further training.



## Reseach Paper Link: 
[FedGraph: Federated Graph Learning With Intelligent Sampling](https://ieeexplore.ieee.org/abstract/document/9606516)



## Datasets
We use the following datasets for training the GCN models:
1. **Cora**: A citation network dataset containing 2708 nodes, 5429 edges, and 7 classes.
2. **CiteSeer**: A citation dataset with 3327 nodes, 4732 edges, and 6 classes.
3. **KarateClub**: A social network dataset with 34 nodes, 78 edges, and 2 classes.



## Model
The **GCN model** used for both clients includes:
- **GCNConv Layer**: Graph convolution layer that aggregates information from node neighbors.
- **Linear Layer**: Used for classification into dataset-specific classes.
- **ReLU Activation**: Applied after graph convolution.



## Project Structure
### Client Code
Each client performs the following operations:
1. **Initialize a GCN model**: The GCN model is set up for the dataset the client is working on.
2. **Train the model**: The client trains on local data using **CrossEntropyLoss** and **Adam optimizer**.
3. **Serialize the model**: After training, the model parameters are serialized and saved for sending to the server.

### Server Code
1. **Receive client parameters**: The server receives serialized model parameters from the clients.
2. **Update model**: The server loads these parameters and updates its own model.
3. **Further training**: Optionally, the server can perform additional training using the aggregated parameters.


