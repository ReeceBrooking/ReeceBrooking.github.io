<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Personal portfolio showcasing my projects and skills.">
    <link rel="stylesheet" href="assets/styles.css">
    <script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>
    <title>Portfolio</title>
</head>
<body>
    <!-- Header Section -->
    <header class="header">
        <h1><i class="fas fa-user-circle"></i>Data Science and Machine Learning Portfolio</h1>
    </header>

    <!-- About Section -->
  <section class="plaque about">
        <div class="about-content">
            <img src="assets/headshot.jpg" alt="Headshot" class="headshot">
            <div>
                <h2>About Me</h2>
                <p>
                    I am an undergraduate in Mathematics with a solid foundation in Physics, Machine Learning, and Life Sciences. Inspired by my parents’ contributions to the Human Genome Project, I cultivated a deep passion for science, which later evolved into a keen interest in applying data science to interdisciplinary challenges.
                </p>
                <p>
                    My journey into machine learning stems from a strong grounding in applied mathematics, honed during my A-Levels in Further Mathematics and carried forward into diverse, hands-on projects. These include bioinformatics, image classification, and sentiment analysis, where I leveraged my expertise in <strong>Python</strong> and key libraries such as <strong>Pandas</strong>, <strong>Scikit-learn</strong>, <strong>TensorFlow</strong>, Keras, NumPy, SciPy, and Matplotlib.
                </p>
                <p>
                    I am enthusiastic about opportunities to integrate my analytical and technical skills in collaborative environments, particularly those that connect data science with other fields. My goal is to contribute to innovative solutions at the intersection of technology, mathematics, and the sciences.
                </p>
            </div>
        </div>
    </section>

    <!-- Education Section -->
<section class="plaque">
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
                <p>Exploring strategic interactions and decision-making in competitive and cooperative environments.</p>
            </div>
            <div class="card">
                <h4>Operational Research</h4>
                <p>Applying mathematical techniques to optimize processes and decision-making in complex systems.</p>
            </div>
            <div class="card">
                <h4>Probability Theory</h4>
                <p>Advanced concepts in probability and stochastic processes.</p>
            </div>
            <div class="card">
                <h4>Mathematical Biology</h4>
                <p>Modeling biological systems using mathematical frameworks to study dynamics and patterns.</p>
            </div>
            <div class="card">
                <h4>Game Theory</h4>
                <p>Exploring strategic interactions and decision-making in competitive and cooperative environments.</p>
            </div>
            <div class="card">
                <h4>Communicating Mathematics</h4>
                <p>Communicating complex mathematical concepts in an easy-to-digest presentation.</p>
            </div>
        </div>
    </section>

    <!-- Skills Section -->
<section class="plaque">
        <h2><i class="fas fa-tools"></i> Skills</h2>
        <div class="collapsible">
            <button class="collapsible-btn">Technical Skills</button>
            <div class="collapsible-content">
                <ul>
                    <li><strong>Statistical Analysis and Data Visualisation</strong></li>
                    <li><strong>Regression and Supervised/Unsupervised Machine Learning</strong></li>
                    <li><strong>Deep Learning</strong></li>
                    <li>Discrete Mathematics and Optimisation Algorithms</li>
                    <li>Computational Methods</li>
                    <li>Mathematical Modelling</li>
                </ul>
            </div>
            <button class="collapsible-btn">Programming Languages</button>
            <div class="collapsible-content">
                <ul>
                    <li><strong>Python</strong></li>
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
                    <li>Effective Communication</li>
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
  <section class="plaque">
        <h2><i class="fas fa-tasks"></i> Projects</h2>
        <article class="project-item">
            <img src="assets/41.png" alt="Screenshot of X-Ray project" class="project-image">
            <div class="project-text">
                <h3><i class="fas fa-x-ray"></i> X-Ray Multi-Class Classification</h3>
                <p>This project focuses on multi-class classification of X-ray images using deep learning techniques.</p>
                <button class="open-modal-btn" data-modal="project-modal-1">View Details</button>
            </div>
        </article>
    </section>

    <!-- Modal -->
 <div id="project-modal-1" class="modal">
        <div class="modal-content">
            <span class="close-modal-btn">&times;</span>
            <h3>X-Ray Multi-Class Classification</h3>
             <p>
                <strong>Technologies Used:</strong> Python, TensorFlow, Keras.
            </p>
            <p>
                This project involves using a convolutional neural network to classify X-ray images into "Healthy", "Covid" or "Pneumonia".
                It demonstrates advanced machine learning techniques for image recognition.
            </p>
            <a href="https://github.com/ReeceBrooking/ReeceBrooking.github.io/tree/main/x-ray-classification" target="_blank" class="modal-link">
                View on GitHub <i class="fas fa-external-link-alt"></i>
            </a>
        </div>
    </div>

    <!-- Footer -->
 <footer>
        <p><a href="https://github.com/ReeceBrooking/ReeceBrooking.github.io"><i class="fab fa-github"></i> GitHub</a> | <a href="https://www.linkedin.com/in/reece-brooking-371b0730a/"><i class="fab fa-linkedin"></i> LinkedIn</a></p>
    </footer>

    <!-- JavaScript -->
 <script>
        // Open modal
        document.querySelectorAll('.open-modal-btn').forEach(button => {
            button.addEventListener('click', () => {
                const modalId = button.getAttribute('data-modal');
                const modal = document.getElementById(modalId);
                modal.style.display = 'flex';
            });
        });

        // Close modal
        document.querySelectorAll('.close-modal-btn').forEach(button => {
            button.addEventListener('click', () => {
                const modal = button.closest('.modal');
                modal.style.display = 'none';
            });
        });

        // Close modal when clicking outside the content
        window.addEventListener('click', (event) => {
            if (event.target.classList.contains('modal')) {
                event.target.style.display = 'none';
            }
        });

        // Collapsible functionality
        const collapsibles = document.querySelectorAll(".collapsible-btn");
        collapsibles.forEach(button => {
            button.addEventListener("click", () => {
                const content = button.nextElementSibling;
                button.classList.toggle("active");
                if (content.style.maxHeight) {
                    content.style.maxHeight = null;
                    content.style.opacity = 0;
                } else {
                    content.style.maxHeight = content.scrollHeight + "px";
                    content.style.opacity = 1;
                }
            });
        });
    </script>
</body>
</html>
