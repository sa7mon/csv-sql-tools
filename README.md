# CSV SQL Tools

## Dataset 
Source: [Los Angeles Crime Data: 2010 - Present](https://data.lacity.org/A-Safe-City/Crime-Data-from-2010-to-Present/y8tr-7khq)

Downloaded la\_crime.csv. Grabbed mo_codes.pdf, then `pdftotext -layout input.pdf output.txt` and cleaned to make mo_codes.csv.


## Testing Notes

[Idea](https://news.ycombinator.com/item?id=16781294)

### Tools

* [https://harelba.github.io/q](https://harelba.github.io/q)
* [https://github.com/BurntSushi/xsv](https://github.com/BurntSushi/xsv)
* [http://bigbash.it/ - Possibly use to compare with coreutils](http://bigbash.it/)
* [https://github.com/dinedal/textql](https://github.com/dinedal/textql)
* [http://johnkerl.org/miller/doc/](http://johnkerl.org/miller/doc/)
* [https://github.com/dbohdan/sqawk](https://github.com/dbohdan/sqawk)
* [https://csvkit.readthedocs.io/en/1.0.3/](https://csvkit.readthedocs.io/en/1.0.3/)
* [https://pandas.pydata.org/pandas-docs/stable/comparison_with_sql.html](https://pandas.pydata.org/pandas-docs/stable/comparison_with_sql.html)
* [https://github.com/BatchLabs/charlatan#charlatan](https://github.com/BatchLabs/charlatan#charlatan )
* [https://drill.apache.org/docs/querying-plain-text-files/](https://drill.apache.org/docs/querying-plain-text-files/)
* [https://jsvine.github.io/intro-to-visidata/](https://jsvine.github.io/intro-to-visidata/)
* [https://metacpan.org/pod/distribution/App-fsql/bin/fsql](https://metacpan.org/pod/distribution/App-fsql/bin/fsql)
* [https://github.com/noborus/trdsql](https://github.com/noborus/trdsql)
* [https://github.com/tobimensch/termsql](https://github.com/tobimensch/termsql)
* [https://github.com/tjunier/sqawk](https://github.com/tjunier/sqawk)
* [https://github.com/turicas/rows](https://github.com/turicas/rows)
* [https://github.com/wireservice/csvkit](https://github.com/wireservice/csvkit)
* [https://github.com/agershun/alasql](https://github.com/agershun/alasql)
* [https://github.com/dbohdan/structured-text-tools/blob/master/sql-based.md](https://github.com/dbohdan/structured-text-tools/blob/master/sql-based.md)

### Test Cases
* ``` SELECT * FROM la_crime-stats_2010-present.csv WHERE victim_age < 20```
* ```SELECT weapon_description FROM la_crime.csv WHERE weapon_description LIKE '%knife%'```
* select count
* select and order
* JOIN 2 tables
* select multiple where multiple fields (strings = target, number > target > number)
* SUM number field

### To Measure mem/time
* [https://superuser.com/a/767491](https://superuser.com/a/767491)

### Template to generate bash baseline with BigBash
<pre>
CREATE TABLE crimes (dr_number,date_reported,date_occurred,time_occurred,area_id,area_name,reporting_district,crime_code,crime_code_description,mo_codes,victim_age,victim_sex,victim_descent,premise_code,premise_description,weapon_used_code,weapon_description,status_code,status_description,crime_code_1,crime_code_2,crime_code_3,crime_code_4,address,cross_street,location);
MAP crimes to 'la_crime-stats_2010-present.csv' DELIMITER ',';
SELECT Crime_Code_Description FROM crimes;
</pre>