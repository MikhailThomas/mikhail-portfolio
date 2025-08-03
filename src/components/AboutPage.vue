<template>
    <div class="about-page">
        <div class="about-content">
            <div class="about-header">
                <h1 class="about-title">ABOUT ME</h1>
                <p class="about-subtitle">Creative Developer & Digital Artist</p>
            </div>

            <div class="about-sections">
                <!-- Personal Info Section -->
                <div class="about-section">
                    <h2 class="section-title">WHO I AM</h2>
                    <div class="personal-info">
                        <div class="info-card">
                            <h3>Full Stack Developer</h3>
                            <p>Passionate about creating innovative web applications with cutting-edge technologies.</p>
                        </div>
                        <div class="info-card">
                            <h3>Digital Artist</h3>
                            <p>Blending creativity with technology to create stunning visual experiences.</p>
                        </div>
                        <div class="info-card">
                            <h3>Problem Solver</h3>
                            <p>Turning complex challenges into elegant, user-friendly solutions.</p>
                        </div>
                    </div>
                </div>

                <!-- Skills Section -->
                <div class="about-section">
                    <h2 class="section-title">SKILLS & TECHNOLOGIES</h2>
                    <div class="skills-grid">
                        <div class="skill-category">
                            <h3 class="category-title">Frontend</h3>
                            <div class="skill-tags">
                                <span class="skill-tag">Vue.js</span>
                                <span class="skill-tag">React</span>
                                <span class="skill-tag">JavaScript</span>
                                <span class="skill-tag">TypeScript</span>
                                <span class="skill-tag">HTML5</span>
                                <span class="skill-tag">CSS3</span>
                                <span class="skill-tag">Sass</span>
                            </div>
                        </div>

                        <div class="skill-category">
                            <h3 class="category-title">Backend</h3>
                            <div class="skill-tags">
                                <span class="skill-tag">Node.js</span>
                                <span class="skill-tag">Python</span>
                                <span class="skill-tag">Express</span>
                                <span class="skill-tag">Django</span>
                                <span class="skill-tag">PostgreSQL</span>
                                <span class="skill-tag">MongoDB</span>
                            </div>
                        </div>

                        <div class="skill-category">
                            <h3 class="category-title">Tools & Others</h3>
                            <div class="skill-tags">
                                <span class="skill-tag">Git</span>
                                <span class="skill-tag">Docker</span>
                                <span class="skill-tag">AWS</span>
                                <span class="skill-tag">Figma</span>
                                <span class="skill-tag">Photoshop</span>
                                <span class="skill-tag">Illustrator</span>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Experience Section -->
                <div class="about-section">
                    <h2 class="section-title">EXPERIENCE</h2>
                    <div class="timeline">
                        <div class="timeline-item">
                            <div class="timeline-marker"></div>
                            <div class="timeline-content">
                                <h3>Senior Frontend Developer</h3>
                                <p class="timeline-company">TechCorp Inc.</p>
                                <p class="timeline-period">2022 - Present</p>
                                <p>Leading frontend development for enterprise applications using Vue.js and modern web
                                    technologies.</p>
                            </div>
                        </div>

                        <div class="timeline-item">
                            <div class="timeline-marker"></div>
                            <div class="timeline-content">
                                <h3>Full Stack Developer</h3>
                                <p class="timeline-company">StartupXYZ</p>
                                <p class="timeline-period">2020 - 2022</p>
                                <p>Built scalable web applications from concept to deployment using React, Node.js, and
                                    cloud services.</p>
                            </div>
                        </div>

                        <div class="timeline-item">
                            <div class="timeline-marker"></div>
                            <div class="timeline-content">
                                <h3>Junior Developer</h3>
                                <p class="timeline-company">Digital Agency</p>
                                <p class="timeline-period">2018 - 2020</p>
                                <p>Developed responsive websites and e-commerce solutions for various clients.</p>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Education Section -->
                <div class="about-section">
                    <h2 class="section-title">EDUCATION</h2>
                    <div class="education-card">
                        <div class="education-info">
                            <h3>Bachelor of Computer Science</h3>
                            <p>University of Technology</p>
                            <p>2014 - 2018</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Floating Elements -->
        <div class="about-floating-elements">
            <div class="floating-code code-1">&lt;/&gt;</div>
            <div class="floating-code code-2">{ }</div>
            <div class="floating-code code-3">[ ]</div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'AboutPage'
}
</script>

<style scoped>
.about-page {
    position: relative;
    width: 100vw;
    min-height: 100vh;
    overflow: hidden;
    /* font-family: 'Arial Black', 'Helvetica Bold', sans-serif; */
    padding-top: 100px;
    background: var(--bg-primary);
}

.about-content {
    position: relative;
    z-index: 1;
    padding: 2rem;
    max-width: 1200px;
    margin: 0 auto;
}

.about-header {
    text-align: center;
    margin-bottom: 4rem;
}

.about-title {
    font-size: clamp(3rem, 8vw, 6rem);
    font-weight: 900;
    color: #ffffff;
    text-shadow:
        4px 4px 0 #ff0000,
        8px 8px 0 #00ffff;
    margin-bottom: 1rem;
    animation: titleFloat 3s ease-in-out infinite;
}

.about-subtitle {
    font-size: clamp(1.5rem, 4vw, 2.5rem);
    color: #ffffff;
    text-shadow: 2px 2px 0 #000000;
    background: linear-gradient(45deg, #ffff00, #ff00ff);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
}

.about-sections {
    display: grid;
    gap: 4rem;
}

.about-section {
    background: rgba(0, 0, 0, 0.8);
    border: 4px solid #ff0000;
    padding: 3rem;
    box-shadow:
        8px 8px 0 #00ffff,
        16px 16px 0 #ffff00;
}

.section-title {
    font-size: clamp(2rem, 5vw, 3rem);
    font-weight: 900;
    color: #ffff00;
    text-align: center;
    margin-bottom: 2rem;
    text-shadow: 2px 2px 0 #000000;
}

/* Personal Info Cards */
.personal-info {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
}

.info-card {
    background: rgba(255, 255, 255, 0.1);
    border: 3px solid #00ffff;

    padding: 2rem;
    text-align: center;
    backdrop-filter: blur(10px);
    transition: all 0.3s ease;
}

.info-card:hover {
    transform: translateY(-5px);
    border-color: #ff00ff;
    box-shadow: 0 10px 30px rgba(255, 0, 255, 0.3);
}



.info-card h3 {
    font-size: 1.5rem;
    color: #ffff00;
    margin-bottom: 1rem;
    text-shadow: 1px 1px 0 #000000;
}

.info-card p {
    color: #ffffff;
    line-height: 1.6;
    text-shadow: 1px 1px 0 #000000;
}

/* Skills Grid */
.skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 2rem;
}

.skill-category {
    background: rgba(255, 255, 255, 0.1);
    border: 3px solid #00ff00;

    padding: 2rem;
    backdrop-filter: blur(10px);
}

.category-title {
    font-size: 1.5rem;
    color: #00ff00;
    text-align: center;
    margin-bottom: 1.5rem;
    text-shadow: 1px 1px 0 #000000;
}

.skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.8rem;
    justify-content: center;
}

.skill-tag {
    background: linear-gradient(45deg, #ff0000, #00ffff);
    color: #ffffff;
    padding: 0.5rem 1rem;
    border-radius: 20px;
    font-weight: bold;
    font-size: 0.9rem;
    border: 2px solid #000000;
    box-shadow: 2px 2px 0 #ffff00;
    transition: all 0.3s ease;
}

.skill-tag:hover {
    transform: translateY(-2px);
    box-shadow: 4px 4px 0 #ffff00;
    background: linear-gradient(45deg, #ffff00, #ff00ff);
    color: #000000;
}

/* Timeline */
.timeline {
    position: relative;
    padding-left: 2rem;
}

.timeline::before {
    content: '';
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    width: 4px;
    background: linear-gradient(to bottom, #ff0000, #00ffff, #ffff00);
}

.timeline-item {
    position: relative;
    margin-bottom: 3rem;
    padding-left: 2rem;
}

.timeline-marker {
    position: absolute;
    left: -1.5rem;
    top: 0.5rem;
    width: 20px;
    height: 20px;
    background: #ff00ff;
    border: 3px solid #000000;
    border-radius: 50%;
    box-shadow: 0 0 0 4px #ffff00;
}

.timeline-content {
    background: rgba(255, 255, 255, 0.1);
    border: 3px solid #ff00ff;

    padding: 1.5rem;
    backdrop-filter: blur(10px);
}

.timeline-content h3 {
    color: #ffff00;
    font-size: 1.3rem;
    margin-bottom: 0.5rem;
    text-shadow: 1px 1px 0 #000000;
}

.timeline-company {
    color: #00ffff;
    font-weight: bold;
    margin-bottom: 0.3rem;
    text-shadow: 1px 1px 0 #000000;
}

.timeline-period {
    color: #ff0000;
    font-weight: bold;
    margin-bottom: 1rem;
    text-shadow: 1px 1px 0 #000000;
}

.timeline-content p:last-child {
    color: #ffffff;
    line-height: 1.6;
    text-shadow: 1px 1px 0 #000000;
}

/* Education */
.education-card {
    display: flex;
    align-items: center;
    gap: 2rem;
    background: rgba(255, 255, 255, 0.1);
    border: 3px solid #ffff00;

    padding: 2rem;
    backdrop-filter: blur(10px);
}



.education-info h3 {
    color: #ffff00;
    font-size: 1.5rem;
    margin-bottom: 0.5rem;
    text-shadow: 1px 1px 0 #000000;
}

.education-info p {
    color: #ffffff;
    margin-bottom: 0.3rem;
    text-shadow: 1px 1px 0 #000000;
}

/* Floating Elements */
.about-floating-elements {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
    z-index: 1;
}

.floating-code {
    position: absolute;
    font-size: 2rem;
    font-weight: bold;
    color: #00ffff;
    opacity: 0.6;
    animation: float 6s ease-in-out infinite;
}

.code-1 {
    top: 20%;
    left: 10%;
    animation-delay: 0s;
}

.code-2 {
    top: 60%;
    right: 15%;
    animation-delay: 2s;
}

.code-3 {
    bottom: 30%;
    left: 20%;
    animation-delay: 4s;
}

/* Animations */
@keyframes titleFloat {

    0%,
    100% {
        transform: translateY(0px);
    }

    50% {
        transform: translateY(-8px);
    }
}

@keyframes bounce {

    0%,
    100% {
        transform: translateY(0px);
    }

    50% {
        transform: translateY(-10px);
    }
}

@keyframes float {

    0%,
    100% {
        transform: translateY(0px) rotate(0deg);
    }

    50% {
        transform: translateY(-20px) rotate(180deg);
    }
}

/* Responsive Design */
@media (max-width: 768px) {
    .about-content {
        padding: 1rem;
    }

    .about-section {
        padding: 2rem;
    }

    .personal-info {
        grid-template-columns: 1fr;
    }

    .skills-grid {
        grid-template-columns: 1fr;
    }

    .education-card {
        flex-direction: column;
        text-align: center;
    }

    .floating-code {
        display: none;
    }
}

@media (max-width: 480px) {
    .about-title {
        font-size: clamp(2rem, 6vw, 3rem);
    }

    .about-subtitle {
        font-size: clamp(1rem, 3vw, 1.5rem);
    }

    .about-section {
        padding: 1.5rem;
    }

    .timeline {
        padding-left: 1rem;
    }

    .timeline-item {
        padding-left: 1rem;
    }
}
</style>