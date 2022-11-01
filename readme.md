### Program for processing users data

Program reads data from jsonl file, remove duplicates, fills empty fields with default data, writes processed data 
in jsonl files named by date of creations users records in it.

#### Using program

After launch program asks for filepath. By default program expect **_data.jsonl_** in same directory with program module.
In this case no need to enter filepath, just press 'Enter'.

If file with data lies in other directory or have another name -  enter filepath, for example **_documents/some_data.jsonl_**

Result of program work are files, created in directory ***user_data*** (which also created).

Also, program outputs report of made operations.

#### Program work description

Stages:
1. Reading lines from jsonl, convert them into dicts and adding in list (finally list converts to tuple)
2. Removing duplicates. Using temp dict for this. Iterating tuple with users records adding to dict records, where keys are tuples with 'name' and 'time_created' values. On each iteration checking if key exists in dict, and if it is - ignoring adding record. Finally make tuple with unique user records.
3. Making set of all fields. Iterating unique users records for this.
4. Making set of empty fields. Empty field - field that's empty or not present at least at one user.
5. Getting empty fields type for further default value calculating. Iterating set of fields and checking data type in first available not None field for this.
6. Calculating default values for int, float and str fields.
7. Updating dict with all fields with types and default values.
8. Filling all not presented or empty fields with default values. Converting datatime values in int. Making tuple with full users data.
9. Writing records in files, named by records created dates.

If set of empty_fields is empty, stages 5, 6, 7 are skipped.



