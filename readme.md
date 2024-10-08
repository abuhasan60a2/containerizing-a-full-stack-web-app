## Getting Started

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <project-directory>
   ```

2. Create a `.env` file in the root directory with the following content:
   ```bash
   MONGO_INITDB_DATABASE=todo
   MONGO_INITDB_ROOT_USERNAME=your_username
   MONGO_INITDB_ROOT_PASSWORD=your_password
   MONGODB_URI=mongodb://${MONGO_INITDB_ROOT_USERNAME}:${MONGO_INITDB_ROOT_PASSWORD}@db:27017/${MONGO_INITDB_DATABASE}?authSource=admin
   ```
   Replace `your_username` and `your_password` with your desired MongoDB credentials.

3. Build and start the containers:
   ```bash
   docker-compose up --build
   ```

4. Access the application:
   - Frontend: http://localhost:3000
   - Backend API: http://localhost:5000

## Development

- The frontend and backend directories are mounted as volumes, so changes will be reflected immediately without rebuilding the containers.
- To run commands inside a container, use:
  ```bash
  docker-compose exec <service-name> <command>
  ```
  For example, to add a new npm package to the frontend:
  ```bash
  docker-compose exec frontend yarn add <package-name>
  ```

## Stopping the Application

To stop the application and remove the containers, volumes, and images:
```
docker-compose down -v --rmi all
```

## Connecting to MongoDB

- From within the Docker network, services can connect to MongoDB using the hostname `localhost`.
- To connect from your host machine (e.g., using MongoDB Compass), use `localhost:27017`.

## Troubleshooting

- If the MongoDB container fails to start, check the logs:
  ```bash
  docker-compose logs db
  ```
- Ensure that the `data/db` directory has the correct permissions.

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
