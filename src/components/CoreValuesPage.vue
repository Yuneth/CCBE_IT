<template>
  <div class="core-values-page">
    <NavBar></NavBar>
    
    <!-- Hero Section -->
    <section class="hero-section">
      <div class="hero-overlay">
        <div class="hero-content">
          <h1 class="hero-title" data-aos="fade-up" data-aos-duration="800">
            Our <span class="highlight">Core Values</span>
          </h1>
          <p class="hero-subtitle" data-aos="fade-up" data-aos-duration="800" data-aos-delay="200">
            The Foundation of Academic Excellence
          </p>
          <p class="hero-description" data-aos="fade-up" data-aos-duration="800" data-aos-delay="400">
            At the heart of our institution lie meticulously cultivated principles that create an environment 
            where excellence thrives and students flourish.
          </p>
        </div>
      </div>
    </section>

    <!-- Core Values Section -->
    <section class="values-section">
      <div class="container">
        <!-- Values Grid -->
        <div class="values-grid">
          <div 
            v-for="(value, index) in coreValues" 
            :key="index" 
            class="value-card-wrapper"
            :data-aos="index % 2 === 0 ? 'fade-right' : 'fade-left'"
            :data-aos-delay="(index % 4) * 100"
          >
            <div class="value-card">
              <!-- Card Front -->
              <div class="card-front">
                <div class="card-header">
                  <div class="value-number">
                    {{ (index + 1).toString().padStart(2, '0') }}
                  </div>
                  <div class="value-icon">
                    <svg width="32" height="32" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                      <path d="M12 15C13.6569 15 15 13.6569 15 12C15 10.3431 13.6569 9 12 9C10.3431 9 9 10.3431 9 12C9 13.6569 10.3431 15 12 15Z" fill="currentColor"/>
                      <path d="M19.071 4.929C20.463 6.321 21.463 8.134 21.941 10.125H15.125V2.059C17.116 2.537 18.929 3.537 19.071 4.929Z" fill="currentColor"/>
                      <path d="M13 21.94C13 21.94 13 21.94 13 21.94V15H21.94C21.463 16.991 20.463 18.804 19.071 20.196C18.929 20.338 18.787 20.48 18.645 20.622C17.116 21.94 15.023 22.841 12.765 22.992C12.51 23.007 12.255 23.015 12 23.015C11.745 23.015 11.49 23.007 11.235 22.992C8.977 22.841 6.884 21.94 5.355 20.622C5.213 20.48 5.071 20.338 4.929 20.196C3.537 18.804 2.537 16.991 2.059 15H11V21.94C11.333 21.98 11.667 22 12 22C12.333 22 12.667 21.98 13 21.94Z" fill="currentColor"/>
                    </svg>
                  </div>
                </div>
                
                <div class="card-image">
                  <v-img 
                    :src="value.image" 
                    cover
                    class="value-image"
                    :alt="value.title"
                  ></v-img>
                  <div class="image-overlay"></div>
                </div>
                
                <div class="card-content">
                  <h3 class="value-title">{{ value.title }}</h3>
                  <div class="read-more">
                    <span>Learn More</span>
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                      <path d="M5 12H19" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                      <path d="M12 5L19 12L12 19" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    </svg>
                  </div>
                </div>
              </div>
              
              <!-- Card Back -->
              <div class="card-back">
                <div class="back-header">
                  <div class="back-number">
                    {{ (index + 1).toString().padStart(2, '0') }}
                  </div>
                </div>
                <div class="back-content">
                  <h4 class="back-title">{{ value.title }}</h4>
                  <p class="back-description">{{ value.description }}</p>
                  <div class="back-actions">
                    <button class="close-btn" @click.stop>
                      <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M18 6L6 18" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                        <path d="M6 6L18 18" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                      </svg>
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Values Summary -->
        <div class="values-summary" data-aos="fade-up">
          <div class="summary-card">
            <div class="summary-icon">
              <svg width="48" height="48" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M22 11.08V12C21.9988 14.1564 21.3005 16.2547 20.0093 17.9818C18.7182 19.709 16.9033 20.9725 14.8354 21.5839C12.7674 22.1953 10.5573 22.1219 8.53447 21.3746C6.51168 20.6273 4.78465 19.2461 3.61096 17.4371C2.43727 15.628 1.87979 13.4881 2.02168 11.3363C2.16356 9.18457 2.99721 7.13633 4.39828 5.49707C5.79935 3.85782 7.69279 2.71538 9.79619 2.24015C11.8996 1.76491 14.1003 1.98234 16.07 2.86" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                <path d="M22 4L12 14.01L9 11.01" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
            </div>
            <div class="summary-content">
              <h3>Our Commitment to Excellence</h3>
              <p>
                These eight core values represent our unwavering dedication to providing the highest quality 
                Cambridge English education. Each principle guides our daily operations and long-term vision, 
                ensuring every student receives an exceptional learning experience.
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <ArrowButton></ArrowButton>
    <ChatBot></ChatBot>
    <FooterPage></FooterPage>
  </div>
</template>

<script>
import NavBar from './NavBar.vue';
import FooterPage from './FooterPage.vue';
import ChatBot from './ChatBot.vue';
import ArrowButton from './ArrowButton.vue';
import AOS from 'aos';
import 'aos/dist/aos.css';

export default {
  name: 'CoreValues',
  components: {
    NavBar,
    FooterPage,
    ChatBot,
    ArrowButton
  },
  mounted() {
    AOS.init({
      duration: 800,
      once: true,
      offset: 100
    });
    
    // Initialize card flip interactions
    this.initCardInteractions();
  },
  methods: {
    initCardInteractions() {
      // Add click event listeners for card flipping
      const cards = document.querySelectorAll('.value-card');
      cards.forEach(card => {
        card.addEventListener('click', function(e) {
          if (!e.target.closest('.close-btn')) {
            this.classList.toggle('flipped');
          }
        });
        
        // Add keyboard support
        card.addEventListener('keypress', function(e) {
          if (e.key === 'Enter' || e.key === ' ') {
            e.preventDefault();
            this.classList.toggle('flipped');
          }
        });
      });
    }
  },
  data() {
    return {
      coreValues: [
        {
          image: require('@/assets/coreValues/CV1.jpg'),
          title: 'State-of-the-Art Facilitated Classrooms',
          description: 'Our commitment to providing a conducive learning atmosphere is reflected in our state-of-the-art classrooms equipped with cutting-edge technology and resources that enhance the educational experience.'
        },
        {
          image: require('@/assets/coreValues/CV2.jpg'),
          title: 'Highly Qualified Lecture Panel',
          description: 'We take pride in our team of exceptionally qualified educators who bring extensive expertise to the classroom, ensuring a robust and enriching learning experience for our students.'
        },
        {
          image: require('@/assets/coreValues/CV3.jpg'),
          title: 'Parent and Student Supportive Administrative Panel',
          description: 'Our administrative team is dedicated to fostering strong partnerships with parents and students, offering unwavering support and guidance throughout their educational journey.'
        },
        {
          image: require('@/assets/coreValues/CV4.jpg'),
          title: 'Monthly Evaluation of Student Skills',
          description: 'To track and enhance student progress, we conduct comprehensive evaluations of their skills on a monthly basis, enabling personalized development plans and targeted improvement strategies.'
        },
        {
          image: require('@/assets/coreValues/CV5.jpg'),
          title: 'Continuous Quality Audit',
          description: 'We adhere to a rigorous system of continuous quality audits, reinforcing our commitment to maintaining the highest standards of education and service delivery.'
        },
        {
          image: require('@/assets/coreValues/CV6.jpg'),
          title: 'Student-Centric Classroom Environment',
          description: 'Our classrooms are designed to be student-centric, with a focus on developing the four essential skills, ensuring a holistic approach to education that caters to individual learning styles.'
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/CV7.jpg?updatedAt=1737780608594",
          title: 'Excellent Student Results',
          description: 'Our dedication to academic excellence is evidenced by the consistently outstanding results achieved by our students in various assessments and examinations.'
        },
        {
          image: require('@/assets/coreValues/CV8.jpg'),
          title: 'Child Safeguarding, First Aid Training, and Fire Safety',
          description: 'We prioritize the safety and well-being of our students through robust safeguarding processes, comprehensive first aid training for staff, and stringent fire safety measures.'
        },
      ]
    };
  }
};
</script>

<style scoped>
.core-values-page {
  background: #ffffff;
  min-height: 100vh;
  color: #333;
}

/* Hero Section */
.hero-section {
  height: 60vh;
  min-height: 500px;
  background: linear-gradient(135deg, white 0%, white 100%);
  position: relative;
  overflow: hidden;
}

.hero-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: 
    radial-gradient(circle at 20% 80%, rgba(255,255,255,0.1) 0%, transparent 50%),
    radial-gradient(circle at 80% 20%, rgba(255,255,255,0.1) 0%, transparent 50%);
}

.hero-overlay {
  position: relative;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2;
}

.hero-content {
  text-align: center;
  padding: 2rem;
  max-width: 800px;
  color: white;
}

.hero-title {
  font-family: 'Inter', 'Poppins', sans-serif;
  font-size: 3.5rem;
  font-weight: 800;
  margin-bottom: 1rem;
  letter-spacing: -0.5px;
  color: black;
}

.highlight {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-subtitle {
  font-family: 'Inter', sans-serif;
  font-size: 1.2rem;
  font-weight: 500;
  margin-bottom: 1.5rem;
  color: black;
  text-transform: uppercase;
  letter-spacing: 3px;
}

.hero-description {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  line-height: 1.6;
  color: black;
  max-width: 600px;
  margin: 0 auto;
}

/* Values Section */
.values-section {
  padding: 6rem 1rem;
  background: #f8f9ff;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

.values-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
  margin-bottom: 4rem;
}

.value-card-wrapper {
  perspective: 1000px;
  height: 380px;
}

.value-card {
  position: relative;
  width: 100%;
  height: 100%;
  transform-style: preserve-3d;
  transition: transform 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  cursor: pointer;
  border-radius: 20px;
  overflow: hidden;
}

.value-card.flipped {
  transform: rotateY(180deg);
}

.card-front,
.card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  border-radius: 20px;
  overflow: hidden;
}

.card-front {
  background: white;
  box-shadow: 0 10px 40px rgba(0,0,0,0.08);
  border: 1px solid rgba(102,126,234,0.1);
}

.card-back {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  transform: rotateY(180deg);
  padding: 2rem;
  color: white;
  display: flex;
  flex-direction: column;
}

/* Card Front Styles */
.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem 1.5rem 1rem;
}

.value-number {
  font-family: 'Inter', sans-serif;
  font-size: 0.9rem;
  font-weight: 700;
  color: #667eea;
  background: rgba(102,126,234,0.1);
  padding: 0.5rem 1rem;
  border-radius: 50px;
}

.value-icon {
  color: #667eea;
  opacity: 0.7;
}

.card-image {
  position: relative;
  height: 160px;
  overflow: hidden;
}

.value-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.6s ease;
}

.value-card:hover .value-image {
  transform: scale(1.05);
}

.image-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(to bottom, transparent 50%, rgba(0,0,0,0.2) 100%);
}

.card-content {
  padding: 1.5rem;
}

.value-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 1.5rem;
  line-height: 1.4;
  height: 60px;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.read-more {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: #667eea;
  font-family: 'Inter', sans-serif;
  font-weight: 600;
  font-size: 0.9rem;
  transition: gap 0.3s ease;
}

.value-card:hover .read-more {
  gap: 0.75rem;
}

/* Card Back Styles */
.back-header {
  display: flex;
  justify-content: flex-start;
  margin-bottom: 1.5rem;
}

.back-number {
  font-family: 'Inter', sans-serif;
  font-size: 0.9rem;
  font-weight: 700;
  color: rgba(255,255,255,0.9);
  background: rgba(255,255,255,0.2);
  padding: 0.5rem 1rem;
  border-radius: 50px;
}

.back-content {
  flex: 1;
}

.back-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.2rem;
  font-weight: 700;
  margin-bottom: 1.5rem;
  color: white;
  line-height: 1.3;
}

.back-description {
  font-family: 'Inter', sans-serif;
  font-size: 0.95rem;
  line-height: 1.6;
  color: rgba(255,255,255,0.9);
  margin-bottom: 2rem;
  display: -webkit-box;
  -webkit-line-clamp: 8;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.back-actions {
  display: flex;
  justify-content: flex-end;
}

.close-btn {
  background: rgba(255,255,255,0.2);
  border: none;
  width: 44px;
  height: 44px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.3s ease;
  color: white;
}

.close-btn:hover {
  background: rgba(255,255,255,0.3);
  transform: rotate(90deg);
}

/* Values Summary */
.values-summary {
  max-width: 800px;
  margin: 0 auto;
}

.summary-card {
  background: white;
  border-radius: 20px;
  padding: 3rem;
  box-shadow: 0 20px 60px rgba(0,0,0,0.08);
  border: 1px solid rgba(102,126,234,0.1);
  display: flex;
  align-items: center;
  gap: 2rem;
}

.summary-icon {
  flex-shrink: 0;
  color: #667eea;
}

.summary-content h3 {
  font-family: 'Inter', sans-serif;
  font-size: 1.8rem;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 1rem;
}

.summary-content p {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  line-height: 1.6;
  color: #555;
}

/* Hover Effects */
.value-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, rgba(102,126,234,0.1) 0%, rgba(118,75,162,0.1) 100%);
  opacity: 0;
  transition: opacity 0.3s ease;
  z-index: 2;
}

.value-card:hover::before {
  opacity: 1;
}

/* Accessibility */
.value-card:focus {
  outline: 2px solid #667eea;
  outline-offset: 4px;
}

/* Animation */
@keyframes float {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}

.value-card-wrapper:nth-child(odd) .value-card:not(.flipped) {
  animation: float 6s ease-in-out infinite;
}

.value-card-wrapper:nth-child(even) .value-card:not(.flipped) {
  animation: float 6s ease-in-out infinite 1.5s;
}

/* Responsive Design */
@media (max-width: 1200px) {
  .values-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 768px) {
  .hero-section {
    height: 50vh;
    min-height: 400px;
  }
  
  .hero-title {
    font-size: 2.5rem;
  }
  
  .hero-subtitle {
    font-size: 1rem;
    letter-spacing: 2px;
  }
  
  .hero-description {
    font-size: 1rem;
  }
  
  .values-section {
    padding: 4rem 1rem;
  }
  
  .values-grid {
    grid-template-columns: 1fr;
    max-width: 400px;
    margin: 0 auto 4rem;
  }
  
  .value-card-wrapper {
    height: 350px;
  }
  
  .summary-card {
    flex-direction: column;
    text-align: center;
    padding: 2rem;
  }
  
  .summary-icon {
    margin-bottom: 1rem;
  }
}

@media (max-width: 480px) {
  .hero-title {
    font-size: 2rem;
  }
  
  .hero-subtitle {
    font-size: 0.9rem;
    letter-spacing: 1px;
  }
  
  .hero-description {
    font-size: 0.9rem;
  }
  
  .value-card-wrapper {
    height: 320px;
  }
  
  .card-header {
    padding: 1rem 1rem 0.5rem;
  }
  
  .card-content {
    padding: 1rem;
  }
  
  .value-title {
    font-size: 1rem;
    height: 54px;
  }
  
  .back-title {
    font-size: 1.1rem;
  }
  
  .back-description {
    font-size: 0.9rem;
  }
}

/* Touch device optimizations */
@media (hover: none) {
  .value-card {
    cursor: default;
  }
  
  .value-card:hover .value-image {
    transform: none;
  }
  
  .value-card:hover .read-more {
    gap: 0.5rem;
  }
  
  .value-card::before {
    display: none;
  }
}

/* Reduced motion */
@media (prefers-reduced-motion: reduce) {
  .value-card,
  .value-card-wrapper .value-card,
  .close-btn,
  .value-image {
    animation: none !important;
    transition: none !important;
  }
}
</style>