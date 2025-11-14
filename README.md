# Smart Student Management System

## Project Overview

This is a web-based Student Management System built with Flask, designed to help schools and institutes efficiently manage student records. The application allows administrators to securely add, view, edit, and delete student information online, replacing manual record-keeping with a digital, accessible solution.

### Key Features
- **Secure Admin Authentication**: Register and login functionality with password hashing and session management.
- **CRUD Operations**: Full Create, Read, Update, Delete operations for student records.
- **Student Attributes**: Name, Age, Course, Email (unique), Contact, Enrollment Date.
- **Responsive UI**: Bootstrap-powered interface for desktop and mobile compatibility.
- **Dashboard**: Quick stats and navigation to main functions.
- **Data Validation**: Form validation for secure data entry.

### Tech Stack
- **Backend**: Python Flask with extensions (Flask-SQLAlchemy, Flask-WTF, Flask-Login)
- **Frontend**: HTML5, CSS3, JavaScript, Bootstrap 5
- **Database**: SQLite
- **Hosting**: Designed for PythonAnywhere or similar platforms

## Prerequisites and Required Items

- **Python**: Version 3.7 or higher
- **Pip**: Python package installer (usually comes with Python)
- **Git**: For version control (optional but recommended)
- **Web Browser**: Any modern browser for testing the application
- **Operating System**: Windows, macOS, or Linux

## Installation Instructions

1. **Clone or Download the Project**:
   ```
   git clone <repository-url>
   cd flask-student-management
   ```
   Or download and extract the ZIP file to your desired directory.

2. **Set Up Virtual Environment** (Recommended):
   ```
   python -m venv venv
   venv\Scripts\activate  # On Windows
   # source venv/bin/activate  # On macOS/Linux
   ```

3. **Install Dependencies**:
   ```
   pip install -r requirements.txt
   ```
   This will install all required packages including Flask, SQLAlchemy, Flask-WTF, Flask-Login, and Werkzeug.

## Configuration Details

### Application Configuration
The main configuration is handled in `app.py`:

- **SECRET_KEY**: Change this in production for security (currently set to 'your-secret-key-change-in-production')
- **SQLALCHEMY_DATABASE_URI**: SQLite database file 'students.db'
- **UPLOAD_FOLDER**: For profile pictures (static/uploads)
- **Debug Mode**: Enabled for development

### Database Models

#### User Model (for Admin Authentication)
- `id`: Primary key (Integer)
- `username`: Unique username (String, 150 chars)
- `password`: Hashed password (String, 150 chars)

#### Student Model
- `id`: Primary key (Integer)
- `name`: Student full name (String, 150 chars)
- `age`: Student age (Integer)
- `course`: Course name (String, 150 chars) - Predefined options: Computer Science, Mathematics, Engineering
- `email`: Unique email address (String, 150 chars)
- `contact`: Contact number (String, 20 chars)
- `enrollment_date`: Auto-generated timestamp (DateTime)
- `profile_picture`: Optional image path (String, 300 chars)

### Routes and Endpoints
- `/`: Homepage
- `/register`: Admin registration
- `/login`: Admin login
- `/logout`: Admin logout
- `/dashboard`: Main dashboard with stats
- `/add_student`: Add new student form
- `/view_students`: List all students
- `/edit_student/<id>`: Edit student by ID
- `/delete_student/<id>`: Delete student by ID (POST request)

## Running the Application

1. **Initialize Database**:
   When you first run the app, the database and tables will be created automatically.

2. **Start the Development Server**:
   ```
   python app.py
   ```
   The application will start on `http://127.0.0.1:8000` (configured for port 8000).

3. **Access the Application**:
   Open your web browser and navigate to `http://127.0.0.1:8000`.

4. **Initial Setup**:
   - First, register a new admin account at `/register`
   - Then login at `/login`
   - Access the dashboard to start managing students

## Usage Guide

### Admin Registration and Login
1. Navigate to the homepage and click "Register" or "Login"
2. For registration: Enter a unique username and password
3. For login: Enter your credentials
4. Upon successful authentication, you'll be redirected to the dashboard

### Dashboard
- View summary statistics: Total students, Active enrollments, Courses offered
- Use buttons to "Add New Student" or "View All Students"
- Recent additions table shows the last 5 enrolled students

### Adding a Student
1. From dashboard, click "Add New Student"
2. Fill in the form fields:
   - Name: Full name (required)
   - Age: Numeric value between 1-120 (required)
   - Course: Select from dropdown: Computer Science, Mathematics, Engineering (required)
   - Email: Unique email address (required, must be valid format)
   - Contact: Phone number (required)
3. Click "Submit" to add the student
4. Success message will appear, and you'll be redirected to dashboard

### Viewing Students
1. From dashboard, click "View All Students"
2. See all students in a table with columns: ID, Name, Age, Course, Email, Contact, Enrollment Date, Actions
3. Use "Edit" button to modify student details
4. Use "Delete" button to remove student (confirmation required)
5. "Back to Dashboard" returns to main dashboard

### Editing a Student
1. From view students page, click "Edit" next to any student
2. Modify any fields as needed
3. Click "Submit" to save changes
4. Success message appears, redirected to view students page

### Deleting a Student
1. From view students page, click "Delete" next to any student
2. Confirm deletion in browser popup
3. Student is permanently removed, success message appears

## Troubleshooting

### Common Issues

1. **"Permission denied" when running app**:
   - Try changing the port: Edit `app.py` and modify `app.run(port=8000)` to a different port like 5000 or 3000
   - Ensure no other applications are using the same port

2. **"Module not found" errors**:
   - Ensure virtual environment is activated
   - Reinstall dependencies: `pip install -r requirements.txt`

3. **Database errors**:
   - Delete `students.db` file and restart the app to recreate tables
   - Ensure write permissions in the project directory

4. **Form validation errors**:
   - Check that email addresses are unique and properly formatted
   - Ensure age is a number between 1-120
   - All required fields must be filled

5. **Login issues**:
   - Verify username and password are correct
   - Check if account was registered successfully
   - Clear browser cache/cookies if persistent issues

6. **Static files not loading (CSS/JS)**:
   - Ensure `static` folder exists with proper structure
   - Check browser console for 404 errors on static resources

### Debug Mode
- The app runs in debug mode by default (`debug=True`)
- This provides detailed error messages in the browser
- For production, set `debug=False` and use a proper web server

### Logs and Error Messages
- Check terminal/console output for Flask error messages
- Browser developer tools (F12) can show network errors or JavaScript issues

## Additional Notes

### Security Best Practices
- Change the SECRET_KEY in production
- Use HTTPS in production environments
- Regularly update dependencies for security patches
- Implement rate limiting for authentication endpoints if needed

### Performance Considerations
- SQLite is suitable for small to medium-sized applications
- For larger deployments, consider PostgreSQL or MySQL
- Implement pagination for very large student lists

### Deployment
- For production deployment on PythonAnywhere:
  1. Upload all files to PythonAnywhere
  2. Install dependencies in virtual environment
  3. Configure WSGI file to point to `app` object in `app.py`
  4. Database will be created automatically on first run

### Future Enhancements
- Add search and filter functionality
- Implement pagination for large datasets
- Add CSV export/import features
- Include student profile picture uploads
- Add email notifications for new registrations

### Support
If you encounter issues not covered in this manual, check the Flask documentation or create an issue in the project repository.

---

**Version**: 1.0.0
**Last Updated**: November 2025
**License**: MIT