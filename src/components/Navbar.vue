<template>
    <nav class="pop-art-navbar">
        <div class="navbar-container">
            <div class="navbar-links">
                <button v-for="link in navLinks" :key="link.name" @click="$emit('navigate', link.page)"
                    :class="['nav-link', { active: currentPage === link.page }]">
                    <span class="link-text">{{ link.name }}</span>
                </button>
            </div>

            <div class="navbar-toggle" @click="toggleMobileMenu">
                <span class="hamburger-line"></span>
                <span class="hamburger-line"></span>
                <span class="hamburger-line"></span>
            </div>
        </div>

        <!-- Mobile Menu -->
        <div v-if="isMobileMenuOpen" class="mobile-menu">
            <button v-for="link in navLinks" :key="link.name" @click="handleMobileNav(link.page)"
                :class="['mobile-nav-link', { active: currentPage === link.page }]">
                <span class="link-text">{{ link.name }}</span>
            </button>
        </div>
    </nav>
</template>

<script>
export default {
    name: 'Navbar',
    props: {
        currentPage: {
            type: String,
            default: 'home'
        }
    },
    data() {
        return {
            isMobileMenuOpen: false,
            navLinks: [
                { name: 'HOME', page: 'home' },
                { name: 'ABOUT', page: 'about' },
                { name: 'PROJECTS', page: 'projects' },
                { name: 'TESTIMONIALS', page: 'testimonials' },
                { name: 'CONTACT', page: 'contact' }
            ]
        }
    },
    methods: {
        toggleMobileMenu() {
            this.isMobileMenuOpen = !this.isMobileMenuOpen
        },
        handleMobileNav(page) {
            this.$emit('navigate', page)
            this.isMobileMenuOpen = false
        }
    }
}
</script>

<style scoped>
.pop-art-navbar {
    position: fixed;
    top: 0;
    right: 0;
    z-index: var(--z-navbar);
    background: var(--bg-primary);
    border-bottom: var(--border-extra-thick);
    border-bottom-color: var(--pop-black);
    left: 25%;
    width: 50%;
    backdrop-filter: blur(10px);
}

.navbar-container {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 1rem 2rem;
    max-width: 1400px;
    margin: 0 auto;
}

.navbar-brand {
    flex-shrink: 0;
}

.brand-text {
    font-size: 1.8rem;
    font-weight: 900;
    color: var(--text-primary);
    text-shadow: var(--text-shadow-glow);
    margin: 0;
    letter-spacing: 2px;
    animation: brandGlow 3s ease-in-out infinite;
}

.navbar-links {
    display: flex;
    gap: 2rem;
    align-items: center;
}

.nav-link {
    position: relative;
    padding: 1rem 1.5rem;
    border: var(--border-thick);
    color: #000000;
    font-weight: 900;
    font-size: 1rem;
    text-transform: uppercase;
    letter-spacing: 1px;
    cursor: pointer;
    transition: all var(--animation-fast) ease;
    display: flex;
    align-items: center;
    gap: 0.5rem;
}

.nav-link:hover {
    transform: translate(-2px, -2px);
    color: var(--pop-black);
}

.nav-link.active {
    color: #000000;
    transform: translate(-1px, -1px);
    box-shadow:
        5px 5px 0 var(--pop-black),
        10px 10px 0 var(--pop-yellow);
}

.nav-link.active:hover {
    transform: translate(-2px, -2px);
    transition: all var(--animation-fast) ease;
}

.nav-link:active {
    transform: translate(0, 0);
}

.link-text {
    font-weight: 900;
}



.navbar-toggle {
    display: none;
    flex-direction: column;
    gap: 4px;
    cursor: pointer;
    padding: 0.5rem;
    border: var(--border-medium);
    border-color: var(--pop-cyan);
    border-radius: 8px;
    background: var(--bg-card);
}

.hamburger-line {
    width: 25px;
    height: 4px;
    background: var(--pop-yellow);
    border-radius: 2px;
    transition: all var(--animation-fast) ease;
}

.navbar-toggle:hover .hamburger-line {
    background: var(--pop-magenta);
}

.mobile-menu {
    display: none;
    background: var(--bg-primary);
    border-top: var(--border-thick);
    border-top-color: var(--pop-cyan);
    padding: 1rem;
    animation: slideDown var(--animation-fast) ease-out;
}

.mobile-nav-link {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    padding: 1rem;
    margin-bottom: 0.5rem;
    background: var(--gradient-primary);
    border: var(--border-medium);
    color: var(--text-primary);
    font-weight: 900;
    font-size: 1rem;
    text-transform: uppercase;
    letter-spacing: 1px;
    cursor: pointer;
    transition: all var(--animation-fast) ease;
    box-shadow:
        3px 3px 0 var(--pop-yellow),
        6px 6px 0 var(--pop-magenta);
    border-radius: 8px;
}

.mobile-nav-link:hover {
    transform: translate(-2px, -2px);
    box-shadow:
        5px 5px 0 var(--pop-yellow),
        10px 10px 0 var(--pop-magenta);
    background: var(--gradient-secondary);
    color: var(--pop-black);
}

.mobile-nav-link.active {
    background: var(--gradient-secondary);
    color: var(--pop-black);
}

/* Animations */
@keyframes brandGlow {

    0%,
    100% {
        text-shadow:
            3px 3px 0 var(--pop-red),
            6px 6px 0 var(--pop-cyan);
    }

    50% {
        text-shadow:
            3px 3px 0 var(--pop-red),
            6px 6px 0 var(--pop-cyan),
            0 0 20px var(--pop-yellow);
    }
}

@keyframes slideDown {
    from {
        opacity: 0;
        transform: translateY(-20px);
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* Responsive Design */
@media (max-width: 1024px) {
    .navbar-links {
        gap: 1rem;
    }

    .nav-link {
        padding: 0.8rem 1.2rem;
        font-size: 0.9rem;
    }
}

@media (max-width: 768px) {
    .navbar-links {
        display: none;
    }

    .navbar-toggle {
        display: flex;
    }

    .mobile-menu {
        display: block;
    }

    .navbar-container {
        padding: 1rem;
    }

    .brand-text {
        font-size: 1.5rem;
    }
}

@media (max-width: 480px) {
    .navbar-container {
        padding: 0.8rem;
    }

    .brand-text {
        font-size: 1.3rem;
    }

    .mobile-nav-link {
        padding: 0.8rem;
        font-size: 0.9rem;
    }
}
</style>