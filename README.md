# curly-computing-machine

This project is a basic example of a full-stack application with a FastAPI backend and a React frontend.

## Backend

*   **main.py:** Contains the main application logic, including API endpoints for user registration, login, and accessing a protected route.
*   **models.py:** Defines the database models (User).
*   **schemas.py:** Defines the data schemas (UserCreate, User).
*   **crud.py:** Contains database operations (get\_user\_by\_username, create\_user, verify\_password).
*   **database.py:** Configures the database connection (using SQLite for local development).
*   **Dockerfile:** Defines the Docker image for the backend.
*   **docker-compose.yml:** Defines the Docker Compose configuration.
*   **requirements.txt:** Lists the Python dependencies.

### Running the Backend

1.  Make sure you have Python and pip installed.
2.  Navigate to the `backend` directory.
3.  Install the dependencies: `pip install -r requirements.txt`
4.  Run the server: `uvicorn backend.main:app --reload`

### API Endpoints

*   `/auth/register` (POST): Registers a new user.
*   `/auth/token` (POST): Logs in a user and returns an access token.
*   `/users/me` (GET): Returns the current user's information (requires authentication).
*   `/users` (GET): Returns a list of all users.

## Frontend

*   **src/App.tsx:** Contains the main React application logic, including a registration form.
*   **components/ui/button.tsx:** Contains the button component.
*   **package.json:** Lists the JavaScript dependencies and scripts.

### Running the Frontend

1.  Make sure you have Node.js and npm installed.
2.  Navigate to the `frontend` directory.
3.  Install the dependencies: `npm install`
4.  Run the development server: `npm start`

## Authentication

The application uses JSON Web Tokens (JWT) for authentication.

1.  A user registers with a username and password.
2.  The user logs in with their username and password, receiving an access token.
3.  The access token is included in the `Authorization` header of subsequent requests to protected routes (e.g., `/users/me`).

## Database

The backend uses an SQLite database for local development. The database file is `sql_app.db`.

## Docker

The project includes a Dockerfile and docker-compose.yml for containerization.

## Next Steps

*   Implement frontend functionality to interact with the backend API.
*   Add more features to the backend, such as user profile management.
*   Improve the user interface.

## Frontend Problems and Plan

**Problems:**

1.  The frontend application is not starting due to a "react-scripts not found" error.
2.  The registration form in `App.tsx` might not be correctly sending requests to the backend.

**Plan:**

1.  **Resolve "react-scripts not found" error:**
    *   Ensure Node.js and npm are installed correctly.
    *   Verify the "start" script in `frontend/package.json`.
    *   Clear the npm cache: `npm cache clean --force`.
    *   Reinstall dependencies: `npm install`.
    *   If the issue persists, try uninstalling and reinstalling `react-scripts` globally.
    *   If still not working, try using yarn or pnpm.
2.  **Verify the registration form:**
    *   Check the `fetch` request in `frontend/src/App.tsx` to ensure it is sending the correct data to the correct endpoint (`/auth/register`).
    *   Check the backend logs for any errors related to the registration request.
3.  **Implement Login Functionality:**
    *   Create a login form in `App.tsx`.
    *   Implement a `fetch` request to the `/auth/token` endpoint.
    *   Store the access token in local storage.
4.  **Implement Protected Route Access:**
    *   Use the access token to authorize requests to protected routes (e.g., `/users/me`).
