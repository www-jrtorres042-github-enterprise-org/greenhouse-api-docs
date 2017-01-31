## Job Post deleted

This web hook fires when a job post is deleted.  This occurs when the delete link is clicked on a job post. Only job posts that are not live may be deleted. This will not fire if a job itself is deleted; a job being deleted implies all of its posts have been deleted with them.

```json
{
  "action": "job_post_deleted",
  "payload": {
    "job_post": {
      "id": 258341,
      "job_id": 284999,
      "title": "Software Engineer",
      "location": "Dallas",
      "content": "<p>A pretty interesting job post!</p>",
      "updated_at": "2017-01-19T20:01:53.146Z",
      "internal_content": null,
      "questions": [
        {
          "required": false,
          "private": false,
          "label": "LinkedIn Profile",
          "type": "input_text",
          "values": []
        },
        {
          "required": false,
          "private": false,
          "label": "Website",
          "type": "input_text",
          "values": []
        },
        {
          "required": false,
          "private": false,
          "label": "How did you hear about this job?",
          "type": "input_text",
          "values": []
        },
        {
          "required": true,
          "private": true,
          "label": "Are you a cool engineer?",
          "type": "multi_value_single_select",
          "values": [
            "Yes",
            "No",
            "As a cucumber"
          ]
        }
      ],
      "external": true,
      "internal": false,
      "live": false
    }
  }
}
```
