# Chapter 2: Planning
## 2.3 goals and objectives

- **Gain Comprehensive Insights into Environmental Dynamics**: The primary goal of this project is to acquire a deep understanding of the various factors influencing land cover changes across the study area, considering a spectrum of multispectral data and historical records.

- **Develop Advanced Analytical Tools for Environmental Assessment**: Create a user-friendly toolkit for land cover analysis and change detection, tailored to the needs of environmental experts, researchers, and policymakers. This tool will serve as a valuable resource for informed decision-making.

- **Advance Knowledge in Environmental Sciences**: Contribute to the body of knowledge in environmental sciences by unearthing novel insights into land cover dynamics. This includes uncovering trends, patterns, and underlying drivers of environmental transformations.

- **Establish Accessible AI-driven Environmental Assessment System**: Design and implement an artificial intelligence-driven system that enables widespread access, particularly among environmental professionals, for accurate and efficient land cover analysis. This system will enhance the capacity for timely and reliable environmental assessments.

- **Integrate Multimodal Data for Early Environmental Diagnosis**: Develop a comprehensive framework capable of early environmental diagnosis using a combination of imagery and tabular data. This innovative approach aims to provide a holistic understanding of environmental dynamics.

- **Leverage Cutting-Edge Machine Learning and Deep Learning Techniques**: Explore and adopt state-of-the-art machine learning and deep learning models and algorithms, as identified through an extensive literature survey, to enhance the accuracy and efficiency of land cover analysis.

- **Optimize Data Engineering Processes**: Implement robust data engineering techniques to ensure the accurate preparation of diverse datasets prior to model training. This critical step will lay the foundation for robust and reliable analytical results.

- **Leverage Convolutional Neural Networks (CNNs) and Variants for Image Analysis**: Utilize CNNs and their variants for in-depth analysis of image-based data, enhancing the project's capability to accurately detect and classify land cover types.

- **Provide User-friendly Interface for Model Interaction**: Develop a web-based framework to deploy the models, offering an intuitive user interface for effective interaction. This will facilitate easy access and utilization of the analytical tools.

- **Disseminate Research Findings through Scholarly Publications**: Summarize the key findings and model results in the form of a research paper, contributing to the academic discourse surrounding multispectral land cover analysis and change detection.

- **Ensure Ongoing Model Relevance and Performance**: Commit to regular refinement and updates of the model by incorporating the latest advancements in machine learning, data engineering, and acquiring training data based on the most recent research, ensuring the model remains at the forefront of environmental assessment practices.

## 2.4 background information

- introduction to the topic
	- Remote sensing multispectral satellite data and its use in LULC
- historical context
- prev research and studies
	- datasets used
		- landsat-8
		- Operational Land Imager-OLI
	- image processing techniques like 
		- extraction, geometric correction or georeferencing, atmospheric correction, topographic correction, layer stacking (band selection and combination), image enhancement and subsetting (clipping)
	- classification techniques used
		- SVM
		- Neural Networks
		- maximum likelihood
		- logistic–multicriteria evaluation–cellular automata–Markov (LMCM) model
		- sub-pixel, knowledge-based, contextual-based, object-based image analysis (OBIA)
		- random forest
	- change detection algorithms used
		- post classification comparison method, most common method to compare maps
- key concepts and terminologies of LULC classification and change detection
- relevance and significance of LULC image classification and change detection

**Introduction to the Topic**
Remote sensing multispectral satellite data stands at the forefront of modern environmental monitoring and analysis. This technology involves capturing imagery of Earth's surface using sensors aboard satellites, which can detect a range of wavelengths across the electromagnetic spectrum. Multispectral data provides a wealth of information about land cover types, enabling us to distinguish between various features like vegetation, water bodies, urban areas, and natural landscapes. The key advantage of multispectral data lies in its ability to capture different spectral signatures, allowing for detailed characterization of Earth's surface. This wealth of information is indispensable in Land Use and Land Cover (LULC) studies, where accurate classification and assessment of surface features are vital for tasks ranging from urban planning to ecological monitoring. By harnessing the power of remote sensing multispectral satellite data, we unlock a comprehensive view of our environment, providing critical insights for informed decision-making and sustainable land management practices.

**prev work**
A multitude of datasets have been employed in LULC studies, with Landsat-8 and Operational Land Imager-OLI standing out as prominent sources. These platforms provide high-quality, multispectral imagery that is crucial for accurate classification and change detection analyses. Image processing techniques, such as geometric correction, atmospheric correction, and layer stacking, are commonly employed to enhance the quality and suitability of satellite data for further analysis.

Various classification techniques have been instrumental in LULC studies. Support Vector Machines (SVM), Neural Networks, Maximum Likelihood, Logistic-Multicriteria Evaluation-Cellular Automata-Markov (LMCM) models, sub-pixel, knowledge-based, contextual-based, and Object-Based Image Analysis (OBIA) have all been utilized to discern land cover classes. Furthermore, employing algorithms like Random Forest has proven effective in achieving precise classification results.

In the realm of change detection, the post-classification comparison method stands as one of the most widely used techniques. It allows for the direct comparison of classified maps over different time periods, enabling the identification of areas that have undergone significant land cover transformations. This method provides a robust foundation for tracking changes in the landscape and understanding the dynamics of environmental alterations.

**Key Concepts and Terminologies of LULC Classification and Change Detection**
Land Use and Land Cover (LULC) classification and change detection are pivotal processes in environmental monitoring and assessment. LULC classification involves the categorization of Earth's surface into distinct classes, such as forests, urban areas, water bodies, and agricultural land, based on spectral information derived from remote sensing data. This classification facilitates a comprehensive understanding of the spatial distribution of various land cover types, enabling informed decision-making for resource management and environmental conservation. Change detection, on the other hand, focuses on identifying alterations in land cover over time. It involves the comparison of classified images from different temporal periods to pinpoint areas that have experienced significant transformations. This process is instrumental in detecting land use shifts, urban expansion, deforestation, and other critical environmental changes. Accurate and timely LULC classification and change detection are imperative for sustainable land management, providing essential information for policymakers, researchers, and environmental practitioners. Additionally, these techniques play a crucial role in assessing the impacts of human activities and natural phenomena on the landscape, contributing to a more holistic understanding of environmental dynamics.

**Relevance and Significance of LULC Image Classification and Change Detection**
Land Use and Land Cover (LULC) image classification and change detection serve as indispensable tools in modern environmental research and resource management. These techniques hold particular relevance in addressing pressing global challenges such as urbanization, deforestation, and climate change. Through LULC classification, we gain valuable insights into the spatial distribution of different land cover types, which is crucial for informed decision-making in agriculture, urban planning, and natural resource conservation. Additionally, change detection offers the ability to monitor alterations in the landscape over time, enabling the identification of areas undergoing rapid transformation. This is essential for assessing the impacts of human activities and natural disasters, as well as for devising effective mitigation and adaptation strategies. Moreover, the data derived from LULC analysis forms the basis for a wide range of applications, from habitat conservation to disaster management and climate modeling. As such, the relevance and significance of LULC image classification and change detection cannot be overstated, making them indispensable tools in the pursuit of sustainable and resilient environments.

## 2.5 scope

- project scope
	- deliverables
		- an image classification model that maps a particular geographical co-ordinate to its corresponding land form class
		- a change detection pipeline that gives s a comprehensive change detection analysis for a geo-location over a given period of time.
		- a cloud-based platform that enables easy and transparent access to models
	- functional (and non functional) requirements that can be expected from the project outcome
		- functional requirements
			1. **Geographical Mapping**: The model should accurately classify the land form class corresponding to a given geographical co-ordinate.
			2. **Multi-class Classification**: It should support classification into multiple land form classes, allowing for a comprehensive assessment.
			3. **High Accuracy**: The model should achieve a high classification accuracy to ensure reliable results.
			4. **Real-time Processing**: The classification should be performed efficiently, providing results in near real-time for responsive decision-making.
			5. **Temporal Analysis**: The pipeline should be capable of analyzing changes over a given period of time for a specified geo-location.
			6. **Change Visualization**: Provide visual representations or maps highlighting areas of significant change to aid interpretation.
			7. **Thresholding and Significance Testing**: Implement thresholding techniques and statistical significance testing to differentiate meaningful changes from noise.
		- non functional requirements
			1. **Scalability**: The model should be able to handle a large number of geographical co-ordinates simultaneously, ensuring scalability for broader applications.
			2. **Model Training Time**: The training time for the model should be reasonable to facilitate timely updates and adjustments.
			3. **Robustness**: The model should be robust against variations in input data quality and environmental conditions.
			4. **Adaptability**: It should be adaptable to different geographical regions or environments, allowing for widespread applicability.
			5. **Computational Efficiency**: The pipeline should be optimized for computational efficiency to handle large datasets and deliver timely results.
			6. **Temporal Resolution**: The pipeline should be capable of handling data with varying temporal resolutions, accommodating different data sources.
	- activities, very general description
- constraints
	- geographical and temporal boundaries
	- assumptions
	- resolution

**Project Scope**
The project will yield three key deliverables, each contributing significantly to the advancement of environmental analysis and decision-making. Firstly, an image classification model will be developed, capable of accurately mapping a specific geographical coordinate to its corresponding land form class. This model will leverage state-of-the-art techniques in remote sensing and machine learning to provide precise categorizations, enabling a detailed understanding of the Earth's surface features. Additionally, a comprehensive change detection pipeline will be established, allowing for a thorough analysis of alterations in a given geo-location over a specified time period. This pipeline will utilize advanced algorithms and processing methodologies to identify and quantify significant changes, offering valuable insights into dynamic environmental phenomena. Lastly, a cloud-based platform will be created to facilitate seamless access to both the image classification model and the change detection pipeline. This platform will offer an intuitive interface, ensuring easy navigation and transparent utilization of these analytical tools. Through these deliverables, the project aims to empower researchers, environmental professionals, and decision-makers with valuable resources for informed and sustainable land management practices.

The requirements for this project serve as the guiding framework that defines the functionalities, constraints, and expectations for the final deliverables. They provide a clear blueprint for the development and implementation of the image classification model, change detection pipeline, and cloud-based platform. These requirements encompass technical specifications, data constraints, and performance benchmarks that will govern the project's development process. By adhering to these requirements, the project aims to ensure that the final deliverables meet the highest standards of accuracy, efficiency, and accessibility, ultimately contributing to the advancement of environmental analysis and decision-making processes.

The requirements are as follows:

1. **Functional Requirements**:
	- **Geographical Mapping**: The model should accurately classify the land form class corresponding to a given geographical co-ordinate.
	- **Multi-class Classification**: It should support classification into multiple land form classes, allowing for a comprehensive assessment.
	- **High Accuracy**: The model should achieve a high classification accuracy to ensure reliable results.
	- **Real-time Processing**: The classification should be performed efficiently, providing results in near real-time for responsive decision-making.
	- **Temporal Analysis**: The pipeline should be capable of analyzing changes over a given period of time for a specified geo-location.
	- **Change Visualization**: Provide visual representations or maps highlighting areas of significant change to aid interpretation.
	- **Thresholding and Significance Testing**: Implement thresholding techniques and statistical significance testing to differentiate meaningful changes from noise.

2. **Non-Functional Requirements**:
	- **Scalability**: The model should be able to handle a large number of geographical co-ordinates simultaneously, ensuring scalability for broader applications.
	- **Model Training Time**: The training time for the model should be reasonable to facilitate timely updates and adjustments.
	- **Robustness**: The model should be robust against variations in input data quality and environmental conditions.
	- **Adaptability**: It should be adaptable to different geographical regions or environments, allowing for widespread applicability.
	- **Computational Efficiency**: The pipeline should be optimized for computational efficiency to handle large datasets and deliver timely results.
	- **Temporal Resolution**: The pipeline should be capable of handling data with varying temporal resolutions, accommodating different data sources.

**Constraints Over the Project**
1. **Geographical and Temporal Boundaries**:
The project operates within defined geographical and temporal boundaries to ensure a focused and manageable scope. Geographically, the study area is delimited to a specific region or set of regions. This constraint helps narrow down the analysis to a manageable scale, allowing for more detailed and accurate land cover assessments. Temporally, the project considers a specific time period or range of time intervals. This restriction ensures that the analysis is conducted within a defined timeframe, enabling the detection of changes and trends over a particular duration. Adhering to these boundaries allows for a targeted and meaningful assessment of land cover dynamics within the designated study area and time frame.

2. **Assumptions**:
The project is built on certain assumptions that influence the methodologies and outcomes. These assumptions may pertain to factors such as data quality, consistency, and the stability of environmental conditions. For instance, it may assume that the remote sensing data used is accurately calibrated and free from significant anomalies. Additionally, assumptions about the persistence of land cover classes over time periods are made, assuming that major changes do not occur due to unforeseen events. It is crucial to document and validate these assumptions to ensure the reliability and validity of the project's findings.

3. **Resolution of Images**:
The resolution of the remote sensing images used in the project is a critical constraint. Higher resolution images provide finer details of the land surface, enabling more precise classification and change detection. However, they may come with increased computational demands and data storage requirements. On the other hand, lower resolution images cover larger areas but may lack the level of detail necessary for certain analyses. Balancing resolution with computational resources is crucial to ensure that the project remains feasible and the chosen images align with the project's objectives.

# Chapter 3: Literature Review



# Chapter 4: Project Dependencies



# Chapter 5: Conclusion and Future Work

# references

- techniques
	- malawi
		- supervised
		- PCC
		- https://repository.up.ac.za/bitstream/handle/2263/71103/Munthali_MultiTemporal_2019.pdf?sequence=1
	- kashmir
		- maximum likelihood
		- https://link.springer.com/article/10.1007/s10708-019-10037-x
	- SVM
		- https://www.sciencedirect.com/science/article/abs/pii/S0303243409000464
	- An assessment of support vector machines for land cover classification
		- https://www.tandfonline.com/doi/pdf/10.1080/01431160110040323?casa_token=v-qQdjqQrzoAAAAA:LBlkOCDdthQsOVeUxEFbrrlmBmCAOYBgc0Gmv-fnwmeBQysd8jIGokbAaEJhjRoOz-GQeQlQePME-L8
	- comparison of classification techniques
		- ANN, SVM, maximum likelihood 
		- https://www.researchgate.net/profile/Brian-Szuster/publication/251509915_A_comparison_of_classification_techniques_to_support_land_cover_and_land_use_analysis_in_tropical_coastal_zones/links/5cdb7baf299bf14d95987aaa/A-comparison-of-classification-techniques-to-support-land-cover-and-land-use-analysis-in-tropical-coastal-zones.pdf
	- land cover 2.0
		- 
		- https://www.tandfonline.com/doi/pdf/10.1080/01431161.2018.1452075
	- LULC hybrid model
		- Hybrid Logistic-Multicriteria Evaluation-Cellular Automata-Markov Model
		- https://www.mdpi.com/2073-445X/12/10/1899
	- land cover classification methods
		- various image based techniques
		- https://www.mdpi.com/2072-4292/9/9/967
	- pune
		- random forest
		- visual and statistical change analysis using ARCGIS
		- https://tiss.edu/uploads/files/Land_Use_Land_Cover_Analysis_of_Indian_Cities.pdf
	- remote sensing image classification review
		- pixel-wise, sub-pixel-wise, object based image classification
		- Spatio-contextual analysis for image classification
		- https://www.tandfonline.com/doi/abs/10.5721/EuJRS20144723
	- multi-temporal landsat classification, italy
		- Neural Networks using JavaNNS
		- maximum likelihood
		- https://www.igi-global.com/gateway/article/137164
	- geotiff
		- https://iopscience.iop.org/article/10.1088/1742-6596/1577/1/012003/pdf
- datasets
	- Operational Land Imager-OLI (kashmir)
		- https://landsat.gsfc.nasa.gov/satellites/landsat-8/spacecraft-instruments/operational-land-imager/
	- Landsat (kashmir)
	- hidden
		- UAE LULC
			- https://dspace.aus.edu/xmlui/handle/11073/25374
		- LandCoverNet Asia
		- Sentinel-2 10m Land Use/Land Cover Time Series

- [x] malawi
- [x] kashmir
- [x] kernel analysis
- [x] svm review
- [x] comparison of classification techniques
- [x] LULC hybrid model
- [x] land cover 2.0
- [ ] *land cover classification methods*
- [ ] *pune*
- [ ] remote sensing image classification review
- [ ] multi-temporal landsat classification, italy
- [ ] geotiff