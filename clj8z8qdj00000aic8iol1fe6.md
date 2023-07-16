---
title: "Linux commands for awk"
datePublished: Fri Jun 23 2023 19:40:33 GMT+0000 (Coordinated Universal Time)
cuid: clj8z8qdj00000aic8iol1fe6
slug: linux-commands-for-awk
tags: devops, trainwithshubham

---

![Using AWK command in Bash on Linux | A Cloud Guru](https://res.cloudinary.com/acloud-guru/image/fetch/c_thumb,f_auto,q_auto/https://acg-wordpress-content-production.s3.us-west-2.amazonaws.com/app/uploads/2020/06/full-colored-dark-264x300.jpg align="center")

1. **Printing and Filtering:**
    
    * `awk '{print}' file`: Print the entire file.
        
    * `awk '/pattern/ {print}' file`: Print lines matching a pattern.
        
    * `awk '{print $1, $2}' file`: Print specific columns (e.g., 1st and 2nd columns).
        
    * `awk '$3 > 10 {print}' file`: Print lines where the 3rd column is greater than 10.
        
    * `awk 'length($0) > 80 {print}' file`: Print lines longer than 80 characters.
        
        1. **Variables and Arithmetic:**
            
            * `awk '{sum += $1} END {print sum}' file`: Calculate and print the sum of values in a column.
                
            * `awk '{avg += $1; count++} END {print avg/count}' file`: Calculate and print the average of values in a column.
                
            * `awk '{if ($1 > 10) print $1; else print "N/A"}' file`: Use conditional statements to control printing.
                
            * `awk '{total = $2 * $3; print total}' file`: Perform arithmetic operations on columns.
                
        2. **Formatting and Output:**
            
            * `awk '{printf "%-10s %5d\n", $1, $2}' file`: Format and print columns with specific widths.
                
            * `awk '{print NR, $0}' file`: Print line numbers with each line.
                
            * `awk 'BEGIN {FS=","; OFS="\t"} {print $1, $2}' file`: Set field separators (input and output) to customize data processing.
                
        3. **Regular Expressions:**
            
            * `awk '/^pattern/ {print}' file`: Print lines starting with a specific pattern.
                
            * `awk '/pattern$/ {print}' file`: Print lines ending with a specific pattern.
                
            * `awk '/pattern1/ && /pattern2/ {print}' file`: Print lines matching multiple patterns.
                
                ![Rhonda Byrne Quote: “There is always something to be grateful for.”](https://quotefancy.com/media/wallpaper/3840x2160/1793104-Rhonda-Byrne-Quote-There-is-always-something-to-be-grateful-for.jpg align="left")