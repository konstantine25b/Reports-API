# Reports API

This Django application provides an API for managing reports, users, and their roles. It's built using Django Rest Framework.

## Installation

1. Clone the repository:
   ```bash
   git clone github.com/konstantine25b/Reports-API
   ```

2. Navigate to the project directory:
   ```bash
   cd your_repository
   ```

3. Install dependencies (it's recommended to do this in a virtual environment):
   ```bash
   pip install -r requirements.txt
   ```

4. Apply migrations:
   ```bash
   python manage.py migrate
   ```

5. Run the development server:
   ```bash
   python manage.py runserver
   ```

## API Endpoints

- **Users:**  
  - `GET /api/users/`: List all users. (Administrator access required)
  - `POST /api/users/`: Create a new user. (Administrator access required)
  - `GET /api/users/{id}/`: Retrieve a specific user. (Administrator access required)
  - `PUT /api/users/{id}/`: Update a specific user. (Administrator access required)
  - `DELETE /api/users/{id}/`: Delete a specific user. (Administrator access required)

- **Reports:**  
  - `GET /api/reports/`: List all reports.
  - `POST /api/reports/`: Create a new report. (Office worker access required)
  - `GET /api/reports/{id}/`: Retrieve a specific report.
  - `PUT /api/reports/{id}/`: Update a specific report. (Administrator access required)
  - `DELETE /api/reports/{id}/`: Delete a specific report. (Courier access required)

## Permissions

- `IsAdministrator`: Only allows access to users with the role 'administrator'.
- `CanDeleteReport`: Allows access to delete reports for users with the role 'courier'.
- `CanAddReport`: Allows access to add reports for users with the role 'office_worker'.

## Models

- `CustomUser`: Represents a user with additional fields like `role`.
- `Report`: Represents a report with fields for `title`, `content`, `created_at`, and `created_by`.

## Serializers

- `UserSerializer`: Serializes user data for API interactions.
- `ReportSerializer`: Serializes report data for API interactions.
