<template>
  <div class="contact-page">
    <div class="contact-content">
      <div class="contact-header">
        <h1 class="contact-title">GET IN TOUCH</h1>
        <p class="contact-subtitle">Let's create something amazing together!</p>
      </div>

      <div class="contact-form-container">
        <form class="contact-form" @submit.prevent="submitForm">
          <div class="form-group">
            <label for="name" class="form-label">NAME</label>
            <input type="text" id="name" v-model="formData.name" class="form-input" required />
          </div>

          <div class="form-group">
            <label for="email" class="form-label">EMAIL</label>
            <input type="email" id="email" v-model="formData.email" class="form-input" required />
          </div>

          <div class="form-group">
            <label for="message" class="form-label">MESSAGE</label>
            <textarea id="message" v-model="formData.message" class="form-textarea" rows="5" required></textarea>
          </div>

          <button type="submit" class="submit-button">
            <span class="button-text">SEND MESSAGE</span>
          </button>
        </form>
      </div>

      <div class="contact-info">
        <div class="info-item">
          <span class="info-text">mikhail@example.com</span>
        </div>
        <div class="info-item">
          <span class="info-text">+1 (555) 123-4567</span>
        </div>
        <div class="info-item">
          <span class="info-text">New York, NY</span>
        </div>
      </div>

      <button class="back-button" @click="goBack">
        <span class="button-text">← BACK TO PORTFOLIO</span>
      </button>
    </div>

    <!-- Floating Elements -->
    <div class="contact-floating-elements">
      <div class="floating-star star-1">★</div>
      <div class="floating-star star-2">★</div>
      <div class="floating-diamond diamond-1">◆</div>
      <div class="floating-diamond diamond-2">◆</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ContactPage',
  data() {
    return {
      formData: {
        name: '',
        email: '',
        message: ''
      }
    }
  },
  methods: {
    submitForm() {
      // Handle form submission here
      console.log('Form submitted:', this.formData);
      alert('Thank you for your message! I\'ll get back to you soon.');
      this.formData = { name: '', email: '', message: '' };
    },
    goBack() {
      this.$emit('go-back');
    }
  }
}
</script>

<style scoped>
.contact-page {
  position: relative;
  width: 100vw;
  min-height: 100vh;
  overflow: hidden;
  padding-top: 100px;
  background: var(--bg-primary);
}

.contact-content {
  position: relative;
  z-index: 1;
  padding: 4rem 2rem;
  max-width: 1200px;
  margin: 0 auto;
}

.contact-header {
  text-align: center;
  margin-bottom: 4rem;
}

.contact-title {
  font-size: clamp(2.5rem, 6vw, 5rem);
  font-weight: 900;
  color: #ffffff;
  text-shadow:
    4px 4px 0 #ff0000,
    8px 8px 0 #00ffff;
  margin-bottom: 1rem;
  animation: titleFloat 3s ease-in-out infinite;
}

.contact-subtitle {
  font-size: clamp(1.2rem, 3vw, 1.8rem);
  color: #ffffff;
  text-shadow: 2px 2px 0 #000000;
  background: linear-gradient(45deg, #ffff00, #ff00ff);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.contact-form-container {
  background: rgba(0, 0, 0, 0.8);
  border: 4px solid #ff0000;
  border-radius: 20px;
  padding: 3rem;
  margin-bottom: 3rem;
  box-shadow:
    8px 8px 0 #00ffff,
    16px 16px 0 #ffff00;
}

.contact-form {
  display: grid;
  gap: 2rem;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.form-label {
  font-size: 1.2rem;
  font-weight: 900;
  color: #ffff00;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.form-input,
.form-textarea {
  padding: 1rem;
  font-size: 1rem;
  font-family: inherit;
  border: 3px solid #00ffff;
  border-radius: 10px;
  background: rgba(255, 255, 255, 0.9);
  color: #000000;
  transition: all 0.3s ease;
}

.form-input:focus,
.form-textarea:focus {
  outline: none;
  border-color: #ff00ff;
  box-shadow: 0 0 20px rgba(255, 0, 255, 0.5);
  transform: scale(1.02);
}

.form-textarea {
  resize: vertical;
  min-height: 120px;
}

.submit-button {
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

.submit-button:hover {
  transform: translate(-3px, -3px);
  box-shadow:
    9px 9px 0 #ffff00,
    15px 15px 0 #ff00ff;
  background: linear-gradient(45deg, #ffff00, #ff00ff);
  color: #000000;
}

.submit-button:active {
  transform: translate(0, 0);
  box-shadow:
    3px 3px 0 #ffff00,
    6px 6px 0 #ff00ff;
}

.button-text {
  margin-right: 1rem;
}



.contact-info {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  margin-bottom: 3rem;
}

.info-item {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1.5rem;
  background: rgba(255, 255, 255, 0.1);
  border: 3px solid #00ff00;
  border-radius: 15px;
  backdrop-filter: blur(10px);
}



.info-text {
  font-size: 1.1rem;
  font-weight: bold;
  color: #ffffff;
  text-shadow: 1px 1px 0 #000000;
}

.back-button {
  display: block;
  margin: 0 auto;
  padding: 1rem 2rem;
  font-size: 1rem;
  font-weight: 900;
  text-transform: uppercase;
  letter-spacing: 1px;
  background: linear-gradient(45deg, #000000, #333333);
  border: 3px solid #ffffff;
  color: #ffffff;
  cursor: pointer;
  transition: all 0.3s ease;
  border-radius: 10px;
}

.back-button:hover {
  background: linear-gradient(45deg, #ffffff, #cccccc);
  color: #000000;
  transform: scale(1.05);
}

/* Floating Elements */
.contact-floating-elements {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 1;
}

.floating-star {
  position: absolute;
  font-size: 2rem;
  color: #ffff00;
  opacity: 0.8;
  animation: twinkle 3s ease-in-out infinite;
}

.star-1 {
  top: 15%;
  left: 10%;
  animation-delay: 0s;
}

.star-2 {
  top: 25%;
  right: 15%;
  animation-delay: 1.5s;
}

.floating-diamond {
  position: absolute;
  font-size: 1.5rem;
  color: #ff00ff;
  opacity: 0.7;
  animation: rotate 4s linear infinite;
}

.diamond-1 {
  bottom: 20%;
  left: 20%;
  animation-delay: 0s;
}

.diamond-2 {
  bottom: 30%;
  right: 10%;
  animation-delay: 2s;
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

@keyframes twinkle {

  0%,
  100% {
    opacity: 0.8;
    transform: scale(1);
  }

  50% {
    opacity: 1;
    transform: scale(1.2);
  }
}

@keyframes rotate {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}

/* Responsive Design */
@media (max-width: 768px) {
  .contact-content {
    padding: 2rem 1rem;
  }

  .contact-form-container {
    padding: 2rem;
  }

  .contact-info {
    grid-template-columns: 1fr;
  }

  .floating-star,
  .floating-diamond {
    display: none;
  }
}

@media (max-width: 480px) {
  .contact-title {
    font-size: clamp(2rem, 5vw, 3rem);
  }

  .contact-subtitle {
    font-size: clamp(1rem, 2.5vw, 1.3rem);
  }

  .contact-form-container {
    padding: 1.5rem;
  }

  .submit-button {
    padding: 1rem 2rem;
    font-size: 1rem;
  }
}
</style>