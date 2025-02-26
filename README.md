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

## Employee Refresh token Endpoint Details
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
