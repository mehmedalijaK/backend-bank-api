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
	"email": "john.doe@example.com",
	"password": "password"
}
```
#### Response
```json
{
	"access_token": "eyJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiZW1wbG95ZWUiLCJpZCI6IjFmYWQyYzAxLWY4MmYtNDFhNi04MjJjLThjYTFiMzIzMjU3NSIsInN1YiI6ImpvaG4uZG9lQGV4YW1wbGUuY29tIiwiaWF0IjoxNzQwNTgwMDkzLCJleHAiOjE3NDA1ODAyNzN9.MNBiu0na0E79cV40cDGbAi-N4D2UaM5pOWuGcVzJ0iU",
	"refresh_token": "eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJqb2huLmRvZUBleGFtcGxlLmNvbSIsImlhdCI6MTc0MDU4MDA5MywiZXhwIjoxNzQxMTg0ODkzfQ.ooWSrJql55T7jceyYiPbZo69PvkZjpCYuEFB2XIWCSI"
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
    "refresh_token": "eyJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiZW1wbG95ZWUiLCJpZCI6IjFmYWQyYzAxLWY4MmYtNDFhNi04MjJjLThjYTFiMzIzMjU3NSIsInN1YiI6ImpvaG4uZG9lQGV4YW1wbGUuY29tIiwiaWF0IjoxNzQwNTgwNzU1LCJleHAiOjE3NDA1ODA5MzV9.c1bScaBFM8JCeTbhx0myy9CgYHzG6k84299V_HDtTy"
}
```
#### Response
```json
{
    "access_token": "eyJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiZW1wbG95ZWUiLCJpZCI6IjFmYWQyYzAxLWY4MmYtNDFhNi04MjJjLThjYTFiMzIzMjU3NSIsInN1YiI6ImpvaG4uZG9lQGV4YW1wbGUuY29tIiwiaWF0IjoxNzQwNTg1MzM1LCJleHAiOjE3NDA1ODU1MTV9.LOmZObVdgrzk7Joqa8JLFiZlevvBomPuAZjJIOQc8Sc"
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
    "refresh_token": "eyJhbGciOiJIUzI1NiJ9.eyJyb2xlIjoiZW1wbG95ZWUiLCJpZCI6IjFmYWQyYzAxLWY4MmYtNDFhNi04MjJjLThjYTFiMzIzMjU3NSIsInN1YiI6ImpvaG4uZG9lQGV4YW1wbGUuY29tIiwiaWF0IjoxNzQwNTgwNzU1LCJleHAiOjE3NDA1ODA5MzV9.c1bScaBFM8JCeTbhx0myy9CgYHzG6k84299V_HDtTy"
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
    "first_name": "John",
    "last_name": "Doe",
    "date_of_birth": "1990-01-01",
    "gender": "Male",
    "email": "john.doe@example.com",
    "phone": "123-456-7890",
    "address": "123 Main St",
    "username": "johndoe",
    "position": "Developer",
    "department": "IT",
    "privileges": [
        "ADMIN"
    ]
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
  "firstName": "John",
  "lastName": "Doe",
  "username": "johndoee",
  "dateOfBirth": "1990-05-15",
  "gender": "Male",
  "email": "johndoe@example.com",
  "phone": "+1234567890",
  "address": "123 Main Street, City, Country",
  "privilege": ["TRADE_STOCKS", "CONTRACTS"],
  "position": "Software Engineer",
  "department": "IT"
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
            "id": "1fad2c01-f82f-41a6-822c-8ca1b3232575",
            "firstName": "John",
            "lastName": "Doe",
            "dateOfBirth": "1990-01-01",
            "gender": "Male",
            "email": "john.doe@example.com",
            "phone": "123-456-7890",
            "address": "123 Main St",
            "username": "johndoe",
            "position": "Developer",
            "department": "IT"
        },
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
            "department": "IT"
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
            "department": "IT"
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
    "totalElements": 3,
    "totalPages": 1,
    "size": 10,
    "number": 0,
    "sort": {
        "empty": true,
        "sorted": false,
        "unsorted": true
    },
    "first": true,
    "numberOfElements": 3,
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
public record EmployeeUpdateDto(
    @JsonProperty("first_name")
    String firstName,
    @JsonProperty("last_name")
    String lastName,
    @JsonProperty("date_of_birth")
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
    String department
) {
}
```
