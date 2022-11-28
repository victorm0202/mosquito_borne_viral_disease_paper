# Model fitting
Here, we will show different parameterizations of our model for a house-level risk index for dengue disease in an urban region of Tapachula, Chiapas, Mexico.

Main parameters are:
<table>
 <thead>
  <tr>
   <th style="text-align:left;"> Parameter </th>
   <th style="text-align:right;"> Description </th>
   <th style="text-align:right;"> Values </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> $PC_{DroneImage}$ </td>
   <td style="text-align:right;"> The number of principal components (PCA) used to represent the vegetation indices (NDVI, GNDVI, NDVIre and CIgreen), and cartographic information (DSM and DTM) </td>
   <td style="text-align:right;"> $\lbrace 1,2 \rbrace$ </td>
  </tr>  
  <tr>
   <td style="text-align:left;"> $nclust$ </td>
   <td style="text-align:right;"> The number of clusters considered to model the spatial relationships between the houses  </td>
   <td style="text-align:right;"> $\lbrace 2, 3, 4, 5, 6 \rbrace$ </td>
  </tr>   
  <tr>
   <td style="text-align:left;"> $k_{nn}$ </td>
   <td style="text-align:right;"> The number of $k$ nearest neighboring houses for defining the connectivities in the agglomerative hierarchical clustering with spatial constraints  </td>
   <td style="text-align:right;"> $\lbrace 3,4,5 \rbrace$ </td>
  </tr>
  <tr>
   <td style="text-align:left;"> $PC_{FAMD}$ </td>
   <td style="text-align:right;"> The number of principal components to be used, obtained with FAMD  </td>
   <td style="text-align:right;"> $\lbrace 2, 3,4,5, 6 \rbrace$ </td>
  </tr>
 <tr>
   <td style="text-align:left;"> $PC_{PLS}$ </td>
   <td style="text-align:right;"> The maximum number of principal components to obtain in PLS to generate our proposed index. Observe that, altough we use just the first score of PLS ($\tilde{X}a_1$), results may vary for different values of $PC_{PLS}$. Also, this parameter must satisfy $PC_{PLS}\leq PC_{FAMD}$ </td>
   <td style="text-align:right;"> $\lbrace 2, 3,4,5, 6 \rbrace$ </td>
  </tr>
</tbody>
</table>

# Evaluation

As any regression-based model, in PLS we can obtain some metrics accounting for its predictive performance, however, it is not our objective (it is very easy to show that a performance metric such as the coefficient of determination, can be artificially "inflated", resulting in an overfitted model). In our case, we want to take advantage of an unique characteristic of PLS: to construct the best set of latent variables (components) based on the set of factors we obtained with FAMD,  which are correlated to our response variable of interest, as we explained in Section 3.4.3. In this sense, we want to exploit the explanatory habilities of PLS which will allows us to obtain a set of components that can represent all covariates we used (from different sources and types) in an useful way to be considered as a risk index. 
Then, our main evaluation critera was the explained inertia obtained with the FAMD procedure according to the $PC_{FAMD}$ variable, and the residuals on log counts of the response variables. 

# Experiments

We did an extensive set of experiments with different parameterizations, however, because we have many possible combinations of the parameters, we will show just some of them.

## Model 1

<table>
 <thead>
  <tr>
   <td style="text-align:left;"> $PC_{DroneImage}$ </td>
   <td style="text-align:left;"> $nclust$ </td>
   <td style="text-align:left;"> $k_{nn}$ </td>
   <td style="text-align:left;"> $PC_{FAMD}$ </td>
   <td style="text-align:left;"> $PC_{PLS}$ </td>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:right;"> $1$ </td>
   <td style="text-align:right;"> $2$ </td>
   <td style="text-align:right;"> $3$ </td>
   <td style="text-align:right;"> $2$ </td>
   <td style="text-align:right;"> $2$ </td>
  </tr>
</tbody>
</table>

Explained inertia: 0.72

### Hierarchical clustering with connectivity constraints. 
<img src="model1/clust_spatial_constraints_100px.png" height="55%" width="55%" align="center"/>

### House-level risk index 
<img src="model1/pls_index_allIndex.png" height="65%" width="65%" align="center"/>

### House-level risk index (geographic distribution)
<img src="model1/geo_index.png" height="55%" width="55%" align="center"/>

## Model 2

<table>
 <thead>
  <tr>
   <td style="text-align:left;"> $PC_{DroneImage}$ </td>
   <td style="text-align:left;"> $nclust$ </td>
   <td style="text-align:left;"> $k_{nn}$ </td>
   <td style="text-align:left;"> $PC_{FAMD}$ </td>
   <td style="text-align:left;"> $PC_{PLS}$ </td>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:right;"> $1$ </td>
   <td style="text-align:right;"> $2$ </td>
   <td style="text-align:right;"> $3$ </td>
   <td style="text-align:right;"> $4$ </td>
   <td style="text-align:right;"> $4$ </td>
  </tr>
</tbody>
</table>

Explained inertia: 0.72

### Hierarchical clustering with connectivity constraints. 
<img src="model2/clust_spatial_constraints_100px.png" height="55%" width="55%" align="center"/>

### House-level risk index 
<img src="model2/pls_index_allIndex.png" height="65%" width="65%" align="center"/>

### House-level risk index (geographic distribution)
<img src="model2/geo_index.png" height="55%" width="55%" align="center"/>

## Model 3 (overfitted)

<table>
 <thead>
  <tr>
   <td style="text-align:left;"> $PC_{DroneImage}$ </td>
   <td style="text-align:left;"> $nclust$ </td>
   <td style="text-align:left;"> $k_{nn}$ </td>
   <td style="text-align:left;"> $PC_{FAMD}$ </td>
   <td style="text-align:left;"> $PC_{PLS}$ </td>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:right;"> $1$ </td>
   <td style="text-align:right;"> $2$ </td>
   <td style="text-align:right;"> $3$ </td>
   <td style="text-align:right;"> $6$ </td>
   <td style="text-align:right;"> $6$ </td>
  </tr>
</tbody>
</table>

Explained inertia: 0.72

### Hierarchical clustering with connectivity constraints. 
<img src="model3/clust_spatial_constraints_100px.png" height="55%" width="55%" align="center"/>

### House-level risk index 
<img src="model3/pls_index_allIndex.png" height="65%" width="65%" align="center"/>

### House-level risk index (geographic distribution)
<img src="model3/geo_index.png" height="55%" width="55%" align="center"/>

## Model 4

<table>
 <thead>
  <tr>
   <td style="text-align:left;"> $PC_{DroneImage}$ </td>
   <td style="text-align:left;"> $nclust$ </td>
   <td style="text-align:left;"> $k_{nn}$ </td>
   <td style="text-align:left;"> $PC_{FAMD}$ </td>
   <td style="text-align:left;"> $PC_{PLS}$ </td>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:right;"> $1$ </td>
   <td style="text-align:right;"> $3$ </td>
   <td style="text-align:right;"> $5$ </td>
   <td style="text-align:right;"> $3$ </td>
   <td style="text-align:right;"> $3$ </td>
  </tr>
</tbody>
</table>

Explained inertia: 0.695

### Hierarchical clustering with connectivity constraints. 
<img src="model6/clust_spatial_constraints_100px.png" height="55%" width="55%" align="center"/>

### House-level risk index 
<img src="model6/pls_index_allIndex.png" height="65%" width="65%" align="center"/>

### House-level risk index (geographic distribution)
<img src="model6/geo_index.png" height="55%" width="55%" align="center"/>

## Model 5

<table>
 <thead>
  <tr>
   <td style="text-align:left;"> $PC_{DroneImage}$ </td>
   <td style="text-align:left;"> $nclust$ </td>
   <td style="text-align:left;"> $k_{nn}$ </td>
   <td style="text-align:left;"> $PC_{FAMD}$ </td>
   <td style="text-align:left;"> $PC_{PLS}$ </td>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:right;"> $1$ </td>
   <td style="text-align:right;"> $6$ </td>
   <td style="text-align:right;"> $4$ </td>
   <td style="text-align:right;"> $4$ </td>
   <td style="text-align:right;"> $4$ </td>
  </tr>
</tbody>
</table>

Explained inertia: 0.616

### Hierarchical clustering with connectivity constraints. 
<img src="model11/clust_spatial_constraints_100px.png" height="55%" width="55%" align="center"/>

### House-level risk index 
<img src="model11/pls_index_allIndex.png" height="65%" width="65%" align="center"/>

### House-level risk index (geographic distribution)
<img src="model11/geo_index.png" height="55%" width="55%" align="center"/>


## Model 6

<table>
 <thead>
  <tr>
   <td style="text-align:left;"> $PC_{DroneImage}$ </td>
   <td style="text-align:left;"> $nclust$ </td>
   <td style="text-align:left;"> $k_{nn}$ </td>
   <td style="text-align:left;"> $PC_{FAMD}$ </td>
   <td style="text-align:left;"> $PC_{PLS}$ </td>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:right;"> $2$ </td>
   <td style="text-align:right;"> $5$ </td>
   <td style="text-align:right;"> $3$ </td>
   <td style="text-align:right;"> $4$ </td>
   <td style="text-align:right;"> $4$ </td>
  </tr>
</tbody>
</table>

Explained inertia: 0.594

### Hierarchical clustering with connectivity constraints. 
<img src="model16/clust_spatial_constraints_100px.png" height="55%" width="55%" align="center"/>

### House-level risk index 
<img src="model16/pls_index_allIndex.png" height="65%" width="65%" align="center"/>

### House-level risk index (geographic distribution)
<img src="model16/geo_index.png" height="55%" width="55%" align="center"/>

