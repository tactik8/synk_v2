# analyze_records

Python functions to try to identify the schema and fields of an unknown record.

## Requirements
- For each fields of a record:
  - Determine the data type (str, int, float, dict, list, etc)
  - Determine the field schema:
    - Email
    - URL 
    - Phone
    - address
    - monetary
    - first name
    - last name
    - date
- Compile most frequent schemas for each fields across a series of record
- Guess best schema - type
- Guess overall record schema base don available fields.


- Output result in a list of json-ld schema.org records
  - email: https://schema.org/ContactPoint 
  - phone: https://schema.org/ContactPoint
  - url: https://schema.org/WebPage
- Develop test cases for each extractors that includes the following scenarios:
  - Valid, typical input
  - Null input
  - Non-string input
  - Non-existing object in string (for example, testing the phone extractor and no phone number is in the test input string).
  - Multiple object in string
  

## input:
string: the text to extract information from
or list of strings

## output:
json list of structured records

## Description
The function accepts a string or list of string and returns a list of structured records. The information is extracted using regex or python libraries. 

Each record contains a reference to the extractor that has been used. 
For example, the string "Steve can be reached at steve@apple.com" would give:
```
    {
    "@type": schema:contactpoint",
    "schema:email": "steve@apple.com",
    "kraken:extractor": "extract_from_text-email_extractor",
    "kraken:extracteddate": 2020-10-28T20:43:55+00:00
    }
```






