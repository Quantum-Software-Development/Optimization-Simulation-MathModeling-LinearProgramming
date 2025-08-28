
# Exercise in  Excel to Find Final Solution Using Hungarian Method   


### Problem Statement

 In a factory there are 4 different cutting machines. 4 tasks must be processed daily. 
 Tasks can be performed on any of the machines. The table below represents the processing times, in hours, of each task on each of the machines.
 Designate a machine for each task in such a way as to minimize the total time spent.

<br>

## Step 1: Input the Cost Matrix in Excel  

<br>


Enter the processing times (hours) in a 4x4 grid (cells `B2:E5`):  

<br>

| Machine \ Task | Task 1 | Task 2 | Task 3 | Task 4 |  
|----------------|--------|--------|--------|--------|  
| **Machine 1**  | 5      | 24     | 13     | 7      |  
| **Machine 2**  | 10     | 25     | 3      | 23     |  
| **Machine 3**  | 28     | 9      | 8      | 5      |  
| **Machine 4**  | 10     | 17     | 15     | 3      |  


<br><br>


## Step 2: Row Reduction  

<br>

Subtract the minimum value in each row from all elements in that row.  

<br>

1. **Row Minimums**:  
   - **Machine 1**: `=MIN(B2:E2)` → **5**  
   - **Machine 2**: `=MIN(B3:E3)` → **3**  
   - **Machine 3**: `=MIN(B4:E4)` → **5**  
   - **Machine 4**: `=MIN(B5:E5)` → **3**  


   <br>

2. **Row-Reduced Matrix** (cells `G2:J5`):  
   - **Machine 1**: `=B2-$F2` → `0, 19, 8, 2`  
   - **Machine 2**: `=B3-$F3` → `7, 22, 0, 20`  
   - **Machine 3**: `=B4-$F4` → `23, 4, 3, 0`  
   - **Machine 4**: `=B5-$F5` → `7, 14, 12, 0`  



<br><br>


## Step 3: Column Reduction  

<br>

Subtract the minimum value in each column from all elements in that column.  

<br>

1. **Column Minimums** (cells `G6:J6`):  
   - **Task 1**: `=MIN(G2:G5)` → **0**  
   - **Task 2**: `=MIN(H2:H5)` → **4**  
   - **Task 3**: `=MIN(I2:I5)` → **0**  
   - **Task 4**: `=MIN(J2:J5)` → **0**  

   <br>

2. **Column-Reduced Matrix** (cells `K2:N5`):  
   - **Task 1**: `=G2-$G$6` → `0, 7, 23, 7`  
   - **Task 2**: `=H2-$H$6` → `15, 18, 0, 10`  
   - **Task 3**: `=I2-$I$6` → `8, 0, 3, 12`  
   - **Task 4**: `=J2-$J$6` → `2, 20, 0, 0`  


<br><br>



## Step 4: Cover Zeros with Minimum Lines  

<br>

Use Excel’s **conditional formatting** to highlight zeros. Draw lines to cover all zeros:  

<br>

- **Row 1**: Task 1 (0)  
- **Row 2**: Task 3 (0)  
- **Row 3**: Task 4 (0)  
- **Row 4**: Task 4 (0)  

**Result**: 4 lines (equal to matrix size), so proceed to assignment.  

<br><br>

## Step 5: Optimal Assignment  

<br>

Assign tasks to machines where zeros are located:  

<br>

| Machine  | Task Assigned | Time |  
|----------|---------------|------|  
| **1**    | Task 1        | 5    |  
| **2**    | Task 3        | 3    |  
| **3**    | Task 4        | 5    |  
| **4**    | Task 2        | 17   |  

**Total Time**: \(5 + 3 + 5 + 17 = 30\)  


<br><br>


