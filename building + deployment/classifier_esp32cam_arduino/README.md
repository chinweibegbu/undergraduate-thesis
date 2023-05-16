# Data Processing

## Dataset Overview
The table below shows the original class distribution from the [FrontiersIn Cassava Leaf Disease Image Dataset](https://scholarsphere.psu.edu/resources/215d1acd-2c1e-440b-a27a-03d212761ef7).

<center>

| Category                          | Number of examples     | Percentage of Total  |
| --------------------------------- | ----------------------:| --------------------:|
| Cassava Brown Streak Disease      | 398                    | 17%                  |
| Cassava Mosaic Disease            | 388                    | 17%                  |
| Cassava Brown Leaf Spot           | 386                    | 17%                  |
| Cassava Green Mite Damage         | 309                    | 13%                  |
| Cassava Red Mite Damage           | 415                    | 18%                  |
| Healthy                           | 353                    | 15%                  | 
| **Total**                         | **2249**               | **100%**             |

</center>

## File Details
The `data-processing.ipynb` file in this folder assumes that you have *not* made any changes to the original [Frontierin dataset](https://scholarsphere.psu.edu/resources/215d1acd-2c1e-440b-a27a-03d212761ef7) used to view the original dataset from the link  is divided into three sections:
1. **Data Viewing**: This section will use the `matplotlib` and `PIL` libraries to view a sample image along with its dimensions
2. **Data Processing**: This section creates a folder for the new "Other" category and combines the unneeded disease folders
3. **Data Processing (Ver. 2)**: This section creates a new "OtherMini" folder and reduces the size of the "Other" folder to make the processed dataset balanced

## Steps
1. Download the [FrontiersIn Cassava Leaf Disease Image Dataset](https://scholarsphere.psu.edu/resources/215d1acd-2c1e-440b-a27a-03d212761ef7)
2. Unzip the dataset folder
3. Copy the `data-processing.ipynb` into the same folder as the `Cassava_paper_dataset` folder
4. Run the cells up to the end of the `Data Processing` section if you want to end at creating an "Other" folder
5. Alternatively, run all the cells to created a balanced dataset which should have the following class distribution:

<center>

| Category                          | Number of examples     | Percentage of Total  |
| --------------------------------- | ----------------------:| --------------------:|
| Cassava Brown Streak Disease      | 398                    | 26%                  |
| Cassava Mosaic Disease            | 388                    | 26%                  |
| Healthy                           | 353                    | 23%                  | 
| Other                             | 378                    | 25%                  |
| **Total**                         | **1517**               | **100%**             |

</center>
