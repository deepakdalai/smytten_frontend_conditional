# smytten_frontend_conditional

## Consider the following as a list of available questions

```
[
    {
        "id": "62b300d7965ea3e2ee01af3b",
        "question_text": "What categories do you buy from online the most?",
        "question_type": "SINGLE_SELECT",
        "next_question_id": "62b300d1965ea3e2ee01af3a",
        "options": [
            "Personal Care",
            "Health and Welness",
            "Beauty and Grooming",
            "Child Care",
            "Electronics"
        ]
    },
    {
        "id": "62b300d1965ea3e2ee01af3a",
        "question_text": "What Categories that you would consider buying online?",
        "question_type": "MULTI_SELECT",
        "next_question_id": "62b300c3965ea3e2ee01af39",
        "options": [
            "Personal Care",
            "Health and Welness",
            "Beauty and Grooming",
            "Child Care",
            "Electronics"
        ]
    },
    {
        "id": "62b300c3965ea3e2ee01af39",
        "question_text": "What Categories that you would not consider buying online?",
        "question_type": "MULTI_SELECT",
        "next_question_id": "62b2df0c965ea3e2ee01af05",
        "options": [
            "Personal Care",
            "Health and Welness",
            "Beauty and Grooming",
            "Child Care",
            "Electronics"
        ]
    },
    {
        "id": "62b2de94965ea3e2ee01af04",
        "question_text": "How would you rate the overall quality of the ptoduct?",
        "question_type": "RANGE_SELECTION",
        "next_question_id": "62a6ef76f4b287a7cb206e23",
        "options": [
            "1",
            "2",
            "3",
            "4",
            "5",
            "6",
            "7",
            "8",
            "9",
            "10"
        ]
    },
    {
        "id": "62a6ef76f4b287a7cb206e23",
        "question_text": "Please select your gender?",
        "question_type": "SINGLE_SELECT",
        "next_question_id": "62a6ef6ef4b287a7cb206e22",
        "options": [
            "MALE",
            "FEMALE",
            "OTHER"
        ]
    },
    {
        "id": "62a6ef6ef4b287a7cb206e22",
        "question_text": "Which city do you live in?",
        "question_type": "SINGLE_SELECT",
        "next_question_id": "62a6ef65f4b287a7cb206e21",
        "options": [
            "Bengaluru",
            "Mumbai",
            "Delhi",
            "Pune",
            "Chennai",
            "Kolkata",
            "Patna"
        ]
    },
    {
        "id": "62a6ef65f4b287a7cb206e21",
        "question_text": "Please select your age group",
        "question_type": "SINGLE_SELECT",
        "next_question_id": null,
        "options": [
            "Less than 15 years",
            "15 - 19 Years",
            "20 - 24 Years",
            "25 - 29 Years",
            "30 - 34 Years",
            "35 - 39 Years",
            "40 - 44 Years",
            "45 - 49 Years",
            "50 - 54 Years",
            "55 + Years"
        ]
    },
    {
        "id": "62a6f7edbf6f5d81231ced5d",
        "question_text": "Which of the following categories have you browsed/ searched/ looked up online in the past 12 months?",
        "question_type": "MULTI_SELECT",
        "next_question_id": "62a6f7d6bf6f5d81231ced5c",
        "options": [
            "Personal Care (Skincare, Haircare, Bodycare)",
            "Men's Grooming",
            "Food and Beverages",
            "Health and Wellness",
            "Makeup",
            "Fragrances",
            "Clothes and Accessories",
            "Baby Care",
            "Electronics",
            "Household Decor and Accessories",
            "Others"
        ]
    },
    {
        "id": "62a6f7edbf6f5d81231ced51",
        "question_text": "Do you buy online?",
        "question_type": "SINGLE_SELECT",
        "next_question_id": "62a6f7d6bf6f5d81231ced5c",
        "options": [
            "Personal Care (Skincare, Haircare, Bodycare)",
            "Men's Grooming",
            "Food and Beverages"
        ]
    },
    {
        "id": "62a6f7edbf6f5d81231ced52",
        "question_text": "Would you consider buying online?",
        "question_type": "SINGLE_SELECT",
        "next_question_id": "62a6f7d6bf6f5d81231ced5c",
        "options": [
            "Personal Care (Skincare, Haircare, Bodycare)",
            "Men's Grooming",
            "Food and Beverages"
        ]
    }
    
    
    
]
```


**-- We need to build a logic builder utility. It results in a logical expression with respect to the questions provided. Following is an example**




1. We start off with a default True condition 

![Screenshot 2022-07-07 at 11 50 45 AM](https://user-images.githubusercontent.com/13539319/177705360-a5530f81-e963-4841-8c77-4206306ee6c3.png)

This results in an expression:
```
{
    "type": "DEFAULT_TRUE",
    "expression" : None
}
```



<br>
2. If we select the type as SIMPLE_EXPRESSION it allows us to select the question to be used in the expression and the expected output value for it to be true. Once created, an expression should be displayed in a minified format.

![Screenshot 2022-07-07 at 11 58 44 AM](https://user-images.githubusercontent.com/13539319/177706489-1f8fddd8-8635-44f5-b0df-0298f7ef960b.png)

The question is one from the list above.
The comparison depends on the question type: SINGLE_SELECT can have EQUAL/NOT_EQUAL, MULTI_SELECT CAN HAVE CONTAINS/DOES_NOT_CONTAIN/IS_EXACTLY
Choices available should be based on the question selected. 
Once done, the condition should minify itself to a small descriptive form. 

![Screenshot 2022-07-07 at 12 02 30 PM](https://user-images.githubusercontent.com/13539319/177707078-00237fc4-72b9-4b96-bfd7-2eb5ef34ed3d.png)

This results the following expression:

```
{
    "type": "SIMPLE_CONDITION",
    "expression" : {
        "question": "62a6ef76f4b287a7cb206e23",
        "question_text": "Please select your gender?"
        "comparisoon": "IS",
        "value": "MALE"
    }
}
```




<br>
3. If the type of the condition selected is AND/OR/NOT EXPRESSION the tool lets adding of complex conditions within it

![Screenshot 2022-07-07 at 12 11 01 PM](https://user-images.githubusercontent.com/13539319/177708529-d747670a-868b-4291-80c8-a9db844dbe80.png)

Compressed, it would look like

![Screenshot 2022-07-07 at 12 11 48 PM](https://user-images.githubusercontent.com/13539319/177708651-bcf5c74a-959c-4948-a87d-faf311d86f53.png)

And the resulting expression would be:

```
{
    "type": "AND_CONDITON",
    "expression" : [
        {
            "type": "SIMPLE_CONDITION",
            "expression" : {
                "question": "62a6ef76f4b287a7cb206e23",
                "question_text": "What is your gender",
                "comparisoon": "IS",
                "value": "MALE"
            }
        },
        {
            "type": "OR_CONDITON",
            "expression" : [
                {
                    "type": "SIMPLE_CONDITION",
                    "expression" : {
                        "question": "62a6f7edbf6f5d81231ced51",
                        "question_text": "Do you buy online",
                        "comparisoon": "IS",
                        "value": "YES"
                    }
                },
                {
                    "type": "SIMPLE_CONDITION",
                    "expression" : {
                        "question": "62a6f7d6bf6f5d81231ced5c",
                        "question_text": "Would you consider buying online",
                        "comparisoon": "IS",
                        "value": "YES"
                    }
                }
            ]
        }
    ]
}
```

Please proviude a solution to the said problem and host it on any platform of your choice. 
The list of questions could be considered to be hardcoded as given above.

The display output any any point in time should be the current expression generated. 


