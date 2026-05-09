# 🎓 Smart Academic Advisor API

## 📊 Latest API Test Results
- **Run Date:** 2026-05-09
- **Overall Pass Rate:** 66% (33 Passed ✅ / 17 Failed ❌)

### 🧪 Detailed Execution Table
| Request Name | Method | Response | Time (ms) | Pass | Fail | Result |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| 1.1 Login - Student | **POST** | `200 OK` | 1194 | 2 | 0 | ✅ |
| 1.2 Login - Advisor | **POST** | `200 OK` | 379 | 2 | 0 | ✅ |
| 1.3 Login - Admin | **POST** | `200 OK` | 368 | 2 | 0 | ✅ |
| 2.1 Get All Courses | **GET** | `200 OK` | 667 | 3 | 0 | ✅ |
| 2.5 Student Completed Courses | **GET** | `404 Not Found` | 352 | 0 | 2 | ❌ |
| 3.1 Create Schedule Draft | **POST** | `400 Bad Request` | 305 | 0 | 2 | ❌ |
| 3.2 Add Course to Draft | **POST** | `400 Bad Request` | 284 | 0 | 2 | ❌ |
| 4.1 Advisor - Get Students | **GET** | `200 OK` | 294 | 2 | 0 | ✅ |
| 5.1 Admin - Create Test User | **POST** | `200 OK` | 6952 | 2 | 0 | ✅ |
| 6.2 Unauthenticated RLS Test | **GET** | `200 OK` | 294 | 0 | 1 | ❌ |

---
*Note: This table highlights key results. For the full report of all 27 requests, please view the [Postman JSON file](./Smart%20Academic%20Advisor%20-%20Full%20Test%20Suite.postman_test_run.json).*
