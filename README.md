# API Endpoint Documentation

## Employee Login Endpoint Details

-  **Method:** POST 
-  **URL:**  `/auth/employee/login` 
 -  **Authentication Required?** No 
-  **Permissions?** No
- **ErrorMessage:**  IncorrectCredentials() || InvalidData()
#### Request Payload  
```json
{
    "email": "markovicmarko@example.com",
    "password": "securepassword"
}
```
#### Response
```json
{
    "accessToken": "eyJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiZW1wbG95ZWUiLCJpZCI6Ijk1NDM3MDdkLTcxNjQtNGI4My1iNzMxLTVlMGExZGExYzJmOSIsInN1YiI6Im1hcmtvdmljbWFya29AZXhhbXBsZS5jb20iLCJpYXQiOjE3NDA2NjQ0MTQsImV4cCI6MTc0MDY2NDU5NH0.COm2g-SUtLF5v58yKduivRfm5PFOqgFRAoGvnjactUw",
    "refreshToken": "eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJtYXJrb3ZpY21hcmtvQGV4YW1wbGUuY29tIiwiaWF0IjoxNzQwNjY0NDE0LCJleHAiOjE3NDEyNjkyMTR9.yoAY9A0OdOef8EoC3cJlArTQRYigjKkMONLpZ0w1DRQ"
}
```
#### ErrorReponse
```json
{
	"code": "InvalidData",
	"extra": {
		"password": "Password must be at least 8 characters long"
	},
	"failed": true
}
```

```json
{
	"code": "IncorrectCredentials",
	"failed": true
}
```

## Employee Refresh token Endpoint Details

-  **Method:** POST 
-  **URL:**  `/auth/refresh-token` 
 -  **Authentication Required?** No 
-  **Permissions?** No
- **ErrorMessage:**  InvalidData() || ExpiredJwt() || MalformedJwt() || IllegalArgumentJwt() || UnsupportedJwt() || IncorrectCredentials() || RefreshTokenRevoked()
#### Request Payload  
```json
{
    "refreshToken": "eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJqb2huLmRvZUBleGFtcGxlLmNvbSIsImlhdCI6MTc0MDY2MjQ3NywiZXhwIjoxNzQxMjY3Mjc3fQ.szCTuNBdv7H5g_VGQ4k5EHRPX0ccUWO-kzdX7-LNXzY"
}
```
#### Response
```json
{
    "accessToken": "eyJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiZW1wbG95ZWUiLCJpZCI6IjFmYWQyYzAxLWY4MmYtNDFhNi04MjJjLThjYTFiMzIzMjU3NSIsInN1YiI6ImpvaG4uZG9lQGV4YW1wbGUuY29tIiwiaWF0IjoxNzQwNjYyNTI4LCJleHAiOjE3NDA2NjI3MDh9.6MinKaS95BDlEfyhhUhuu70sB58pOj5OhHirkqs6QVs"
}
```

## Employee logout Endpoint Details
-  **Method:** POST 
-  **URL:**  `/auth/logout` 
 -  **Authentication Required?** Yes 
-  **Permissions?** No
- **ErrorMessage:**  InvalidData() || RefreshTokenRevoked()
#### Request Payload  
```json
{
    "refreshToken": "eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJqb2huLmRvZUBleGFtcGxlLmNvbSIsImlhdCI6MTc0MDY2MjQ3NywiZXhwIjoxNzQxMjY3Mjc3fQ.szCTuNBdv7H5g_VGQ4k5EHRPX0ccUWO-kzdX7-LNXzY"
}
```

## Employee Get Me as Employee token Endpoint Details
-  **Method:** GET 
-  **URL:**  `/employee/me` 
 -  **Authentication Required?** Yes 
-  **Permissions?** No
- **ErrorMessage:**  All token errors
#### Response Payload  
```json
{
    "id": "1fad2c01-f82f-41a6-822c-8ca1b3232575",
    "firstName": "Mehmedalija",
    "lastName": "Doe",
    "dateOfBirth": "1990-01-01",
    "gender": "Male",
    "email": "john.doe@example.com",
    "phone": "123-456-7890",
    "address": "123 Main St",
    "username": "johndoe",
    "position": "Developer",
    "department": "IT",
    "privileges": [
        "ADMIN"
    ],
    "active": false
}
```

## Employee get employee privileges Endpoint Details
-  **Method:** GET 
-  **URL:**  `/employee/privileges` 
 -  **Authentication Required?** Yes 
-  **Permissions?** Admin
- **ErrorMessage:**  All token errors
#### Response Payload  
```json
{
    "privileges": [
        "ADMIN",
        "FILTER",
        "SEARCH",
        "TRADE_STOCKS",
        "VIEW_STOCKS",
        "CONTRACTS",
        "NEW_INSURANCES"
    ]
}
```

## Admin creates new Employee Endpoint Details
-  **Method:** POST 
-  **URL:**  `/employee` 
 -  **Authentication Required?** Yes 
-  **Permissions?** Admin
- **ErrorMessage:**  InvalidData() || DuplicateEmail(email) || DuplicateUsername(username) || PrivilegeDoesNotExist(privilege)
#### Request Payload  
```json
{
  "firstName": "Ognjen",
  "lastName": "Jukic",
  "username": "funfa2c1t",
  "dateOfBirth": "1990-05-15",
  "gender": "Joncic",
  "email": "mljubic9422112rn@raf.rs",
  "phone": "+1234567890",
  "address": "123 Grove Street, City, Country",
  "privilege": ["TRADE_STOCKS", "CONTRACTS"],
  "position": "Software Engineer",
  "department": "IT",
  "active": true
}
```

## Search Employees Endpoint Details
-  **Method:** Get 
-  **URL:**  `/employee/search?firstName=John&lastName=Doe&email=john.doe@example.com&position=Manager&page=0&size=10` 
 -  **Authentication Required?** Yes 
-  **Permissions?** Admin
- **ErrorMessage:**  InvalidData()
#### Response Payload  
```json
{
    "content": [
        {
            "id": "1de54a3a-d879-4154-aa3a-e40598186f93",
            "firstName": "John",
            "lastName": "Doe",
            "dateOfBirth": "1990-05-15",
            "gender": "Male",
            "email": "johndoe@example.com",
            "phone": "+1234567890",
            "address": "123 Main Street, City, Country",
            "username": "johndoee",
            "position": "Software Engineer",
            "department": "IT",
            "active": false
        },
        {
            "id": "434b7887-e493-4707-a84c-0f93e922321a",
            "firstName": "John",
            "lastName": "Doe",
            "dateOfBirth": "1990-05-15",
            "gender": "Male",
            "email": "alija@example.com",
            "phone": "+1234567890",
            "address": "123 Main Street, City, Country",
            "username": "alija",
            "position": "Software Engineer",
            "department": "IT",
            "active": false
        }
    ],
    "pageable": {
        "pageNumber": 0,
        "pageSize": 10,
        "sort": {
            "empty": true,
            "sorted": false,
            "unsorted": true
        },
        "offset": 0,
        "paged": true,
        "unpaged": false
    },
    "last": true,
    "totalPages": 1,
    "totalElements": 2,
    "size": 10,
    "number": 0,
    "sort": {
        "empty": true,
        "sorted": false,
        "unsorted": true
    },
    "first": true,
    "numberOfElements": 2,
    "empty": false
}
```

## Search Employees Endpoint Details
-  **Method:** Put 
-  **URL:**  `/employee/1fad2c01-f82f-41a6-822c-8ca1b3232575`
 -  **Authentication Required?** Yes 
-  **Permissions?** Admin
- **ErrorMessage:**  InvalidData() || DuplicateEmail(email) || DuplicateUsername(username)
#### Request Payload  

```
public record UpdateEmployeeDto(
    String firstName,
    String lastName,
    LocalDate dateOfBirth,
    String gender,
    @Email
    String email,
    String password,
    String username,
    String phone,
    String address,
    List<String> privilege,
    String position,
    String department,
    boolean active
) {
}
```
