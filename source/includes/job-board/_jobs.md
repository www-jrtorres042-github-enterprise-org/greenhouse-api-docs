# Jobs

## List jobs

```json
{
  "id":44444,
  "title":"Product Engineer",
  "updated_at":"2013-07-02T19:39:23Z",
  "location":{
    "name":"San Francisco, CA"
  },
  "absolute_url":"http://your.co/careers?gh_jid=444444",
  "internal_job_id":55555,
  "metadata":[]
}
```

Returns the list of all job posts. The `id` field contains the unique identifier for the job post, while `internal_job_id` contains the unique identifier for the job itself. Any job custom fields you have selected to be exposed in the job board API will be shown in the `metadata` attribute.

<aside class="warning">
When submitting a job application, you will use the <code>id</code> field to specify the application's target job post. 
</aside>


### HTTP Request

`GET https://api.greenhouse.io/v1/boards/{job_board_id}/embed/jobs`

### URL Parameters

Parameter | Description
--------- | -----------
job_board_id | The unique URL token for the job board.

### Optional Querystring Parameters

Parameter | Description
--------- | -----------
content | If set to `true`, include the description of each job post.


| Attribute | Data Type | Description |
|-----------|-----------|-------------|
| id | integer | Job ID |
| title | string | Job title |
| updated_at | datetime | Timestamp of last change to this job |
| location.name | string | Job location |
| absolute_url | string | URL of the job post's description page |
| internal_job_id | integer | TODO: what is this?
| metadata | array | Contains custom fields TODO: describe custom field objects

## Retrieve a job

