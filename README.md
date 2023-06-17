# TCL_Workshop_Rakshith
Complete Documentation of vsd TCL Workshop course.

## Day_1

**Key Points**
- Create a TCL box interface to get the output table format. 
- Convert all inputs to format1 and SDC format and pass it to yosys file.
- Convert all inputs to format1 and SDC to format2 (required for Opentimer) and pass it to Opentimer.

**Command to make the file accessible**
~~~
chmod 777 rakshith 
~~~

**General Scenarios**
- When user hasn't provided .csv file as input
- When user specifies a .csv file that doesn't exist
- To code -help to find out usage


**Creating a command rakshith and pass .csv**

![image](https://github.com/rakshith0609/TCL_Workshop_Rakshith/assets/112770970/c5b1f271-903d-4b5b-9f12-1fde2b2c1978)


------


## Day_2

**Conversion of .csv file into matrix format**
![image](https://github.com/rakshith0609/TCL_Workshop_Rakshith/assets/112770970/c7befefc-6294-4d6b-95cc-bfc09de6c11d)

**Code Snippet for the same**
~~~
set filename [lindex $argv 0]
	package require csv
	package require struct::matrix
	struct::matrix m
	set f [open $filename]
	csv::read2matrix $f m , auto
	close $f
	set columns [m columns]
	m add columns $columns
	m link my_arr
	set num_of_rows [m rows]
	set i 0
	while {$i < $num_of_rows} {
		 puts "\nInfo: Setting $my_arr(0,$i) as '$my_arr(1,$i)'"
		 if {$i == 0} {
			 set [string map {" " ""} $my_arr(0,$i)] $my_arr(1,$i)
		 } else {
			 set [string map {" " ""} $my_arr(0,$i)] [file normalize $my_arr(1,$i)]
		 }
		  set i [expr {$i+1}]
	}
 ~~~
 
 **If directory doesn't exist, displays this error message:**
 
 ![image](https://github.com/rakshith0609/TCL_Workshop_Rakshith/assets/112770970/2870509d-cf04-4319-b061-37c92331f405)

**When directory exists, it passes the arguement**

![image](https://github.com/rakshith0609/TCL_Workshop_Rakshith/assets/112770970/7ba30f6f-c1a1-44f1-943f-037ad94af5d8)

