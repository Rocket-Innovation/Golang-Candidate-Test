# Golang-Candidate-Test
Golang test for candidates who apply to Rocket-innovation

## Sumarize covid data
Create the API for summarizing COVID records data from https://raw.githubusercontent.com/Rocket-Innovation/Golang-Candidate-Test/refs/heads/main/files/covid-cases.json

### Requirement
- The project must provide the endpoint `/covid/summary` with received query parameters
- The endpoint must return the data in JSON format
The returned JSON must contain the number of occurrences of each value for the query parameters. For the string occurrences, the JSON must be sorted alphabetically.
- If the query parameters query the qualitative data and provide the range of the data, it must provide those ranges and the total of data in each range. If there is no data put it in `N/A`

### Requirement2
- The project must use go module
- The project must use gin or fiber framework
- please note that a blank string is not equal to null

### Bonus point
- Writing test for the business logic

# Test case
this example is for this query: `/covid/summary?Province=[]`
result
```
{
    "Province": {
        "Amnat Charoen": 17,
        "Ang Thong": 36,
        "Bangkok": 27,
        .
        .
        .
        "Yasothon": 26
    }
}
```
this example is for this query: `/covid/summary?Age=[30,60]`
result
```
{
    "Age": {
        "0-30": 602,
        "31-60": 607,
        "61+": 769,
        "N/A": 22
    }
}
```
this example is for this query: `/covid/summary?Age=[]`
result
```
{
    "Age": {
        "0": 20,
        "1": 25,
        "10": 25,
        .
        .
        .
        "99": 28
        "N/A": 22
    }
}
```
this example is for this query: `/covid/summary?GenderEn=[]`
result
```
{
    "GenderEn": {
        "Female": 674,
        "Male": 682,
        "N/A": 644
    }
}
```
this example is for this query: `/covid/summary?GenderEn=[]&Age=[30,60]`
result
```
{
    "GenderEn": {
        "Female": 674,
        "Male": 682,
        "N/A": 644
    },
    "Age": {
        "0-30": 602,
        "31-60": 607,
        "61+": 769,
        "N/A": 22
    }
}
```
this example is for this query: `/covid/summary?Province=[]&Age=[30,60]`
result
```
{
    "Province": {
        "Amnat Charoen": 17,
        "Ang Thong": 36,
        "Bangkok": 27,
        .
        .
        .
        "Yasothon": 26
    },
    "Age": {
        "0-30": 602,
        "31-60": 607,
        "61+": 769,
        "N/A": 22
    }
}
```
