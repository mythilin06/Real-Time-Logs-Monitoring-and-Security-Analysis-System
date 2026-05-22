# Running multiple projects at once

Each project needs **its own API port** and **its own Python port**. MongoDB can be shared, but use **different database names** in `MONGODB_URI`.

## Default ports (this project — Log Monitoring)

| Setting | Port |
|---------|------|
| `PORT` (Node / dashboard) | **4110** |
| `PYTHON_PORT` | **5110** |

Open: **http://localhost:4110**

## Example: two projects side by side

| Project | `.env` PORT | `.env` PYTHON_PORT | MongoDB database |
|---------|-------------|---------------------|------------------|
| **Log Monitoring** (this folder) | 4110 | 5110 | `log_monitoring` |
| **Fraud Detection** (other folder) | 5000 | 5100 | `fraud_detection` |
| Third project | 4200 | 5200 | `my_app_db` |

In each project’s `.env`:

```env
PORT=4110
PYTHON_PORT=5110
PYTHON_SERVICE_URL=http://127.0.0.1:5110
MONGODB_URI=mongodb://127.0.0.1:27017/log_monitoring
```

**Important:** `PYTHON_SERVICE_URL` must match `PYTHON_PORT`.

## Check ports before starting

```powershell
npm run ports
```

## If port is still in use

1. Stop the old terminal (`Ctrl+C`), or  
2. `netstat -ano | findstr :4110` then `taskkill /PID <id> /F`, or  
3. Bump ports in `.env` (e.g. `4111` / `5111`) and restart both Python and Node.
