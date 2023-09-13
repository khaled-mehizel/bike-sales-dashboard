# Welcome to my Excel dashboard!
This is a readme that details the process of cleaning a dataset related bike sales in a company. We will also create a dashboard, and extract any insights we can

# Resources and tools used:
- The dataset has been provided by [Alex the Analyst](https://www.youtube.com/@AlexTheAnalyst), he also helped guide me in this project.
- Microsoft Excel, my beloved. So robust and versatile!

# Cleaning and preparing the data
- Checked the data type of every column, keeping the ID as a string since it has no quantitative value.

- Checked the ID column for any duplicate values:
  - Used sorting to sort the IDs from smallest to largest
  - Used **Conditional Formatting** to highlight duplicate values.
  - Used **Remove Duplicates** to remove the duplicate, and had the criteria to be every column just to be safe.
    <p> &nbsp; </p>

- Changed marital status and gender values to the full words to ensure the end user will understand will not have a problem understanding. This is simply done through **Find & Replace**.

- Changed income column to numeric values just in case we need to run any calculations on it.

- Changed age column values into age brackets, our visualizations will be quite messy otherwise. 
  - This is done through an **XLOOKUP()** function. We make a lookup table, first column (lookup array) has the starts and ends of each range, and the second column has the groups themselves (return array).
  - We make both arrays fixed so Auto Fill doesn't break them
  - Match mode is to select lowest matching value.
        
        =XLOOKUP(L2,$P$5:$P$10,$Q$5:$Q$10,,-1)
  - We copy the values into the original age column so they're actual values, not results of a formula.
  

- Used **Data Validation** to ensure columns that only support a few values will not contain anything other than those values, ensuring that our data will stay clean even down the line:
  - Married Status can only be "S" for single or "M" for married.
  - Home Owner column will only accept "Yes" and "No".
  - Ditto with the Purchased Bike column.
  <p> &nbsp; </p>



- Made the values of the Commute Distance numerical and removed the "miles" unit, placing it in the column header instead, to reduce clutter.
  
  - This was done using a **FIND()** function nested in a **LEFT()** function in a new column. The inner function will return the position of the delimiter (it's a space in our case) and the outer function will only keep letters up until the space excluding (thanks to -1)
    
        =LEFT(J2,(FIND(" ", J2)-1))
  
  - Then we let Auto Fill fill the rest of the rows, then copy the values into the original column, so as it'll be filled with values rather than the results of a formula.

  <p> &nbsp; </p>

  # Building the dashboard

- Added the now cleaned data to a pivot table.

# Insights


- Age
- Cars
- commute
- region
