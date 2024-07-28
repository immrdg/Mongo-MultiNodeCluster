# Mongo MultiNodeCluster

---

### Initializing the Replica Set

1. **Generate Authentication Key File**:
    ```sh
    bash setup.sh
    ```

2. **Start the Containers**:
    ```sh
    docker-compose up -d
    ```

3. **Bash into One Container**:
    ```sh
    docker exec -it mongo1 bash
    ```

4. **Run `mongosh`**:
    ```sh
    mongosh -u root -p admin
    ```

5. **Initiate the Replica Set**:
    ```javascript
    rs.initiate({
        _id: "rs0",
        version: 1,
        members: [
            { _id: 0, host: "mongo1:27017" },
            { _id: 1, host: "mongo2:27018" },
            { _id: 2, host: "mongo3:27019" }
        ]
    });
    ```

6. **Confirm Replica Status**:
    ```javascript
    rs.status();
    ```

---
