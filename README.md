### API Documentation:

**API-01: Sign Up Functionality**
   - **Endpoint:** `/api/delivery-app/register`
   - **Method:** POST
   - **Payload:** User Data [P-01]
   - **Response:** Response Data [R-01]

**API-02: Login Functionality**
   - **Endpoint:** `/api/delivery-app/login`
   - **Method:** POST
   - **Payload:** User Data [P-02]
   - **Response:** Response Data [R-02]

**API-03: Forgot Password**
   - **Endpoint:** `/api/delivery-app/password/forgot`
   - **Method:** POST
   - **Payload:** User Data [P-03]
   - **Response:** Response Data [R-03]

**API-04: Reset Password**
   - **Endpoint:** `/api/delivery-app/password/reset`
   - **Method:** POST
   - **Payload:** User Data [P-04]
   - **Response:** Response Data [R-04]

**API-05: Profile Details Endpoint**
   - **Endpoint:** `/api/delivery-app/profile`
   - **Method:** GET
   - **Response:** Response Data [R-05]

**API-06: All Jobs Endpoint**
   - **Endpoint:** `/api/delivery-app/all-jobs/{user_id}`
   - **Method:** GET
   - **Response:** Response Data [R-06]

**API-07: Mark Job as Collected**
   - **Endpoint:** `/api/delivery-app/mark-collected/{job_id}`
   - **Method:** PUT
   - **Payload:** No payload is required for this request.
   - **Response:** Response Data [R-07]

**API-09: Active Job Details Endpoint**
   - **Endpoint:** `/api/delivery-app/delivery-jobs/{job_id}`
   - **Method:** GET
   - **Response:** Response Data [R-09]

**API-11: Mark As Delivered Endpoint**
    - **Endpoint:** `/api/delivery-app/mark-delivered/{job_id}`
    - **Method:** PUT
    - **Response:** Response Data [R-11]

**API-12: Mark Delivery Complete Endpoint**
    - **Endpoint:** `/api/delivery-app/mark-delivery-complete/{job_id}`
    - **Method:** PUT
    - **Response:** Response Data [R-12]

**API-13: New Jobs Endpoint**
    - **Endpoint:** `/api/delivery-app/job-offers/{user_id}`
    - **Method:** GET
    - **Response:** Response Data [R-13]

**API-14: Accept Job Offers**
    - **Endpoint:** `/api/delivery-app/job-offers/{job_id}/accept`
    - **Method:** GET
    - **Response:** Response Data [R-14]

**API-15: Reject Job Offers**
    - **Endpoint:** `/api/delivery-app/job-offers/{job_id}/reject`
    - **Method:** GET
    - **Response:** Response Data [R-15]

**API-16: Dispatched Jobs Endpoint**
    - **Endpoint:** `/api/delivery-app/dispatched-jobs/{user_id}`
    - **Method:** GET
    - **Response:** Response Data [R-16]

**API-17: Collected Jobs Endpoint**
    - **Endpoint:** `/api/delivery-app/collected-jobs/{user_id}`
    - **Method:** GET
    - **Response:** Response Data [R-17]

**API-18: Mark Job as Dispatched**
    - **Endpoint:** `/api/delivery-app/dispatch-job/{job_id}`
    - **Method:** GET
    - **Response:** Response Data [R-18]

**API-19: Notifications**
    - **Endpoint:** `/api/delivery-app/notifications/{user_id}`
    - **Method:** GET
    - **Response:** Response Data [R-19]

**API-20: Forgot Password Confirm**
   - **Endpoint:** `/api/delivery-app/password/confirm`
   - **Method:** POST
   - **Payload:** User Data [P-05]
   - **Response:** Response Data [R-20]



##Reqeust Payloads
#### API-01: Sign Up Functionality
- **Request Payload**:
  ```json
  {
      "email": "newuser@example.com",
      "password": "newpassword123",
      "name": "New User",
      "phone": "1234567890"
  }
  ```

#### API-02: Login Functionality
- **Request Payload**:
  ```json
  {
      "email": "user@example.com",
      "password": "password123"
  }
  ```

#### API-03: Forgot Password
- **Request Payload**:
  ```json
  {
      "email": "user@example.com"
  }
  ```

#### API-04: Reset Password
- **Request Payload**:
  ```json
  {
      "email": "user@example.com",
      "password": "newpassword123",
      "confirmation_code": "confirmation_code_received_in_email"
  }
  ```

#### API-20: Forgot Password Confirm
- **Request Payload**:
  ```json
  {
      "email": "user@example.com",
      "confirmation_code": "confirmation_code_received_in_email"
  }
  ```

### Response Payload Documentation:

#### API-01: Sign Up Functionality
- **Successful Response**:
  ```json
  {
      "status": true,
      "message": "Your registration is successful. Please wait for admin approval.",
      "api_token": "..."
  }
  ```
- **Error Response**:
  ```json
  {
      "status": false,
      "message": "The email is already taken.",
      "errors": {
          "password": [
              "password must be 8 characters",
              "password must contain at least 1 symbol"
          ],
          "phone": [
              "phone number is not valid"
          ]
      }
  }
  ```

#### API-02: Login Functionality
- **Successful Response**:
  ```json
  {
      "status": true,
      "message": "success",
      "api_token": "..."
  }
  ```
- **Error Response**:
  ```json
  {
      "status": false,
      "message": "Invalid email or password"
  }
  ```

- **Error Response**:
  ```json
  {
      "status": false,
      "message": "User is not Delivery Person"
  }
  ```
#### API-03: Forgot Password
- **Successful Response**:
  ```json
  {
      "status": true,
      "message": "Verification code sent to your email."
  }
  ```
- **Error Response**:
  ```json
  {
      "status": false,
      "message": "User not found"
  }
  ```

#### API-04: Reset Password
- **Successful Response**:
  ```json
  {
      "status": true,
      "message": "Password reset successful."
  }
  ```
- **Error Response**:
  ```json
  {
      "status": false,
      "message": "Password reset token is invalid or expired."
  }
  ```

#### API-05: Profile Details Endpoint
- **Successful Response**:
  ```json
  {
      "status": true,
      "data": {
          "id": 123,
          "name": "John Doe",
          "email": "john@example.com",
          "phone": "1234567890",
          "created_at": "2024-05-10T12:00:00Z",
          "updated_at": "2024-05-12T08:30:00Z",
          "token": "api_token"
      }
  }
  ```
- **Error Response** (if unauthorized):
  ```json
  {
      "status": false,
      "message": "Unauthorized"
  }
  ```

#### API-06: All Jobs Endpoint
- **Successful Response**:
  ```json
  {
      "status": true,
      "data": {
          "delivery_jobs": [
              {
                  "id": "1",
                  "customer_name": "John Doe",
                  "delivery_address": "123 Main St, Anytown, USA",
                  "delivery_time": "2024-05-15 09:00:00",
                  "status": "In progress"
              },
              {
                  "id": "2",
                  "customer_name": "Jane Smith",
                  "delivery_address": "456 Elm St, Othertown, USA",
                  "delivery_time": "2024-05-15 10:30:00",
                  "status": "Pending"
              }
          ]
      }
  }
  ```
- **Error Response** (if unauthorized):
  ```json
  {
      "status": false,
      "message": "Unauthorized"
  }
  ```

#### API-07: Mark Job as Collected
- **Successful Response**:
  ```json
  {
      "status": true,
      "message": "Job marked as collected."
  }
  ```
- **Error Response** (if unauthorized or job not found):
  ```json
  {
      "status": false,
      "message": "Unauthorized or job not found"
  }
  ```

#### API-08: Active Job Details Endpoint
- **Successful Response**:
  ```json
  {
      "status": true,
      "data": {
        "delivery_jobs": [
            {
              "id": "1",
              "customer_name": "John Doe",
              "delivery_address": "123 Main St, Anytown, USA",
              "delivery_time": "2024-05-15 09:00:00",
              "status": "In progress"
            },
            {
              "id": "2",
              "customer_name": "Jane Smith",
              "delivery_address": "456 Elm St, Othertown, USA",
              "delivery_time": "2024-05-15 10:30:00",
              "status": "Pending"
            },
             
          ]
      }
  }
  ```
- **Error Response** (if unauthorized or job not found):
  ```json
  {
      "status": false,
      "message": "Unauthorized or job not found"
  }
  ```

#### API-09: Active Job Details Endpoint
- **Successful Response**:
  ```json
  {
      "status": true,
      "data": {
          "id": "1",
          "customer_name": "John Doe",
          "delivery_address": "123 Main St, Anytown, USA",
          "delivery_time": "2024-05-15 09:00:00",
          "status": "In progress"
      }
  }
  ```
- **Error Response** (if unauthorized or job not found):
  ```json
  {
      "status": false,
      "message": "Unauthorized or job not found"
  }
  ```

#### API-11: Mark As Delivered Endpoint
- **Successful Response**:
  ```json
  {
      "status": true,
      "message": "Job marked as delivered."
  }
  ```
- **Error Response** (if unauthorized or job not found):
  ```json
  {
      "status": false,
      "message": "Unauthorized or job not found"
  }
  ```

#### API-12: Mark Delivery Complete Endpoint
- **Successful Response**:
  ```json
  {
      "status": true,
      "message": "Delivery marked as complete."
  }
  ```
- **Error Response** (if unauthorized or job not found):
  ```json
  {
      "status": false,
      "message": "Unauthorized or job not found"
  }
  ```

#### API-13: New Jobs Endpoint
- **Successful Response**:
  ```json
  {
      "status": true,
      "data": {
          "delivery_jobs": [
              {
                  "id": "1",
                  "customer_name": "John Doe",
                  "delivery_address": "123 Main St, Anytown, USA",
                  "delivery_time": "2024-05-15 09:00:00",
                  "status": "In progress",
                  "accept": "/api/delivery-app/job-offers/1/accept",
                  "reject": "/api/delivery-app/job-offers/1/reject"
              },
              {
                  "id": "2",
                  "customer_name": "Jane Smith",
                  "delivery_address": "456 Elm St, Othertown, USA",
                  "delivery_time": "2024-05-15 10:30:00",
                  "status": "Pending",
                  "accept": "/api/delivery-app/job-offers/2/accept",
                  "reject": "/api/delivery-app/job-offers/2/reject"
              }
          ]
      }
  }
  ```
- **Error Response** (if unauthorized):
  ```json
  {
      "status": false,
      "message": "Unauthorized"
  }
  ```

#### API-14: Accept Job Offers
- **Successful Response**:
  ```json
  {
      "status": true,
      "message": "Job offer accepted."
  }
  ```
- **Error Response** (if unauthorized or job not found):
  ```json
  {
      "status": false,
      "message": "Unauthorized or job not found"
  }
  ```

#### API-15: Reject Job Offers
- **Successful Response**:
  ```json
  {
      "status": true,
      "message": "Job offer rejected."
  }
  ```
- **Error Response** (if unauthorized or job not found):
  ```json
  {
      "status": false,
      "message": "Unauthorized or job not found"
  }
  ```

#### API-16: Dispatched Jobs Endpoint
- **Successful Response**:
  ```json
  {
      "status": true,
      "data": {
          "dispatched_jobs": [
              {
                  "id": "1",
                  "customer_name": "John Doe",
                  "delivery_address": "123 Main St, Anytown, USA",
                  "delivery_time": "2024-05-15 09:00:00",
                  "status": "Dispatched"
              },
              {
                  "id": "2",
                  "customer_name": "Jane Smith",
                  "delivery_address": "456 Elm St, Othertown, USA",
                  "delivery_time": "2024-05-15 10:30:00",
                  "status": "Dispatched"
              }
          ]
      }
  }
  ```

#### API-17: Completed Jobs Endpoint
- **Successful Response**:
  ```json
  {
      "status": true,
      "data": {
          "completed_delivery_jobs": [
              {
                  "id": "1",
                  "customer_name": "John Doe",
                  "delivery_address": "123 Main St, Anytown, USA",
                  "delivery_time": "2024-05-10 09:00:00",
                  "status": "Completed",
                  "completion_time": "2024-05-10 09:30:00"
              },
              {
                  "id": "2",
                  "customer_name": "Jane Smith",
                  "delivery_address": "456 Elm St, Othertown, USA",
                  "delivery_time": "2024-05-12 10:30:00",
                  "status": "Completed",
                  "completion_time": "2024-05-12 11:00:00"
              }
          ]
      }
  }
  ```
- **Error Response** (if unauthorized or job not found):
  ```json
  {
      "status": false,
      "message": "Unauthorized or job not found"
  }
  ```

These are the corrected response payloads for each API. Let me know if you need further assistance!
