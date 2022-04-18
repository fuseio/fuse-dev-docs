# Jobs API

Jobs API is used to fetch and interact with the issued jobs. Job is a unit of work that is executed in an asynchronous way.&#x20;

Since it takes a couple of seconds to confirm a blockchain transaction, the transaction is wrapped in a job. The job issuer gets a jobId and can check the job's status. He can also retry the job in case it failed. Jobs are used extensively in the [Admin API](admin-api.md).

Base URL: [https://studio.fuse.io/](https://studio.fuse.io)

### Fetch job by correlationId

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Fetches agenda job by job's correlationId

```
GET api/v2/jobs/correlationId/:correlationId
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type     | Description |
| ---- | -------- | ----------- |
| data | `Object` | Job object  |

### Fetch job by id <a href="#user-content-fetch-job-by-id" id="user-content-fetch-job-by-id"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Fetch job by id

```
GET api/v2/jobs/:jobId
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type     | Description |
| ---- | -------- | ----------- |
| data | `Object` | Job object  |

### Retry failed job by id <a href="#user-content-retry-failed-job-by-id" id="user-content-retry-failed-job-by-id"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Retry failed job by id

```
GET api/v2/jobs/retry/:jobId
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type     | Description |
| ---- | -------- | ----------- |
| data | `Object` | Job object  |

### Retry failed job by query <a href="#user-content-retry-failed-job-by-query" id="user-content-retry-failed-job-by-query"></a>

[Back to top](https://github.com/fuseio/fuse-studio/blob/master/server/docs/api-v2.md#top)

Retry failed job by id

```
GET api/v2/jobs/retry
```

#### Headers

| Name          | Type   | Description                                       |
| ------------- | ------ | ------------------------------------------------- |
| Authorization | String | JWT Authorization in a format "Bearer {jwtToken}" |

#### Success 200

| Name | Type     | Description |
| ---- | -------- | ----------- |
| data | `Object` | Job object  |
