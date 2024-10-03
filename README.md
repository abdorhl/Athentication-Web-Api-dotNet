# .NET 8 Web API Authentication with Identity, Bearer Tokens & Cookies

This project demonstrates how to implement authentication in a .NET 8 Web API using ASP.NET Core Identity with Bearer Tokens and Cookies for session management. It is designed for developers looking to secure Web APIs and manage user authentication using both token-based and cookie-based approaches.

## Features

- **ASP.NET Core Identity Integration**: Provides user registration, login, and role management.
- **Bearer Token Authentication**: Secures API endpoints with JWT (JSON Web Tokens).
- **Cookie Authentication**: Allows session-based authentication for web clients.
- **Entity Framework Core**: Used to interact with the SQL Server database.
- **Role-Based Authorization**: Secure certain actions based on user roles.

## Requirements

- .NET SDK 8.0
- SQL Server (or SQL Server Express)
- Postman (for testing API endpoints)
- Visual Studio / VS Code

## Getting Started

Follow these instructions to get the project up and running on your local machine.

### 1. Clone the Repository

```bash
git clone https://github.com/abdorhl/Athentication-Web-Api-dotNet.git
cd AuthDotNet
```

### 2. Install Dependencies

Make sure you have .NET 8 installed on your machine. Then, restore the NuGet packages:

```bash
dotnet restore
```

### 3. Configure the Database

Update the `appsettings.json` file with your SQL Server connection string:

```json
"ConnectionStrings": {
  "DefaultConnection": "Server=your-server;Database=your-database;User Id=your-user;Password=your-password;"
}
```

Run the following commands to apply migrations and seed the database:

```bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

### 4. Running the API

To start the API:

```bash
dotnet run
```

The API should now be running on `https://localhost:5001` or `http://localhost:5000`.

### 5. Testing Authentication

#### Register a User

Send a POST request to the `/api/auth/register` endpoint with the following JSON body:

```json
{
  "email": "user@example.com",
  "password": "YourPassword123!"
}
```

#### Login and Retrieve Bearer Token

Send a POST request to the `/api/auth/login` endpoint with the user’s credentials:

```json
{
  "email": "user@example.com",
  "password": "YourPassword123!"
}
```

The response will include a Bearer token. Use this token to authenticate requests to secured endpoints by including it in the `Authorization` header:

```bash
Authorization: Bearer <token>
```

#### Testing Cookie Authentication

Cookie authentication is automatically handled when accessing web routes. No special steps are needed if you're using cookies instead of tokens.

### 6. Secured Endpoints

- `GET /api/user/profile` - Requires authentication (Bearer Token or Cookies).
- `POST /api/admin/create-role` - Requires **Admin** role.

## Technologies Used

- **ASP.NET Core 8.0**
- **ASP.NET Core Identity**
- **JWT Bearer Tokens**
- **Entity Framework Core**
- **SQL Server**
- **Swagger** (for API documentation)

## License

This project is licensed under the MIT License.

---

Feel free to adjust the README to better match your project's structure and requirements!
