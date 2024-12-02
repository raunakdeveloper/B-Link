Welcome Page

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Welcome to URL Shortener</title>
    <style>
    body {
        font-family: Arial, sans-serif;
        padding: 4rem;
      }
      h1 {
        margin-bottom: 20px; /* Space below the heading */
      }
      .button-container {
        display: flex;
        gap: 20px; 
      }
      button {
        padding: 3px 8px;
      }
    </style>
  </head>
  <body>
    <h1>Welcome to URL Shortener</h1>
    <div class="button-container">
      <form action="/login" method="get">
        <button type="submit">Login</button>
      </form>
      <form action="/register" method="get">
        <button type="submit">Register</button>
      </form>
    </div>
  </body>
</html>

//login 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Login</title>
    <style>
      body {
        font-family: Arial, sans-serif;
        padding: 3rem;
      }
      .login-btn {
        margin-top: 20px;
        padding: 3px 8px;
        cursor: pointer;
      }
      .error {
        color: red; /* Style for error messages */
        margin-bottom: 10px;
      }
    </style>
</head>
<body>
    <h1>Login</h1>
    {% if error %}
        <div class="error">{{ error }}</div> <!-- Display the error message -->
    {% endif %}
    <form method="POST">
      <table>
        <tr>
          <td><label>Email:</label></td>
          <td><input type="email" name="email" required /></td>
        </tr>
        <tr>
          <td><label>Password:</label></td>
          <td><input type="password" name="password" required /></td>
        </tr>
        <tr>
          <td colspan="2">
            <button class="login-btn" type="submit">Login</button>
          </td>
        </tr>
      </table>
    </form>
    <p><a href="/register">Don't have an account? Register here</a></p>
</body>
</html>


// register 
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Register</title>
    <style>
      body {
        font-family: Arial, sans-serif;
        padding: 3rem;
      }
      .register-btn {
        margin-top: 20px;
        padding: 3px 8px;
        cursor: pointer;
      }
    </style>
  </head>
  <body>
    <h1>Register</h1>
    <form method="POST">
      <table>
        <tr>
          <td><label for="username">Username:</label></td>
          <td><input type="text" name="username" required /></td>
        </tr>
        <tr>
          <td><label for="email">Email:</label></td>
          <td><input type="email" name="email" required /></td>
        </tr>
        <tr>
          <td><label for="password">Password:</label></td>
          <td><input type="password" name="password" required /></td>
        </tr>
        <tr>
          <td colspan="2">
            <button class="register-btn" type="submit">Register</button>
          </td>
        </tr>
      </table>
    </form>
    <p><a href="/login">Already have an account? Login here</a></p>
  </body>
</html>

//otp-verfication
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Verify OTP</title>
    <style>
      body {
        font-family: Arial, sans-serif;
        padding: 3rem;
      }
      button {
        padding: 2px 8px;
        cursor: pointer;
        margin-top: 1rem;
      }
      a {
        display: block;
        text-decoration: none;
        margin-top: 1rem;
      }
    </style>
  </head>
  <body>
    <h1>Verify OTP</h1>
    <form method="POST">
      <label>Enter OTP:</label>
      <input type="text" name="otp" required /><br />
      <button type="submit">Verify</button>
    </form>
    <a href="/register">Resend OTP</a>
  </body>
</html>


// Main app Home Page

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>URL Shortener</title>
    <style>
      body {
        font-family: Arial, sans-serif;
        padding: 3rem;
      }
      h1 {
        color: #333;
      }
      form {
        margin-top: 20px;
      }
      a {
        text-decoration: none;
      }
      .dash-link {
        cursor: pointer;
      }
      @media (max-width: 500px) {
        .shortenbtn {
          margin-top: 1rem;
          cursor: pointer;
        }
      }
    </style>
  </head>
  <body>
    <h1>URL Shortener</h1>

    <form action="/shorten" method="POST">
      <input
        type="text"
        name="url"
        placeholder="Enter your URL here"
        required
      />
      <button class="shortenbtn" type="submit">Shorten</button>
    </form>

    <br /><br />

    <p>Total URLs shortened: {{ total_urls }}</p>
    <!-- Display total URLs -->

    <!-- Link to the dashboard -->
    <form action="/dashboard" method="get">
      <button class="dash-link" type="submit">Go to Dashboard</button>
    </form>
  </body>
</html>

//Shortened Page
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Shortened URL</title>
    <style>
      body {
        font-family: Arial, sans-serif;
        padding: 3rem;
      }
      a {
        text-decoration: none;
        color: #007bff;
      }
      .home-link {
        margin-top: 2rem;
        cursor: pointer;
      }
      .copybtn {
        cursor: pointer;
        margin-right: 0.5rem;
      }
      .sharebtn {
        cursor: pointer;
      }
      .controlbtn {
        display: inline;
        margin-left: 2rem;
      }
      @media (max-width: 500px) {
        .controlbtn {
          margin-top: 1rem;
          margin-left: 0;
          display: flex;
          gap: 10px;
        }
        .copybtn {
        margin-right: 0;
      }
      }
    </style>
  </head>
  <body>
    <h1>Shortened URL</h1>
    <p>{{ message if message else 'Your shortened URL is Ready.' }}</p>
    <a href="{{ short_url }}" target="_blank" id="short-url">{{ short_url }}</a>
    <div class="controlbtn">
      <button class="copybtn" onclick="copyToClipboard()">Copy</button>
      <button class="sharebtn" onclick="shareUrl()">Share</button>
    </div>

    <br />
    <form action="/" method="get">
      <button class="home-link" type="submit">Back to Home</button>
    </form>
    <script>
      function copyToClipboard() {
        const url = document.getElementById("short-url").textContent;
        navigator.clipboard
          .writeText(url)
          .then(() => {
            alert("URL copied to clipboard!");
          })
          .catch((err) => {
            console.error("Could not copy URL: ", err);
          });
      }

      function shareUrl() {
        const url = document.getElementById("short-url").textContent;
        if (navigator.share) {
          navigator
            .share({
              title: "Check out this shortened URL!",
              url: url,
            })
            .then(() => {
              console.log("URL shared successfully");
            })
            .catch((err) => {
              console.error("Error sharing URL:", err);
            });
        } else {
          alert("Sharing is not supported in this browser.");
        }
      }
    </script>
  </body>
</html>

//dashboard 
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Dashboard</title>
    <style>
      body {
        font-family: Arial, sans-serif;
        margin: 20px;
      }
      h1 {
        color: #333;
      }
      a {
        text-decoration: none;
      }
      table {
        width: 100%;
        border-collapse: collapse;
        margin-top: 20px;
      }
      th,
      td {
        border: 1px solid #ddd;
        padding: 8px;
        text-align: left;
      }
      th {
        background-color: #f2f2f2;
      }
      /* Set specific widths for table columns */
      th.original-url {
        width: 50%;
      }
      th.shortened-url,
      td.shortened-url {
        width: 25%;
        word-wrap: break-word;
        overflow-wrap: break-word;
      }
      th.actions,
      td.actions {
        width: 25%;
        white-space: nowrap;
      }
      td.original-url {
        word-wrap: break-word;
        overflow-wrap: break-word;
      }
      .actions button {
        margin-right: 10px;
      }
      .bottom-btn {
        margin-top: 20px;
      }
      .bottom-btn a {
        margin-right: 15px;
        text-decoration: none;
      }
      p {
        font-size: 25px;
        color: #666;
      }

      .head {
        display: flex;
        justify-content: space-between;
        align-items: center;
      }
      .bottom-btn {
        margin: 50px 0;
        text-align: center; /* Center align the buttons */
      }
      .bottom-btn a {
        margin-right: 15px;
        text-decoration: none;
        padding: 8px 16px; /* Make buttons look like standard buttons */
        background-color: #E5E5E5;
        color: rgb(0, 0, 0);
        display: inline-block;
        cursor: pointer;
        border-radius: 5px;
        border: 1px solid #666666;
      }
      /* Responsive design for medium and small screens */
      @media (max-width: 900px) {
        th.original-url {
          width: auto;
        }
        td.original-url {
          word-break: break-word;
        }
      }
      /* Mobile-friendly design for very small screens */
      @media (max-width: 767px) {
        table,
        thead,
        tbody,
        th,
        td,
        tr {
          display: block;
        }
        th {
          display: none;
        }
        th.original-url {
          width: auto;
        }
        th.shortened-url,
        td.shortened-url {
          width: auto;
          word-wrap: break-word;
          overflow-wrap: break-word;
        }
        th.actions,
        td.actions {
          width: auto;
          padding-left: 30%;
        }
        tr {
          margin-bottom: 15px;
          padding: 10px;
          border: 1px solid #ddd;
          background-color: white;
          box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
        }
        td {
          text-align: right;
          position: relative;
          padding-left: 50%;
        }
        td::before {
          content: attr(data-label);
          position: absolute;
          left: 0;
          width: 50%;
          padding-left: 10px;
          white-space: nowrap;
          text-align: left;
          font-weight: bold;
        }
        .actions button {
          margin: 5px 0;
        }
        .head {
          display: block;
        }
      }
    </style>
  </head>
  <body>
    <div class="head">
      <h1>Dashboard</h1>
      <p>Welcome, {{ user.username }} 😊</p>
    </div>

    <h3>Your Shortened URLs</h3>
    <h3>Total URLs shortened: {{ total_urls }}</h3>

    {% if urls|length > 0 %}
    <table>
      <thead>
        <tr>
          <th class="original-url">Original URL</th>
          <th class="shortened-url">Shortened URL</th>
          <th class="actions">Actions</th>
        </tr>
      </thead>
      <tbody>
        {% for url in urls %}
        <tr>
          <td class="original-url" data-label="Original URL">
            {{ url.original_url }}
          </td>
          <td class="shortened-url" data-label="Shortened URL">
            <a
              href="{{ request.host_url }}{{ url.short_hash }}"
              target="_blank"
            >
              {{ request.host_url }}{{ url.short_hash }}
            </a>
          </td>
          <td class="actions" data-label="Actions">
            <button
              onclick="copyToClipboard('{{ request.host_url }}{{ url.short_hash }}')"
            >
              Copy
            </button>
            <button
              onclick="shareUrl('{{ request.host_url }}{{ url.short_hash }}')"
            >
              Share
            </button>
            <form
              action="/delete/{{ url.short_hash }}"
              method="POST"
              style="display: inline"
            >
              <button type="submit">Delete</button>
            </form>
          </td>
        </tr>
        {% endfor %}
      </tbody>
    </table>
    {% else %}
    <p>You have not shortened any URLs yet.</p>
    {% endif %}

    <div class="bottom-btn">
      <a href="/" class="displayBtn">Home</a>
      <a href="/logout" class="displayBtn">Logout</a>
    </div>

    <script>
      function copyToClipboard(text) {
        navigator.clipboard
          .writeText(text)
          .then(() => alert("URL copied to clipboard!"))
          .catch((err) => console.error("Failed to copy:", err));
      }

      function shareUrl(url) {
        if (navigator.share) {
          navigator
            .share({
              title: "Check out this shortened URL!",
              url: url,
            })
            .catch((err) => console.error("Failed to share:", err));
        } else {
          alert("Sharing is not supported in this browser.");
        }
      }
    </script>
  </body>
</html>


server app.py

from flask import Flask, render_template, request, redirect, url_for, session, flash
from flask_pymongo import PyMongo
from flask_session import Session
from datetime import datetime, timedelta
import os
import random
import string
from dotenv import load_dotenv
import bcrypt
import smtplib
from email.mime.text import MIMEText
from redis import Redis
import logging

# Load environment variables from .env file
load_dotenv()

# Initialize Flask app
app = Flask(__name__)

# MongoDB configuration
app.config['MONGO_URI'] = f"mongodb+srv://{os.environ.get('MONGO_USER')}:{os.environ.get('MONGO_PASS')}@url-short-python.br0gv.mongodb.net/{os.environ.get('MONGO_DB')}?retryWrites=true&w=majority"
mongo = PyMongo(app)

# Session configuration for Redis
app.config['SESSION_TYPE'] = 'redis'
app.config['SESSION_PERMANENT'] = False
app.config['SESSION_USE_SIGNER'] = True
app.config['SESSION_KEY_PREFIX'] = 'url_shortener:'
app.config['SESSION_REDIS'] = Redis(
    host=os.getenv('REDIS_HOST', 'localhost'),  
    port=int(os.getenv('REDIS_PORT', 6379)),   
    password=os.getenv('REDIS_PASSWORD')      
)
app.config['SECRET_KEY'] = os.getenv('SECRET_KEY')
app.config['PERMANENT_SESSION_LIFETIME'] = timedelta(days=7)  # Set session lifetime to 7 days
Session(app)

# Logging configuration
logging.basicConfig(level=logging.INFO)

# OTP generation and email configuration
def generate_otp():
    """Generate a 6-digit OTP."""
    return ''.join(random.choices(string.digits, k=6))

def send_otp_email(email, otp, username):
    """Send an OTP email to the user."""
    message_body = f"""
    Hi {username},

    Your One-Time Password (OTP) is: **{otp}**.

    Please enter this OTP to complete your registration. Once registered, you can log in with your email and password.

    Note: This OTP is valid for a limited time and should not be shared with anyone.

    Thank you,
    bLink Shortener Team
    """
    msg = MIMEText(message_body)
    msg['Subject'] = 'bLink Shortener Registration OTP Code'
    msg['From'] = os.getenv('OTP_EMAIL')
    msg['To'] = email

    try:
        with smtplib.SMTP_SSL('smtp.gmail.com', 465) as server:
            server.login(os.getenv('OTP_EMAIL'), os.getenv('OTP_EMAIL_PASSWORD'))
            server.sendmail(msg['From'], [email], msg.as_string())
        logging.info(f"OTP sent to {email}.")
    except Exception as e:
        logging.error(f"Failed to send email: {e}")

# Routes for authentication
@app.route('/')
def home():
    if 'user' in session:
        return redirect(url_for('index'))
    return render_template('home.html')

@app.route('/register', methods=['GET', 'POST'])
def register():
    if request.method == 'POST':
        username = request.form['username']
        email = request.form['email']
        password = request.form['password']

        existing_user = mongo.db.loginUsers.find_one({'email': email})
        if existing_user:
            flash("Email already registered!")
            return redirect(url_for('register'))

        otp = generate_otp()
        logging.info(f"Generated OTP: {otp}")
        send_otp_email(email, otp, username)

        session['pending_user'] = {
            'username': username,
            'email': email,
            'password': bcrypt.hashpw(password.encode('utf-8'), bcrypt.gensalt()),
            'otp': otp
        }

        return redirect(url_for('verify_otp'))
    return render_template('register.html')

@app.route('/verify_otp', methods=['GET', 'POST'])
def verify_otp():
    if 'pending_user' not in session:
        return redirect(url_for('register'))

    if request.method == 'POST':
        input_otp = request.form['otp']
        if input_otp == session['pending_user']['otp']:
            user_data = session.pop('pending_user')
            mongo.db.loginUsers.insert_one({
                'username': user_data['username'],
                'email': user_data['email'],
                'password': user_data['password'],
                'urls': []
            })
            flash("Registration successful! Please login.")
            return redirect(url_for('login'))
        else:
            flash("Invalid OTP! Please try again.")

    return render_template('verify_otp.html')

@app.route('/login', methods=['GET', 'POST'])
def login():
    if 'user' in session:
        return redirect(url_for('index'))

    error = None
    if request.method == 'POST':
        email = request.form['email']
        password = request.form['password']

        user = mongo.db.loginUsers.find_one({'email': email})
        if user is None:
            error = "This email is not registered. Please check or register."
        elif not bcrypt.checkpw(password.encode('utf-8'), user['password']):
            error = "Invalid password! Please try again."
        else:
            session['user'] = {'username': user['username'], 'email': user['email']}
            session.permanent = True  # Make the session permanent
            return redirect(url_for('index'))

    return render_template('login.html', error=error)

@app.route('/logout')
def logout():
    session.pop('user', None)
    flash("You have been logged out.")
    return redirect(url_for('home'))

# URL Shortener and Dashboard
def generate_random_string(length=4):
    """Generate a random string of given length for URL shortening."""
    characters = string.ascii_letters
    return ''.join(random.choice(characters) for _ in range(length))

@app.route('/index')
def index():
    if 'user' not in session:
        return redirect(url_for('home'))
    total_urls = mongo.db.urls.count_documents({'user_email': session['user']['email']})
    return render_template('index.html', total_urls=total_urls)

@app.route('/dashboard')
def dashboard():
    if 'user' not in session:
        return redirect(url_for('home'))
    urls = list(mongo.db.urls.find({'user_email': session['user']['email']}))
    total_urls = len(urls)
    return render_template('dashboard.html', urls=urls, user=session['user'], total_urls=total_urls)

@app.route('/shorten', methods=['POST'])
def shorten_url():
    if 'user' not in session:
        return redirect(url_for('home'))

    original_url = request.form['url']
    existing_url = mongo.db.urls.find_one({'original_url': original_url, 'user_email': session['user']['email']})
    if existing_url:
        short_url = request.host_url + existing_url['short_hash']
        return render_template('shortened.html', short_url=short_url, message="This URL has already been shortened.")

    while True:
        random_string = generate_random_string()
        if not mongo.db.urls.find_one({'short_hash': random_string}):
            break

    short_url = request.host_url + random_string
    mongo.db.urls.insert_one({
        'user_email': session['user']['email'],
        'short_hash': random_string,
        'original_url': original_url,
        'created_at': datetime.utcnow()
    })

    return render_template('shortened.html', short_url=short_url)

@app.route('/<short_hash>')
def redirect_url(short_hash):
    url_entry = mongo.db.urls.find_one({'short_hash': short_hash})
    if url_entry:
        return redirect(url_entry['original_url'])
    else:
        return "URL not found!", 404

@app.route('/delete/<short_hash>', methods=['POST'])
def delete_url(short_hash):
    if 'user' not in session:
        return redirect(url_for('home'))

    mongo.db.urls.delete_one({'short_hash': short_hash, 'user_email': session['user']['email']})
    flash("URL deleted successfully!")
    return redirect(url_for('dashboard'))

@app.errorhandler(Exception)
def handle_exception(e):
    logging.error(f"Error: {e}")
    return "An error occurred.", 500

if __name__ == '__main__':
    app.run(debug=True)
