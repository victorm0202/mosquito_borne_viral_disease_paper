# Model fitting
Here, we will show different parameterizations of our model for a house-level risk index for dengue disease in an urban region of Tapachula, Chiapas, Mexico.

- $PC_{DroneImage}$: The number of principal components (PCA) used to represent the *vegetation indices* (NDVI, GNDVI, NDVIre and CIgreen), and cartographic information (DSM and DTM)
- 
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
   <td style="text-align:right;"> The number of principal components (PCA) used to represent the *vegetation indices* (NDVI, GNDVI, NDVIre and CIgreen), and cartographic information (DSM and DTM) </td>
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
   <td style="text-align:right;"> The maximum number of principal components to obtain in PLS to generate our proposed index. Observe that, altough we use just the first score of PLS ($\widetilde{\mathbf{X}}\mathbf{a}_1$), results may vary for different values of $PC_{PLS}$. Also, this parameter must satisfy $PC_{PLS}\leq $PC_{FAMD}$ </td>
   <td style="text-align:right;"> $\lbrace 2, 3,4,5, 6 \rbrace$ </td>
  </tr>
</tbody>
</table>

