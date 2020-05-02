# Tableau learning notes
----

## Getting Started with Tableau Desktop
[https://elearning.tableau.com/series/developer/getting-started-with-tableau-desktop](https://elearning.tableau.com/series/developer/getting-started-with-tableau-desktop)

### Data connection
- When user dataset is connected to Tableau, the data fields of the dataset are automatically assigned a role & a type.
- A data field can be assigned to a `Dimension` role or a `Measure` role
- The field's data type are assigned as `string`, `integer`, `date` etc. The type can be changed by the user as well. The changes are saved in a Tableau data source(.tds) file as `metadata`
- **In Tableau, quantitative fields are referred to as `Measures` & qualitative fields are referred to as `Dimensions`**
    - Quantitative
    
        Numerical data, provides the measurement for qualitative category, can be used in calculation
    - Qualitative

        Describes or categorizes data, tells you what/when/who, slices the quantitative data 
- **Dimensions & Measures are the building blocks of Tableau charts**