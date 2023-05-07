# TinyML for the Detection of Plant Diseases in Resource-Constrained Areas within West Africa
Undergraduate Thesis <br />
Ashesi University <br />
Completed April 2023

### Abstract
Most of West Africa's rural farmers do not have access to smartphones, stable internet connection or electricity - additionally, they typically have low English proficiency and technological competency. Subsistence farmers in the Akuapim-South Municipal Assembly of Ghana face the same reality but have to face the added problem of limited access to agricultural extension agents who provide plant disease identification services. While many technological solutions to plant disease identification exist, they are cloud-based and, thus, require resources not accessible to a rural farmer in this population.  This study investigates the use of Tiny Machine Learning (TinyML), a subset of computing which facilitates low latency, low power, low cost, and high privacy computing. While this technology has been proven comparable to cloud-based ML, there is a lack of research regarding its applicability both to the area of plant disease identification and the West African context. In order to fill this gap, this study develops a TinyML-based system and compares it to an existing mobile plant disease identification mobile app. The results of this study suggest TinyML is a comparable tool in terms of performance to cloud-based solutions and a better tool in terms of resource consumption. Additionally, a combination of cloud-based model training and on-device inference is suggested as the most suitable ML set-up to address this problem for this particular population.  This study also identifies some areas for improvement and further research, such as the creation of a context-specific dataset, expanded experiment scope and use of alternative TinyML development platforms. 

### Data Used
FrontiersIn Cassava Leaf Disease Image Dataset ([Link to dataset in .ZIP format](https://scholarsphere.psu.edu/resources/215d1acd-2c1e-440b-a27a-03d212761ef7))

Class distribution after dataset formatting:
| Category                          | Number of examples     | Percentage of Total  |
| --------------------------------- | ----------------------:| --------------------:|
| Cassava Brown Streak Disease      | 398                    | 26%                  |
| Cassava Mosaic Disease            | 388                    | 26%                  |
| Healthy                           | 353                    | 23%                  | 
| Other                             | 378                    | 25%                  |
| **Total**                         | **1517**               | **100%**             |

### Technologies Used
1. Jupyter Notebook
2. [Edge Impulse](https://www.edgeimpulse.com/)
3. Arduino IDE v2
