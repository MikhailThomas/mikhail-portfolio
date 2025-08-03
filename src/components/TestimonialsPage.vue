<template>
    <div class="testimonials-page">
        <div class="testimonials-content">
            <div class="testimonials-header">
                <h1 class="testimonials-title">TESTIMONIALS</h1>
                <p class="testimonials-subtitle">What Clients Say About My Work</p>
            </div>

            <!-- Testimonials Grid -->
            <div class="testimonials-grid">
                <div v-for="testimonial in testimonials" :key="testimonial.id" class="testimonial-card"
                    @click="openTestimonialModal(testimonial)">
                    <div class="testimonial-header">
                        <div class="client-avatar">
                            <img :src="testimonial.avatar" :alt="testimonial.name" />
                        </div>
                        <div class="client-info">
                            <h3 class="client-name">{{ testimonial.name }}</h3>
                            <p class="client-position">{{ testimonial.position }}</p>
                            <p class="client-company">{{ testimonial.company }}</p>
                        </div>
                        <div class="rating">
                            <span v-for="star in 5" :key="star" class="star"
                                :class="{ filled: star <= testimonial.rating }">
                                ★
                            </span>
                        </div>
                    </div>

                    <div class="testimonial-content">
                        <p class="testimonial-text">{{ testimonial.text }}</p>
                    </div>

                    <div class="testimonial-footer">
                        <div class="project-info">
                            <span class="project-label">Project:</span>
                            <span class="project-name">{{ testimonial.project }}</span>
                        </div>
                        <div class="testimonial-date">{{ testimonial.date }}</div>
                    </div>
                </div>
            </div>

            <!-- Statistics Section -->
            <div class="statistics-section">
                <h2 class="section-title">SOME NUMBERS</h2>
                <div class="stats-grid">
                    <div class="stat-card">
                        <div class="stat-number">50+</div>
                        <div class="stat-label">Projects Completed</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number">100%</div>
                        <div class="stat-label">Client Satisfaction</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number">24/7</div>
                        <div class="stat-label">Support Available</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number">5.0</div>
                        <div class="stat-label">Average Rating</div>
                    </div>
                </div>
            </div>

            <!-- Call to Action -->
            <div class="cta-section">
                <h2 class="cta-title">Ready to Work Together?</h2>
                <p class="cta-text">Let's create something amazing for your next project!</p>
                <button class="cta-button" @click="$emit('navigate', 'contact')">
                    <span class="button-text">GET STARTED</span>
                </button>
            </div>
        </div>

        <!-- Testimonial Modal -->
        <div v-if="selectedTestimonial" class="testimonial-modal" @click="closeTestimonialModal">
            <div class="modal-content" @click.stop>
                <button class="modal-close" @click="closeTestimonialModal">×</button>
                <div class="modal-testimonial">
                    <div class="modal-header">
                        <div class="modal-avatar">
                            <img :src="selectedTestimonial.avatar" :alt="selectedTestimonial.name" />
                        </div>
                        <div class="modal-client-info">
                            <h2 class="modal-client-name">{{ selectedTestimonial.name }}</h2>
                            <p class="modal-client-position">{{ selectedTestimonial.position }}</p>
                            <p class="modal-client-company">{{ selectedTestimonial.company }}</p>
                            <div class="modal-rating">
                                <span v-for="star in 5" :key="star" class="star"
                                    :class="{ filled: star <= selectedTestimonial.rating }">
                                    ★
                                </span>
                            </div>
                        </div>
                    </div>
                    <div class="modal-content-text">
                        <p>{{ selectedTestimonial.fullText }}</p>
                    </div>
                    <div class="modal-project-details">
                        <h3>Project Details:</h3>
                        <p><strong>Project:</strong> {{ selectedTestimonial.project }}</p>
                        <p><strong>Duration:</strong> {{ selectedTestimonial.duration }}</p>
                        <p><strong>Technologies:</strong> {{ selectedTestimonial.technologies }}</p>
                        <p><strong>Date:</strong> {{ selectedTestimonial.date }}</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Floating Elements -->
        <div class="testimonials-floating-elements">
            <div class="floating-quote quote-1">"</div>
            <div class="floating-quote quote-2">"</div>
            <div class="floating-heart heart-1">❤️</div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TestimonialsPage',
    data() {
        return {
            selectedTestimonial: null,
            testimonials: [
                {
                    id: 1,
                    name: 'Sarah Johnson',
                    position: 'CEO',
                    company: 'TechStart Inc.',
                    avatar: 'https://picsum.photos/100/100?random=20',
                    rating: 5,
                    text: 'Mikhail delivered an exceptional e-commerce platform that exceeded our expectations. His attention to detail and creative solutions made our vision come to life.',
                    fullText: 'Mikhail delivered an exceptional e-commerce platform that exceeded our expectations. His attention to detail and creative solutions made our vision come to life. The project was completed on time and within budget, and the final product has received rave reviews from our customers. His technical expertise combined with his artistic eye created a truly unique and functional website.',
                    project: 'E-Commerce Platform',
                    duration: '3 months',
                    technologies: 'Vue.js, Node.js, MongoDB, Stripe',
                    date: 'March 2024'
                },
                {
                    id: 2,
                    name: 'Michael Chen',
                    position: 'Product Manager',
                    company: 'InnovateLab',
                    avatar: 'https://picsum.photos/100/100?random=21',
                    rating: 5,
                    text: 'Working with Mikhail was a game-changer for our startup. His innovative approach and technical skills helped us build a scalable solution.',
                    fullText: 'Working with Mikhail was a game-changer for our startup. His innovative approach and technical skills helped us build a scalable solution that has grown with our business. He not only delivered the technical requirements but also provided valuable insights that improved our product strategy. The collaboration was smooth and professional throughout.',
                    project: 'Task Management App',
                    duration: '4 months',
                    technologies: 'React, Socket.io, Node.js, PostgreSQL',
                    date: 'January 2024'
                },
                {
                    id: 3,
                    name: 'Emily Rodriguez',
                    position: 'Marketing Director',
                    company: 'Creative Agency',
                    avatar: 'https://picsum.photos/100/100?random=22',
                    rating: 5,
                    text: 'Mikhail\'s design skills are outstanding. He created a visually stunning portfolio website that perfectly represents our brand.',
                    fullText: 'Mikhail\'s design skills are outstanding. He created a visually stunning portfolio website that perfectly represents our brand. The pop art style he implemented is unique and memorable, setting us apart from competitors. The website is not only beautiful but also highly functional and user-friendly. Our client feedback has been overwhelmingly positive.',
                    project: 'Portfolio Website',
                    duration: '2 months',
                    technologies: 'HTML5, CSS3, JavaScript, GSAP',
                    date: 'February 2024'
                },
                {
                    id: 4,
                    name: 'David Thompson',
                    position: 'CTO',
                    company: 'DataFlow Systems',
                    avatar: 'https://picsum.photos/100/100?random=23',
                    rating: 5,
                    text: 'The analytics dashboard Mikhail built for us is incredibly powerful and user-friendly. It has transformed how we view our data.',
                    fullText: 'The analytics dashboard Mikhail built for us is incredibly powerful and user-friendly. It has transformed how we view our data and make business decisions. The real-time data visualization and interactive features make complex information accessible to all team members. His understanding of both technical requirements and user experience was invaluable.',
                    project: 'Analytics Dashboard',
                    duration: '5 months',
                    technologies: 'React, D3.js, Node.js, MongoDB',
                    date: 'December 2023'
                },
                {
                    id: 5,
                    name: 'Lisa Wang',
                    position: 'Founder',
                    company: 'FitnessTech',
                    avatar: 'https://picsum.photos/100/100?random=24',
                    rating: 5,
                    text: 'Mikhail developed an amazing mobile app that our users love. His expertise in React Native and user experience design is exceptional.',
                    fullText: 'Mikhail developed an amazing mobile app that our users love. His expertise in React Native and user experience design is exceptional. The app has received thousands of downloads and maintains a 4.8-star rating on the app store. His attention to performance optimization and user interface design created a seamless experience for our fitness community.',
                    project: 'Fitness Tracking App',
                    duration: '6 months',
                    technologies: 'React Native, Firebase, Redux, Expo',
                    date: 'November 2023'
                },
                {
                    id: 6,
                    name: 'Robert Kim',
                    position: 'Operations Manager',
                    company: 'WeatherCorp',
                    avatar: 'https://picsum.photos/100/100?random=25',
                    rating: 5,
                    text: 'The weather dashboard Mikhail created is both beautiful and functional. It provides our users with accurate, real-time weather information.',
                    fullText: 'The weather dashboard Mikhail created is both beautiful and functional. It provides our users with accurate, real-time weather information in an intuitive interface. The integration with multiple weather APIs and the beautiful data visualization make it a pleasure to use. His technical implementation is robust and scalable.',
                    project: 'Weather Dashboard',
                    duration: '3 months',
                    technologies: 'Vue.js, Chart.js, OpenWeather API, Leaflet',
                    date: 'October 2023'
                }
            ]
        }
    },
    methods: {
        openTestimonialModal(testimonial) {
            this.selectedTestimonial = testimonial
        },
        closeTestimonialModal() {
            this.selectedTestimonial = null
        }
    }
}
</script>

<style scoped>
.testimonials-page {
    position: relative;
    width: 100vw;
    min-height: 100vh;
    overflow: hidden;
    /* font-family: 'Arial Black', 'Helvetica Bold', sans-serif; */
    padding-top: 100px;
    background: var(--bg-primary);
}

.testimonials-content {
    position: relative;
    z-index: 1;
    padding: 2rem;
    max-width: 1400px;
    margin: 0 auto;
}

.testimonials-header {
    text-align: center;
    margin-bottom: 4rem;
}

.testimonials-title {
    font-size: clamp(3rem, 8vw, 6rem);
    font-weight: 900;
    color: #ffffff;
    text-shadow:
        4px 4px 0 #ff0000,
        8px 8px 0 #00ffff;
    margin-bottom: 1rem;
    animation: titleFloat 3s ease-in-out infinite;
}

.testimonials-subtitle {
    font-size: clamp(1.5rem, 4vw, 2.5rem);
    color: #ffffff;
    text-shadow: 2px 2px 0 #000000;
    background: linear-gradient(45deg, #ffff00, #ff00ff);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
}

/* Testimonials Grid */
.testimonials-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
    gap: 2rem;
    margin-bottom: 4rem;
}

.testimonial-card {
    background: rgba(0, 0, 0, 0.8);
    border: 4px solid #ff0000;
    border-radius: 20px;
    padding: 2rem;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow:
        8px 8px 0 #00ffff,
        16px 16px 0 #ffff00;
}

.testimonial-card:hover {
    transform: translateY(-10px);
    box-shadow:
        12px 12px 0 #00ffff,
        20px 20px 0 #ffff00;
}

.testimonial-header {
    display: flex;
    align-items: center;
    gap: 1rem;
    margin-bottom: 1.5rem;
}

.client-avatar {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    overflow: hidden;
    border: 3px solid #00ffff;
    flex-shrink: 0;
}

.client-avatar img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.client-info {
    flex: 1;
}

.client-name {
    font-size: 1.3rem;
    color: #ffff00;
    margin-bottom: 0.3rem;
    text-shadow: 1px 1px 0 #000000;
}

.client-position {
    font-size: 0.9rem;
    color: #00ffff;
    margin-bottom: 0.2rem;
    text-shadow: 1px 1px 0 #000000;
}

.client-company {
    font-size: 0.9rem;
    color: #ff00ff;
    text-shadow: 1px 1px 0 #000000;
}

.rating {
    display: flex;
    gap: 0.2rem;
}

.star {
    font-size: 1.2rem;
    color: #666666;
    transition: color 0.3s ease;
}

.star.filled {
    color: #ffff00;
    text-shadow: 0 0 10px #ffff00;
}

.testimonial-content {
    margin-bottom: 1.5rem;
}

.testimonial-text {
    color: #ffffff;
    line-height: 1.6;
    font-style: italic;
    text-shadow: 1px 1px 0 #000000;
}

.testimonial-footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-top: 1rem;
    border-top: 2px solid #00ff00;
}

.project-info {
    display: flex;
    flex-direction: column;
    gap: 0.2rem;
}

.project-label {
    font-size: 0.8rem;
    color: #00ff00;
    text-shadow: 1px 1px 0 #000000;
}

.project-name {
    font-size: 0.9rem;
    color: #ffffff;
    font-weight: bold;
    text-shadow: 1px 1px 0 #000000;
}

.testimonial-date {
    font-size: 0.8rem;
    color: #ff00ff;
    text-shadow: 1px 1px 0 #000000;
}

/* Statistics Section */
.statistics-section {
    background: rgba(0, 0, 0, 0.8);
    border: 4px solid #00ffff;
    border-radius: 20px;
    padding: 3rem;
    margin-bottom: 4rem;
    box-shadow:
        8px 8px 0 #ff0000,
        16px 16px 0 #ffff00;
}

.section-title {
    font-size: clamp(2rem, 5vw, 3rem);
    font-weight: 900;
    color: #00ffff;
    text-align: center;
    margin-bottom: 3rem;
    text-shadow: 2px 2px 0 #000000;
}

.stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 2rem;
}

.stat-card {
    text-align: center;
    padding: 2rem;
    background: rgba(255, 255, 255, 0.1);
    border: 3px solid #ff00ff;

    backdrop-filter: blur(10px);
    transition: all 0.3s ease;
}

.stat-card:hover {
    transform: translateY(-5px);
    border-color: #ffff00;
    box-shadow: 0 10px 30px rgba(255, 255, 0, 0.3);
}



.stat-number {
    font-size: 2.5rem;
    font-weight: 900;
    color: #ffff00;
    margin-bottom: 0.5rem;
    text-shadow: 2px 2px 0 #000000;
}

.stat-label {
    font-size: 1rem;
    color: #ffffff;
    text-shadow: 1px 1px 0 #000000;
}

/* Call to Action */
.cta-section {
    text-align: center;
    background: rgba(0, 0, 0, 0.8);
    border: 4px solid #ffff00;
    border-radius: 20px;
    padding: 3rem;
    box-shadow:
        8px 8px 0 #ff0000,
        16px 16px 0 #00ffff;
}

.cta-title {
    font-size: clamp(2rem, 5vw, 3rem);
    color: #ffff00;
    margin-bottom: 1rem;
    text-shadow: 2px 2px 0 #000000;
}

.cta-text {
    font-size: 1.2rem;
    color: #ffffff;
    margin-bottom: 2rem;
    text-shadow: 1px 1px 0 #000000;
}

.cta-button {
    padding: 1.5rem 3rem;
    font-size: 1.2rem;
    font-weight: 900;
    text-transform: uppercase;
    letter-spacing: 2px;
    background: linear-gradient(45deg, #ff0000, #00ffff);
    border: 4px solid #000000;
    color: #ffffff;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow:
        6px 6px 0 #ffff00,
        12px 12px 0 #ff00ff;
    border-radius: 10px;
}

.cta-button:hover {
    transform: translate(-3px, -3px);
    box-shadow:
        9px 9px 0 #ffff00,
        15px 15px 0 #ff00ff;
    background: linear-gradient(45deg, #ffff00, #ff00ff);
    color: #000000;
}

/* Testimonial Modal */
.testimonial-modal {
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
    max-width: 800px;
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

.modal-testimonial {
    padding: 2rem;
}

.modal-header {
    display: flex;
    align-items: center;
    gap: 2rem;
    margin-bottom: 2rem;
    padding-bottom: 1rem;
    border-bottom: 3px solid #00ffff;
}

.modal-avatar {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    overflow: hidden;
    border: 4px solid #00ffff;
    flex-shrink: 0;
}

.modal-avatar img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.modal-client-name {
    font-size: 2rem;
    color: #ffff00;
    margin-bottom: 0.5rem;
    text-shadow: 2px 2px 0 #000000;
}

.modal-client-position {
    font-size: 1.1rem;
    color: #00ffff;
    margin-bottom: 0.3rem;
    text-shadow: 1px 1px 0 #000000;
}

.modal-client-company {
    font-size: 1.1rem;
    color: #ff00ff;
    margin-bottom: 1rem;
    text-shadow: 1px 1px 0 #000000;
}

.modal-rating {
    display: flex;
    gap: 0.3rem;
}

.modal-content-text {
    margin-bottom: 2rem;
}

.modal-content-text p {
    color: #ffffff;
    line-height: 1.8;
    font-size: 1.1rem;
    text-shadow: 1px 1px 0 #000000;
}

.modal-project-details {
    background: rgba(255, 255, 255, 0.1);
    border: 3px solid #00ff00;

    padding: 1.5rem;
    backdrop-filter: blur(10px);
}

.modal-project-details h3 {
    color: #00ff00;
    margin-bottom: 1rem;
    text-shadow: 1px 1px 0 #000000;
}

.modal-project-details p {
    color: #ffffff;
    margin-bottom: 0.5rem;
    text-shadow: 1px 1px 0 #000000;
}

.modal-project-details strong {
    color: #ffff00;
}

/* Floating Elements */
.testimonials-floating-elements {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
    z-index: 1;
}

.floating-quote {
    position: absolute;
    font-size: 4rem;
    color: #ffff00;
    opacity: 0.6;
    animation: float 6s ease-in-out infinite;
}

.quote-1 {
    top: 20%;
    left: 10%;
    animation-delay: 0s;
}

.quote-2 {
    bottom: 30%;
    right: 15%;
    animation-delay: 3s;
}

.floating-heart {
    position: absolute;
    font-size: 2rem;
    opacity: 0.7;
    animation: pulse 2s ease-in-out infinite;
}

.heart-1 {
    top: 60%;
    left: 20%;
    animation-delay: 1s;
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

@keyframes pulse {

    0%,
    100% {
        transform: scale(1);
    }

    50% {
        transform: scale(1.2);
    }
}

/* Responsive Design */
@media (max-width: 768px) {
    .testimonials-content {
        padding: 1rem;
    }

    .testimonials-grid {
        grid-template-columns: 1fr;
    }

    .stats-grid {
        grid-template-columns: repeat(2, 1fr);
    }

    .modal-header {
        flex-direction: column;
        text-align: center;
    }

    .floating-quote,
    .floating-heart {
        display: none;
    }
}

@media (max-width: 480px) {
    .testimonials-title {
        font-size: clamp(2rem, 6vw, 3rem);
    }

    .testimonials-subtitle {
        font-size: clamp(1rem, 3vw, 1.5rem);
    }

    .stats-grid {
        grid-template-columns: 1fr;
    }

    .testimonial-footer {
        flex-direction: column;
        gap: 1rem;
        align-items: flex-start;
    }
}
</style>