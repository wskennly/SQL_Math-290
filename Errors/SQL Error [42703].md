### SQL Error [42703]

**Task:**\
HW03\
Exercise 4\
One aspect of a primary key is that it is unique. Let's check if the vendor_id could be a candidate to be a primary key by checking if it is unique.

`select count(distinct VendorId) from taxi_data`

**Message:**\
```
SQL Error [42703]: ERROR: column "vendorid" does not exist
  Hint: Perhaps you meant to reference the column "taxi_data.VendorID".
  Position: 24
```

**Screenshot:**\
![](https://github.com/sfnxboy/SQL_Math-290/blob/main/homeworks/images/hw03_03_error_message.png)

**Resolution:**\
DBeaver columns (object) names are case sensitive when specified with double quotes.
Unquoted identifiers are automatically used as lowercase so the correct case sequence must be written with double quotes.
When used with quotes, DBeaver is case sensitive regarding identifier names like table names and column names.
So a common issue that triggers this error is when we use the column name in our commands in any other cases other than that of the original one.
So, DBeaver automatically casts `VendorID` as `vendorid`, which, if you account for case, does not exist in the database.
Conclusively, using the following code resolves this error.

`select count(distinct "VendorId") from taxi_data`
