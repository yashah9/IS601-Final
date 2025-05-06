# Event Manager

## Overview

User Management System is a Python-based FastAPI application designed to manage user accounts, roles, authentication, and profile information. It integrates PostgreSQL for data storage and leverages JWT tokens for secure user authentication.

## Features

- **User Registration & Authentication**
  - Users can register and authenticate via JWT tokens.
  - Roles such as ADMIN and MANAGER are supported with role-based access control.

- **Email Verification**
  - Users must verify their email to complete registration.
  - Email verification is managed using external email services like Mailtrap for testing.

- **Profile Management**
  - Users can set and update their profile information, including nickname, profile picture URL, and social media URLs.

- **Password Validation**
  - Strong password validation is enforced during registration and profile update.

- **Unique Username Validation**
  - The application ensures that all usernames (nicknames) are unique.

## The submission meets the following goals:

Fixed 5+ QA Issues/Bugs across the code.
Implements a NEW feature Profile Picture Upload with Minio into the existing code.
Created 10+ NEW Tests for the new feature implemented and others that already existed.
Includes a Reflection Document for the course.

## [Minio Feature](https://github.com/yashah9/IS601-Final/issues/11)


### 🔧 Setup
	•	Libraries Used:
	•	minio: Official SDK for interacting with MinIO.
	•	os: Used to access environment variables for credentials.
	•	settings.config: Loads MinIO configuration values such as endpoint, bucket name, and SSL usage.
	•	MinIO Client Initialization:
	•	The Minio client is instantiated using environment variables (MINIO_ROOT_USER, MINIO_ROOT_PASSWORD) and app settings (like endpoint and SSL toggle).

### 🪣 Bucket Management
	•	Function: ensure_bucket_exists(bucket_name)
	•	Checks if a bucket exists in MinIO.
	•	If it does not, the function creates the bucket.
	•	Handles and logs any S3Error exceptions.

### 🖼️ File Upload
	•	Function: upload_profile_picture(file_data, file_name)
	•	Validates file extensions (jpg, jpeg, png, gif).
	•	Uploads the file using put_object with automatic size handling.
	•	Returns a direct file URL if successful.
	•	Raises a ValueError for unsupported file types and handles S3Error exceptions during upload.



### Issues Solved


### 1. [Profile picture validation](https://github.com/yashah9/IS601-Final/issues/1)
   - **Problem**: The image uploaded was not in correct format as needed.
   - **Solution**: Fixed the code so only specific image types can be uploaded.

### 2. [Password Reset & Mailtrap Setup](https://github.com/yashah9/IS601-Final/issues/16)
   - **Problem**: Password reset wasn't working and also emails were not sent.
   - **Solution**: Corrected the logic to ensure consistent password handling across the registration process and also setted up mailtrap.

### 3. [Password Validation](https://github.com/yashah9/IS601-Final/issues/6)
   - **Problem**: The application lacked proper password validation.
   - **Solution**: Implemented password strength validation to ensure security and user compliance.

### 4. [Role Management](https://github.com/yashah9/IS601-Final/issues/8)
   - **Problem**:  Only had default role.
   - **Solution**: Fixed critical bug where users were created without default roles.

### 5. [Unverified Email Users](https://github.com/yashah9/IS601-Final/issues/3)
   - **Problem**: Users with unverified emails could update their profiles, leading to potential security issues.
   - **Solution**: Added a check to ensure that only verified email users can update their profile information.

### 6. [Unique Username (Nickname) Validation without infinite loop](https://github.com/yashah9/IS601-Final/issues/18)
   - **Problem**: Users could insert the same nickname, which was invalid and kept generating new nickname everytime.
   - **Solution**: Added unique nickname validation to prevent duplicate usernames during registration and also only 1 nickname per user.

## Tests Created 

### [Minio Tests](https://github.com/yashah9/IS601-Final/blob/main/tests/test_minio.py)
### [User Role tests](https://github.com/yashah9/IS601-Final/blob/file-upload-testcase/tests/test_api/test_users_api.py)

## Final Report
[Link to report](https://docs.google.com/document/d/1i6nceZyJk_IJ1KxSrgse8WizR98XxTYEnV8c7nLSybM/edit?usp=sharing)

## Docker Hub Deploy
[Link to deployed project](https://hub.docker.com/r/yashshah0910/is601_final_api)
## Image on dockerhub
<img width="1512" alt="image" src="https://github.com/user-attachments/assets/b17c865a-817f-433e-819e-5c7bf49baf16" />
