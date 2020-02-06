---
title: API Reference

<!--language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - java
  - python
-->

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the EasyYU open data API.

# Authentication

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: testtesttest`

<aside class="notice">
You must replace <code>testtesttest</code> with your personal API key.
</aside>

# Courses 

## Get courses by subject

This endpoint retrieves courses based on subject parameters.

### HTTP Request

`GET http://example.com/api/v1/courses/<subject>`

Parameter | Description
--------- | -----------
Subject | Get all courses for a given subject code (ie. EECS, MATH)


## Get courses by query

Search for courses based on given parameters.

### Query Parameters

Parameter | Optional | Description
--------- | ------- | -----------
subject, course_number | yes | Get course info with subject and course number (ie. EECS 1019)
faculty | yes | List all courses under a given faculty (ie. LE, HH, etc.) 


## Get courses by instructor

> Example response:

```json
[
  {
    "faculty": "LE",
    "subject": "EECS",
    "course_number": "4101",
    "name": "Advanced Data Structures",
    "description": "Amortized and worst-case analysis of data structures. Data structuring paradigms: self-adjustment and persistence. Lists: self-adjustment with the move-to-front heuristic. Search trees: splay trees, finger search trees. Heaps: skew heaps, Fibonacci heaps. Union-find trees. Link-and-cut trees. Multidimensional data structures and dynamization. Integrated with: GS/CSE 5101 3.00. Prerequisites: cumulative GPA of 4.50 or better over all major EECS courses (without second digit \"5\"); LE/EECS 2030 3.00 or LE/EECS 1030 3.00; LE/EECS 2001 3.00, LE/EECS 3101 3.00. Previously offered as: LE/CSE 4101 3.00. PRIOR TO SUMMER 2013: SC/CSE 4101 3.00.",
    "credit": "3.00",
    "instruction_language": "English",
    "offerings": [
      {
        "term": "W",
        "section": "Section M",
        "course_info": [
          {
            "type": "LECT 01",
            "meet_info": [
              {
                "day": "T",
                "start_time": "13:00",
                "duration": "90",
                "location": "CC 108"
              },
              {
                "day": "R",
                "start_time": "13:00",
                "duration": "90",
                "location": "CC 108"
              }
            ],
            "cat": [
              "F19A01"
            ],
            "instructor": [
              "Patrick Dymond"
            ],
            "notes": [
              "$5.00 - Course Materials"
            ]
          }
        ]
      }
    ],
    "course_url": "https://w2prod.sis.yorku.ca/Apps/WebObjects/cdm.woa/wa/crsq?fa=LE&sj=EECS&cn=4101&cr=3.00&ay=2019&ss=FW"
  }
]
```

This endpoint retrieves courses taught by the requested instructor query.

### HTTP Request

`GET http://example.com/api/v1/courses/search?q=<instructor>`

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

# Subject

## Get All Subjects

> Response should look like this:

```json
[
  {
    "subject": "ACTG",
    "name": "Accounting"
  },
  {
    "subject": "ADLW",
    "name": "Administrative Law"
  },
  ...
  {
    "subject": "YSDN",
    "name": "York/Sheridan Design"
  }
]
```

Retrieves all subject codes and its respective name

### HTTP Request
`GET http://example.com/api/v1/subject`

# Faculty

## Get All Faculty

```json
[
  {
    "code": "HH",
    "name": "Faculty of Health"
  },
  {
    "code": "SB",
    "name": "Schulich School of Business"
  },
  ...
  {
    "code": "ES",
    "name": "Faculty of Environmental Studies"
  }
]
```

Returns list of all faculty present at York University.

### HTTP Request
`GET http://example.com/api/v1/faculty`


## Get Specific Faculty

```json
{
  "code": "LE",
  "name": "Lassonde School of Engineering"
}
```
Returns information about a specific faculty.

### HTTP Request
`GET http://example.com/api/v1/faculty/<Faculty>`

### URL Parameters

Parameter | Description
--------- | -----------
Faculty | Faculty code to retrieve both the code and full name of the faculty.

