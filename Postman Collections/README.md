# 🎓 Smart Academic Advisor API

## 📊 Latest API Test Results
- **Run Date:** 2026-05-09
- **Overall Pass Rate:** 66% (33 Passed ✅ / 17 Failed ❌)

### 🧪 Detailed Execution Table

| Request Name | Method | Response Code | Time (ms) | Pass | Fail | Result |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| 1.1 Login - Student | POST | `200 OK` | 1194 | 2 | 0 | ✅ |
| 1.2 Login - Advisor | POST | `200 OK` | 379 | 2 | 0 | ✅ |
| 1.3 Login - Admin | POST | `200 OK` | 368 | 2 | 0 | ✅ |
| 1.4 Wrong Password - Should Fail | POST | `400 Bad Request` | 366 | 1 | 0 | ✅ |
| 2.1 Get All Courses | GET | `200 OK` | 667 | 3 | 0 | ✅ |
| 2.2 Get Plannable Courses Only | GET | `200 OK` | 342 | 2 | 0 | ✅ |
| 2.3 Get Courses with Dept Names | GET | `200 OK` | 370 | 2 | 0 | ✅ |
| 2.4 Get Historical Course Stats | GET | `200 OK` | 308 | 2 | 0 | ✅ |
| 2.5 Get Student Completed Courses | GET | `404 Not Found` | 352 | 0 | 2 | ❌ |
| 2.6 Get Departments | GET | `200 OK` | 295 | 2 | 0 | ✅ |
| 3.1 Create Schedule Draft | POST | `400 Bad Request` | 305 | 0 | 2 | ❌ |
| 3.2 Add Course to Draft | POST | `400 Bad Request` | 284 | 0 | 2 | ❌ |
| 3.3 View Draft with Courses | GET | `400 Bad Request` | 285 | 0 | 2 | ❌ |
| 3.4 Get All My Drafts | GET | `200 OK` | 295 | 2 | 0 | ✅ |
| 3.5 Get Schedule Evaluations | GET | `400 Bad Request` | 284 | 0 | 2 | ❌ |
| 3.6 Delete Test Draft (Cleanup) | DELETE | `400 Bad Request` | 289 | 0 | 1 | ❌ |
| 4.1 Advisor - Get All Students | GET | `200 OK` | 294 | 2 | 0 | ✅ |
| 4.2 Advisor - Get Student Profiles | GET | `200 OK` | 287 | 2 | 0 | ✅ |
| 4.3 Advisor - Get Messages | GET | `400 Bad Request` | 295 | 0 | 2 | ❌ |
| 5.1 Admin - Create Test User | POST | `200 OK` | 6952 | 2 | 0 | ✅ |
| 5.2 Admin - Reset Test User Password | POST | `400 Bad Request` | 562 | 0 | 2 | ❌ |
| 5.3 Admin - Delete Test User | POST | `200 OK` | 3226 | 2 | 0 | ✅ |
| 5.4 Admin - Get All Users (Supabase) | GET | `200 OK` | 332 | 2 | 0 | ✅ |
| 6.1 Student CANNOT call admin API | POST | `500 Internal Error` | 1894 | 1 | 0 | ✅ |
| 6.2 Unauthenticated RLS Test | GET | `200 OK` | 294 | 0 | 1 | ❌ |
| 6.3 Student CANNOT see other drafts | GET | `200 OK` | 287 | 2 | 0 | ✅ |
| 6.4 Advisor token CANNOT reset pass | POST | `400 Bad Request` | 323 | 0 | 1 | ❌ |

---
*Note: Generated from Postman Test Runner on 2026-05-09.*
