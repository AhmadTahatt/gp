<div align="center">

# 📝 Comprehensive API Test Execution Report
**Smart Academic Advisor - Core Backend Services**

![Status](https://img.shields.io/badge/Status-FAILED-red?style=for-the-badge&logo=postman)
![Pass Rate](https://img.shields.io/badge/Pass_Rate-66%25-orange?style=for-the-badge)
![Total Tests](https://img.shields.io/badge/Total_Tests-50-blue?style=for-the-badge)
![Duration](https://img.shields.io/badge/Duration-21.13s-lightgrey?style=for-the-badge)

</div>

---

## Table of Contents
1. [Report Header](#1-report-header)
2. [Executive Summary](#2-executive-summary)
3. [Environment Details](#3-environment-details)
4. [Request-by-Request Breakdown](#4-request-by-request-breakdown)
5. [Performance Metrics](#5-performance-metrics)
6. [Error Analysis](#6-error-analysis)
7. [Test Coverage Summary](#7-test-coverage-summary)
8. [Final Verdict](#8-final-verdict)

---

## 1. Report Header

| Attribute | Detail |
| :--- | :--- |
| **Project Name** | Smart Academic Advisor |
| **Environment Name** | Production / Staging Replica (Env ID: 0) |
| **Collection Name** | Smart Academic Advisor - Full Test Suite |
| **Execution Date & Time** | 2026-05-09 20:26:45 UTC |
| **Executed By** | Automated CI/CD Runner |
| **Newman/Postman Version** | Standard Test Runner JSON Export |
| **Total Execution Duration** | 21,129 ms (21.13 seconds) |

---

## 2. Executive Summary

### 📊 Status Overview

| Metric | Count | Percentage | Status |
| :--- | :---: | :---: | :---: |
| **Total Requests Executed** | 27 | 100% | 🔵 |
| **Total Test Assertions** | 50 | 100% | 🔵 |
| **Passed Tests** | 33 | **66.0%** | ✅ |
| **Failed Tests** | 17 | **34.0%** | ❌ |

**Performance Snapshot:** Average response time across all endpoints is **782.5 ms**.

---

## 3. Environment Details

* **Primary Base URL (Supabase):** `https://zsvoupdsqvqqumrkmqis.supabase.co`
* **Secondary Base URL (Custom API):** `https://psut.site`
* **Authentication Method:** Bearer Token (JWT via Supabase Auth) / Resource Level Security (RLS)
* **Runtime Configuration:** Data persistence enabled (`"persist": true`), zero artificial delay (`"delay": 0`).

---

## 4. Request-by-Request Breakdown

*Note: Request/Response bodies are omitted from basic test runner exports to prevent credential leakage. Endpoint validation relies on assertions.*

<details>
<summary><b>🟢 1.1 Login - Student</b> <code>[POST] /auth/v1/token?grant_type=password</code></summary>

- **Response:** `200 OK` (1194 ms)
- **Tests (2/2 Passed):**
  - ✅ Status 200 OK
  - ✅ Has access_token
</details>

<details>
<summary><b>🟢 1.2 Login - Advisor</b> <code>[POST] /auth/v1/token?grant_type=password</code></summary>

- **Response:** `200 OK` (379 ms)
- **Tests (2/2 Passed):**
  - ✅ Status 200 OK
  - ✅ Has access_token
</details>

<details>
<summary><b>🟢 1.3 Login - Admin</b> <code>[POST] /auth/v1/token?grant_type=password</code></summary>

- **Response:** `200 OK` (368 ms)
- **Tests (2/2 Passed):**
  - ✅ Status 200 OK
  - ✅ Has access_token
</details>

<details>
<summary><b>🟢 1.4 Wrong Password - Should Fail</b> <code>[POST] /auth/v1/token?grant_type=password</code></summary>

- **Response:** `400 Bad Request` (366 ms)
- **Tests (1/1 Passed):**
  - ✅ Wrong password is rejected (400 or 422)
</details>

<details>
<summary><b>🟢 2.1 Get All Courses</b> <code>[GET] /rest/v1/courses?...</code></summary>

- **Response:** `200 OK` (667 ms)
- **Tests (3/3 Passed):**
  - ✅ Status 200 OK
  - ✅ Returns array of courses
  - ✅ Courses have required fields
</details>

<details>
<summary><b>🟢 2.2 Get Plannable Courses Only</b> <code>[GET] /rest/v1/courses?is_plannable=eq.true</code></summary>

- **Response:** `200 OK` (342 ms)
- **Tests (2/2 Passed):**
  - ✅ Status 200 OK
  - ✅ All courses are plannable
</details>

<details>
<summary><b>🟢 2.3 Get Courses with Department Names</b> <code>[GET] /rest/v1/courses?...</code></summary>

- **Response:** `200 OK` (370 ms)
- **Tests (2/2 Passed):**
  - ✅ Status 200 OK
  - ✅ Courses include department info
</details>

<details>
<summary><b>🟢 2.4 Get Historical Course Stats</b> <code>[GET] /rest/v1/historical_course_stats?...</code></summary>

- **Response:** `200 OK` (308 ms)
- **Tests (2/2 Passed):**
  - ✅ Status 200 OK
  - ✅ Stats have required fields
</details>

<details open>
<summary><b>🔴 2.5 Get Student Completed Courses (RLS Test)</b> <code>[GET] /rest/v1/student_completed_courses?...</code></summary>

- **Response:** `404 Not Found` (352 ms)
- **Tests (0/2 Passed):**
  - ❌ Status 200 OK
  - ❌ Returns student transcript
- **Error Analysis:** Endpoint returned 404. Check if the table `student_completed_courses` is exposed via PostgREST or if the route is misconfigured.
</details>

<details>
<summary><b>🟢 2.6 Get Departments</b> <code>[GET] /rest/v1/departments?...</code></summary>

- **Response:** `200 OK` (295 ms)
- **Tests (2/2 Passed):**
  - ✅ Status 200 OK
  - ✅ At least one department
</details>

<details open>
<summary><b>🔴 3.1 Create Schedule Draft</b> <code>[POST] /rest/v1/schedule_drafts</code></summary>

- **Response:** `400 Bad Request` (305 ms)
- **Tests (0/2 Passed):**
  - ❌ Draft created (201)
  - ❌ Draft has ID
- **Error Analysis:** Payload validation failed. Supabase rejected the insert.
</details>

<details open>
<summary><b>🔴 3.2 Add Course to Draft</b> <code>[POST] /rest/v1/schedule_draft_courses</code></summary>

- **Response:** `400 Bad Request` (284 ms)
- **Tests (0/2 Passed):**
  - ❌ Course added to draft (201)
  - ❌ Entry has ID
</details>

<details open>
<summary><b>🔴 3.3 View Draft with Courses (Nested)</b> <code>[GET] /rest/v1/schedule_drafts?...</code></summary>

- **Response:** `400 Bad Request` (285 ms)
- **Tests (0/2 Passed):**
  - ❌ Status 200 OK
  - ❌ Draft contains nested course data
</details>

<details>
<summary><b>🟢 3.4 Get All My Drafts</b> <code>[GET] /rest/v1/schedule_drafts?...</code></summary>

- **Response:** `200 OK` (295 ms)
- **Tests (2/2 Passed):**
  - ✅ Status 200 OK
  - ✅ Drafts returned (RLS - only mine)
</details>

<details open>
<summary><b>🔴 3.5 Get Schedule Evaluations</b> <code>[GET] /rest/v1/schedule_evaluations?...</code></summary>

- **Response:** `400 Bad Request` (284 ms)
- **Tests (0/2 Passed):**
  - ❌ Status 200 OK
  - ❌ Evaluations response is array
</details>

<details open>
<summary><b>🔴 3.6 Delete Test Draft (Cleanup)</b> <code>[DELETE] /rest/v1/schedule_drafts?...</code></summary>

- **Response:** `400 Bad Request` (289 ms)
- **Tests (0/1 Passed):**
  - ❌ Draft deleted (204)
</details>

<details>
<summary><b>🟢 4.1 Advisor - Get All Students</b> <code>[GET] /rest/v1/app_users?role=eq.student</code></summary>

- **Response:** `200 OK` (294 ms)
- **Tests (2/2 Passed):**
  - ✅ Status 200 OK
  - ✅ Students list returned
</details>

<details>
<summary><b>🟢 4.2 Advisor - Get Student Profiles</b> <code>[GET] /rest/v1/student_profiles?...</code></summary>

- **Response:** `200 OK` (287 ms)
- **Tests (2/2 Passed):**
  - ✅ Status 200 OK
  - ✅ Student profiles returned
</details>

<details open>
<summary><b>🔴 4.3 Advisor - Get Messages</b> <code>[GET] /rest/v1/messages?...</code></summary>

- **Response:** `400 Bad Request` (295 ms)
- **Tests (0/2 Passed):**
  - ❌ Status 200 OK
  - ❌ Messages array returned
</details>

<details>
<summary><b>🟢 5.1 Admin - Create Test User</b> <code>[POST] https://psut.site/api/admin-create-user</code></summary>

- **Response:** `200 OK` (6952 ms)
- **Tests (2/2 Passed):**
  - ✅ Status 200 OK
  - ✅ User created successfully
</details>

<details open>
<summary><b>🔴 5.2 Admin - Reset Test User Password</b> <code>[POST] https://psut.site/api/admin-reset-password</code></summary>

- **Response:** `400 Bad Request` (562 ms)
- **Tests (0/2 Passed):**
  - ❌ Status 200 OK
  - ❌ Password reset successful
</details>

<details>
<summary><b>🟢 5.3 Admin - Delete Test User (Cleanup)</b> <code>[POST] https://psut.site/api/admin-delete-user</code></summary>

- **Response:** `200 OK` (3226 ms)
- **Tests (2/2 Passed):**
  - ✅ Status 200 OK
  - ✅ User deleted successfully
</details>

<details>
<summary><b>🟢 5.4 Admin - Get All Users (Supabase)</b> <code>[GET] /rest/v1/app_users?...</code></summary>

- **Response:** `200 OK` (332 ms)
- **Tests (2/2 Passed):**
  - ✅ Status 200 OK
  - ✅ All users returned
</details>

<details>
<summary><b>🟢 6.1 Student CANNOT call admin-create-user</b> <code>[POST] https://psut.site/api/admin-create-user</code></summary>

- **Response:** `500 Internal Server Error` (1894 ms)
- **Tests (1/1 Passed):**
  - ✅ Student blocked from admin API *(Note: 500 implies unhandled exception rather than clean 401/403)*
</details>

<details open>
<summary><b>🔴 6.2 Unauthenticated - No data from app_users (RLS)</b> <code>[GET] /rest/v1/app_users?...</code></summary>

- **Response:** `200 OK` (294 ms)
- **Tests (0/1 Passed):**
  - ❌ Unauthenticated gets no user data (RLS working)
- **Error Analysis:** Security vulnerability. Endpoint returned 200 OK to an unauthenticated request, indicating RLS policies on `app_users` are misconfigured or bypassed.
</details>

<details>
<summary><b>🟢 6.3 Student CANNOT see other students' drafts (RLS)</b> <code>[GET] /rest/v1/schedule_drafts?...</code></summary>

- **Response:** `200 OK` (287 ms)
- **Tests (2/2 Passed):**
  - ✅ Status 200 OK
  - ✅ RLS restricts drafts to own records only
</details>

<details open>
<summary><b>🔴 6.4 Advisor token CANNOT call admin-reset-password</b> <code>[POST] https://psut.site/api/admin-reset-password</code></summary>

- **Response:** `400 Bad Request` (323 ms)
- **Tests (0/1 Passed):**
  - ❌ Advisor blocked from admin password reset
- **Error Analysis:** Expected a 401/403 security block, but received a 400 Payload error, meaning the authorization middleware might not be intercepting the request properly before body validation.
</details>

---

## 5. Performance Metrics

| Metric | Time (ms) | Endpoint Reference |
| :--- | :---: | :--- |
| **Fastest Response** | 284 | `3.2 Add Course to Draft` / `3.5 Get Schedule Evaluations` |
| **Slowest Response** | 6952 | `5.1 Admin - Create Test User` |
| **Average Response** | 782 | *Calculated across all 27 requests* |

**Performance Observations:**
* Supabase `/rest/v1/` endpoints show excellent performance, consistently resolving under 400ms (averaging ~320ms).
* The custom API endpoint `psut.site/api/admin-create-user` exhibits severe latency (**6.9 seconds**), which could result in frontend timeout errors.

---

## 6. Error Analysis

### Critical Failures & Root Causes

| Module | Failed Endpoint(s) | Observed Response | Probable Root Cause & Recommendation |
| :--- | :--- | :--- | :--- |
| **Drafting Workflows** | 3.1, 3.2, 3.3, 3.5, 3.6 | `400 Bad Request` | **Data Schema Mismatch:** Supabase is rejecting the `POST`/`DELETE` operations. Ensure JSON payload maps exactly to Supabase column constraints (e.g., missing required foreign keys, incorrect UUID formatting). |
| **Security (RLS)** | 6.2 Unauthenticated Access | `200 OK` | **CRITICAL:** The `app_users` table is leaking data to unauthenticated users. **Fix:** Update Supabase RLS policies immediately to block `anon` roles (`create policy ... to authenticated`). |
| **Missing Endpoints** | 2.5 Student Completed Courses | `404 Not Found` | **Routing/Exposure:** The PostgREST endpoint is not accessible. Verify that the table `student_completed_courses` exists in the `public` schema and has grants for the active role. |
| **Authorization Logic** | 6.4 Advisor Admin Access | `400 Bad Request` | **Middleware Order:** The custom API is validating the body (resulting in 400) *before* validating the role (which should result in 401/403). Move role-checking middleware to execute first. |

---

## 7. Test Coverage Summary

### ✅ Positively Covered Domains
* **Authentication:** Login flows for all 3 user roles function correctly.
* **Course Catalog (GET):** Successful retrieval of courses, plannable filters, and historical stats.
* **User Management (GET):** Advisors can successfully retrieve student lists and profiles.
* **RLS Isolation:** Students are properly restricted to only their own schedule drafts.

### ⚠️ Gaps & Negative Coverage Issues
* **Schedule Draft Creation (POST/DELETE):** Currently blocked by `400` errors. Complete failure of write-operations in this domain.
* **Message Systems:** Messaging endpoints are failing schema validation.
* **Negative Security Coverage:** Failed. System does not properly handle unauthorized attempts (returning 500s or 400s instead of standard 401/403s), and unauthenticated RLS read access is open.

---

## 8. Final Verdict

### Overall Health: <span style="color:red">**POOR (Failing CI/CD Build)**</span>

**Release Readiness:** 🚫 **NO GO**

### Critical Blockers:
1. **Data Leak:** RLS policy on `app_users` is not preventing unauthenticated access (Test 6.2).
2. **Core Feature Failure:** The core functionality of "Creating a Schedule Draft" is completely broken (Tests 3.1 - 3.6).
3. **Custom API Latency:** Admin user creation taking ~7 seconds is a significant bottleneck.

**Recommendations:**
Halt deployment to production. Prioritize patching the Supabase RLS policies for unauthenticated roles. Following the security patch, investigate the Supabase database logs for the `400 Bad Request` errors on the `schedule_drafts` table to correct the frontend JSON payloads. Re-run test suite upon completion.
