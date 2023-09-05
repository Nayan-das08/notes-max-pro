## important questions/topics for minor and end term
1. explain the different maximum entropy models
2. write short notes on articulative primitives, auditory primitives and acoustic primitives.
3. discuss important tools available for the development of NLP applications.
4. explain transfer model of machine translation and its 3 phases.
5. explain different stages speech recognition system.
6. numerical
	1. design a finite state transducer with E insertion orthographic rule that parses from surface level "spoons" through the lexical phases "spoon+N+PL".
	2. identify the head and morphological types (noun, phrase, verb phrase, adjective phrase, adverbial phrase) of the following sentence
		- the student of the school
		- looked up the star
		- angry as a lion
		- rapidly like a mosquito
	3. in a corpus of N documents, one randomly chosen document contains a total of T terms and the term "hello" appears K times. what is the correct value for the product of TF (term frequency) and IDF (Inverse Document Frequency), if the term "hello" appears in approximately 1/3 of the total documents.
		- $TF = K/T$ 
		- $IDF = log_{10}(\text{total document} / \text{no. of documents containing data})$ 

---

The paper titled “Multi-temporal Analysis of Land Use and Land Cover Change Detection for Dedza District of Malawi using Geospatial Techniques” is a study that analyzed the changes in land use and land cover (LULC) in Dedza district of Malawi for the years 1991, 2001, and 2015 using remote sensing and GIS. The study used both supervised and unsupervised classification algorithms on each image and achieved an overall accuracy of 91.86%.

The results revealed that forest land, water bodies, wetlands, and agricultural land drastically declined while built-up areas and barren land substantially increased between 1991 and 2015. The long-term annual rate of change declined for water bodies from 5.54% ha-1 to 1.74% ha-1 within the period of study. Likewise, the forest land, agricultural land, and built-up area experienced increased annual rates of change from 1.71% ha-1 to 1.94% ha-1, 0.02% ha-1 to 0.11% ha-1, and 7.22% ha-1 to 9.80% ha-1 respectively.

Post-classification comparison of the classified images based on the transition matrix indicated that approximately 61.48% of the total forest land in 1991 was converted to barren land in 2015 while about 2.70% of agricultural land in 1991 has been converted to built-up land in 2015. This study provides reliable LULC data which captured the extent and rate of land use changes that has occurred in the Dedza district of Malawi for the period ranging from 1991-2015. It is believed that the trends identified in this study would be useful in guiding planners and decision-makers of land management and policy decisions geared towards a more sustainable natural resource management strategy in the Dedza district and other districts of similar setting. It is recommended that a study be undertaken to establish the apparent socio-economic and spatial drivers of the LULC changes between 1991 and 2015 over Dedza district of Malawi

---
The paper titled “Using Landsat satellite data for assessing the land use and land cover change in Kashmir valley” is a study that examined the land use and land cover changes in the Kashmir valley between the time periods from 1992–2001–2015 using a set of compatible moderate resolution Landsat satellite imageries. The study adopted a supervised approach with maximum likelihood classifier for the classification and generation of LULC maps for the selected time periods.

The results revealed that there have been substantial changes in the land use and cover during the chosen time periods. In general, three land use and land cover change patterns were observed in the study area: (1) consistent increase of the area under marshy, built-up, barren, plantation, and shrubs; (2) continuous decrease in agriculture and water; (3) decrease (1992–2001) and increase (2001–2015) in forest and pasture classes. In terms of the area under each LULC category, most significant changes have been observed in agriculture (-), plantation (+), built-up (+), and water (-); however, with reference to percent change within each class, the maximum variability was recorded in built-up (198.45%), plantation (87.98%), pasture (-71%), water (-48%) and agriculture (-28.85%).

The massive land transformation is largely driven by anthropogenic actions and has been mostly adverse in nature, giving rise to multiple environmental issues in the ecologically sensitive Kashmir valley. The study provides valuable insights into the land use and land cover changes in the Kashmir valley over a period of time and can be useful for environmental conservation, resource management, land use planning, and sustainable development.

---
The paper titled “Deep learning-based object detection and geographic coordinate estimation system for GeoTiff imagery” is a research that focuses on applying a Convolutional Neural Network (CNN) to detect objects and estimate the geographic coordinate of airplanes, ships, and cars in GeoTiff images. The system prototype was tested to measure the accuracy and precision for object detection, and a Mean Absolute Error (MAE) analysis was done to measure object coordinate estimation performance.

The accuracy and precision for object detection of the system prototype are 81.05% and 93.29%, respectively. The system has MAE values which vary from 0.000012° to 0.000034° for object coordinate estimation. This research proposed a system for detecting and estimating the coordinate of specific objects in GeoTiff images using CNN, which has been proven to result in good performance to detect objects from aerial and satellite imagery.

---
- **STAC Catalog**: The **SpatioTemporal Asset Catalog (STAC)** is a specification that provides a common language to describe geospatial information, so it can be more easily worked with, indexed, and discovered. The STAC Catalog is a simple, flexible JSON file of links that provides a structure to organize and browse STAC Items. A series of best practices helps make recommendations for creating real-world STAC Catalogs.
    
- **GeoJSON**: GeoJSON is an open standard format designed for representing simple geographical features, along with their non-spatial attributes. It is based on the JSON format. The features include points (therefore addresses and locations), line strings (therefore streets, highways, and boundaries), polygons (countries, provinces, tracts of land), and multi-part collections of these types.
    
- **GeoTIFF**: GeoTIFF is a public domain metadata standard that allows georeferencing information to be embedded within a TIFF file. The potential additional information includes map projection, coordinate systems, ellipsoids, datums, and everything else necessary to establish the exact spatial reference for the file. The GeoTIFF format is fully compliant with TIFF 6.0, so software incapable of reading and interpreting the specialized metadata will still be able to open a GeoTIFF format file.

