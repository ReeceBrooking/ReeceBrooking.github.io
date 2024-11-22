<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Personal portfolio showcasing my projects and skills.">
    <link rel="stylesheet" href="assets/styles.css">
    <script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>
    <title>Portfolio with Collapsible Skills</title>
</head>
<body>
    <!-- Header Section -->
    <header>
        <h1><i class="fas fa-user-circle"></i> My Portfolio</h1>
        <nav>
            <ul class="inline-list">
                <li><a href="index.html"><i class="fas fa-home"></i> Home</a></li>
                <li><a href="projects.html"><i class="fas fa-project-diagram"></i> Projects</a></li>
                <li><a href="about.html"><i class="fas fa-info-circle"></i> About Me</a></li>
            </ul>
        </nav>
    </header>

    <!-- About Section -->
<section class="about">
        <div class="about-content">
            <img src="assets/headshot.jpg" alt="Headshot" class="headshot">
            <div>
                <h2>About Me</h2>
                <p>
                    I am a passionate Data Scientist with a strong background in mathematics and machine learning. I specialize in creating data-driven solutions to complex problems and love collaborating with teams to bring ideas to life. 
                </p>
            </div>
        </div>
    </section>

    <!-- Education Section -->
<section>
        <h2><i class="fas fa-graduation-cap"></i> Education</h2>
        <h3>BSc, Mathematics</h3>
        <p><em>Loughborough University, UK</em> (<span>2021–2024</span>)</p>
        <div class="card-list">
            <div class="card">
                <h4>Statistics for Large Data</h4>
                <p>Advanced methods for analyzing and interpreting big datasets.</p>
            </div>
            <div class="card">
                <h4>Linear Algebra</h4>
                <p>Foundational mathematical concepts for computational modeling.</p>
            </div>
            <div class="card">
                <h4>Graph Theory</h4>
                <p>Studying network structures and algorithms.</p>
            </div>
            <div class="card">
                <h4>Calculus</h4>
                <p>In-depth study of limits, derivatives, and integrals.</p>
            </div>
            <div class="card">
                <h4>Probability Theory</h4>
                <p>Advanced concepts in probability and stochastic processes.</p>
            </div>
            <div class="card">
                <h4>Mathematical Modeling</h4>
                <p>Modeling real-world problems using mathematical techniques.</p>
            </div>
        </div>
    </section>

    <!-- Skills Section -->
  <section>
        <h2><i class="fas fa-tools"></i> Skills</h2>
        <div class="collapsible">
            <button class="collapsible-btn">Technical Skills</button>
            <div class="collapsible-content">
                <ul>
                    <li>Data Analysis</li>
                    <li>Machine Learning</li>
                    <li>Deep Learning</li>
                    <li>Optimization</li>
                </ul>
            </div>
            <button class="collapsible-btn">Programming Languages</button>
            <div class="collapsible-content">
                <ul>
                    <li>Python</li>
                    <li>R</li>
                    <li>SQL</li>
                    <li>MATLAB</li>
                </ul>
            </div>
            <button class="collapsible-btn">Soft Skills</button>
            <div class="collapsible-content">
                <ul>
                    <li>Team Coordination</li>
                    <li>Client Communication</li>
                    <li>Problem Solving</li>
                </ul>
            </div>
            <button class="collapsible-btn">Languages</button>
            <div class="collapsible-content">
                <ul>
                    <li>English (Native)</li>
                    <li>Spanish (B2)</li>
                    <li>French (A2)</li>
                </ul>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
 <section class="projects">
        <h2><i class="fas fa-tasks"></i> Projects</h2>
        <article class="project-item">
            <img src="assets/40.png" alt="Screenshot of X-Ray project" class="project-image">
            <div>
                <h3><i class="fas fa-x-ray"></i> X-Ray Multi-Class Classification</h3>
                <p>This project focuses on multi-class classification of X-ray images using deep learning techniques.</p>
                <a href="https://github.com/your-github-repo" target="_blank">View on GitHub <i class="fas fa-external-link-alt"></i></a>
            </div>
        </article>
    </section>

    <!-- Footer -->
<footer>
        <p><a href="https://github.com/username"><i class="fab fa-github"></i> GitHub</a> | <a href="https://linkedin.com/in/username"><i class="fab fa-linkedin"></i> LinkedIn</a></p>
    </footer>
</body>
</html>
<script>
    const collapsibles = document.querySelectorAll(".collapsible-btn");
    collapsibles.forEach(button => {
        button.addEventListener("click", () => {
            const content = button.nextElementSibling;
            content.style.display = content.style.display === "block" ? "none" : "block";
        });
    });
</script>

