# TABLES LIBRARY                                                   
> Author  : Fabio Falcucci (Allanon)  
> Contact : info@a-mc.biz  
> License : Freeware  
> Version : 1.4  
> Release : 30.01.2020  
> Dependancies : Helpers, Easing  

**SUPPORT ME ON PATREON**  : https://www.patreon.com/Allanon71  
**SUPPORT ME WITH PAYPAL** : mailto:hijoe@tin.it

---
 
## DESCRIPTION
Tables library is a collection of functions used to manipulate and process tables, it holds many functions to sort, shift, compare, join and merge tables.

### INDEX

<!-- Start Document Outline -->

* [FUNCTIONS](#functions)
	* [Campare Functions](#campare-functions)
		* [TB.Compare(table1, table2, compare_funcs)](#tbcomparetable1-table2-compare_funcs)
		* [TB.CompareScore(table1, table2, compare_funcs, count, equals)](#tbcomparescoretable1-table2-compare_funcs-count-equals)
	* [Conversion Functions](#conversion-functions)
		* [TB.Convert.String2Table(string, separator)](#tbconvertstring2tablestring-separator)
		* [TB.Convert.Table2String(table, separator)](#tbconverttable2stringtable-separator)
		* [TB.Serialize(table)](#tbserializetable)
		* [TB-Deserialize(txt)](#tb-deserializetxt)
	* [Table Items Related Functions](#table-items-related-functions)
		* [TB.Item.Compare(record1, record2, greater, columns)](#tbitemcomparerecord1-record2-greater-columns)
		* [TB.Item.Exists(table, index)](#tbitemexiststable-index)
		* [TB.Item.Find(table, value, caseSensitive, exactString)](#tbitemfindtable-value-casesensitive-exactstring)
		* [TB.Item.IsNil(table, index)](#tbitemisniltable-index)
	* [Misc Table Functions](#misc-table-functions)
		* [TB.Copy(Source, SkipFunc)](#tbcopysource-skipfunc)
		* [TB.Count(table)](#tbcounttable)
		* [TB.Fill(Source, StartIndex, EndIndex, Value)](#tbfillsource-startindex-endindex-value)
		* [TB.Interpolate(Source, StartIndex, EndIndex, StartValue, EndValue, mode)](#tbinterpolatesource-startindex-endindex-startvalue-endvalue-mode)
		* [TB.Join(table1, table2)](#tbjointable1-table2)
		* [TB.PushDown(table, pos)](#tbpushdowntable-pos)
		* [TB.PushUp(table, pos)](#tbpushuptable-pos)
		* [TB.ReIndex(oldKey, newKey, source)](#tbreindexoldkey-newkey-source)
		* [TB.ReplaceChars(table, chars, replacer, recursive, casing)](#tbreplacecharstable-chars-replacer-recursive-casing)
		* [TB.Set(Source, Changes, ReturnsNew)](#tbsetsource-changes-returnsnew)
		* [TB.ShiftDown(table)](#tbshiftdowntable)
		* [TB.ShiftUp(table)](#tbshiftuptable)
		* [TB.Sort(table, descending, column, associated, type)](#tbsorttable-descending-column-associated-type)
		* [TB.TrimSpaces(table, recursive)](#tbtrimspacestable-recursive)
* [EXAMPLES](#examples)
	* [Comparing Tables](#comparing-tables)
		* [TB.TEST_Compare()](#tbtest_compare)
		* [TB.Compare(table1, table2, compare_funcs)](#tbcomparetable1-table2-compare_funcs-1)
		* [TB.CompareScore(table1, table2, compare_funcs, count, equals)](#tbcomparescoretable1-table2-compare_funcs-count-equals-1)
	* [Interpolation](#interpolation)
	* [Item Comparisons](#item-comparisons)
	* [Finding Table Items](#finding-table-items)
	* [How to merge tables](#how-to-merge-tables)
	* [Push &amp; Pull](#push--pull)
	* [Reindexing a table](#reindexing-a-table)
	* [Replacing strings in table items](#replacing-strings-in-table-items)
	* [Setting Table Items](#setting-table-items)
	* [Shifting Items up and down](#shifting-items-up-and-down)
	* [Sorting Tables](#sorting-tables)

<!-- End Document Outline -->

## FUNCTIONS
### Campare Functions
All comparison functions are mapped in the **TB** root table, using them it is really easy compare tables.

+ TB.Compare(table1, table2, compare_funcs)
+ TB.CompareScore(table1, table2, compare_funcs, count, equals)

---
#### TB.Compare(table1, table2, compare_funcs)
```plaintext
result = TB.Compare(table1, table2, compare_funcs)
    Compare 'table1' and 'table2' and returns TRUE if they are equal.
    Set 'compare_funcs' to TRUE if you want to compare function entries too.
    The function is fully recursive so that all items will be compared.

INPUT
- table1 : The first table to compare
- table2 : The second table to compare
- compare_func : Set to TRUE to compare also function fields

OUTPUT
- result : The result of the comparison: TRUE or FALSE
```
---
#### TB.CompareScore(table1, table2, compare_funcs, count, equals)
```plaintext
score, compared, equals = TB.CompareScore(table1, table2, compare_funcs, count, equals)
    Compare 'table1' and 'table2' and returns a score. Set 'compare_funcs' to
    TRUE if you want to compare function entries too. The comparisons are
    recursive.

INPUT
- table1 : The first table to compare
- table2 : The second table to compare
- compare_func : Set to TRUE to compare also function fields
- count : This argument is used internally to handle recursive calls
- equals : This argument is used internally to handle recursive calls

OUTPUT
- score : The resulting score between 0 and 1 where 1 means identical tables.
- compared : Count of the compared items
- equals : Count of the identical items
```
---
### Conversion Functions
All Table conversion functions are mapped on the TB.Convert table.

+ TB.Convert.String2Table(string, separator)
+ TB.Convert.Table2String(table, separator)
+ TB.Serialize(table)
+ TB.Deserialize(table)

---
#### TB.Convert.String2Table(string, separator)
```plaintext
result = TB.Convert.String2Table(string, separator)
    Converts the given 'string' into a table splitting its items using the
    provided 'separator' as delimiter between each item. Returns the resulting
    table.
    Leading spaces will be trimmed out from the resulting items.

INPUT
- string : The string to split
- separator : The items delimiter (one character)

OUTPUT
- result : The resulting table
```
---
#### TB.Convert.Table2String(table, separator)
```plaintext
result = TB.Convert.Table2String(table, separator)
    Converts all 'table' items into a string using 'separator' as delimiter
    between each item. Returns the resulting string.

INPUT
- table : The table of strings to convert
- separator : The character to use as a separator (one character)

OUTPUT
- result : The resulting string

NOTE
This function is usable on tables of strings with consecutive numeric indexes starting from 0.
```
---
#### TB.Serialize(table)
```plaintext
txt = TB.Serialize(table)
    Serialize the given table transforming all the stored fields into a single string.
    
INPUT
- table : the table we want to convert

OUTPUT
- txt : the serialized table

NOTE
This function is not able to serialize functions.
```
---
#### TB-Deserialize(txt)
```plaintext
table = TB.Deserialize(txt)
    Deserialize a previously serialized table decoding the text 'txt' and rebuilding the original table.
    
INPUT
- txt : a previously serialized table

OUTPUT
- table : the decoded table
```
---
### Table Items Related Functions
All Table's items related functions are mapped on the **TB.Item** table. These functions are used to performs various actions on the table entries.

+ TB.Item.Compare(record1, record2, greater, columns)
+ TB.Item.Exists(table, index)
+ TB.Item.Find(table, value, caseSensitive, exactString)
+ TB.Item.IsNil(table, index)

---
#### TB.Item.Compare(record1, record2, greater, columns)
```plaintext
result = TB.Item.Compare(record1, record2, greater, columns)
    This routine is used to compare two records (tables). The comparison is based
    on one or more fields (indexes), this fields must be specified in the
    'columns' table. 'greater' is a table with booleans and specify what kind of
    comparisons must be performed. If set to TRUE means that the following check will be performed: record1.field is greater then record2.field ?

    This routine supports multilevel comparisons, just supply the field names in
    the 'columns' table and in the right order.

INPUT
- record1 : First record to compare
- record2 : Second record to compare
- greater : One or more comparison specification(s)
- columns : One or more field name(s)

OUTPUT
- result : Returns TRUE if the comparison(s) is/are satisfied.
```
---
#### TB.Item.Exists(table, index)
```plaintext
result = TB.Item.Exists(table, index)
    Returns TRUE if 'index' is not NIL within 'table' otherwise returns FALSE.
    This function is usefull to test if there are defined items within tables.

INPUT
- table : The table you need to check for 'index' key
- index : The index to check

OUTPUT
- result : True if 'index' is defined within 'table'

NOTE
Recently Hollywood have the implemented 'HaveItem()' that has the same purpose of
this function, however TB.Item.Exists() is still usefull because it is
case-sensitive while HaveItem() is not.
```
---
#### TB.Item.Find(table, value, caseSensitive, exactString)
```plaintext
found, index = TB.Item.Find(table, value, caseSensitive, exactString)
    Search in 'table' an item with the value equal to 'value'. The search will be
    performed only on the first table level (subtables will not be scanned).
    'value' can be of any type.

INPUT
- table : Source table
- value : Value to find
- caseSensitive : Set to TRUE for case sensitive searches (strings)
- exactString : Set to TRUE to match for the exact value, in this case casing  
                will be ignored.

OUTPUT
- found : TRUE if a result have been found
- index : Index of the found item

NOTE
Only the first occurence will be returned. For string values you can use pattern
matching conventions as follow:
   * : Matches all characters.
   ? : Matches just a single character.
   # : Matches all numbers.
  [] : Matches one or several characters or a range of characters
```
---
#### TB.Item.IsNil(table, index)
```plaintext
result = TB.Item.IsNil(table, index)
    Returns TRUE if 'index' doesn't exists in 'table' otherwise returns FALSE.
    This function is usefull to test if there are undefined items within tables.

INPUT
- table : The table you need to check for the <index> key
- index : The index/key to check

OUTPUT
- result : TRUE if 'index' is not defined in 'table', otherwise FALSE.
           FALSE will be returned also if 'table' is NIL.

NOTE
Recently Hollywood have the implemented 'HaveItem()' that has the same purpose of
this function, however TB.Item.IsNil() is still usefull because it is
case-sensitive while HaveItem() is not.
```
---
### Misc Table Functions
All Tables related functions are mapped on the **TB** table.

+ TB.Copy(Source, SkipFunc)
+ TB.Count(table)
+ TB.Fill(Source, StartIndex, EndIndex, Value)
+ TB.Interpolate(Source, StartIndex, EndIndex, StartValue, EndValue, mode)
+ TB.Join(table1, table2)
+ TB.Merge(table1, table2, overwrite)
+ TB.PushDown(table, pos)
+ TB.PushUp(table, pos)
+ TB.ReIndex(oldKey, newKey, source)
+ TB.ReplaceChars(table, chars, replacer, recursive, casing)
+ TB.Set(Source, Changes, ReturnsNew)
+ TB.ShiftDown(table)
+ TB.ShiftUp(table)
+ TB.Sort(table, descending, column, associated, type)
+ TB.TrimSpaces(table, recursive)

---
#### TB.Copy(Source, SkipFunc)
```plaintext
result = TB.Copy(source, skipFunc)
   Use this function to copy tables recursively, you can skip functions setting
   'skipFunc' to TRUE.

INPUT
- source : Source table too copy
- skipFunc : Set to TRUE to exclude functions from the copy

OUTPUT
- result : Copied table

NOTE
   Recently Hollywood has implemented its own **CopyTable()** function, that
replaces this one, althougth TB.Copy() could still be usefull to copy all table's
items but function fields.
```
---
#### TB.Count(table)
```plaintext
count = TB.Count(table)
    Return how many entries are stored in 'table'. This function is able to count
any type of table with any type of index.

INPUT
- table : Source table

OUTPUT
- count : Returns the number of items in the table or -1 if an error occurred.

NOTE
   Recently Hollywood has implemented its own **TableItems()** function that
replaces TB.Count().
```
---
#### TB.Fill(Source, StartIndex, EndIndex, Value)
```plaintext
source = TB.Fill(Source, StartIndex, EndIndex, Value)
    Simple function to fill/initialize a table range with a value.

INPUT
- source : The table we want to fill with 'value'
- startIndex : Starting table's index
- endIndex : Ending table's index
- value : The value used to fill the table 'source'

OUTPUT
- source : The modified source table

NOTE
- This function can be used only on tables indexed by consecutive numeric values.
```
---
#### TB.Interpolate(Source, StartIndex, EndIndex, StartValue, EndValue, mode)
```plaintext
source = TB.Interpolate(Source, StartIndex, EndIndex, StartValue, EndValue, mode)
   This function is used to fill the table 'source' with values. The index range
is delimited by 'startIndex' and 'endIndex', the values range is delimited by
'startValue' and 'endValue'. 'mode' defines the interpolation mode, for all
supported modes have a look at the Easing library.

INPUT
- source : The table we want to fill with values
- startIndex : Starting table's index
- endIndex : Ending table's index
- startValue : Starting value
- endValue : Ending value
- mode : Interpolation mode, one easing mode supported by the easing library

OUTPUT
- source : The source table modified

NOTE
   This function can be used only on tables indexed with consecutive numbers.
With this function you can easily precalculate paths for your moving objects.
```
---
#### TB.Join(table1, table2)
```plaintext
table1 = TB.Join(table1, table2)
   Join 'table1' and 'table2', 'table1' will be modified directly adding all
'table2' entries.
This function can be used only on tables with consecutive numeric indexes.

INPUT
- table1 : 'table1' to join
- table2 : 'table2' to join

OUTPUT
- table1 : 'table1' with all the 'table2' entries added at the end
```
---
##### TB.Merge(table1, table2, overwrite)
```plaintext
table1 = TB.Merge(table1, table2, overwrite)
   Adds all 'table2' items to 'table1', note that 'table1'will be directly
modified. 'overwrite' is used to specify if any existing 'table1' item should be
overwritten by 'table2' items or not.

INPUT
- table1 : Target table
- table2 : Table to merge into 'table1'
- overwrite : Set to TRUE to overwrite existing items

OUTPUT
- table1 : The modified table (same as 'table1')

NOTE
   This function is fully recursive.
```
---
#### TB.PushDown(table, pos)
```plaintext
TB.PushUp(table, pos)
   Move the item at position 'pos' from its current position to the bottom and
move all the rest up by one position.

INPUT
- table : Source table
- pos : Index of the item to push down

OUTPUT
- none

NOTES
   This function is only for tables with consecutive numeric indexes starting
from 0.
```
---
#### TB.PushUp(table, pos)
```plaintext
TB.PushUp(table, pos)
   Move the item at position 'pos' from its current position to position 0 (to
the top of the table) and move all the rest down by one position.

INPUT
- table : Source table
- pos : Index of the item to push up

OUTPUT
- none

NOTES
   This function is only for tables with consecutive numeric indexes starting
from 0.
```
---
#### TB.ReIndex(oldKey, newKey, source)
```plaintext
TB.ReIndex(oldKey, newKey, source)
   For the given 'source' table, change the current index with the given column.
A new table will be generated and returned.

INPUT
- oldKey : Old index name, the original index will be stored in this field
- newKey : New index name, the new index will be determined by this field
- source : Source table

OUTPUT
- reindexed : Reindexed table
```
---
#### TB.ReplaceChars(table, chars, replacer, recursive, casing)
```plaintext
table = TB.ReplaceChars(table, chars, replacer, recursive)
   Scans 'table' for each string entry and replaces any occurrencies of 'chars'
with the string 'replacer'. Set 'recursive' to TRUE if you want to scan 'table'
recusively.

INPUT
- table : The table to process
- chars : String to replace with 'replacer'
- replacer : String that will replace 'chars'
- recursive : Set to TRUE to process 'table' recursively
- casing : True for case sensitive (default false)

OUTPUT
- table : Processed source 'table'

NOTE
   Non-string items will be skipped
```
---
#### TB.Set(Source, Changes, ReturnsNew)
```plaintext
result = TB.Set(Source, Changes, ReturnsNew)
   Sets all fields found in the table 'source' with the corrisponding fields in
the table 'changes', returns a new modified table if 'returnsNew' has been set to
TRUE otherwise modify 'source' directly.
The process is recursive.

INPUT
- source : The source table (the one we need to update)
- changes : The table of changes
- returnsNew : Set to TRUE to obtain a new table instead of modify directly the
               'source' table.
OUTPUT
- result : Nil in case of error or the new, updated table
```
---
#### TB.ShiftDown(table)
```plaintext
result = TB.ShiftDown(table)
   Shifts all 'table' items down by one position, the last item will be placed at
the first position.

INPUT
- table : Source table

OUTPUT
- result : Returns TRUE if 'table' was processed correctly

NOTES
   This function is for tables with consecutive numeric indexes starting from 0.
```
---
#### TB.ShiftUp(table)
```plaintext
result = TB.ShiftUp(table)
   Shifts all 'table' items up by one position, the first item will be placed at
the last position.

INPUT
- table : Source table

OUTPUT
- result : Returns TRUE if 'table' was processed correctly

NOTES
   This function is for tables with consecutive numeric indexes starting from 0.
```
---
#### TB.Sort(table, descending, column, associated, type)
```plaintext
sorted = TB.Sort(table, descending, column, associated, type)
   Sort the given 'table' basing the sorting on column(s) specified in the column
field. 'table' must be composed by subtables, like records, and indexed with
numeric values. 'table' will be directly modified while sorting items.
You can set sorting order setting 'descending' to TRUE or FALSE, 'column' can be
a field name or a table width field names we want to use to sort the 'table'.

INPUT
- table : The table we want to sort
- descending : To sort in descending order set this flag to TRUE, if you are are
               sorting the table using multiple columns you have to provide a
               table with one flag for each column.
- column : Column name or a table of strings with columns names used for the
           sorting operation.
- associated : A table holding further tables associated with 'table', the
               subtable items will follow the sorting order of the master table.
               This argument is optional.
- type : Sort method, default = combsort Possible sorting algorhythms are:
          ▪ combsort                       ▪ quicksort
          ▪ circlesort (need ti be fixed)  ▪ bubblesort
          ▪ cocktailsort
          
OUTPUT
- sorted : The source table after the sorting process
```
---
#### TB.TrimSpaces(table, recursive)
```plaintext
table = TB.TrimSpaces(table, recursive)
   Remove from any string entries in the given 'table' any trailing or leading
spaces. The source 'table' will be directly modified.

INPUT
- table : The table we want to process
- recursive : Set to TRUE to process the table recursivly

OUTPUT
- table : Processed source 'table'
```
---
---
## EXAMPLES
### Comparing Tables
In Hollywood you can compare tables using something like this:
```plaintext
Local table1 = { a = 10 }
Local table2 = { a = 10 }
If table1 = table2 Then DebugPrint("table1 and table2 are equal!")
```
However the above comparison will return always **FALSE** because the comparison is made using the table pointers and not their contents.

If you add the following code to the previous example you will understand what I mean:
```plaintext
DebugPrint(table1, table2)
```
As you can see the two tables point to two different memory chunks, the standard comparison will work only on two variables pointing to the same table like this:
```plaintext
Local table1 = { a = 10 }
Local table2 = table1
If table1 = table2 Then DebugPrint("table1 and table2 are equal!")
```
That's the reason because I have developed some functions to compare two tables by their contents.

#### TB.TEST_Compare()
The function `TB.TEST_Compare()` performs a test and shows how you can use the comparing functions :

#### TB.Compare(table1, table2, compare_funcs)
#### TB.CompareScore(table1, table2, compare_funcs, count, equals)
Here is the example. 
First of all we will define two tables composed by subtables (records) with a single small difference between them:
```plaintext
Local tab01 = { { name = "Spiderman", power = "Web, Speed, Strenght" },
                { name = "Thor", power = "Hammer" },
                { name = "Flash", power = "Speed" },
                { name = "Iron Man", power = "Armour" },
                { name = "Iron Man", power = "Weapons" },
                { name = "Hulk", power = "Strenght" } }

Local tab02 = { { name = "Spiderman", power = "Web" },  ; <== Here is the
                                                              differce!
                { name = "Thor", power = "Hammer" },
                { name = "Flash", power = "Speed" },
                { name = "Iron Man", power = "Armour" },
                { name = "Iron Man", power = "Weapons" },
                { name = "Hulk", power = "Strenght" } }
```
Then we will print to the screen the contents of the two tables with a simple loop:
```plaintext
NPrint("TABLE 01 CONTENT")
For Local i = 0 To 5
  Local v = tab01[i]
  NPrint("INDEX : [color=#red]" .. i .. "[/color], NAME : [color=#yellow]" .. v.name .. "[/color], POWER : " .. v.power)
Next
      
NPrint("\nTABLE 02 CONTENT")
For i = 0 To 5
  Local v = tab02[i]
  NPrint("INDEX : [color=#red]" .. i .. "[/color], NAME : [color=#yellow]" .. v.name .. "[/color], POWER : " .. v.power)
Next
NPrint("-> Please note that the two tables have a different value in item 0")
```
And now we will use the comparison functions:
```plaintext
NPrint("\n[b]COMPARING USING TB.Compare()...[/b]")
Local result = TB.Compare(tab01, tab02, False)
  
NPrint(IIf(result, "THE TABLES HAVE THE SAME CONTENTS", 
                   "THE TABLES DOES NOT HAVE THE SAME CONTENTS"))
```
We can also calculate a % score that indicate how much the two tables are equal:
```plaintext
NPrint("\n[b]COMPARING USING TB.CompareScore()...[/b]")
Local score, compared, equals = TB.CompareScore(tab01, tab02, False)
  
NPrint("SCORE          : " .. ToString(Int(Score*10000)/100) .. "%")
NPrint("COMPARED ITEMS : " .. ToString(compared))
NPrint("EQUAL ITEMS    : " .. ToString(equals))
  
NPrint("\nLeft mouse to QUIT.")
  
WaitLeftMouse()
```
---
---
### Interpolation
The function `TB.Interpolate()` is able to fill a table with a range of values so that you can easily precalculate value variations. 
It uses the **Easing library** so that you can make use of any easing function available.

Here is the example, coming with the library, stored in the `TB.TEST_Interpolate()` function.

```plaintext
NPrint("Creating a linear value range from 1 To 50 in 50 items")
Local table = {}
TB.Interpolate(table, 0, 49, 1, 50, "linear")
  
For i = 0 To 49 Do NPrint(PadNum(i, 2) .. " : " .. table[i])
  
NPrint("\nLeft mouse to CONTINUE...")
WaitLeftMouse()
 
Cls
Locate(0, 0)
NPrint("Creating an InSine value range from 5 To 10 in 50 items")
Local table = {}
TB.Interpolate(table, 0, 49, 5, 10, "insine")
  
For i = 0 To 49 Do NPrint(PadNum(i, 2) .. " : " .. table[i])
  
NPrint("\nLeft mouse to CONTINUE...")
WaitLeftMouse()

Cls
Locate(0, 0)
NPrint("Creating an OutElastic value range from 5 To 7 in 30 items")
Local table = {}
TB.Interpolate(table, 0, 29, 5, 7, "outelastic")
  
For i = 0 To 29 Do NPrint(PadNum(i, 2) .. " : " .. table[i])
  
NPrint("\nLeft mouse to QUIT.")
WaitLeftMouse()

```

In the above script you can see how easy is to precalculate values and store them into a table, you just need to provide a destination table, where all the values will be saved, the first and last index positions to use, the starting and ending values and the easing function to use.

---
---
### Item Comparisons
Tables library comes with a very useful function to compare records, with records I mean tables with the same members (fields or columns).

A possible scenario could be that you have a table that works as a database, each entry is a subtable (record) that have exactly the same structure (fields).

With this function you can easily compare them specifying the comparison type and the fields you want to compare, here is the example coming with the library.
```plaintext
Function TB.TEST_ItemCompare()
  ; Compares one or more fields of two records, if the comparison is
  ; between two equal values then the next specified fields will be
  ; checked otherwise the result of the first comparison is returned.
  DebugPrint("TESTING TB.Item.Compare()")
  
  Local record1 = { name = "Spiderman", age = 34, job = "Super Hero" }
  Local record2 = { name = "Batman",    age = 41, job = "Super Hero" }
  
  DebugPrint("Comparing field 'name' : record1.name > record2.name ?")
  DebugPrint(record1.name .. " > " .. record2.name .. " ?")
  Local result = TB.Item.Compare(record1, record2, { True }, { "name" })
  DebugPrint(IIf(result, "YES", "NO"))
  DebugPrint("")
  
  DebugPrint("Comparing field 'age' : record1.age < record2.age ?")
  DebugPrint(record1.age .. " < " .. record2.age .. " ?")
  Local result = TB.Item.Compare(record1, record2, { False }, { "age" })
  DebugPrint(IIf(result, "YES", "NO"))
  DebugPrint("")
  
  DebugPrint("Comparing fields 'job', 'age' : record1.job < record2.job, record1.age < record2.age ?")
  DebugPrint(record1.job .. " < " .. record2.job .. ", " .. record1.age .. " < " .. record2.age .. " ?")
  Local result = TB.Item.Compare(record1, record2, { False, False }, { "job", "age" })
  DebugPrint(IIf(result, "YES", "NO"))
  DebugPrint("\nNOTE:\nThe result is YES because the first comparison is between\ntwo equal values so the check continue to the next specified field.")
  
  
  DebugPrompt("Hit ENTER to quit?")
EndFunction
```
---
---
### Finding Table Items
With `TB.Item.Find()` it's easy to retrieve strings from a table and here is the example coming with the library:
```plaintext
Function TB.TEST_ItemFind()
  DebugPrint("TESTING TB.Item.Find()")
  
  Local items = { "Jhonny", 
                  "Michael", 
                  "Henry", 
                  "Mark", 
                  "Ryan", 
                  "Cody", 
                  "Fred", 
                  "Jim", 
                  "Paul", 
                  "Sam",
                  "*Joe" }
  
  DebugPrint("\nLooking for 'mark' : Case Sensitive : OFF, Exact String : OFF")
  Local found, index = TB.Item.Find(items, "mark", False, False)
  
  If found
    DebugPrint("First result @ " .. index .. " -> " .. items[index])
  Else
    DebugPrint("NOT FOUND!")
  EndIf
  
  DebugPrint("\nLooking for '*a*' : Case Sensitive : OFF, Exact String : OFF")
  Local found, index = TB.Item.Find(items, "*a*", False, False)
  
  If found
    DebugPrint("First result @ " .. index .. " -> " .. items[index])
  Else
    DebugPrint("NOT FOUND!")
  EndIf
  
  DebugPrint("\nLooking for 'Ma*' : Case Sensitive : ON, Exact String : OFF")
  Local found, index = TB.Item.Find(items, "*a*", False, False)
  
  If found
    DebugPrint("First result @ " .. index .. " -> " .. items[index])
  Else
    DebugPrint("NOT FOUND!")
  EndIf
  
  DebugPrint("\nLooking for 'Joe' : Case Sensitive : ON, Exact String : On")
  Local found, index = TB.Item.Find(items, "Joe", False, False)
  
  If found
    DebugPrint("First result @ " .. index .. " -> " .. items[index])
  Else
    DebugPrint("NOT FOUND!")
  EndIf  
  
  DebugPrint("\nLooking for '*Joe' : Case Sensitive : ON, Exact String : On")
  Local found, index = TB.Item.Find(items, "*Joe", False, False)
  
  If found
    DebugPrint("First result @ " .. index .. " -> " .. items[index])
  Else
    DebugPrint("NOT FOUND!")
  EndIf  
  
  DebugPrompt("\n\nHit ENTER to quit?")
EndFunction
```
---
---
### How to merge tables
Sometimes it's useful to have a function able to merge two tables, this function is `TB.Merge()`. This function recursively add all missing items on the source table to the destination table, optionally it can overwrite existing items.

Here is the example provided with the library ecapsulated in the function TB.TEST_Merge().
```plaintext
  Local table1 = { name = "Fabio", surname = "Falcucci", age = 44 }
  Local table2 = { hobby = "Programming", nick = "Allanon", name = "What's up?" }
  
  NPrint("TABLE 1")
  ForEach(table1, NPrint)
  
  NPrint("\nTABLE 2")
  ForEach(table2, NPrint)
  
  Local result = TB.Merge(table1, table2, True)
  NPrint("\nTABLE 1")
  ForEach(table1, NPrint)
  
  NPrint("\nENTER TO QUIT")
  InKeyStr(#ALL)
```

The example does not need further explanations as you can see.

---
---
### Push & Pull
There are two very handy functions in Tables Library, an they are `TB.PushUp(table, position)` and `TB.PushDown(table, position)`.
These functions take the item at the given position and move it, respectively, to the top of the table or to the bottom of the table.

Here is a brief example that comes with the library:
```plaintext
Function TB.TEST_Push()
  
  Local items = { "Jhonny", 
                  "Michael", 
                  "Henry", 
                  "Mark", 
                  "Ryan", 
                  "Cody", 
                  "Fred", 
                  "Jim", 
                  "Paul", 
                  "Sam" }  
  
  Local drawScreen = Function()
                        Cls
                        Locate(0, 0)
                        NPrint("TESTING TB.Item.PushUp(), TB.Item.PushDown()\n")
                        NPrint("TABLE CONTENTS:")
                        For Local i = 0 To 9 Do NPrint(i, items[i])
                        
                        NPrint("\nType your choice and hit ENTER:")
                        NPrint("1) PushUp, 2) PushDown, Q) Quit")
                        
                        Local command = InKeyStr(#ALL)
                        
                        If command = "Q"
                          End
                          
                        ElseIf command = "1"
                          NPrint("\n   Type item number and hit ENTER:")
                          Local i = ToNumber(InKeyStr(#ALL))
                          TB.PushUp(items, i)
                          
                        ElseIf command = "2"
                          NPrint("\n   Type item number and hit ENTER:")
                          Local i = ToNumber(InKeyStr(#ALL))
                          TB.PushDown(items, i)
                          
                        EndIf
                      EndFunction
                      
  Repeat
    drawScreen()
  Forever
  
EndFunction
```
---
---
### Reindexing a table
Sometimes it is very useful to have a function able to reindex a table, reindexing a table is something like this:

**Table contents**

<table>
<thead>
	<tr>
		<th>INDEX</th>
		<th>CONTENT</th>
	</tr>
</thead>
<tbody>
	<tr>
		<td>alpha</td>
		<td>{ name = &quot;Jhon&quot;, type = &quot;Medic&quot; }</td>
	</tr>
	<tr>
		<td>beta</td>
		<td>{ name = &quot;Ted&quot;, type = &quot;Soldier&quot; }</td>
	</tr>
	<tr>
		<td>gamma</td>
		<td>{ name = &quot;Ryan&quot;, type = &quot;Scientist&quot; }</td>
	</tr>
</tbody>
</table>

You want to reindex the table on column name so you want to get:


<table>
<thead>
	<tr>
		<th>INDEX</th>
		<th>CONTENTS</th>
	</tr>
</thead>
<tbody>
	<tr>
		<td>Jhon</td>
		<td>{ code = “alpha”, type = “Medic” }</td>
	</tr>
	<tr>
		<td>Ted</td>
		<td>{ code = “beta”, type = “Soldier”}</td>
	</tr>
	<tr>
		<td>Ryan</td>
		<td>{ name = “gamma”, type = “Scientist}</td>
	</tr>
</tbody>
</table>

Using the `TB.Reindex()` function it is very easy to achieve the result.
```plaintext
Function TB.TEST_ReIndex()
  Local table = { { name = "Spiderman", power = "Web" },
                  { name = "Thor", power = "Hammer" },
                  { name = "Flash", power = "Speed" },
                  { name = "Iron Man", power = "Armour" },
                  { name = "Iron Man", power = "Weapons" },
                  { name = "Hulk", power = "Strenght" } }
                  
  NPrint("TABLE CONTENT")
  For i = 0 To 5
    Local v = table[i]
    NPrint("INDEX : [color=#red]" .. i .. "[/color], NAME : [color=#yellow]" .. v.name .. "[/color], POWER : " .. v.power)
  Next

  NPrint("\nReindexing by power")
  Local table = TB.ReIndex("id", "power", table)
  For i, v In Pairs(table)
    NPrint("INDEX : [color=#red]" .. i .. "[/color], NAME : [color=#yellow]" .. v.name .. "[/color], ID : " .. v.id)
  Next
  
  NPrint("\nReindexing by name")
  Local table = TB.ReIndex("power", "name", table)
  For i, v In Pairs(table)
    NPrint("INDEX : [color=#red]" .. i .. "[/color], POWER : [color=#yellow]" .. v.power .. "[/color], ID : " .. v.id)
  Next
  NPrint("[b][color=#blue]>> ONE RECORD <IRON MAN> AS BEEN DELETED <<[/color][/b]")

  NPrint("\nLeft mouse to QUIT.")
  
  WaitLeftMouse()
  
EndFunction
```
If you run the example you can see that it could be a problem with items with the same index because they are overwritten, infact if you have:
```plaintext
INDEX |	CONTENT
------+-------------------------------------
alpha |	{ name = “Jhon”, type = “Medic” }
beta  |	{ name = “Jhon”, type = “Soldier”}
```
And you reindex the table on the 'name' column you will get only one entry:
```plaintext
INDEX |	CONTENT
------+-------------------------------------
Jhon  |	{ code = “beta”, type = “Soldier”}
```

That's because the index must be unique.

---
---
### Replacing strings in table items
`TB.ReplaceChars()` is a very powerful function that scan a table and replaces any occurancies of a string with another. The process can optionally be fully recursive.
```plaintext
Function TB.TEST_ReplaceChars()
  Local table = { { name = "Spiderman", power = "Web" },
                  { name = "Thor", power = "Hammer" },
                  { name = "Flash", power = "Speed" },
                  { name = "Iron Man", power = "Armour" },
                  { name = "Iron Man", power = "Weapons" },
                  { name = "Hulk", power = "Strenght" } }
                  
  NPrint("TABLE CONTENT")
  For i = 0 To 5
    Local v = table[i]
    NPrint("INDEX : [color=#red]" .. i .. "[/color], NAME : [color=#yellow]" .. v.name .. "[/color], POWER : " .. v.power)
  Next

  NPrint("\nLOCATING AND REPLACING ALL <man> WITH <woman>")
  TB.ReplaceChars(table, "man", "woman", True, False)
  
  NPrint("\nTABLE CONTENT")
  For i = 0 To 5
    Local v = table[i]
    NPrint("INDEX : [color=#red]" .. i .. "[/color], NAME : [color=#yellow]" .. v.name .. "[/color], POWER : " .. v.power)
  Next
  
  NPrint("\nLeft mouse to QUIT.")
  
  WaitLeftMouse()
  
EndFunction
```
---
---
### Setting Table Items
Here is an example on how you can use a very powerful table manipulation function: `TB.Set()`.

The purpose of this function is to set recursively a destination table with the items on a source table. If destination table have an item found on the source table it will be overwritten.

This is particularly useful if you have large tables and you need to set only a subset.
```plaintext
Function TB.TEST_Set()
  Local table = { name     = "Fabio Falcucci", 
                  age      = 49, 
                  hobbies  = "music, programming, videogames, science",
                  job      = "programmer",
                  gender   = "male",
                  location = "Italy",
                  aspect   = 
                    { eyes   = "brown",
                      height = "1.75m",
                      hair   = "few",
                      weight = "too much" },
                  }
                  
  NPrint("\nTABLE CONTENT")
  For i, v In Pairs(table)
    If GetType(v) = #TABLE
      NPrint("[Color=#GREEN]" .. i .. " : [/color] sub-table")
      For ii, vv In Pairs(v)        
        NPrint("   [Color=#GREEN]" .. ii .. " : [/color]" .. vv)
      Next
    Else
      NPrint("[Color=#GREEN]" .. i .. " : [/color]" .. v)
    EndIf
  Next
  
  NPrint("\nChanging contents using TB.Set()")
  NPrint("In red all changed items.\n")
  TB.Set(table, { job = "[color=#RED]programmer, consultant[/color]", 
                  name = "[color=#RED]Fabio Falcucci (Allanon)[/color]",
                  aspect = { hair = "[color=#RED]none[/color]" }
                  }, 
                  False)
  
  NPrint("\nUPDATED TABLE CONTENT")
  For i, v In Pairs(table)
    If GetType(v) = #TABLE
      NPrint("[Color=#YELLOW]" .. i .. " : [/color] sub-table")
      For ii, vv In Pairs(v)        
        NPrint("   [Color=#YELLOW]" .. ii .. " : [/color]" .. vv)
      Next
    Else
      NPrint("[Color=#YELLOW]" .. i .. " : [/color]" .. v)
    EndIf
  Next

  NPrint("\nLeft mouse to QUIT.")
  
  WaitLeftMouse()
  
EndFunction
```
The above example is a very simple one, but try to think about a project where you don't know in advance the source and destination table structure to see its utility.

---
---
### Shifting Items up and down
There are two functions, `TB.ShiftUp()` and `TB.ShiftDown()` that allow to shift table items, here is a brief example provided with the library:
```plaintext
Function TB.TEST_Shift()
  EscapeQuit(True)
  
  ; I've added spaces to simplify the output formatting
  Local items1 = { "Jhonny ", "Michael", "Henry  ", "Mark   ", "Ryan   ", "Cody   ", "Fred   ", "Jim    ", "Paul   ", "Sam    " }  
  Local items2 = CopyTable(items1)
  
  Repeat
    Cls
    Locate(0, 0)
    NPrint("ESC to Quit")
    NPrint("")
    NPrint("ShiftUp   ShiftDown")
    NPrint("-------------------")
    For i = 0 To 9 Do NPrint(i, items1[i], items2[i])
    NPrint("")
    TB.ShiftUp(items1)
    TB.ShiftDown(items2)
    Wait(150, #MILLISECONDS)
  Forever
  
EndFunction
```
---
---
### Sorting Tables
You can sort tables by one or more fields using the `TB.Sort()` function. Here is a simple example that shows how you can use sort your tables using various sorting methods :
```
Function TB.TEST_Sort()
  Local table = { { name = "Spiderman", power = "Web" },
                  { name = "Thor"     , power = "Hammer" },
                  { name = "Flash"    , power = "Speed" },
                  { name = "Iron Man" , power = "Armour" },
                  { name = "Iron Man" , power = "Weapons" },
                  { name = "Hulk"     , power = "Strenght" } }
                  
  NPrint("TABLE CONTENT")
  For i = 0 To 5
    Local v = table[i]
    NPrint("[color=#yellow]" .. v.name .. "[/color] " .. v.power)
  Next
  
  NPrint("\nSORTED by Name (descending order)")
  TB.Sort(table, True, "name", Nil, "quicksort")
  For i = 0 To 5
    Local v = table[i]
    NPrint("[color=#yellow]" .. v.name .. "[/color] " .. v.power)
  Next
  
  NPrint("\nSORTED by Power (ascending order)")
  TB.Sort(table, False, "power", Nil, "combsort")
  For i = 0 To 5
    Local v = table[i]
    NPrint("[color=#yellow]" .. v.name .. "[/color] " .. v.power)
  Next
  
  NPrint("\nSORTED by Name & Power (descending/descending order)")
  TB.Sort(table, { True, True }, { "name", "power" }, Nil, "quicksort")
  For i = 0 To 5
    Local v = table[i]
    NPrint("[color=#yellow]" .. v.name .. "[/color] " .. v.power)
  Next

  NPrint("\nSORTED by Name & Power (descending/ascending order)")
  TB.Sort(table, { True, False }, { "name", "power" }, Nil, "quicksort")
  For i = 0 To 5
    Local v = table[i]
    NPrint("[color=#yellow]" .. v.name .. "[/color] " .. v.power)
  Next
  
  NPrint("\nLeft mouse to QUIT.")
  
  WaitLeftMouse()
EndFunction
```
---
