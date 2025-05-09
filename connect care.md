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
  <!-- Emergency Button -->
  <button class="emergency-btn" onclick="scrollToEmergency()">
    <svg viewBox="0 0 24 24"><path d="M12 2v4M12 18v4M4.93 4.93l2.83 2.83M16.24 16.24l2.83 2.83M2 12h4M18 12h4M4.93 19.07l2.83-2.83M16.24 7.76l2.83-2.83"/></svg>
    Emergency
  </button>
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
      { title: "General physician consultation", category: "Healthcare Services", image: "https://images.unsplash.com/photo-1550831107-1553da8c8464?auto=format&fit=crop&w=800&q=80" },
      { title: "Plumbing", category: "Home Services", image: "https://images.unsplash.com/photo-1520880867055-1e30d1cb001c?auto=format&fit=crop&w=800&q=80" },
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
</body>
</html>
