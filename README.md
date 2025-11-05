
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Itz Faysal Portfolio</title>
<link rel="icon" type="image/x-icon" href="favicon.ico">
<link rel="apple-touch-icon" href="apple-touch-icon.png">
<link rel="manifest" href="site.webmanifest">
<link href='https://unpkg.com/boxicons@2.1.4/css/boxicons.min.css' rel='stylesheet'>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800&family=Hind+Siliguri:wght@400;500;700&display=swap" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@3/dist/email.min.js"></script>
<script src="https://www.google.com/recaptcha/api.js" async defer></script>
<script src="https://cdn.jsdelivr.net/npm/particles.js@2.0.0/particles.min.js"></script>
<script type="text/javascript">
    var gk_isXlsx = false;
    var gk_xlsxFileLookup = {};
    var gk_fileData = {};
    function filledCell(cell) {
      return cell !== '' && cell != null;
    }
    function loadFileData(filename) {
    if (gk_isXlsx && gk_xlsxFileLookup[filename]) {
        try {
            var workbook = XLSX.read(gk_fileData[filename], { type: 'base64' });
            var firstSheetName = workbook.SheetNames[0];
            var worksheet = workbook.Sheets[firstSheetName];
            var jsonData = XLSX.utils.sheet_to_json(worksheet, { header: 1, blankrows: false, defval: '' });
            var filteredData = jsonData.filter(row => row.some(filledCell));
            var headerRowIndex = filteredData.findIndex((row, index) =>
              row.filter(filledCell).length >= filteredData[index + 1]?.filter(filledCell).length
            );
            if (headerRowIndex === -1 || headerRowIndex > 25) {
              headerRowIndex = 0;
            }
            var csv = XLSX.utils.aoa_to_sheet(filteredData.slice(headerRowIndex));
            csv = XLSX.utils.sheet_to_csv(csv, { header: 1 });
            return csv;
        } catch (e) {
            console.error(e);
            return "";
        }
    }
    return gk_fileData[filename] || "";
    }
</script>
<style>
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        text-decoration: none;
        border: none;
        outline: none;
        scroll-behavior: smooth;
        font-family: "Poppins", sans-serif;
    }
    :root {
        --bg-color: #080808;
        --second-bg-color: #131313;
        --text-color: white;
        --main-color: #00ffee;
    }
    html {
        font-size: 62.5%;
        overflow-x: hidden;
    }
    body {
        background: var(--bg-color);
        color: var(--text-color);
        position: relative;
        overflow-x: hidden;
    }
    #particles-js {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: -1;
    }
    .header {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        padding: 2rem 12%;
        background: rgba(0, 0, 0, 0.3);
        backdrop-filter: blur(10px);
        display: flex;
        justify-content: space-between;
        align-items: center;
        z-index: 100;
    }
    .logo {
        font-size: 3rem;
        color: var(--text-color);
        font-weight: 800;
        cursor: pointer;
        transition: 0.3s ease;
    }
    .logo:hover {
        transform: scale(1.1);
    }
    .logo span {
        text-shadow: 0 0 25px var(--main-color);
        color: var(--main-color);
    }
    .navbar {
        display: flex;
    }
    .navbar a {
        font-size: 1.8rem;
        color: var(--text-color);
        margin-left: 4rem;
        font-weight: 500;
        transition: 0.3s ease;
        border-bottom: 3px solid transparent;
    }
    .navbar a:hover,
    .navbar a.active {
        color: var(--main-color);
        border-bottom: 3px solid var(--main-color);
    }
    #menu-icon {
        font-size: 3.6rem;
        color: var(--main-color);
        display: none;
        cursor: pointer;
    }
    section {
        min-height: 100vh;
        padding: 10rem 12% 10rem;
    }
    .home {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 15rem;
    }
    .home-content {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        text-align: left;
        justify-content: center;
        margin-top: 3rem;
    }
    .home-content h1 {
        font-size: 7rem;
        font-weight: 700;
        line-height: 1;
        margin: 1.5rem 0;
    }
    .home-content h3 {
        font-size: 3.5rem;
        margin: 1rem 0 2rem;
    }
    .home-content p {
        font-size: 1.6rem;
        font-weight: 500;
        line-height: 1.8;
        max-width: 1000px;
    }
    .home-img img {
        width: 32vw;
        border-radius: 50%;
        box-shadow: 0 0 25px var(--main-color);
        transition: 0.4s ease-in-out;
        position: relative;
        top: 3rem;
    }
    .home-img img:hover {
        box-shadow: 0 0 25px var(--main-color), 0 0 50px var(--main-color), 0 0 100px var(--main-color);
    }
    .social-icons a {
        display: inline-flex;
        justify-content: center;
        align-items: center;
        width: 4.5rem;
        height: 4.5rem;
        background: transparent;
        border: 2px solid var(--main-color);
        font-size: 2.5rem;
        border-radius: 50%;
        color: var(--main-color);
        margin: 3rem 1.5rem 3rem 0;
        transition: 0.3s ease-in-out;
    }
    .social-icons a:hover {
        color: var(--text-color);
        transform: scale(1.3) translateY(-5px);
        box-shadow: 0 0 25px var(--main-color);
        background-color: var(--main-color);
    }
    .btn {
        display: inline-block;
        padding: 1rem 2.8rem;
        background: var(--main-color);
        box-shadow: 0 0 25px var(--main-color);
        border-radius: 4rem;
        font-size: 1.6rem;
        color: black;
        border: 2px solid transparent;
        letter-spacing: 0.1rem;
        font-weight: 600;
        transition: 0.3s ease-in-out;
        cursor: pointer;
    }
    .btn:hover {
        transform: scale(1.05);
        box-shadow: 0 0 50px var(--main-color);
    }
    .btn-group {
        display: flex;
        align-items: center;
        gap: 1.5rem;
    }
    .btn-group a:nth-of-type(2) {
        background-color: black;
        color: var(--main-color);
        border: 2px solid var(--main-color);
        box-shadow: 0 0 25px transparent;
    }
    .btn-group a:nth-of-type(2):hover {
        box-shadow: 0 0 25px var(--main-color);
        background-color: var(--main-color);
        color: black;
    }
    .text-animation {
        font-size: 3.4rem;
        font-weight: 600;
        min-width: 280px;
    }
    .text-animation span {
        position: relative;
        white-space: nowrap;
    }
    .text-animation span::before {
        content: "Web Developer";
        color: var(--main-color);
        animation: words 24s infinite;
    }
    .text-animation span::after {
        content: "";
        background-color: var(--bg-color);
        position: absolute;
        width: calc(100% + 8px);
        height: 100%;
        border-left: 3px solid var(--bg-color);
        right: -8px;
        animation: cursor 0.6s infinite, typing 24s steps(14) infinite;
    }
    @keyframes cursor {
        to {
            border-left: 3px solid var(--main-color);
        }
    }
    @keyframes words {
        0%, 16.66% { content: "BD Hacker"; }
        16.67%, 33.33% { content: "Web Designer"; }
        33.34%, 50% { content: "UI/UX Designer"; }
        50.01%, 66.66% { content: "Web Developer"; }
        66.67%, 83.33% { content: "App Devoloper"; }
        83.34%, 100% { content: "Graphic Desinger"; }
    }
    @keyframes typing {
        8.33%, 12.5%, 25%, 29.17%, 41.67%, 45.83%, 58.33%, 62.5%, 75%, 79.17%, 91.67%, 95.83% { width: 0; }
        4.17%, 20.83%, 37.5%, 54.17%, 70.83%, 87.5% { width: calc(100% + 8px); }
    }
    .heading {
        font-size: 8rem;
        text-align: center;
        margin: 5rem 0;
    }
    .education {
        padding: 10rem 12%;
    }
    .education h2 {
        margin-bottom: 5rem;
    }
    .timeline-items {
        max-width: 1200px;
        margin: auto;
        display: flex;
        flex-wrap: wrap;
        position: relative;
    }
    .timeline-items::before {
        content: "";
        position: absolute;
        width: 5px;
        height: 100%;
        background-color: var(--main-color);
        left: calc(50% - 2.5px);
    }
    .timeline-item {
        margin-bottom: 40px;
        width: 100%;
        position: relative;
    }
    .timeline-item:last-child {
        margin-bottom: 0;
    }
    .timeline-item:nth-child(odd) {
        padding-right: calc(50% + 30px);
        text-align: right;
    }
    .timeline-item:nth-child(even) {
        padding-left: calc(50% + 30px);
    }
    .timeline-dot {
        height: 21px;
        width: 21px;
        background-color: var(--main-color);
        box-shadow: 0 0 25px var(--main-color), 0 0 50px var(--main-color);
        position: absolute;
        left: calc(50% - 10.5px);
        border-radius: 50%;
        top: 10px;
    }
    .timeline-date {
        font-size: 2rem;
        font-weight: 800;
        color: white;
        margin: 6px 0 15px;
    }
    .timeline-content {
        background-color: var(--bg-color);
        border: 3px solid var(--main-color);
        padding: 30px 50px;
        border-radius: 4rem;
        box-shadow: 0 0 10px var(--main-color);
        cursor: pointer;
        transition: 0.3s ease-in-out;
    }
    .timeline-content:hover {
        transform: scale(1.05);
        box-shadow: 0 0 25px var(--main-color);
    }
    .timeline-content h3 {
        font-size: 2rem;
        color: white;
        margin: 0 0 10px;
        font-weight: 500;
    }
    .timeline-content p {
        color: white;
        font-size: 1.6rem;
        font-weight: 300;
        line-height: 22px;
    }
    .services {
        padding: 10rem 12%;
    }
    .services h2 {
        margin-bottom: 5rem;
    }
    .services-container {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 3rem;
    }
    .service-box {
        background-color: var(--bg-color);
        border: 3px solid var(--main-color);
        padding: 3rem;
        border-radius: 4rem;
        box-shadow: 0 0 10px var(--main-color);
        transition: 0.3s ease-in-out;
        text-align: center;
    }
    .service-box:hover {
        transform: scale(1.05);
        box-shadow: 0 0 25px var(--main-color);
    }
    .service-box h3 {
        font-size: 2.2rem;
        color: white;
        margin-bottom: 1rem;
    }
    .service-box p {
        font-size: 1.6rem;
        color: white;
        font-weight: 300;
        line-height: 1.6;
    }
    .contact {
        padding: 10rem 12%;
    }
    .contact h2 {
        margin-bottom: 5rem;
    }
    .contact form {
        max-width: 700px;
        margin: 0 auto;
        display: flex;
        flex-direction: column;
        gap: 2rem;
    }
    .contact input,
    .contact textarea {
        background-color: var(--second-bg-color);
        border: 2px solid var(--main-color);
        border-radius: 1rem;
        padding: 1.5rem;
        font-size: 1.6rem;
        color: white;
        resize: vertical;
    }
    .contact textarea {
        min-height: 150px;
    }
    .contact .btn {
        align-self: center;
    }
    .g-recaptcha {
        margin: 2rem auto;
        display: flex;
        justify-content: center;
    }
    .error {
        color: red;
        font-size: 1.4rem;
        margin-top: -1rem;
    }
    .modal {
        display: none;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.7);
        z-index: 1000;
        justify-content: center;
        align-items: center;
    }
    .modal-content {
        background: var(--bg-color);
        border: 3px solid var(--main-color);
        border-radius: 4rem;
        padding: 3rem 5rem;
        text-align: center;
        box-shadow: 0 0 25px var(--main-color);
        max-width: 500px;
        width: 90%;
        animation: fadeIn 0.3s ease-in-out;
    }
    .modal-content h3 {
        font-size: 2.5rem;
        color: var(--text-color);
        margin-bottom: 2rem;
        font-family: "Poppins", sans-serif;
    }
    .modal-content p#modal-message {
        font-size: 1.6rem;
        color: var(--text-color);
        margin-bottom: 3rem;
        font-family: "Hind Siliguri", sans-serif;
    }
    .modal-content .btn {
        padding: 1rem 4rem;
        font-family: "Poppins", sans-serif;
    }
    @keyframes fadeIn {
        from { opacity: 0; transform: scale(0.8); }
        to { opacity: 1; transform: scale(1); }
    }
    ::-webkit-scrollbar {
        width: 15px;
    }
    ::-webkit-scrollbar-thumb {
        background-color: var(--main-color);
    }
    ::-webkit-scrollbar-track {
        background-color: var(--bg-color);
    }
    @media (max-width: 991px) {
        .header {
            padding: 2rem 4%;
        }
        section {
            padding: 10rem 4% 2rem;
        }
        .home {
            flex-direction: column; /* Restored original column layout for mobile */
            gap: 5rem;
        }
        .home-img {
            order: -1; /* Added: Moves image to top in mobile view */
            text-align: center; /* Center image */
        }
        .home-content h1 {
            font-size: 5rem;
        }
        .home-img img {
            width: 50vw; /* Restored original size */
            top: 0; /* Removed top offset for better alignment */
        }
        .education {
            padding: 8rem 4% 2rem;
        }
        .timeline-items {
            position: relative;
        }
        .timeline-items::before {
            left: 10px;
            width: 4px;
        }
        .timeline-item {
            margin-bottom: 30px;
            padding-left: 40px !important;
            padding-right: 20px !important;
            text-align: left !important;
        }
        .timeline-dot {
            left: 3px;
            height: 16px;
            width: 16px;
            top: 8px;
        }
        .timeline-date {
            font-size: 1.8rem;
            margin: 4px 0 10px;
        }
        .timeline-content {
            padding: 20px 30px;
            border-radius: 2rem;
            box-shadow: 0 0 8px var(--main-color);
        }
        .timeline-content h3 {
            font-size: 1.8rem;
        }
        .timeline-content p {
            font-size: 1.4rem;
            line-height: 20px;
        }
    }
    @media (max-width: 768px) {
        #menu-icon {
            display: block;
        }
        .navbar {
            position: absolute;
            top: 100%;
            left: 0;
            width: 100%;
            padding: 1rem 4%;
            background: var(--bg-color);
            flex-direction: column;
            display: none;
        }
        .navbar.active {
            display: flex;
        }
        .navbar a {
            display: block;
            font-size: 2rem;
            margin: 3rem 0;
        }
        .home {
            flex-direction: column; /* Restored original column layout */
            gap: 5rem;
        }
        .home-img {
            order: -1; /* Added: Moves image to top */
            text-align: center;
        }
        .home-img img {
            width: 50vw;
            top: 0;
        }
        .education {
            padding: 6rem 4% 2rem;
        }
        .heading {
            font-size: 6rem;
        }
        .timeline-item {
            margin-bottom: 25px;
            padding-left: 35px !important;
        }
        .timeline-content {
            padding: 15px 25px;
        }
        .timeline-date {
            font-size: 1.6rem;
        }
        .timeline-content h3 {
            font-size: 1.6rem;
        }
        .timeline-content p {
            font-size: 1.3rem;
        }
    }
    @media (max-width: 480px) {
        .home {
            flex-direction: column; /* Restored original column layout */
            gap: 5rem;
        }
        .home-img {
            order: -1; /* Added: Moves image to top */
            text-align: center;
        }
        .home-img img {
            width: 50vw;
            top: 0;
        }
        .education {
            padding: 5rem 3% 2rem;
        }
        .timeline-items::before {
            left: 8px;
            width: 3px;
        }
        .timeline-dot {
            left: 2px;
            height: 14px;
            width: 14px;
            top: 7px;
        }
        .timeline-item {
            padding-left: 30px !important;
        }
        .timeline-content {
            padding: 12px 20px;
            border-radius: 1.5rem;
        }
        .timeline-date {
            font-size: 1.5rem;
        }
        .timeline-content h3 {
            font-size: 1.5rem;
        }
        .timeline-content p {
            font-size: 1.2rem;
            line-height: 18px;
        }
    }
</style>
</head>
<body>
<div id="particles-js"></div>
<header class="header">
    <a href="#home" class="logo">FAY<span>SAL</span></a>
    <i class='bx bx-menu' id="menu-icon"></i>
    <nav class="navbar">
        <a href="#home" class="active">Home</a>
        <a href="#education">Education</a>
        <a href="#services">Services</a>
        <a href="#contact">Contact</a>
    </nav>
</header>

<section class="home" id="home">
    <div class="home-content">
        <h3>Hi, It's Me <span>Faysal </span></h1>
        <h3 class="text-animation">I'm a <span></span></h3>
        <p>I am a skilled Hacker App Developer, Ha, and Web Developer with a passion for 
            creating innovative and user-friendly digital solutions. With expertise in mobile 
            app development, modern web design, and professional graphic design, I strive to 
            deliver high-quality work that meets client needs and enhances user experience. Whether it's 
            developing a dynamic mobile application, designing a stunning website, or crafting visually appealing 
            graphics, I am committed to bringing ideas to life with precision and creativity. If you're looking for 
            a reliable professional to transform your vision into reality, feel free to get in touch!</p>
        <div class="social-icons">
            <a href="https://wa.me/01648289823" target="_blank"><i class='bx bxl-whatsapp'></i></a>
            <a href="https://t.me/ariyan_Cyber_Zone" target="_blank"><i class='bx bxl-telegram'></i></a>
            <a href="https://www.youtube.com/@DreamStory-n7ef" target="_blank"><i class='bx bxl-youtube'></i></a>
        </div>
        <div class="btn-group">
            <a href="#" class="btn" onclick="showModal('Hire functionality coming soon!')">Hire</a>
            <a href="#contact" class="btn">Contact</a>
        </div>
    </div>
    <div class="home-img">
        <img src="https://i.ibb.co/TDXYxnBW/c93074fa35.jpg" alt="Profile Image">
    </div>
</section>

<section class="education" id="education">
    <h2 class="heading">Education</h2>
    <div class="timeline-items">
        <div class="timeline-item">
            <div class="timeline-dot"></div>
            <div class="timeline-date">2025-2026</div>
            <div class="timeline-content">
                <h3>High School</h3>
                <p>I completed my HSC examination under Dhaka Board in 2025 . Where I got very good results. Since then, my addiction to programming has increased.</p>
            </div>
        </div>
        </div>
        <div class="timeline-item">
            <div class="timeline-dot"></div>
            <div class="timeline-date">2020 - 25</div>
            <div class="timeline-content">
                <h3>Job Skill</h3>
                <p>I was working in Computer Science at a private school since 2020 and left the job in 2025 to join my university life.</p>
            </div>
        </div>
    </div>
</section>

<section class="services" id="services">
    <h2 class="heading">Services</h2>
    <div class="services-container">
        <div class="service-box">
            <h3>Web Development</h3>
            <p>Building responsive and high-performance websites using modern technologies like HTML, CSS, and JavaScript.</p>
        </div>
        <div class="service-box">
            <h3>UI/UX Design</h3>
            <p>Creating user-friendly and visually appealing interfaces with a focus on user experience.</p>
        </div>
        <div class="service-box">
            <h3>App Development</h3>
            <p>Professional app designer. We develop apps in line with current modern technology.</p>
        </div>
        <div class="service-box">
            <h3>Frontend Development</h3>
            <p>Developing dynamic and interactive frontends using frameworks like React and Vue.js.</p>
        </div>
    </div>
</section>

<section class="contact" id="contact">
    <h2 class="heading">Contact</h2>
    <form id="contact-form">
        <input type="text" id="name" placeholder="Your Name" required>
        <div id="name-error" class="error"></div>
        <input type="email" id="email" placeholder="Your Email" required>
        <div id="email-error" class="error"></div>
        <textarea id="message" placeholder="Your Message" required></textarea>
        <div id="message-error" class="error"></div>
        <div class="g-recaptcha" data-sitekey="6LfxuCsrAAAAAFNKnI8eXC2oHh-Y6u98JmMM1Fg_"></div>
        <div id="recaptcha-error" class="error"></div>
        <button type="submit" class="btn">Send Message</button>
    </form>
    <div class="social-icons" style="text-align: center; margin-top: 3rem;">

        <a href="ttps://wa.me/01648289823" target="_blank"><i class='bx bxl-whatsapp'></i></a>
        <a href="https://t.me/ariyan_Cyber_Zone" target="_blank"><i class='bx bxl-telegram'></i></a>
        <a href="https://www.youtube.com/@DreamStory-n7ef" target="_blank"><i class='bx bxl-youtube'></i></a>
    </div>
    <div class="modal" id="message-modal">
        <div class="modal-content">
            <h3>Message</h3>
            <p id="modal-message"></p>
            <button class="btn" onclick="closeModal()">Close</button>
        </div>
    </div>
</section>

<script>
    // EmailJS initialization
    (function(){
        emailjs.init("PdF1OyscdLdhNl91N");
    })();

    // Particles.js initialization with enhanced interactivity
    particlesJS('particles-js', {
        particles: {
            number: { value: 80, density: { enable: true, value_area: 800 } },
            color: { value: '#00ffee' },
            shape: { type: 'circle', stroke: { width: 0, color: '#000000' } },
            opacity: { value: 0.5, random: false, anim: { enable: false } },
            size: { value: 3, random: true, anim: { enable: false } },
            line_linked: { enable: true, distance: 150, color: '#00ffee', opacity: 0.4, width: 1 },
            move: { enable: true, speed: 4, direction: 'none', random: false, straight: false, out_mode: 'out', bounce: false } // Increased speed for normal movement
        },
        interactivity: {
            detect_on: 'canvas',
            events: { 
                onhover: { enable: true, mode: 'grab' }, // Changed to 'grab' for mouse interaction
                onclick: { enable: true, mode: 'push' }, 
                resize: true 
            },
            modes: { 
                grab: { distance: 140, line_linked: { opacity: 1 } }, // Particles connect to cursor
                push: { particles_nb: 4 } 
            }
        },
        retina_detect: true
    });

    // Hamburger Menu Toggle
    const menuIcon = document.getElementById('menu-icon');
    const navbar = document.querySelector('.navbar');
    menuIcon.addEventListener('click', () => {
        navbar.classList.toggle('active');
        menuIcon.classList.toggle('bx-x');
    });

    // Active Link on Scroll
    const sections = document.querySelectorAll('section');
    const navLinks = document.querySelectorAll('.navbar a');
    window.addEventListener('scroll', () => {
        let current = '';
        sections.forEach(section => {
            const sectionTop = section.offsetTop;
            if (pageYOffset >= sectionTop - 60) {
                current = section.getAttribute('id');
            }
        });
        navLinks.forEach(link => {
            link.classList.remove('active');
            if (link.getAttribute('href').slice(1) === current) {
                link.classList.add('active');
            }
        });
    });

    // Close Navbar on Link Click (Mobile)
    navLinks.forEach(link => {
        link.addEventListener('click', () => {
            navbar.classList.remove('active');
            menuIcon.classList.remove('bx-x');
        });
    });

    // Modal Functions
    function showModal(message) {
        const modal = document.getElementById('message-modal');
        const modalMessage = document.getElementById('modal-message');
        modalMessage.textContent = message;
        modal.style.display = 'flex';
    }

    function closeModal() {
        const modal = document.getElementById('message-modal');
        modal.style.display = 'none';
    }

    // Contact Form Validation and Submission
    const form = document.getElementById('contact-form');
    const nameInput = document.getElementById('name');
    const emailInput = document.getElementById('email');
    const messageInput = document.getElementById('message');
    const nameError = document.getElementById('name-error');
    const emailError = document.getElementById('email-error');
    const messageError = document.getElementById('message-error');
    const recaptchaError = document.getElementById('recaptcha-error');

    form.addEventListener('submit', (e) => {
        e.preventDefault();
        let isValid = true;

        // Reset error messages
        nameError.textContent = '';
        emailError.textContent = '';
        messageError.textContent = '';
        recaptchaError.textContent = '';

        // Validate Name
        if (nameInput.value.trim().length < 2) {
            nameError.textContent = 'নাম কমপক্ষে ২ অক্ষরের হতে হবে';
            isValid = false;
        }

        // Validate Email
        const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        if (!emailRegex.test(emailInput.value.trim())) {
            emailError.textContent = 'দয়া করে একটি বৈধ ইমেইল ঠিকানা দিন';
            isValid = false;
        }

        // Validate Message
        if (messageInput.value.trim().length < 10) {
            messageError.textContent = 'মেসেজ কমপক্ষে ১০ অক্ষরের হতে হবে';
            isValid = false;
        }

        // Validate reCAPTCHA
        const recaptchaResponse = grecaptcha.getResponse();
        if (!recaptchaResponse) {
            recaptchaError.textContent = 'দয়া করে reCAPTCHA যাচাই করুন';
            isValid = false;
        }

        if (isValid) {
            // Send message with EmailJS
            emailjs.send('service_d4l75m9', 'template_kzu7diw', {
                name: nameInput.value.trim(),
                email: emailInput.value.trim(),
                message: messageInput.value.trim(),
                'g-recaptcha-response': recaptchaResponse
            })
            .then(() => {
                showModal('মেসেজ সফলভাবে পাঠানো হয়েছে!');
                form.reset();
                grecaptcha.reset();
            }, (error) => {
                showModal('মেসেজ পাঠাতে ব্যর্থ। দয়া করে আবার চেষ্টা করুন।');
                console.error('EmailJS error:', error);
            });
        }
    });
</script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9396a12b1e42b099',t:'MTc0NjE3OTU4NS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'93976e006d43b042',t:'MTc0NjE4Nzk3NS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'93978162ab4e7b9b',t:'MTc0NjE4ODc2OS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script>
<script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'93982a23cceb453d',t:'MTc0NjE5NTY4MS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script>
</body>
</html>
