# Cat Fact Django Application

This Django application provides endpoints to retrieve cat facts asynchronously from an external API.

## Requirements

- Python (>= 3.6)
- Django (>= 3.0)
- Dramatiq
- Redis

## Setup

1. Clone the repository:

    ```bash
    git clone <repository_url>
    ```

2. Install dependencies:

    ```bash
    pip install -r requirements.txt
    ```

3. Start Redis server:

    ```bash
    redis-server
    ```

4. Apply migrations:

    ```bash
    python manage.py migrate
    ```

## Running the Application

1. Start the Django development server:

    ```bash
    python manage.py runserver
    ```

2. Access the following endpoints:

    - `/health_check`: Returns a status code of 200 when the application is running.
    
    - `/fetch_fact`: Queues an asynchronous task to fetch data from the cat facts API. Send a POST request to this endpoint.
    
    - `/get_fact`: Returns the first cat fact fetched by the `/fetch_fact` endpoint. Send a GET request to this endpoint.

## Testing Endpoints

You can use tools like cURL or Postman to test the endpoints:

1. Test `/health_check`:

    ```bash
    curl http://localhost:8000/health_check/
    ```

2. Test `/fetch_fact`:

    ```bash
    curl -X POST http://localhost:8000/fetch_fact/
    ```

3. Test `/get_fact`:

    ```bash
    curl http://localhost:8000/get_fact/
    ```

## Deploying to Production

For production deployment, you can use platforms like AWS ECS + Fargate or any other hosting provider of your choice. Make sure to set the appropriate environment variables for production settings.

## Additional Notes

- Ensure that Redis is running before starting the Django server.
- Modify settings such as `ALLOWED_HOSTS`, `SECRET_KEY`, and `DEBUG` in `settings.py` for production deployment.
- Refer to Django and Dramatiq documentation for more advanced configurations and usage.
