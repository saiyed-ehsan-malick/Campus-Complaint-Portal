# Campus-Complaint-Portal
A fully functional College Complaint Website where students can submit complaints related to hostel, academics, food, teacher behavior, ragging, and other issues. The portal includes a password-protected admin panel and an AI Chat simulation to provide guidance for complaints.




<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Campus Complaint Portal</title>
    <style>
        :root {
            --primary-color: #3498db;
            --secondary-color: #2c3e50;
            --accent-color: #e74c3c;
            --light-color: #ecf0f1;
            --dark-color: #2c3e50;
            --success-color: #2ecc71;
            --warning-color: #f39c12;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
        }
        
        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        header {
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            color: white;
            padding: 1.5rem 0;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        
        header h1 {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 0.5rem;
        }
        
        nav {
            background-color: var(--secondary-color);
            padding: 0.5rem 0;
        }
        
        .nav-container {
            display: flex;
            justify-content: center;
        }
        
        .nav-btn {
            background: none;
            border: none;
            color: white;
            padding: 0.5rem 1rem;
            margin: 0 0.5rem;
            cursor: pointer;
            font-size: 1rem;
            border-radius: 4px;
            transition: background-color 0.3s;
        }
        
        .nav-btn:hover, .nav-btn.active {
            background-color: rgba(255, 255, 255, 0.2);
        }
        
        .page {
            display: none;
            padding: 2rem 0;
        }
        
        .page.active {
            display: block;
        }
        
        .card {
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            padding: 2rem;
            margin-bottom: 2rem;
        }
        
        h2 {
            color: var(--secondary-color);
            margin-bottom: 1.5rem;
            text-align: center;
        }
        
        .form-group {
            margin-bottom: 1.5rem;
        }
        
        label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
        }
        
        input, select, textarea {
            width: 100%;
            padding: 0.75rem;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 1rem;
        }
        
        textarea {
            min-height: 120px;
            resize: vertical;
        }
        
        .checkbox-group {
            display: flex;
            align-items: center;
        }
        
        .checkbox-group input {
            width: auto;
            margin-right: 0.5rem;
        }
        
        button {
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 0.75rem 1.5rem;
            font-size: 1rem;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        
        button:hover {
            background-color: #2980b9;
        }
        
        .btn-danger {
            background-color: var(--accent-color);
        }
        
        .btn-danger:hover {
            background-color: #c0392b;
        }
        
        .btn-success {
            background-color: var(--success-color);
        }
        
        .btn-success:hover {
            background-color: #27ae60;
        }
        
        .admin-actions {
            display: flex;
            gap: 1rem;
            margin-bottom: 1.5rem;
            justify-content: center;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 1.5rem;
        }
        
        th, td {
            padding: 0.75rem;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }
        
        th {
            background-color: var(--light-color);
            font-weight: 600;
        }
        
        tr:hover {
            background-color: #f9f9f9;
        }
        
        .complaint-id {
            font-weight: 600;
            color: var(--primary-color);
        }
        
        .confirmation {
            background-color: var(--success-color);
            color: white;
            padding: 1.5rem;
            border-radius: 8px;
            text-align: center;
            margin-bottom: 2rem;
        }
        
        .login-form {
            max-width: 400px;
            margin: 0 auto;
        }
        
        .dynamic-field {
            display: none;
        }
        
        .dynamic-field.active {
            display: block;
        }
        
        .file-preview {
            margin-top: 0.5rem;
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
        }
        
        .file-preview-item {
            position: relative;
            width: 100px;
            height: 100px;
            border-radius: 4px;
            overflow: hidden;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        
        .file-preview-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .file-preview-item .remove-btn {
            position: absolute;
            top: 4px;
            right: 4px;
            background: rgba(255,255,255,0.8);
            border: none;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            font-size: 12px;
        }
        
        .filter-bar {
            display: flex;
            gap: 1rem;
            margin-bottom: 1.5rem;
            flex-wrap: wrap;
        }
        
        .filter-bar select {
            flex: 1;
            min-width: 150px;
        }
        
        .forgot-password {
            text-align: center;
            margin-top: 1rem;
        }
        
        .forgot-password a {
            color: var(--primary-color);
            text-decoration: none;
        }
        
        .forgot-password a:hover {
            text-decoration: underline;
        }
        
        .ai-chat-btn {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 60px;
            height: 60px;
            background-color: var(--primary-color);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
            z-index: 1000;
        }
        
        .ai-chat-btn img {
            width: 70%;
            height: 70%;
        }
        
        .chat-popup {
            position: fixed;
            bottom: 90px;
            right: 20px;
            width: 350px;
            height: 450px;
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            display: flex;
            flex-direction: column;
            z-index: 1000;
            display: none;
        }
        
        .chat-header {
            background-color: var(--primary-color);
            color: white;
            padding: 15px;
            border-top-left-radius: 10px;
            border-top-right-radius: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .chat-header h3 {
            margin: 0;
        }
        
        .chat-close {
            background: none;
            border: none;
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
        }
        
        .chat-messages {
            flex: 1;
            padding: 15px;
            overflow-y: auto;
        }
        
        .message {
            margin-bottom: 15px;
            padding: 10px;
            border-radius: 8px;
            max-width: 80%;
        }
        
        .user-message {
            background-color: #e3f2fd;
            margin-left: auto;
        }
        
        .ai-message {
            background-color: #f1f1f1;
        }
        
        .chat-input {
            display: flex;
            padding: 10px;
            border-top: 1px solid #ddd;
        }
        
        .chat-input input {
            flex: 1;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 20px;
            margin-right: 10px;
        }
        
        .chat-input button {
            padding: 10px 15px;
            border-radius: 20px;
        }
        
        .otp-form {
            display: none;
        }
        
        @media (max-width: 768px) {
            .admin-actions, .filter-bar {
                flex-direction: column;
            }
            
            table {
                display: block;
                overflow-x: auto;
            }
            
            .file-preview-item {
                width: 80px;
                height: 80px;
            }
            
            .chat-popup {
                width: 300px;
                height: 400px;
                right: 10px;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <h1>Campus Complaint Portal</h1>
        </div>
    </header>
    
    <nav>
        <div class="container nav-container">
            <button class="nav-btn active" data-page="home">Home</button>
            <button class="nav-btn" data-page="submit">Submit Complaint</button>
            <button class="nav-btn" data-page="admin">Admin Login</button>
        </div>
    </nav>
    
    <main class="container">
        <!-- Home Page -->
        <section id="home" class="page active">
            <div class="card">
                <h2>Welcome to the Campus Complaint Portal</h2>
                <p>This portal allows students to submit complaints regarding various campus issues. Your feedback helps us improve the campus environment for everyone.</p>
                <p>To submit a complaint, click on the "Submit Complaint" tab in the navigation menu.</p>
                <p>If you are an administrator, please use the "Admin Login" tab to access the complaint management system.</p>
            </div>
            
            <div class="card">
                <h2>Recent Complaints</h2>
                <p>Students cannot view complaints. Only authorized administrators have access to the complaint database.</p>
                <p>If you have submitted a complaint, you will receive a confirmation with your unique Complaint ID for reference.</p>
            </div>
        </section>
        
        <!-- Complaint Submission Page -->
        <section id="submit" class="page">
            <div class="card">
                <h2>Submit a Complaint</h2>
                <form id="complaint-form">
                    <div class="form-group">
                        <label for="name">Name *</label>
                        <input type="text" id="name" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="rollno">Roll No *</label>
                        <input type="text" id="rollno" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="year">Year *</label>
                        <select id="year" required>
                            <option value="">Select Year</option>
                            <option value="1st">1st Year</option>
                            <option value="2nd">2nd Year</option>
                            <option value="3rd">3rd Year</option>
                            <option value="4th">4th Year</option>
                        </select>
                    </div>
                    
                    <div class="form-group">
                        <label for="college">College Name *</label>
                        <select id="college" required>
                            <option value="">Select College</option>
                            <option value="Engineering College">Engineering College</option>
                            <option value="Arts and Science College">Arts and Science College</option>
                            <option value="Medical College">Medical College</option>
                            <option value="Law College">Law College</option>
                            <option value="Business School">Business School</option>
                        </select>
                    </div>
                    
                    <div class="form-group">
                        <label for="department">Department *</label>
                        <select id="department" required>
                            <option value="">Select Department</option>
                            <option value="Computer Science">Computer Science</option>
                            <option value="Electrical Engineering">Electrical Engineering</option>
                            <option value="Mechanical Engineering">Mechanical Engineering</option>
                            <option value="Physics">Physics</option>
                            <option value="Chemistry">Chemistry</option>
                            <option value="Mathematics">Mathematics</option>
                            <option value="English">English</option>
                            <option value="History">History</option>
                        </select>
                    </div>
                    
                    <div class="form-group">
                        <label for="category">Complaint Category *</label>
                        <select id="category" required>
                            <option value="">Select Category</option>
                            <option value="Hostel">Hostel</option>
                            <option value="Food">Food/Mess</option>
                            <option value="Warden">Warden</option>
                            <option value="Ragging">Ragging/Harassment</option>
                            <option value="Teacher">Teacher</option>
                            <option value="Class">Class/Academic</option>
                            <option value="Other">Other</option>
                        </select>
                    </div>
                    
                    <!-- Dynamic Fields Container -->
                    <div id="dynamic-fields">
                        <!-- Hostel Fields -->
                        <div class="dynamic-field" data-category="Hostel">
                            <div class="form-group">
                                <label for="roomNo">Room No</label>
                                <input type="text" id="roomNo">
                            </div>
                            <div class="form-group">
                                <label for="messComplaints">Mess Complaints</label>
                                <select id="messComplaints">
                                    <option value="">Select Issue</option>
                                    <option value="Quality">Food Quality</option>
                                    <option value="Hygiene">Hygiene Issues</option>
                                    <option value="Timing">Timing Issues</option>
                                    <option value="Other">Other</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label for="wardenBehaviour">Warden Behaviour Issues</label>
                                <textarea id="wardenBehaviour"></textarea>
                            </div>
                            <div class="form-group">
                                <label for="utilityIssues">Water/Electricity Issues</label>
                                <select id="utilityIssues">
                                    <option value="">Select Issue</option>
                                    <option value="Water">Water Supply</option>
                                    <option value="Electricity">Electricity Supply</option>
                                    <option value="Both">Both Water and Electricity</option>
                                </select>
                            </div>
                        </div>
                        
                        <!-- Class/Academic Fields -->
                        <div class="dynamic-field" data-category="Class">
                            <div class="form-group">
                                <label for="subject">Subject</label>
                                <input type="text" id="subject">
                            </div>
                            <div class="form-group">
                                <label for="teacherName">Teacher Name</label>
                                <input type="text" id="teacherName">
                            </div>
                            <div class="form-group">
                                <label for="incidentDate">Date of Incident</label>
                                <input type="date" id="incidentDate">
                            </div>
                            <div class="form-group">
                                <label for="attendanceIssue">Late Attendance Marking</label>
                                <select id="attendanceIssue">
                                    <option value="">Select Issue</option>
                                    <option value="Yes">Yes</option>
                                    <option value="No">No</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label for="teacherBehaviour">Teacher Behaviour Issues</label>
                                <textarea id="teacherBehaviour"></textarea>
                            </div>
                        </div>
                        
                        <!-- Ragging/Harassment Fields -->
                        <div class="dynamic-field" data-category="Ragging">
                            <div class="form-group">
                                <label for="witnessNames">Witness Names</label>
                                <input type="text" id="witnessNames" placeholder="Separate names with commas">
                            </div>
                            <div class="form-group">
                                <label for="incidentLocation">Incident Location</label>
                                <input type="text" id="incidentLocation">
                            </div>
                            <div class="form-group">
                                <label for="harassmentType">Type of Harassment</label>
                                <select id="harassmentType">
                                    <option value="">Select Type</option>
                                    <option value="Verbal">Verbal</option>
                                    <option value="Physical">Physical</option>
                                    <option value="Cyber">Cyber Bullying</option>
                                    <option value="Other">Other</option>
                                </select>
                            </div>
                        </div>
                        
                        <!-- Food/Mess Fields -->
                        <div class="dynamic-field" data-category="Food">
                            <div class="form-group">
                                <label for="messName">Mess Name</label>
                                <input type="text" id="messName">
                            </div>
                            <div class="form-group">
                                <label for="foodDate">Date of Incident</label>
                                <input type="date" id="foodDate">
                            </div>
                            <div class="form-group">
                                <label for="foodQuality">Food Quality Issues</label>
                                <select id="foodQuality">
                                    <option value="">Select Issue</option>
                                    <option value="Poor Quality">Poor Quality</option>
                                    <option value="Unhygienic">Unhygienic Preparation</option>
                                    <option value="Insufficient">Insufficient Quantity</option>
                                    <option value="Other">Other</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label for="illness">Illness After Eating</label>
                                <select id="illness">
                                    <option value="">Select Option</option>
                                    <option value="Yes">Yes</option>
                                    <option value="No">No</option>
                                </select>
                            </div>
                        </div>
                    </div>
                    
                    <div class="form-group">
                        <label for="details">Complaint Details *</label>
                        <textarea id="details" required></textarea>
                    </div>
                    
                    <div class="form-group">
                        <label for="evidence">Upload Evidence (Images, Videos, Audio)</label>
                        <input type="file" id="evidence" multiple accept="image/*,video/*,audio/*">
                        <div class="file-preview" id="file-preview"></div>
                    </div>
                    
                    <div class="form-group checkbox-group">
                        <input type="checkbox" id="anonymous">
                        <label for="anonymous">Submit as Anonymous (Hide Personal Details)</label>
                    </div>
                    
                    <button type="submit">Submit Complaint</button>
                </form>
            </div>
            
            <div id="confirmation" class="confirmation" style="display: none;">
                <h2>Complaint Submitted Successfully!</h2>
                <p>Your Complaint ID is: <span id="complaint-id" class="complaint-id"></span></p>
                <p>Thank you for your feedback. We will review your complaint and take appropriate action.</p>
            </div>
        </section>
        
        <!-- Admin Login Page -->
        <section id="admin" class="page">
            <div class="card">
                <h2>Admin Login</h2>
                <form id="login-form" class="login-form">
                    <div class="form-group">
                        <label for="username">Username</label>
                        <input type="text" id="username" required>
                    </div>
                    <div class="form-group">
                        <label for="password">Password</label>
                        <input type="password" id="password" required>
                    </div>
                    <button type="submit">Login</button>
                </form>
                
                <div class="forgot-password">
                    <a href="#" id="forgot-password-link">Forgot Username/Password?</a>
                </div>
            </div>
            
            <div id="forgot-password-form" class="card" style="display: none;">
                <h2>Reset Password</h2>
                <form id="reset-form">
                    <div class="form-group">
                        <label for="phone">Registered Phone Number</label>
                        <input type="tel" id="phone" required>
                    </div>
                    <div class="form-group">
                        <label for="email">Registered Email ID</label>
                        <input type="email" id="email" required>
                    </div>
                    <button type="submit">Send OTP</button>
                </form>
                
                <div id="otp-form" class="otp-form">
                    <div class="form-group">
                        <label for="otp">Enter 6-digit OTP</label>
                        <input type="text" id="otp" maxlength="6" required>
                    </div>
                    <div class="form-group">
                        <label for="new-password">New Password</label>
                        <input type="password" id="new-password" required>
                    </div>
                    <button type="button" id="verify-otp">Verify OTP</button>
                </div>
            </div>
            
            <div id="admin-panel" style="display: none;">
                <div class="admin-actions">
                    <button id="export-btn" class="btn-success">Export as JSON</button>
                    <button id="clear-btn" class="btn-danger">Clear All Complaints</button>
                </div>
                
                <div class="filter-bar">
                    <select id="filter-college">
                        <option value="">Filter by College</option>
                    </select>
                    <select id="filter-department">
                        <option value="">Filter by Department</option>
                    </select>
                    <select id="filter-category">
                        <option value="">Filter by Category</option>
                    </select>
                    <select id="filter-status">
                        <option value="">Filter by Status</option>
                        <option value="Pending">Pending</option>
                        <option value="In Progress">In Progress</option>
                        <option value="Resolved">Resolved</option>
                    </select>
                    <button id="apply-filters" class="btn-success">Apply Filters</button>
                    <button id="clear-filters" class="btn-danger">Clear Filters</button>
                </div>
                
                <div class="card">
                    <h2>All Complaints</h2>
                    <table id="complaints-table">
                        <thead>
                            <tr>
                                <th>ID</th>
                                <th>Student</th>
                                <th>College</th>
                                <th>Department</th>
                                <th>Category</th>
                                <th>Details</th>
                                <th>Date</th>
                                <th>Status</th>
                                <th>Anonymous</th>
                            </tr>
                        </thead>
                        <tbody>
                            <!-- Complaints will be populated here -->
                        </tbody>
                    </table>
                </div>
            </div>
        </section>
    </main>

    <!-- AI Chat Button -->
    <div class="ai-chat-btn" id="ai-chat-btn">
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="white">
            <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8zm-1-13h2v6h-2zm0 8h2v2h-2z"/>
        </svg>
    </div>

    <!-- AI Chat Popup -->
    <div class="chat-popup" id="chat-popup">
        <div class="chat-header">
            <h3>Campus Assistant</h3>
            <button class="chat-close" id="chat-close">&times;</button>
        </div>
        <div class="chat-messages" id="chat-messages">
            <div class="message ai-message">
                Hello! I'm your campus assistant. How can I help you with your complaint today?
            </div>
        </div>
        <div class="chat-input">
            <input type="text" id="chat-input" placeholder="Type your message here...">
            <button id="chat-send">Send</button>
        </div>
    </div>

    <script>
        // Navigation
        document.querySelectorAll('.nav-btn').forEach(button => {
            button.addEventListener('click', () => {
                // Remove active class from all buttons and pages
                document.querySelectorAll('.nav-btn').forEach(btn => btn.classList.remove('active'));
                document.querySelectorAll('.page').forEach(page => page.classList.remove('active'));
                
                // Add active class to clicked button
                button.classList.add('active');
                
                // Show corresponding page
                const pageId = button.getAttribute('data-page');
                document.getElementById(pageId).classList.add('active');
            });
        });
        
        // Dynamic form fields based on category
        document.getElementById('category').addEventListener('change', function() {
            // Hide all dynamic fields
            document.querySelectorAll('.dynamic-field').forEach(field => {
                field.classList.remove('active');
            });
            
            // Show fields for selected category
            const selectedCategory = this.value;
            if (selectedCategory) {
                const fieldToShow = document.querySelector(`.dynamic-field[data-category="${selectedCategory}"]`);
                if (fieldToShow) {
                    fieldToShow.classList.add('active');
                }
            }
        });
        
        // File upload preview
        document.getElementById('evidence').addEventListener('change', function(e) {
            const previewContainer = document.getElementById('file-preview');
            previewContainer.innerHTML = '';
            
            if (this.files) {
                Array.from(this.files).forEach(file => {
                    const previewItem = document.createElement('div');
                    previewItem.className = 'file-preview-item';
                    
                    if (file.type.startsWith('image/')) {
                        const img = document.createElement('img');
                        img.src = URL.createObjectURL(file);
                        previewItem.appendChild(img);
                    } else {
                        const icon = document.createElement('div');
                        icon.textContent = '📄 ' + file.name;
                        icon.style.padding = '10px';
                        icon.style.textAlign = 'center';
                        previewItem.appendChild(icon);
                    }
                    
                    const removeBtn = document.createElement('button');
                    removeBtn.className = 'remove-btn';
                    removeBtn.textContent = '×';
                    removeBtn.addEventListener('click', () => {
                        previewItem.remove();
                        // Create a new FileList without this file would be complex
                        // So we'll handle this during form submission
                    });
                    
                    previewItem.appendChild(removeBtn);
                    previewContainer.appendChild(previewItem);
                });
            }
        });
        
        // College and department mapping for HOD and Technical Director
        const collegeData = {
            "Engineering College": {
                departments: ["Computer Science", "Electrical Engineering", "Mechanical Engineering"],
                hod: "Dr. Rajesh Kumar",
                director: "Prof. Sanjay Patel"
            },
            "Arts and Science College": {
                departments: ["Physics", "Chemistry", "Mathematics", "English", "History"],
                hod: "Dr. Meena Sharma",
                director: "Prof. Anil Desai"
            },
            "Medical College": {
                departments: ["Medicine", "Surgery", "Dentistry"],
                hod: "Dr. Vijay Malhotra",
                director: "Prof. Rekha Singh"
            },
            "Law College": {
                departments: ["Criminal Law", "Corporate Law", "International Law"],
                hod: "Dr. Priya Joshi",
                director: "Prof. Arun Verma"
            },
            "Business School": {
                departments: ["Finance", "Marketing", "Human Resources"],
                hod: "Dr. Sameer Gupta",
                director: "Prof. Neeta Kapoor"
            }
        };
        
        // Populate college dropdown and update department options
        const collegeSelect = document.getElementById('college');
        Object.keys(collegeData).forEach(college => {
            const option = document.createElement('option');
            option.value = college;
            option.textContent = college;
            collegeSelect.appendChild(option);
        });
        
        collegeSelect.addEventListener('change', function() {
            const departmentSelect = document.getElementById('department');
            const filterDepartment = document.getElementById('filter-department');
            
            // Clear previous options except the first one
            while (departmentSelect.options.length > 1) {
                departmentSelect.remove(1);
            }
            while (filterDepartment.options.length > 1) {
                filterDepartment.remove(1);
            }
            
            // Add new options based on selected college
            if (this.value && collegeData[this.value]) {
                collegeData[this.value].departments.forEach(dept => {
                    const option = document.createElement('option');
                    option.value = dept;
                    option.textContent = dept;
                    departmentSelect.appendChild(option);
                    
                    const filterOption = document.createElement('option');
                    filterOption.value = dept;
                    filterOption.textContent = dept;
                    filterDepartment.appendChild(filterOption);
                });
            }
        });
        
        // Populate filter dropdowns
        const filterCollege = document.getElementById('filter-college');
        Object.keys(collegeData).forEach(college => {
            const option = document.createElement('option');
            option.value = college;
            option.textContent = college;
            filterCollege.appendChild(option);
        });
        
        const filterCategory = document.getElementById('filter-category');
        document.getElementById('category').querySelectorAll('option').forEach(option => {
            if (option.value) {
                const filterOption = document.createElement('option');
                filterOption.value = option.value;
                filterOption.textContent = option.value;
                filterCategory.appendChild(filterOption);
            }
        });
        
        // Complaint Form Submission
        document.getElementById('complaint-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Generate a unique complaint ID
            const complaintId = 'CC' + Date.now();
            
            // Get college data
            const college = document.getElementById('college').value;
            const department = document.getElementById('department').value;
            const hod = collegeData[college]?.hod || 'Not specified';
            const director = collegeData[college]?.director || 'Not specified';
            
            // Create complaint object
            const complaint = {
                id: complaintId,
                name: document.getElementById('name').value,
                rollno: document.getElementById('rollno').value,
                year: document.getElementById('year').value,
                college: college,
                department: department,
                hod: hod,
                director: director,
                category: document.getElementById('category').value,
                details: document.getElementById('details').value,
                anonymous: document.getElementById('anonymous').checked,
                date: new Date().toLocaleString(),
                status: 'Pending'
            };
            
            // Add dynamic field data based on category
            const category = complaint.category;
            if (category === 'Hostel') {
                complaint.roomNo = document.getElementById('roomNo').value;
                complaint.messComplaints = document.getElementById('messComplaints').value;
                complaint.wardenBehaviour = document.getElementById('wardenBehaviour').value;
                complaint.utilityIssues = document.getElementById('utilityIssues').value;
            } else if (category === 'Class') {
                complaint.subject = document.getElementById('subject').value;
                complaint.teacherName = document.getElementById('teacherName').value;
                complaint.incidentDate = document.getElementById('incidentDate').value;
                complaint.attendanceIssue = document.getElementById('attendanceIssue').value;
                complaint.teacherBehaviour = document.getElementById('teacherBehaviour').value;
            } else if (category === 'Ragging') {
                complaint.witnessNames = document.getElementById('witnessNames').value;
                complaint.incidentLocation = document.getElementById('incidentLocation').value;
                complaint.harassmentType = document.getElementById('harassmentType').value;
            } else if (category === 'Food') {
                complaint.messName = document.getElementById('messName').value;
                complaint.foodDate = document.getElementById('foodDate').value;
                complaint.foodQuality = document.getElementById('foodQuality').value;
                complaint.illness = document.getElementById('illness').value;
            }
            
            // Get existing complaints or initialize empty array
            const complaints = JSON.parse(localStorage.getItem('complaints')) || [];
            
            // Add new complaint
            complaints.push(complaint);
            
            // Save back to localStorage
            localStorage.setItem('complaints', JSON.stringify(complaints));
            
            // Show confirmation
            document.getElementById('complaint-id').textContent = complaintId;
            document.getElementById('confirmation').style.display = 'block';
            
            // Reset form
            this.reset();
            document.querySelectorAll('.dynamic-field').forEach(field => {
                field.classList.remove('active');
            });
            document.getElementById('file-preview').innerHTML = '';
            
            // Scroll to confirmation
            document.getElementById('confirmation').scrollIntoView({ behavior: 'smooth' });
        });
        
        // Admin Login
        document.getElementById('login-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            if (username === 'admin' && password === 'admin123') {
                // Show admin panel
                document.getElementById('admin-panel').style.display = 'block';
                
                // Load complaints
                loadComplaints();
            } else {
                alert('Incorrect username or password. Please try again.');
            }
        });
        
        // Forgot Password Link
        document.getElementById('forgot-password-link').addEventListener('click', function(e) {
            e.preventDefault();
            document.getElementById('login-form').style.display = 'none';
            document.getElementById('forgot-password-form').style.display = 'block';
        });
        
        // Reset Password Form
        document.getElementById('reset-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const phone = document.getElementById('phone').value;
            const email = document.getElementById('email').value;
            
            // Generate a 6-digit OTP
            const otp = Math.floor(100000 + Math.random() * 900000);
            alert(`Your OTP is: ${otp}\n(In a real application, this would be sent to your phone/email)`);
            
            // Store OTP for verification
            localStorage.setItem('resetOTP', otp);
            
            // Show OTP form
            document.getElementById('otp-form').style.display = 'block';
        });
        
        // Verify OTP
        document.getElementById('verify-otp').addEventListener('click', function() {
            const enteredOTP = document.getElementById('otp').value;
            const storedOTP = localStorage.getItem('resetOTP');
            const newPassword = document.getElementById('new-password').value;
            
            if (enteredOTP === storedOTP) {
                alert('Password reset successfully! You can now login with your new password.');
                
                // In a real application, you would update the password here
                // For demo purposes, we'll just reset the form
                document.getElementById('reset-form').reset();
                document.getElementById('otp-form').style.display = 'none';
                document.getElementById('forgot-password-form').style.display = 'none';
                document.getElementById('login-form').style.display = 'block';
            } else {
                alert('Invalid OTP. Please try again.');
            }
        });
        
        // Load complaints into admin table
        function loadComplaints(filters = {}) {
            const complaints = JSON.parse(localStorage.getItem('complaints')) || [];
            const tableBody = document.querySelector('#complaints-table tbody');
            
            // Clear existing rows
            tableBody.innerHTML = '';
            
            // Apply filters
            let filteredComplaints = complaints;
            if (filters.college) {
                filteredComplaints = filteredComplaints.filter(c => c.college === filters.college);
            }
            if (filters.department) {
                filteredComplaints = filteredComplaints.filter(c => c.department === filters.department);
            }
            if (filters.category) {
                filteredComplaints = filteredComplaints.filter(c => c.category === filters.category);
            }
            if (filters.status) {
                filteredComplaints = filteredComplaints.filter(c => c.status === filters.status);
            }
            
            // Add each complaint to the table
            filteredComplaints.forEach(complaint => {
                const row = document.createElement('tr');
                
                row.innerHTML = `
                    <td>${complaint.id}</td>
                    <td>${complaint.anonymous ? 'Anonymous' : complaint.name}</td>
                    <td>${complaint.college}</td>
                    <td>${complaint.department}</td>
                    <td>${complaint.category}</td>
                    <td>${complaint.details.length > 50 ? complaint.details.substring(0, 50) + '...' : complaint.details}</td>
                    <td>${complaint.date}</td>
                    <td>${complaint.status}</td>
                    <td>${complaint.anonymous ? 'Yes' : 'No'}</td>
                `;
                
                tableBody.appendChild(row);
            });
        }
        
        // Apply filters
        document.getElementById('apply-filters').addEventListener('click', function() {
            const filters = {
                college: document.getElementById('filter-college').value,
                department: document.getElementById('filter-department').value,
                category: document.getElementById('filter-category').value,
                status: document.getElementById('filter-status').value
            };
            
            loadComplaints(filters);
        });
        
        // Clear filters
        document.getElementById('clear-filters').addEventListener('click', function() {
            document.getElementById('filter-college').value = '';
            document.getElementById('filter-department').value = '';
            document.getElementById('filter-category').value = '';
            document.getElementById('filter-status').value = '';
            
            loadComplaints();
        });
        
        // Export complaints as JSON
        document.getElementById('export-btn').addEventListener('click', function() {
            const complaints = JSON.parse(localStorage.getItem('complaints')) || [];
            
            if (complaints.length === 0) {
                alert('No complaints to export.');
                return;
            }
            
            const dataStr = JSON.stringify(complaints, null, 2);
            const dataUri = 'data:application/json;charset=utf-8,'+ encodeURIComponent(dataStr);
            
            const exportFileDefaultName = 'complaints.json';
            
            const linkElement = document.createElement('a');
            linkElement.setAttribute('href', dataUri);
            linkElement.setAttribute('download', exportFileDefaultName);
            linkElement.click();
        });
        
        // Clear all complaints
        document.getElementById('clear-btn').addEventListener('click', function() {
            if (confirm('Are you sure you want to clear all complaints? This action cannot be undone.')) {
                localStorage.removeItem('complaints');
                loadComplaints(); // Refresh the table
                alert('All complaints have been cleared.');
            }
        });
        
        // AI Chat functionality
        const chatBtn = document.getElementById('ai-chat-btn');
        const chatPopup = document.getElementById('chat-popup');
        const chatClose = document.getElementById('chat-close');
        const chatMessages = document.getElementById('chat-messages');
        const chatInput = document.getElementById('chat-input');
        const chatSend = document.getElementById('chat-send');
        
        chatBtn.addEventListener('click', () => {
            chatPopup.style.display = 'flex';
        });
        
        chatClose.addEventListener('click', () => {
            chatPopup.style.display = 'none';
        });
        
        chatSend.addEventListener('click', sendMessage);
        chatInput.addEventListener('keypress', (e) => {
            if (e.key === 'Enter') {
                sendMessage();
            }
        });
        
        function sendMessage() {
            const message = chatInput.value.trim();
            if (message === '') return;
            
            // Add user message to chat
            addMessage(message, 'user');
            chatInput.value = '';
            
            // Generate AI response
            setTimeout(() => {
                const aiResponse = generateAIResponse(message);
                addMessage(aiResponse, 'ai');
            }, 500);
        }
        
        function addMessage(text, sender) {
            const messageDiv = document.createElement('div');
            messageDiv.className = `message ${sender}-message`;
            messageDiv.textContent = text;
            chatMessages.appendChild(messageDiv);
            chatMessages.scrollTop = chatMessages.scrollHeight;
        }
        
        function generateAIResponse(message) {
            const lowerMessage = message.toLowerCase();
            
            if (lowerMessage.includes('hostel') || lowerMessage.includes('room')) {
                return "For hostel-related issues, please contact your warden or the hostel administration. Make sure to include your room number and specific details about the problem in your complaint.";
            } else if (lowerMessage.includes('food') || lowerMessage.includes('mess')) {
                return "For food quality issues, it's important to report them promptly. Include details about what you ate, when you ate it, and any symptoms you experienced. You can also contact the mess committee directly.";
            } else if (lowerMessage.includes('ragging') || lowerMessage.includes('harassment')) {
                return "Ragging is a serious offense. If you're experiencing or witnessing ragging, please report it immediately. Your complaint will be handled with strict confidentiality. You can also contact the anti-ragging helpline at 1800-180-5522.";
            } else if (lowerMessage.includes('teacher') || lowerMessage.includes('faculty')) {
                return "For issues with teachers, it's best to first discuss the matter with the department head. If the problem persists, you can file a formal complaint with specific details about the incident.";
            } else if (lowerMessage.includes('attendance') || lowerMessage.includes('class')) {
                return "Attendance issues should be addressed with your department administration. Make sure to provide specific details about the class, date, and teacher involved.";
            } else if (lowerMessage.includes('complaint') || lowerMessage.includes('submit')) {
                return "To submit a complaint, use the complaint form on this portal. Provide as much detail as possible, including relevant dates, times, and people involved. You can choose to submit anonymously if you prefer.";
            } else {
                return "I'm here to help with campus-related issues. Please provide more details about your concern, whether it's about hostel, food, teachers, classes, or any other campus matter.";
            }
        }
    </script>
</body>
</html>
