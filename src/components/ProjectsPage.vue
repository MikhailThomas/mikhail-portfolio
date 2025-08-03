<template>
    <div class="projects-page">
        <div class="projects-content">
            <div class="projects-header">
                <h1 class="projects-title">MY PROJECTS</h1>
                <p class="projects-subtitle">Showcasing Creative Development & Design</p>
            </div>

            <!-- Project Filters -->
            <div class="project-filters">
                <button v-for="filter in filters" :key="filter.id" @click="activeFilter = filter.id"
                    :class="['filter-button', { active: activeFilter === filter.id }]">
                    {{ filter.name }}
                </button>
            </div>

            <!-- Projects Grid -->
            <div class="projects-grid">
                <div v-for="project in filteredProjects" :key="project.id" class="project-card"
                    @click="openProjectModal(project)">
                    <div class="project-image">
                        <img :src="project.image" :alt="project.title" />
                        <div class="project-overlay">
                            <div class="project-links">
                                <a :href="project.liveUrl" target="_blank" class="project-link">
                                    <span class="link-text">Live Demo</span>
                                </a>
                                <a :href="project.githubUrl" target="_blank" class="project-link">
                                    <span class="link-text">Code</span>
                                </a>
                            </div>
                        </div>
                    </div>

                    <div class="project-info">
                        <h3 class="project-title">{{ project.title }}</h3>
                        <p class="project-description">{{ project.description }}</p>
                        <div class="project-tech">
                            <span v-for="tech in project.technologies" :key="tech" class="tech-tag">
                                {{ tech }}
                            </span>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Project Modal -->
        <div v-if="selectedProject" class="project-modal" @click="closeProjectModal">
            <div class="modal-content" @click.stop>
                <button class="modal-close" @click="closeProjectModal">×</button>
                <div class="modal-image">
                    <img :src="selectedProject.image" :alt="selectedProject.title" />
                </div>
                <div class="modal-info">
                    <h2 class="modal-title">{{ selectedProject.title }}</h2>
                    <p class="modal-description">{{ selectedProject.fullDescription }}</p>
                    <div class="modal-tech">
                        <h3>Technologies Used:</h3>
                        <div class="tech-list">
                            <span v-for="tech in selectedProject.technologies" :key="tech" class="tech-item">
                                {{ tech }}
                            </span>
                        </div>
                    </div>
                    <div class="modal-links">
                        <a :href="selectedProject.liveUrl" target="_blank" class="modal-link">
                            <span class="link-text">View Live Demo</span>
                        </a>
                        <a :href="selectedProject.githubUrl" target="_blank" class="modal-link">
                            <span class="link-text">View Source Code</span>
                        </a>
                    </div>
                </div>
            </div>
        </div>

        <!-- Floating Elements -->
        <div class="projects-floating-elements">
            <div class="floating-device device-1">💻</div>
            <div class="floating-device device-2">📱</div>
            <div class="floating-device device-3">🎮</div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ProjectsPage',
    data() {
        return {
            activeFilter: 'all',
            selectedProject: null,
            filters: [
                { id: 'all', name: 'ALL' },
                { id: 'web', name: 'WEB APPS' },
                { id: 'mobile', name: 'MOBILE' },
                { id: 'design', name: 'DESIGN' }
            ],
            projects: [
                {
                    id: 1,
                    title: 'E-Commerce Platform',
                    description: 'Full-stack e-commerce solution with payment integration',
                    fullDescription: 'A comprehensive e-commerce platform built with Vue.js and Node.js. Features include user authentication, product management, shopping cart, payment processing with Stripe, and admin dashboard.',
                    image: 'https://picsum.photos/400/300?random=10',
                    category: 'web',
                    technologies: ['Vue.js', 'Node.js', 'MongoDB', 'Stripe', 'Express'],
                    liveUrl: '#',
                    githubUrl: '#'
                },
                {
                    id: 2,
                    title: 'Task Management App',
                    description: 'Collaborative task management with real-time updates',
                    fullDescription: 'A real-time task management application built with React and Socket.io. Features include team collaboration, drag-and-drop interface, real-time notifications, and progress tracking.',
                    image: 'https://picsum.photos/400/300?random=11',
                    category: 'web',
                    technologies: ['React', 'Socket.io', 'Node.js', 'PostgreSQL'],
                    liveUrl: '#',
                    githubUrl: '#'
                },
                {
                    id: 3,
                    title: 'Fitness Tracking Mobile App',
                    description: 'Cross-platform mobile app for fitness tracking',
                    fullDescription: 'A React Native mobile application for tracking workouts, nutrition, and fitness goals. Includes GPS tracking, workout plans, progress charts, and social features.',
                    image: 'https://picsum.photos/400/300?random=12',
                    category: 'mobile',
                    technologies: ['React Native', 'Firebase', 'Redux', 'Expo'],
                    liveUrl: '#',
                    githubUrl: '#'
                },
                {
                    id: 4,
                    title: 'Portfolio Website Design',
                    description: 'Creative portfolio website with pop art styling',
                    fullDescription: 'A visually striking portfolio website featuring pop art design elements, smooth animations, and responsive layout. Built with modern CSS and JavaScript.',
                    image: 'https://picsum.photos/400/300?random=13',
                    category: 'design',
                    technologies: ['HTML5', 'CSS3', 'JavaScript', 'GSAP'],
                    liveUrl: '#',
                    githubUrl: '#'
                },
                {
                    id: 5,
                    title: 'Weather Dashboard',
                    description: 'Real-time weather data visualization',
                    fullDescription: 'An interactive weather dashboard that displays real-time weather data with beautiful charts and maps. Features include location-based weather, forecasts, and historical data.',
                    image: 'https://picsum.photos/400/300?random=14',
                    category: 'web',
                    technologies: ['Vue.js', 'Chart.js', 'OpenWeather API', 'Leaflet'],
                    liveUrl: '#',
                    githubUrl: '#'
                },
                {
                    id: 6,
                    title: 'Social Media Dashboard',
                    description: 'Analytics dashboard for social media management',
                    fullDescription: 'A comprehensive social media analytics dashboard that aggregates data from multiple platforms. Features include performance metrics, content scheduling, and audience insights.',
                    image: 'https://picsum.photos/400/300?random=15',
                    category: 'web',
                    technologies: ['React', 'D3.js', 'Node.js', 'MongoDB'],
                    liveUrl: '#',
                    githubUrl: '#'
                }
            ]
        }
    },
    computed: {
        filteredProjects() {
            if (this.activeFilter === 'all') {
                return this.projects
            }
            return this.projects.filter(project => project.category === this.activeFilter)
        }
    },
    methods: {
        openProjectModal(project) {
            this.selectedProject = project
        },
        closeProjectModal() {
            this.selectedProject = null
        }
    }
}
</script>

<style scoped>
.projects-page {
    position: relative;
    width: 100vw;
    min-height: 100vh;
    overflow: hidden;
    padding-top: 100px;
    background: var(--bg-primary);
}

.projects-content {
    position: relative;
    z-index: 1;
    padding: 2rem;
    max-width: 1400px;
    margin: 0 auto;
}

.projects-header {
    text-align: center;
    margin-bottom: 3rem;
}

.projects-title {
    font-size: clamp(3rem, 8vw, 6rem);
    font-weight: 900;
    color: #ffffff;
    text-shadow:
        4px 4px 0 #ff0000,
        8px 8px 0 #00ffff;
    margin-bottom: 1rem;
    animation: titleFloat 3s ease-in-out infinite;
}

.projects-subtitle {
    font-size: clamp(1.5rem, 4vw, 2.5rem);
    color: #ffffff;
    text-shadow: 2px 2px 0 #000000;
    background: linear-gradient(45deg, #ffff00, #ff00ff);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
}

/* Project Filters */
.project-filters {
    display: flex;
    justify-content: center;
    gap: 1rem;
    margin-bottom: 3rem;
    flex-wrap: wrap;
}

.filter-button {
    padding: 1rem 2rem;
    background: var(--gradient-primary);
    border: var(--border-thick);
    color: var(--text-primary);
    font-weight: 900;
    font-size: 1rem;
    text-transform: uppercase;
    letter-spacing: 1px;
    cursor: pointer;
    transition: all var(--animation-fast) ease;
    box-shadow: var(--box-shadow-primary);
    border-radius: 8px;
}

.filter-button:hover {
    transform: translate(-2px, -2px);
    box-shadow: var(--box-shadow-secondary);
    background: var(--gradient-secondary);
    color: var(--pop-black);
}

.filter-button.active {
    background: linear-gradient(45deg, #ffff00, #ff00ff);
    color: #000000;
    transform: translate(-1px, -1px);
    box-shadow:
        5px 5px 0 #ffff00,
        10px 10px 0 #ff00ff;
}

/* Projects Grid */
.projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
    gap: 2rem;
}

.project-card {
    background: rgba(0, 0, 0, 0.8);
    border: 4px solid #ff0000;
    border-radius: 20px;
    overflow: hidden;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow:
        8px 8px 0 #00ffff,
        16px 16px 0 #ffff00;
}

.project-card:hover {
    transform: translateY(-10px);
    box-shadow:
        12px 12px 0 #00ffff,
        20px 20px 0 #ffff00;
}

.project-image {
    position: relative;
    height: 250px;
    overflow: hidden;
}

.project-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s ease;
}

.project-card:hover .project-image img {
    transform: scale(1.1);
}

.project-overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0, 0, 0, 0.8);
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0;
    transition: opacity 0.3s ease;
}

.project-card:hover .project-overlay {
    opacity: 1;
}

.project-links {
    display: flex;
    gap: 1rem;
}

.project-link {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.8rem 1.5rem;
    background: linear-gradient(45deg, #ff0000, #00ffff);
    border: 3px solid #000000;
    color: #ffffff;
    text-decoration: none;
    font-weight: bold;
    border-radius: 8px;
    transition: all 0.3s ease;
    box-shadow: 3px 3px 0 #ffff00;
}

.project-link:hover {
    transform: translate(-2px, -2px);
    box-shadow: 5px 5px 0 #ffff00;
    background: linear-gradient(45deg, #ffff00, #ff00ff);
    color: #000000;
}

.project-info {
    padding: 2rem;
}

.project-title {
    font-size: 1.5rem;
    color: #ffff00;
    margin-bottom: 1rem;
    text-shadow: 1px 1px 0 #000000;
}

.project-description {
    color: #ffffff;
    line-height: 1.6;
    margin-bottom: 1.5rem;
    text-shadow: 1px 1px 0 #000000;
}

.project-tech {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
}

.tech-tag {
    background: linear-gradient(45deg, #00ffff, #ff00ff);
    color: #000000;
    padding: 0.3rem 0.8rem;

    font-size: 0.8rem;
    font-weight: bold;
    border: 2px solid #000000;
}

/* Project Modal */
.project-modal {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0, 0, 0, 0.9);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;
    padding: 2rem;
}

.modal-content {
    background: rgba(0, 0, 0, 0.95);
    border: 6px solid #ff0000;
    border-radius: 20px;
    max-width: 900px;
    width: 100%;
    max-height: 90vh;
    overflow-y: auto;
    position: relative;
    box-shadow:
        12px 12px 0 #00ffff,
        24px 24px 0 #ffff00;
}

.modal-close {
    position: absolute;
    top: 1rem;
    right: 1rem;
    background: #ff0000;
    border: 3px solid #000000;
    color: #ffffff;
    font-size: 2rem;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    cursor: pointer;
    z-index: 10;
    transition: all 0.3s ease;
}

.modal-close:hover {
    background: #ffff00;
    color: #000000;
    transform: scale(1.1);
}

.modal-image {
    height: 300px;
    overflow: hidden;
}

.modal-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.modal-info {
    padding: 2rem;
}

.modal-title {
    font-size: 2rem;
    color: #ffff00;
    margin-bottom: 1rem;
    text-shadow: 2px 2px 0 #000000;
}

.modal-description {
    color: #ffffff;
    line-height: 1.8;
    margin-bottom: 2rem;
    text-shadow: 1px 1px 0 #000000;
}

.modal-tech h3 {
    color: #00ffff;
    margin-bottom: 1rem;
    text-shadow: 1px 1px 0 #000000;
}

.tech-list {
    display: flex;
    flex-wrap: wrap;
    gap: 0.8rem;
    margin-bottom: 2rem;
}

.tech-item {
    background: linear-gradient(45deg, #ff0000, #00ffff);
    color: #ffffff;
    padding: 0.5rem 1rem;
    border-radius: 20px;
    font-weight: bold;
    border: 2px solid #000000;
    box-shadow: 2px 2px 0 #ffff00;
}

.modal-links {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
}

.modal-link {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    padding: 1rem 2rem;
    background: linear-gradient(45deg, #ff0000, #00ffff);
    border: 4px solid #000000;
    color: #ffffff;
    text-decoration: none;
    font-weight: bold;
    border-radius: 10px;
    transition: all 0.3s ease;
    box-shadow: 4px 4px 0 #ffff00;
}

.modal-link:hover {
    transform: translate(-3px, -3px);
    box-shadow: 7px 7px 0 #ffff00;
    background: linear-gradient(45deg, #ffff00, #ff00ff);
    color: #000000;
}

/* Floating Elements */
.projects-floating-elements {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
    z-index: 1;
}

.floating-device {
    position: absolute;
    font-size: 2.5rem;
    opacity: 0.7;
    animation: float 6s ease-in-out infinite;
}

.device-1 {
    top: 15%;
    left: 10%;
    animation-delay: 0s;
}

.device-2 {
    top: 25%;
    right: 15%;
    animation-delay: 2s;
}

.device-3 {
    bottom: 20%;
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
    .projects-content {
        padding: 1rem;
    }

    .project-filters {
        gap: 0.5rem;
    }

    .filter-button {
        padding: 0.8rem 1.5rem;
        font-size: 0.9rem;
    }

    .projects-grid {
        grid-template-columns: 1fr;
    }

    .modal-content {
        margin: 1rem;
        max-height: 95vh;
    }

    .floating-device {
        display: none;
    }
}

@media (max-width: 480px) {
    .projects-title {
        font-size: clamp(2rem, 6vw, 3rem);
    }

    .projects-subtitle {
        font-size: clamp(1rem, 3vw, 1.5rem);
    }

    .project-filters {
        flex-direction: column;
        align-items: center;
    }

    .modal-links {
        flex-direction: column;
    }
}
</style>