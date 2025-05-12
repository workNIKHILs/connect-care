<!DOCTYPE html>
<html lang="en" >
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Connect Care - All Services</title>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@600&family=Nunito+Sans:wght@400;700&display=swap" rel="stylesheet" />
  <style>
    :root {
      --primary: #1a1a1a;
      --primary-light: #333333;
      --secondary: #666666;
      --accent: #d32f2f;
      --success: #388e3c;
      --warning: #fbc02d;
      --light-bg: #f7f7f7;
      --card-bg: #fff;
      --gray-border: #ddd;
      --gray-text: #555;
      --gray-light: #999;
      --sidebar-bg: #fafafa;
    }
    body {
      font-family: 'Nunito Sans', sans-serif;
      background: var(--light-bg);
      color: var(--primary);
      min-height: 100vh;
      margin: 0;
    }
    h1, h2, h3 {
      font-family: 'Montserrat', sans-serif;
      font-weight: 700;
      color: var(--primary);
    }
    a { color: var(--accent); text-decoration:none; }
    a:hover { text-decoration:underline; }
    /* Login Page */
    #login-container {
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      background: var(--light-bg);
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 2000;
    }
    .login-card {
      background: var(--card-bg);
      padding: 40px 32px 32px 32px;
      border-radius: 18px;
      box-shadow: 0 6px 40px rgba(25, 25, 25, 0.07);
      max-width: 350px;
      width: 100%;
      text-align: center;
      animation: fadeIn 1s;
    }
    .login-card h2 {
      margin-bottom: 20px;
      color: var(--primary);
      font-size: 2em;
    }
    .login-card label {
      display: block;
      margin: 16px 0 8px 0;
      font-weight: 600;
      color: var(--gray-text);
      text-align: left;
    }
    .login-card input {
      width: 100%;
      padding: 12px 10px;
      border-radius: 7px;
      border: 1px solid var(--gray-border);
      font-size: 1em;
      margin-bottom: 6px;
      background: var(--light-bg);
      color: var(--primary);
      transition: border 0.2s;
    }
    .login-card input:focus {
      border: 1.5px solid var(--accent);
      outline: none;
    }
    .login-card button {
      background: var(--accent);
      color: #fff;
      border: none;
      border-radius: 8px;
      padding: 13px 0;
      width: 100%;
      font-size: 1.1em;
      font-family: 'Montserrat', sans-serif;
      font-weight: 700;
      margin-top: 18px;
      cursor: pointer;
      transition: background 0.2s;
      box-shadow: 0 2px 8px rgba(211,47,47,0.15);
    }
    .login-card button:hover {
      background: #9b1c1c;
    }
    /* Emergency Button */
    .emergency-btn {
      position: fixed;
      top: 18px;
      left: 270px;
      z-index: 1200;
      background: var(--accent);
      color: #fff;
      border: none;
      font-size: 18px;
      padding: 14px 32px 14px 46px;
      border-radius: 32px;
      font-family: 'Montserrat', sans-serif;
      font-weight: 700;
      box-shadow: 0 6px 18px rgba(211,47,47,0.3);
      cursor: pointer;
      transition: background 0.2s, box-shadow 0.2s;
      outline: none;
      display: flex;
      align-items: center;
      gap: 10px;
    }
    .emergency-btn:hover {
      background: #9b1c1c;
      box-shadow: 0 10px 24px rgba(211,47,47,0.5);
    }
    .emergency-btn svg {
      position: absolute;
      left: 18px;
      top: 50%;
      transform: translateY(-50%);
      width: 22px;
      height: 22px;
      fill: #fff;
    }
    /* Sidebar */
    .sidebar {
      width: 250px;
      background: var(--sidebar-bg);
      color: var(--primary);
      position: fixed;
      height: 100vh;
      overflow-y: auto;
      box-shadow: 2px 0 8px rgba(0,0,0,0.06);
      z-index: 10;
      top: 0;
      left: 0;
      border-right: 1px solid var(--gray-border);
    }
    .home-button {
      display: block;
      width: 100%;
      background: var(--primary);
      color: #fff;
      border: none;
      padding: 16px 0;
      cursor: pointer;
      font-size: 20px;
      font-family: 'Montserrat', sans-serif;
      font-weight: 700;
      box-shadow: 0 4px 12px rgba(25, 25, 25, 0.1);
      transition: background 0.2s;
      margin-bottom: 8px;
      border-radius: 0 0 10px 10px;
      letter-spacing: 1px;
    }
    .home-button:hover {
      background: var(--primary-light);
    }
    .sidebar button.cat-btn {
      background: none;
      border: none;
      color: var(--primary);
      width: 100%;
      text-align: left;
      padding: 14px 24px;
      cursor: pointer;
      font-size: 16px;
      font-family: 'Montserrat', sans-serif;
      font-weight: 600;
      letter-spacing: 0.5px;
      transition: background 0.3s;
      outline: none;
      border-bottom: 1px solid var(--gray-border);
    }
    .sidebar button.cat-btn:hover {
      background: var(--primary-light);
      color: #fff;
    }
    .sidebar .options {
      display: none;
      padding-left: 18px;
      margin-bottom: 8px;
      border-bottom: 1px solid var(--gray-border);
      background: var(--sidebar-bg);
    }
    .sidebar .options a {
      display: block;
      color: var(--primary);
      text-decoration: none;
      padding: 8px 0;
      font-size: 15px;
      font-family: 'Nunito Sans', sans-serif;
      transition: color 0.3s;
      cursor: pointer;
    }
    .sidebar .options a:hover {
      color: var(--accent);
      text-decoration: underline;
    }
    .main-content {
      margin-left: 250px;
      padding: 38px 28px 38px 28px;
      min-height: 100vh;
      background: transparent;
    }
    .hero {
      background: var(--card-bg);
      color: var(--primary);
      padding: 70px 30px 50px 30px;
      text-align: center;
      border-radius: 18px;
      margin-bottom: 32px;
      box-shadow: 0 6px 18px rgba(0,0,0,0.07);
      animation: fadeIn 1s;
      position: relative;
      overflow: hidden;
    }
    .hero h1 {
      font-size: 2.3em;
      margin-bottom: 0.3em;
      letter-spacing: 1px;
    }
    .hero .tagline {
      font-size: 1.2em;
      margin: 18px 0 30px 0;
      font-weight: 500;
      color: var(--secondary);
    }
    .hero button {
      background: var(--primary);
      color: #fff;
      border: none;
      border-radius: 8px;
      padding: 16px 44px;
      font-size: 21px;
      font-family: 'Montserrat', sans-serif;
      font-weight: 700;
      box-shadow: 0 2px 8px rgba(25, 25, 25, 0.13);
      transition: background 0.2s, transform 0.2s;
      cursor: pointer;
    }
    .hero button:hover {
      background: var(--primary-light);
      color: #fff;
      transform: scale(1.04);
    }
    .search-bar {
      width: 100%;
      max-width: 480px;
      margin: -36px auto 24px auto;
      display: flex;
      align-items: center;
      background: var(--card-bg);
      border-radius: 8px;
      box-shadow: 0 4px 16px rgba(0,0,0,0.07);
      padding: 12px 18px;
      position: relative;
      z-index: 2;
    }
    .search-bar input {
      border: none;
      outline: none;
      font-size: 18px;
      width: 100%;
      background: transparent;
      color: var(--primary);
      font-family: 'Nunito Sans', sans-serif;
    }
    .search-bar svg {
      width: 22px;
      height: 22px;
      margin-right: 10px;
      color: var(--accent);
      opacity: 0.8;
    }
    .why-connect-care {
      background: var(--card-bg);
      color: var(--primary);
      border-radius: 18px;
      margin: 40px auto 30px auto;
      padding: 36px 28px 30px 28px;
      max-width: 800px;
      box-shadow: 0 4px 24px rgba(0,0,0,0.07);
      text-align: center;
    }
    .why-connect-care h2 {
      color: var(--primary);
      margin-bottom: 18px;
    }
    .why-connect-care ul {
      text-align: left;
      margin: 0 auto;
      max-width: 500px;
      font-size: 1.1em;
      color: var(--primary);
    }
    .why-connect-care li {
      margin-bottom: 10px;
      padding-left: 10px;
    }
    .how-it-works {
      margin:40px auto 20px auto;
      max-width:700px;
      text-align:center;
    }
    .how-it-works-steps {
      display:flex;
      flex-wrap:wrap;
      gap:24px;
      justify-content:center;
    }
    .how-it-works-step {
      background: var(--card-bg);
      border-radius: 18px;
      box-shadow: 0 2px 16px rgba(0,0,0,0.07);
      padding: 22px 12px 16px 12px;
      margin: 0 8px;
      flex:1 1 180px;
      min-width:160px;
      color: var(--primary);
    }
    .how-it-works-step img {
      background: var(--primary);
      border-radius: 50%;
      padding: 8px;
      margin-bottom: 8px;
      width:48px;
      filter: drop-shadow(0 0 3px var(--primary));
    }
    .how-it-works-step p {
      margin-top:10px;
    }
    .service-cards {
      display: flex;
      flex-wrap: wrap;
      gap: 28px;
      justify-content: center;
      margin-top: 38px;
    }
    .service-card {
      background: var(--card-bg);
      border-radius: 18px;
      box-shadow: 0 8px 32px rgba(0,0,0,0.07);
      border: 2px solid var(--gray-border);
      transition: transform 0.2s, box-shadow 0.2s, border 0.2s;
      width: 320px;
      padding: 22px 18px;
      text-align: center;
      cursor: pointer;
      position: relative;
      overflow: hidden;
      animation: slideInUp 0.7s;
      color: var(--primary);
    }
    .service-card:hover {
      transform: translateY(-8px) scale(1.03);
      box-shadow: 0 16px 48px rgba(25, 118, 210, 0.13);
      border-color: var(--primary);
      background: var(--secondary);
      color: #fff;
    }
    .service-card img {
      width: 100%;
      height: 138px;
      object-fit: cover;
      border-radius: 10px;
      margin-bottom: 14px;
      background: #eaeaea;
    }
    .service-card h3 {
      margin-bottom: 8px;
      color: inherit;
    }
    .service-card .card-desc {
      color: var(--gray-text);
      font-size: 15px;
      margin-bottom: 12px;
      min-height: 44px;
    }
    .service-card .card-action {
      background: var(--primary);
      color: #fff;
      border: none;
      border-radius: 8px;
      padding: 9px 0;
      width: 100%;
      font-size: 16px;
      font-family: 'Montserrat', sans-serif;
      font-weight: 700;
      margin-top: 8px;
      cursor: pointer;
      transition: background 0.2s;
    }
    .service-card .card-action:hover {
      background: var(--primary-light);
      color: #fff;
      transform: scale(1.04);
    }
    .info {
      background: var(--card-bg);
      padding: 32px 24px;
      border-radius: 18px;
      box-shadow: 0 6px 24px rgba(0,0,0,0.07);
      margin-top: 32px;
      text-align: center;
      animation: fadeIn 0.7s;
      max-width: 500px;
      margin-left: auto;
      margin-right: auto;
      color: var(--primary);
    }
    .info img {
      max-width: 100%;
      border-radius: 12px;
      margin-top: 18px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.07);
    }
    .info .contact-details {
      margin: 18px 0 16px 0;
      text-align: left;
      font-size: 1.07em;
      color: var(--primary);
    }
    .info .contact-details p {
      margin: 7px 0;
    }
    .contact-btn {
      background: var(--primary);
      color: #fff;
      border: none;
      border-radius: 8px;
      padding: 13px 36px;
      font-size: 18px;
      font-family: 'Montserrat', sans-serif;
      font-weight: 700;
      margin-top: 12px;
      cursor: pointer;
      transition: background 0.2s;
      box-shadow: 0 2px 8px rgba(25, 118, 210, 0.13);
    }
    .contact-btn:hover {
      background: var(--primary-light);
      color: #fff;
    }
    .footer {
      background: var(--sidebar-bg);
      color: var(--gray-text);
      padding: 22px;
      text-align: center;
      position: relative;
      bottom: 0;
      width: 100%;
      font-size: 16px;
      letter-spacing: 0.5px;
    }
    @keyframes fadeIn {
      0% { opacity: 0; }
      100% { opacity: 1; }
    }
    @keyframes slideInUp {
      0% { transform: translateY(30px); opacity: 0; }
      100% { transform: translateY(0); opacity: 1; }
    }
    @media (max-width: 900px) {
      .main-content { margin-left: 0; padding: 22px 6vw; }
      .sidebar { position: static; width: 100%; height: auto; padding-top: 0; display: flex; flex-direction: row; overflow-x: auto; }
      .sidebar button.cat-btn { font-size: 16px; padding: 12px 10px; }
      .sidebar .options { position: absolute; background: var(--card-bg); left: 0; width: 100%; }
      .sidebar .options a { font-size: 14px; }
      .home-button { position: static; margin: 10px 0; }
      .emergency-btn { left: 10px; top: 10px; padding: 10px 28px 10px 40px; font-size: 16px; }
    }
    @media (max-width: 700px) {
      .service-cards { flex-direction: column; align-items: center; }
      .service-card { width: 97vw; }
      .main-content { padding: 14px 2vw; }
      .hero { padding: 36px 8px 18px 8px; }
      .footer { font-size: 14px; }
      .search-bar { max-width: 98vw; }
    }
    /* Floating Emergency Button */
.floating-btn {
  position: fixed;
  bottom: 30px;
  right: 30px;
  background-color: #e53935;
  color: white;
  padding: 15px 20px;
  border-radius: 50px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.2);
  cursor: pointer;
  font-weight: bold;
  z-index: 1000;
}

/* Modal Overlay */
.modal {
  display: none;
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background-color: rgba(0,0,0,0.5);
  z-index: 999;
}

/* Modal Content */
.modal-content {
  background-color: #fff;
  margin: 5% auto;
  padding: 30px;
  width: 90%;
  max-width: 900px;
  min-height: 500px;
  border-radius: 12px;
  position: relative;
  box-shadow: 0 8px 24px rgba(0,0,0,0.2);
  overflow-y: auto;
}

/* Close Button */
.close-btn {
  position: absolute;
  top: 15px;
  right: 20px;
  font-size: 28px;
  font-weight: bold;
  cursor: pointer;
}

/* Hospital List Layout */
#hospitalList, #ambulanceList {
  list-style: none;
  padding: 0;
}

/* Hospital Entry */
.hospital-entry {
  display: flex;
  align-items: flex-start;
  gap: 15px;
  margin-bottom: 20px;
  border-bottom: 1px solid #ddd;
  padding-bottom: 15px;
}

/* Hospital Image */
.hospital-img {
  width: 80px;
  height: 80px;
  border-radius: 10px;
  object-fit: cover;
}

/* Hospital Text Info */
.hospital-details {
  flex: 1;
}
.scroll-area {
  max-height: 400px;       /* Adjust this height as needed */
  overflow-y: auto;        /* Enables vertical scroll */
  padding-right: 10px;
}

/* Optional: Styling the scrollbar */
.scroll-area::-webkit-scrollbar {
  width: 8px;
}
.scroll-area::-webkit-scrollbar-thumb {
  background-color: #ccc;
  border-radius: 4px;
}
.scroll-area::-webkit-scrollbar-track {
  background-color: #f1f1f1;
}

    

  </style>
</head>
<body>
  <!-- Login Page -->
  <div id="login-container">
    <form class="login-card" id="loginForm" autocomplete="off">
      <h2>Connect Care Login</h2>
      <label for="userName">Your Name</label>
      <input type="text" id="userName" name="userName" required maxlength="30" placeholder="Enter your name" />
      <label for="userCity">Your City</label>
      <input type="text" id="userCity" name="userCity" required maxlength="30" placeholder="Enter your city" />
      <button type="submit">Continue</button>
    </form>
  </div>
  
  <div class="sidebar" id="sidebar"></div>
  <div class="main-content" id="main-content">
    <section class="hero" id="homeHero">
      <div>
        <h1 id="welcomeText">Connect Care</h1>
        <div class="tagline">All the help you need, in one place.</div>
        <button onclick="document.getElementById('servicesSection').scrollIntoView({behavior:'smooth'})">Explore Popular Services</button>
      </div>
    </section>
    <form class="search-bar" id="searchForm" onsubmit="return false;">
      <svg fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
        <circle cx="11" cy="11" r="8"></circle>
        <line x1="21" y1="21" x2="16.65" y2="16.65"></line>
      </svg>
      <input type="text" id="searchInput" placeholder="Search for any service or category..." autocomplete="off" />
    </form>
    <section class="why-connect-care">
      <h2>Why Connect Care?</h2>
      <ul>
        <li>One-stop platform for all your home, health, legal, and daily needs</li>
        <li>Trusted professionals and verified providers</li>
        <li>Instant booking and emergency help</li>
        <li>24/7 support and easy access</li>
        <li>Modern, secure, and user-friendly experience</li>
      </ul>
    </section>
    <section class="how-it-works">
      <h2>How It Works</h2>
      <div class="how-it-works-steps">
        <div class="how-it-works-step">
          <img src="https://cdn-icons-png.flaticon.com/512/1828/1828884.png" alt="Browse" />
          <p><strong>Browse Services</strong></p>
          <p>Find the right service for your needs from our wide selection.</p>
        </div>
        <div class="how-it-works-step">
          <img src="https://cdn-icons-png.flaticon.com/512/1256/1256650.png" alt="Book" />
          <p><strong>Book Instantly</strong></p>
          <p>Book a trusted professional with just a few clicks.</p>
        </div>
        <div class="how-it-works-step">
          <img src="https://cdn-icons-png.flaticon.com/512/190/190411.png" alt="Relax" />
          <p><strong>Relax</strong></p>
          <p>Sit back and let us take care of everything for you.</p>
        </div>
      </div>
    </section>
    <section id="servicesSection">
      <h2 style="text-align:center; margin-bottom:18px;">Popular Services</h2>
      <div class="service-cards" id="serviceCards"></div>
    </section>
    <div id="emergencySection" style="margin-top: 500px;"></div>
  </div>
  <div class="footer">
    <p>&copy; 2025 Connect Care - All Rights Reserved</p>
  </div>
  <script>
    // Demo contact generator for services
    function getContactDetails(service, category, idx) {
      const firstNames = [
        "Aarav", "Vivaan", "Aditya", "Vihaan", "Arjun", "Sai", "Reyansh", "Ayaan", "Krishna", "Ishaan",
        "Ananya", "Aadhya", "Diya", "Myra", "Anika", "Sara", "Ira", "Avni", "Saanvi", "Aarohi"
      ];
      const lastNames = [
        "Sharma", "Verma", "Patel", "Singh", "Kumar", "Gupta", "Mehra", "Reddy", "Nair", "Das",
        "Joshi", "Bose", "Banerjee", "Chopra", "Kapoor", "Jain", "Mishra", "Rao", "Shetty", "Yadav"
      ];
      const name = firstNames[(idx + category.length) % firstNames.length] + " " +
                   lastNames[(idx * 3 + category.length) % lastNames.length];
      const phone = "+91 9" + String(100000000 + (idx*1234567 + category.length*1000000)%900000000).slice(0,8);
      const email = name.replace(/ /g, ".").toLowerCase() + "@connectcare.com";
      const address = (100 + idx*2) + " " + category.split(" ")[0] + " Road, Mumbai";
      return { name, phone, email, address };
    }

    // Popular services with relevant images
    const popularServices = [
      { title: "General physician consultation", category: "Healthcare Services", image: "data:image/jpeg;base64,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" },
      { title: "Plumbing", category: "Home Services", image: "data:image/jpeg;base64,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" },
      { title: "Cab booking", category: "Transportation Services", image: "https://images.unsplash.com/photo-1503736334956-4c8f8e92946d?auto=format&fit=crop&w=800&q=80" },
      { title: "Online tutoring", category: "Education Services", image: "https://images.unsplash.com/photo-1513258496099-48168024aec0?auto=format&fit=crop&w=800&q=80" },
      { title: "Website development", category: "IT & Tech Services", image: "https://images.unsplash.com/photo-1461749280684-dccba630e2f6?auto=format&fit=crop&w=800&q=80" },
      { title: "Legal consultation", category: "Legal Services", image: "https://images.unsplash.com/photo-1514474959185-147d077df3c0?auto=format&fit=crop&w=800&q=80" },
      { title: "Home cleaning", category: "Home Services", image: "https://images.unsplash.com/photo-1507662228758-08d030c4820b?auto=format&fit=crop&w=800&q=80" },
      { title: "Online food ordering", category: "Food & Delivery Services", image: "https://images.unsplash.com/photo-1504674900247-0877df9cc836?auto=format&fit=crop&w=800&q=80" },
      { title: "Movie streaming", category: "Entertainment Services", image: "https://images.unsplash.com/photo-1519125323398-675f0ddb6308?auto=format&fit=crop&w=800&q=80" },
      { title: "Tour packages", category: "Travel & Tourism Services", image: "https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=800&q=80" },
      { title: "Personal training", category: "Fitness Services", image: "https://images.unsplash.com/photo-1519864600265-abb23847ef2c?auto=format&fit=crop&w=800&q=80" },
      { title: "Wedding planning", category: "Event Services", image: "https://images.unsplash.com/photo-1521737852567-6949f3f9f2b5?auto=format&fit=crop&w=800&q=80" }
    ];

    // All categories and services
    const allServicesList = [
      ["Healthcare Services", "🩺", [
        "General physician consultation", "Telemedicine", "Emergency ambulance", "Mental health counseling", "Dental care", "Diagnostic labs", "Vaccination", "Physiotherapy", "Home nursing", "Health insurance assistance"
      ]],
      ["Education Services", "🎓", [
        "Online tutoring", "Career counseling", "Skill development courses", "Test preparation", "Special education support", "Language learning", "College admission guidance", "Virtual classrooms", "Research mentoring", "E-learning platforms"
      ]],
      ["IT & Tech Services", "💻", [
        "Website development", "App development", "Cybersecurity solutions", "Cloud storage", "IT support/helpdesk", "Data recovery", "Network setup", "UI/UX design", "AI/ML development", "Software maintenance"
      ]],
      ["Government Services", "🏛️", [
        "Passport application", "Driving license renewal", "Tax filing support", "Birth/death certificates", "Voter ID services", "Public grievance portal", "Land record management", "Police verification", "Pension assistance", "Utility bill payments"
      ]],
      ["Financial Services", "💰", [
        "Banking","Investment advice","Loan application","Tax consulting","Insurance services","Credit score check","Mutual fund guidance","Cryptocurrency trading","Online payments","Personal finance coaching"
      ]],
      ["Transportation Services", "🚗", [
        "Cab booking","Bus ticketing","Railway reservations","Flight booking","Courier delivery","Freight logistics","Two-wheeler rentals","EV charging stations","Carpooling","Driving school"
      ]],
      ["Legal Services", "⚖️", [
        "Legal consultation","Document drafting","Will creation","Contract review","Property dispute handling","Company registration","Divorce filing","Trademark registration","Court representation","Consumer rights advice"
      ]],
      ["Home Services", "🏠", [
        "Plumbing","Electrical repair","Home cleaning","Pest control","Appliance repair","Furniture assembly","Interior design","Gardening","Painting","CCTV installation"
      ]],
      ["Food & Delivery Services", "🍕", [
        "Online food ordering","Grocery delivery","Tiffin services","Meal planning","Catering","Organic produce delivery","Food subscription boxes","Pet food delivery","Restaurant table booking","Farm-to-home supply"
      ]],
      ["Entertainment Services", "🎬", [
        "Movie streaming","Music subscriptions","Online gaming","Virtual reality experiences","Event booking","Stand-up comedy shows","Online concerts","E-book lending","Podcast platforms","Virtual tours"
      ]],
      ["Business Services", "🏢", [
        "HR outsourcing","Payroll processing","Marketing consultation","Accounting & bookkeeping","Business registration","Office space rentals","Digital advertising","CRM tools","Business analytics","Vendor management"
      ]],
      ["Travel & Tourism Services", "🌍", [
        "Tour packages","Travel insurance","Visa assistance","Hotel booking","Local guides","Adventure tourism","Cruise booking","Currency exchange","Car rental","Airport shuttle"
      ]],
      ["Environmental Services", "🌱", [
        "Waste management","Water purification","Solar panel installation","Air quality monitoring","Eco-friendly product supply","Tree plantation","Recycling services","Rainwater harvesting","Wildlife protection","Carbon offset programs"
      ]],
      ["Fitness Services", "🏋️", [
        "Personal training","Gym memberships","Yoga classes","Online workouts","Nutrition counseling","Body composition analysis","Fitness equipment rental","Group fitness sessions","Step tracker apps","Meditation coaching"
      ]],
      ["Real Estate Services", "🏘️", [
        "Property listing","House rental","Real estate investment advice","Home valuation","Legal paperwork support","Mortgage consulting","Property inspection","Construction services","Home staging","Property management"
      ]],
      ["Communication Services", "📡", [
        "Mobile network plans","Broadband connection","VOIP calling","Email hosting","Online conferencing","SIM card services","Satellite communication","Messaging apps","Telecom billing","Unified communications"
      ]],
      ["Security Services", "🔒", [
        "Security guard hiring","Alarm system installation","Surveillance monitoring","Cybersecurity audits","Access control systems","Background checks","Fire safety equipment","Emergency response","Biometric authentication","Security software tools"
      ]],
      ["Childcare Services", "🧸", [
        "Babysitting","Daycare centers","Parenting counseling","After-school programs","Online kids’ classes","Pediatric care","Children’s therapy","Educational toys delivery","Nanny services","Child safety audits"
      ]],
      ["Pet Services", "🐾", [
        "Pet grooming","Veterinary care","Pet boarding","Dog walking","Pet adoption","Pet training","Pet food delivery","Mobile vet","Pet insurance","Pet taxi"
      ]],
      ["Event Services", "🎉", [
        "Wedding planning","Birthday party organization","Event photography","DJ services","Stage setup","Catering","Venue decoration","Invitation printing","Event ticketing","Guest management"
      ]]
    ];

    // Assign images to categories (demo: use popularServices or Unsplash placeholder)
    function getCategoryImage(catIdx, srvIdx) {
      const imgIdx = (catIdx + srvIdx) % popularServices.length;
      return popularServices[imgIdx].image;
    }
    const categories = allServicesList.map(([name, icon, services], catIdx) => ({
      name,
      icon,
      services: services.map((title, srvIdx) => ({
        title,
        image: getCategoryImage(catIdx, srvIdx)
      }))
    }));

    // Sidebar rendering
    function renderSidebar() {
      let html = `<button class="home-button" onclick="goHome()">Home</button>`;
      categories.forEach((cat, idx) => {
        const catId = `cat${idx}`;
        html += `<button class="cat-btn" onclick="toggleOptions('${catId}')">${cat.icon || ''} ${cat.name}</button>
        <div class="options" id="${catId}">`;
        cat.services.forEach((service, sidx) => {
          html += `<a href="#" onclick="showService('${service.title.replace(/'/g,"\\'")}', '${cat.name.replace(/'/g,"\\'")}', '${service.image}', ${sidx})">${service.title}</a>`;
        });
        html += `</div>`;
      });
      document.getElementById('sidebar').innerHTML = html;
    }

    // Show service details
    function showService(service, category, image, idx) {
      const contact = getContactDetails(service, category, idx || 0);
      document.getElementById('main-content').innerHTML = `
        <section class="hero">
          <div>
            <h1>${category} - ${service}</h1>
            <p>Find trusted professionals for your needs.</p>
          </div>
        </section>
        <div class="info">
          <h2>${service}</h2>
          <img src="${image}" alt="${service}" />
          <div class="contact-details">
            <p><strong>Name:</strong> ${contact.name}</p>
            <p><strong>Phone:</strong> ${contact.phone}</p>
            <p><strong>Email:</strong> <a href="mailto:${contact.email}">${contact.email}</a></p>
            <p><strong>Address:</strong> ${contact.address}</p>
          </div>
          <button class="contact-btn" onclick="window.location.href='mailto:${contact.email}'">Contact Me</button>
        </div>
      `;
      window.scrollTo({top:0,behavior:'smooth'});
    }

    function toggleOptions(id) {
      const el = document.getElementById(id);
      el.style.display = el.style.display === 'block' ? 'none' : 'block';
    }

    function goHome() {
      window.location.reload();
    }

    function scrollToEmergency() {
      const emergencySection = document.getElementById('emergencySection');
      if (emergencySection) {
        emergencySection.scrollIntoView({behavior:'smooth'});
      } else {
        goHome();
        setTimeout(() => {
          document.getElementById('emergencySection').scrollIntoView({behavior:'smooth'});
        }, 500);
      }
    }

    // Render sidebar and popular cards on load
    renderSidebar();

    // Render popular services cards
    function renderPopularServiceCards(filter = "") {
      let html = '';
      popularServices.forEach((service, idx) => {
        if (
          !filter ||
          service.title.toLowerCase().includes(filter) ||
          service.category.toLowerCase().includes(filter)
        ) {
          html += `
            <div class="service-card" onclick="showService('${service.title.replace(/'/g,"\\'")}', '${service.category.replace(/'/g,"\\'")}', '${service.image}', ${idx})">
              <img src="${service.image}" alt="${service.title}" />
              <h3>${service.title}</h3>
              <div class="card-desc">${service.category}</div>
              <button class="card-action">View Details</button>
            </div>
          `;
        }
      });
      document.getElementById('serviceCards').innerHTML = html || '<p style="text-align:center;color:var(--gray-light);font-size:1.2em;">No popular services found.</p>';
    }
    renderPopularServiceCards();

    // Search bar logic
    document.getElementById('searchInput').addEventListener('input', function() {
      const filter = this.value.trim().toLowerCase();
      renderPopularServiceCards(filter);
    });

    // Login logic (now uses sessionStorage)
    document.getElementById('loginForm').addEventListener('submit', function(e){
      e.preventDefault();
      const userName = document.getElementById('userName').value.trim();
      const userCity = document.getElementById('userCity').value.trim();
      if(userName && userCity){
        sessionStorage.setItem('connectcare_user', userName);
        sessionStorage.setItem('connectcare_city', userCity);
        document.getElementById('login-container').style.display = 'none';
        showWelcome(userName);
      }
    });
    // On load, check login (sessionStorage)
    window.addEventListener('DOMContentLoaded', function(){
      const userName = sessionStorage.getItem('connectcare_user');
      if(userName){
        document.getElementById('login-container').style.display = 'none';
        showWelcome(userName);
      }
    });
    function showWelcome(name){
      document.getElementById('welcomeText').textContent = `Hey ${name}, welcome to Connect Care!`;
    }
  </script>
  <!-- Emergency Floating Button -->
<div id="emergencyBtn" class="floating-btn">🚑 Emergency</div>

<!-- Emergency Popup Modal -->
<div id="emergencyModal" class="modal">
  <div class="modal-content">
    <span class="close-btn" id="closeModal">&times;</span>

    <!-- Scrollable content starts here -->
    <div class="scroll-area">
      <h2>Nearby Hospitals</h2>
      <ul id="hospitalList"></ul>

      <h2>Ambulance Distance</h2>
      <ul id="ambulanceList"></ul>
    </div>
    <!-- Scrollable content ends here -->

    <!-- Alert button -->
    <div style="text-align: center; margin-top: 20px;">
      <button id="alertButton" class="alert-btn">🚨 Send Emergency Alert</button>
    </div>
  </div>
</div>
<script>
  const emergencyBtn = document.getElementById("emergencyBtn");
  const emergencyModal = document.getElementById("emergencyModal");
  const closeModal = document.getElementById("closeModal");
  const hospitalList = document.getElementById("hospitalList");
  const ambulanceList = document.getElementById("ambulanceList");

  // Hospital Info
  const hospitals = [
    {
      name: "City Care Hospital",
      distance: "2.1 km",
      img: "https://ehealth.eletsonline.com/wp-content/uploads/2009/07/best-hospital-in-south-india.jpg",
      address: "123 Main St, City Center",
      phone: "+123 456 789"
    },
    {
      name: "Green Life Hospital",
      distance: "3.4 km",
      img: "https://cdn.britannica.com/12/130512-004-AD0A7CA4/campus-Riverside-Ottawa-The-Hospital-Ont.jpg",
      address: "456 Elm St, Midtown",
      phone: "+987 654 321"
    },
    {
      name: "Health Plus Clinic",
      distance: "5.2 km",
      img: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRt-YdgCgQY4oiyHme5sBtc-U31O2iXRnSuKA&s",
      address: "789 Oak St, West Side",
      phone: "+555 123 456"
    }
  ];

  const ambulances = [
    "Ambulance #1 - 1.2 km away",
    "Ambulance #2 - 2.8 km away"
  ];

  // Show hospitals
  function showHospitals() {
    hospitalList.innerHTML = hospitals.map((h, index) => `
      <li class="hospital-entry">
        <img src="${h.img}" alt="${h.name}" class="hospital-img">
        <div class="hospital-details">
          <strong>${h.name}</strong>
          <p>${h.address}</p>
          <p>Phone: ${h.phone}</p>
          <p>Distance: ${h.distance}</p>
        </div>
        <button class="hospital-alert-btn" data-index="${index}">🚨 Alert</button>
      </li>
    `).join("");

    // Add click listeners to alert buttons
    document.querySelectorAll('.hospital-alert-btn').forEach(btn => {
      btn.addEventListener('click', (e) => {
        const hospitalIndex = e.target.getAttribute('data-index');
        const selected = hospitals[hospitalIndex];
        alert(`🚨 Alert sent to ${selected.name}!\nLocation: ${selected.address}`);
      });
    });
  }

  // Show ambulances
  function showAmbulances() {
    ambulanceList.innerHTML = ambulances.map(a => `<li>${a}</li>`).join("");
  }

  // Open modal
  emergencyBtn.onclick = () => {
    emergencyModal.style.display = "block";
    showHospitals();
    showAmbulances();
  };

  // Close modal
  closeModal.onclick = () => {
    emergencyModal.style.display = "none";
  };

  // Handle main alert button click (if needed)
  const alertButton = document.getElementById("alertButton");
  alertButton.addEventListener("click", () => {
    alert("🚨 Emergency alert sent to nearby services!");
  });
</script>



  
</body>
</html>
