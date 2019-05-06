# Demographic Data

Greenhouse Inclusion ...

## The Demographic Question object

```json
{
  "id": 123,
  "translations": [
    {
      "language": "en",
      "name": "What is your favorite color?"
    }
  ]
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The demographic question's unique identifier |
| translations.language | Only `en` (English) is supported at this time.
| translations.name | The question text
| active | If `false`, the question has been deleted.

## The Demographic Answer Option object

```json
{
  "id": 456,
  "free_form": false,
  "active": true,
  "demographic_question_id": 123,
  "translations": [
    {
      "language": "en",
      "name": "Blue"
    }
  ]
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The demographic answer option's unique identifier |
| translations.language | Only `en` (English) is supported at this time.
| translations.name | The answer option text.
| active | If `false`, the answer option has been deleted.
| free_form | If `true`, the answer option allows free-form user input.
| demographic_question_id | The demographic question for which the answer option belongs to.

## The Demographic Answer object

```json
{
  "id": 51,
  "free_form_text": "12am",
  "application_id": 107594341,
  "demographic_question_id": 25,
  "demographic_answer_option_id": 106,
  "created_at": "2019-04-29T18:46:03.707Z",
  "updated_at": "2019-04-29T18:46:03.707Z"
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The demographic answer's unique identifier |
| free_form_text | If the selected answer option is free-form, this is the value given by the user.  Otherwise `null`.
| application_id | The application for which the demographic question was answered
| demographic_question_id | The demographic question which was answered.
| demographic_answer_option_id | The demographic answer option which was selected.

## GET: List Demographic Questions

List all of an organization's demographic questions.

```shell
curl 'https://harvest.greenhouse.io/v1/demographics/questions'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 123,
    "translations": [
      {
        "language": "en",
        "name": "What is your favorite color?"
      }
    ]
  },
  {
    "id": 456,
    "translations": [
      {
        "language": "en",
        "name": "Pizza or pasta?"
      }
    ]
  }
]
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/demographics/questions`

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
*per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.

<br>
[See noteworthy response attributes.](#the-demographic-question-object)

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.

## GET: Retrieve Demographic Question

Retrieve a demographic question by its `id`.

```shell
curl 'https://harvest.greenhouse.io/v1/demographics/questions/{id}'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
{
  "id": 123,
  "translations": [
    {
      "language": "en",
      "name": "What is your favorite color?"
    }
  ]
}
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/demographics/questions/{id}`


### URL Parameters

Parameter | Description
--------- | -----------
id | ID of the demographic question you want to retrieve.

<br>
[See noteworthy response attributes.](#the-demographic-question-object)


## GET: List Demographic Answer Options

List all of an organization's demographic answer options.

```shell
curl 'https://harvest.greenhouse.io/v1/demographics/answer_options'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 456,
    "free_form": false,
    "active": true,
    "demographic_question_id": 123,
    "translations": [
      {
        "language": "en",
        "name": "Blue"
      }
    ]
  },
  {
    "id": 789,
    "free_form": true,
    "active": true,
    "demographic_question_id": 123,
    "translations": [
      {
        "language": "en",
        "name": "Other"
      }
    ]
  }
]
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/demographics/answer_options`

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
*per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.

<br>
[See noteworthy response attributes.](#the-demographic-answer-option-object)

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.

## GET: List Demographic Answer Options For Demographic Question

List all of the demographic answer options for a demographic question.

```shell
curl 'https://harvest.greenhouse.io/v1/demographics/questions/{id}/answer_options'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 456,
    "free_form": false,
    "active": true,
    "demographic_question_id": 123,
    "translations": [
      {
        "language": "en",
        "name": "Blue"
      }
    ]
  },
  {
    "id": 789,
    "free_form": true,
    "active": true,
    "demographic_question_id": 123,
    "translations": [
      {
        "language": "en",
        "name": "Other"
      }
    ]
  }
]
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/demographics/questions/{id}/answer_options`


### URL Parameters

Parameter | Description
--------- | -----------
id | ID of the demographic question for which you want to retrieve demographic answer options.

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
*per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.

<br>
[See noteworthy response attributes.](#the-demographic-answer-option-object)

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.

## GET: Retrieve Demographic Answer Option

Retrieve a demographic answer option by its `id`.

```shell
curl 'https://harvest.greenhouse.io/v1/demographics/answer_options/{id}'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
{
  "id": 456,
  "free_form": false,
  "active": true,
  "demographic_question_id": 123,
  "translations": [
    {
      "language": "en",
      "name": "Blue"
    }
  ]
}
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/demographics/answer_options/{id}`


### URL Parameters

Parameter | Description
--------- | -----------
id | ID of the demographic answer option you want to retrieve.

<br>
[See noteworthy response attributes.](#the-demographic-answer-option-object)

## GET: List Demographic Answers

List all of an organization's demographic answers.

```shell
curl 'https://harvest.greenhouse.io/v1/demographics/answers'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 123,
    "free_form_text": "12am",
    "application_id": 787,
    "demographic_question_id": 25,
    "demographic_answer_option_id": 106,
    "created_at": "2019-04-29T18:46:03.707Z",
    "updated_at": "2019-04-29T18:46:03.707Z"
  },
  {
    "id": 456,
    "free_form_text": null,
    "application_id": 783,
    "demographic_question_id": 29,
    "demographic_answer_option_id": 109,
    "created_at": "2017-01-29T15:09:46.806Z",
    "updated_at": "2017-01-29T15:09:46.806Z"
  }
]
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/demographics/answers`

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
*per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.

<br>
[See noteworthy response attributes.](#the-demographic-answer-object)

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.

## GET: List Demographic Answers For Application

List all of the demographic answers for an application.

```shell
curl 'https://harvest.greenhouse.io/v1/applications/{id}/demographics/answers'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 123,
    "free_form_text": "12am",
    "application_id": 787,
    "demographic_question_id": 25,
    "demographic_answer_option_id": 106,
    "created_at": "2019-04-29T18:46:03.707Z",
    "updated_at": "2019-04-29T18:46:03.707Z"
  },
  {
    "id": 456,
    "free_form_text": null,
    "application_id": 787,
    "demographic_question_id": 29,
    "demographic_answer_option_id": 109,
    "created_at": "2017-01-29T15:09:46.806Z",
    "updated_at": "2017-01-29T15:09:46.806Z"
  }
]
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/applications/{id}/demographics/answers`


### URL Parameters

Parameter | Description
--------- | -----------
id | ID of the application for which you want to retrieve demographic answers.

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
*per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.

<br>
[See noteworthy response attributes.](#the-demographic-answer-object)

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.

## GET: Retrieve Demographic Answer

Retrieve a demographic answer by its `id`.

```shell
curl 'https://harvest.greenhouse.io/v1/demographics/answers/{id}'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
{
  "id": 123,
  "free_form_text": "12am",
  "application_id": 787,
  "demographic_question_id": 25,
  "demographic_answer_option_id": 106,
  "created_at": "2019-04-29T18:46:03.707Z"
}
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/demographics/answers/{id}`


### URL Parameters

Parameter | Description
--------- | -----------
id | ID of the demographic answer you want to retrieve.

<br>
[See noteworthy response attributes.](#the-demographic-answer-object)