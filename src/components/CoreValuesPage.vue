<template>
  <div class="core-values-page">
    <NavBar></NavBar>
    <v-container class="main-container">
      <!-- Header Section -->
      <section class="header-section">
        <h1 class="page-title" data-aos="fade-up" data-aos-duration="3000">
          OUR <span class="highlight">CORE VALUES</span>
        </h1>

        <p class="intro-text" data-aos="fade-up" data-aos-duration="2000">
          At the heart of our institution lie the following core values, each meticulously cultivated to foster an environment of academic excellence.
        </p>
      </section>

      <!-- Core Values Grid -->
      <section class="values-section">
        <v-row justify="center" class="values-grid" data-aos="fade-up" data-aos-duration="3000">
          <v-col 
            v-for="(value, index) in coreValues" 
            :key="index" 
            cols="12" 
            sm="6" 
            md="4" 
            lg="3"
            class="value-col"
          >
            <v-hover v-slot="{ isHovering, props }">
              <v-card 
                class="value-card" 
                v-bind="props"
                :class="{ 'card-hover': isHovering }"
              >
                <div class="image-container">
                  <v-img 
                    :aspect-ratio="16 / 9" 
                    :src="value.image" 
                    cover
                    class="value-image"
                  >
                    <v-expand-transition>
                      <div 
                        v-if="isHovering"
                        class="card-overlay"
                      >
                        <div class="overlay-content">
                          <v-icon class="overlay-icon">mdi-information</v-icon>
                          <p class="overlay-text">{{ value.description }}</p>
                        </div>
                      </div>
                    </v-expand-transition>
                  </v-img>
                </div>
                
                <v-card-text class="card-content">
                  <div class="value-index">
                    {{ (index + 1).toString().padStart(2, '0') }}
                  </div>
                  <h3 class="value-title">
                    {{ value.title }}
                  </h3>
                  <div class="value-decoration">
                    <div class="decoration-line"></div>
                    <v-icon class="decoration-icon">mdi-star-four-points</v-icon>
                    <div class="decoration-line"></div>
                  </div>
                </v-card-text>
              </v-card>
            </v-hover>
          </v-col>
        </v-row>
      </section>
    </v-container>
    
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
    AOS.init();
  },
  data() {
    return {
      coreValues: [
        {
          image: require('@/assets/coreValues/CV1.jpg'),
          title: 'State-of-the-Art Facilitated Classrooms',
          description: 'Our commitment to providing a conducive learning atmosphere is reflected in our state-of-the-art classrooms equipped with cutting-edge technology and resources.'
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
          description: 'To track and enhance student progress, we conduct comprehensive evaluations of their skills on a monthly basis, enabling personalized development plans.'
        },
        {
          image: require('@/assets/coreValues/CV5.jpg'),
          title: 'Continuous Quality Audit',
          description: 'We adhere to a rigorous system of continuous quality audits, reinforcing our commitment to maintaining the highest standards of education and service delivery.'
        },
        {
          image: require('@/assets/coreValues/CV6.jpg'),
          title: 'Student-Centric Classroom Environment',
          description: 'Our classrooms are designed to be student-centric, with a focus on developing the four essential skills, ensuring a holistic approach to education.'
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/CV7.jpg?updatedAt=1737780608594",
          title: 'Excellent Student Results',
          description: 'Our dedication to academic excellence is evidenced by the consistently outstanding results achieved by our students in various assessments and examinations.'
        },
        {
          image: require('@/assets/coreValues/CV8.jpg'),
          title: 'Child Safeguarding, First Aid Training, and Fire Safety',
          description: 'We prioritize the safety and well-being of our students through the implementation of robust child safeguarding processes, a staff trained in first aid, and stringent fire safety measures to create a secure learning environment.'
        },
      ]
    };
  }
};
</script>

<style scoped>
.core-values-page {
  background: linear-gradient(135deg, white 0%, white 100%);
  min-height: 100vh;
  color: #ffffff;
}

.main-container {
  background: transparent;
  padding: 1rem;
}

/* Header Section */
.header-section {
  text-align: center;
  padding: 2rem 0;
  margin-bottom: 2rem;
}

.page-title {
  font-family: 'Inter', 'Poppins', sans-serif;
  font-size: 2rem;
  font-weight: 800;
  color: black;
  margin-bottom: 1rem;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.highlight {
  background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  position: relative;
}

.highlight::after {
  content: '';
  position: absolute;
  bottom: -3px;
  left: 0;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, #FFD700, transparent);
  opacity: 0.7;
}

.intro-text {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  line-height: 1.6;
  color: black;
  max-width: 700px;
  margin: 0 auto;
  text-align: center;
}

/* Values Section */
.values-section {
  padding: 1rem 0;
}

.values-grid {
  margin: 0 -8px;
}

.value-col {
  padding: 0.75rem;
  animation: fadeInUp 0.6s ease forwards;
  opacity: 0;
}

/* Stagger animations */
.value-col:nth-child(1) { animation-delay: 0.1s; }
.value-col:nth-child(2) { animation-delay: 0.2s; }
.value-col:nth-child(3) { animation-delay: 0.3s; }
.value-col:nth-child(4) { animation-delay: 0.4s; }
.value-col:nth-child(5) { animation-delay: 0.5s; }
.value-col:nth-child(6) { animation-delay: 0.6s; }
.value-col:nth-child(7) { animation-delay: 0.7s; }
.value-col:nth-child(8) { animation-delay: 0.8s; }

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.value-card {
  background: linear-gradient(135deg, #2d2d2d 0%, #1a1a1a 100%);
  border: 2px solid #333;
  border-radius: 15px;
  overflow: hidden;
  transition: all 0.4s ease;
  height: 100%;
  position: relative;
}

.value-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 215, 0, 0.1), transparent);
  transition: left 0.6s ease;
  z-index: 1;
}

.value-card:hover::before {
  left: 100%;
}

.value-card:hover {
  transform: translateY(-10px);
  border-color: #FFD700;
  box-shadow: 0 20px 40px rgba(255, 215, 0, 0.25);
}

.card-hover {
  transform: translateY(-10px);
}

/* Image Container */
.image-container {
  position: relative;
  overflow: hidden;
}

.value-image {
  transition: transform 0.4s ease;
  position: relative;
}

.value-card:hover .value-image {
  transform: scale(1.1);
}

.card-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, rgba(0, 0, 0, 0.9) 0%, rgba(255, 215, 0, 0.3) 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1.5rem;
  z-index: 2;
}

.overlay-content {
  text-align: center;
  color: #ffffff;
}

.overlay-icon {
  font-size: 2.5rem !important;
  color: #FFD700 !important;
  margin-bottom: 0.75rem;
}

.overlay-text {
  font-family: 'Inter', sans-serif;
  font-size: 0.9rem;
  line-height: 1.5;
  color: #ffffff;
  text-align: center;
  margin: 0;
}

/* Card Content */
.card-content {
  padding: 1.5rem;
  position: relative;
  z-index: 2;
}

.value-index {
  font-family: 'Inter', sans-serif;
  font-size: 0.8rem;
  font-weight: 700;
  color: #FFD700;
  margin-bottom: 0.75rem;
  text-align: center;
  background: rgba(255, 215, 0, 0.1);
  padding: 0.4rem 0.8rem;
  border-radius: 15px;
  display: inline-block;
}

.value-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  font-weight: 700;
  color: #ffffff;
  line-height: 1.3;
  margin-bottom: 1rem;
  text-align: center;
  min-height: 2.8rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.value-decoration {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.75rem;
}

.decoration-line {
  width: 25px;
  height: 2px;
  background: linear-gradient(90deg, #FFD700, #FFA500);
  border-radius: 1px;
}

.decoration-icon {
  color: #FFD700 !important;
  font-size: 1rem !important;
}

/* Floating Animation */
.value-card {
  animation: float 6s ease-in-out infinite;
}

.value-card:nth-child(odd) {
  animation-delay: 0s;
}

.value-card:nth-child(even) {
  animation-delay: 1.5s;
}

@keyframes float {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-8px);
  }
}

.value-card:hover {
  animation: none;
}

/* Additional Effects */
.value-card::after {
  content: '';
  position: absolute;
  top: -1px;
  left: -1px;
  right: -1px;
  bottom: -1px;
  background: linear-gradient(45deg, #FFD700, #FFA500, #FFD700);
  border-radius: 16px;
  z-index: -1;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.value-card:hover::after {
  opacity: 0.3;
}

/* Scroll Animation Enhancement */
.values-section {
  perspective: 1000px;
}

.value-col {
  transform-style: preserve-3d;
}

/* Responsive Design */
@media (max-width: 960px) {
  .page-title {
    font-size: 2.2rem;
  }
  
  .intro-text {
    font-size: 1rem;
  }
  
  .value-title {
    font-size: 1rem;
    min-height: 2.5rem;
  }
  
  .values-grid {
    margin: 0 -6px;
  }
  
  .value-col {
    padding: 0.5rem;
  }
}

@media (max-width: 768px) {
  .page-title {
    font-size: 2rem;
  }
  
  .intro-text {
    font-size: 0.95rem;
    text-align: left;
    padding: 0 1rem;
  }
  
  .header-section {
    padding: 1.5rem 0;
  }
  
  .value-col {
    padding: 0.5rem;
  }
  
  .card-content {
    padding: 1rem;
  }
  
  .value-title {
    font-size: 0.95rem;
    min-height: auto;
  }
  
  .overlay-text {
    font-size: 0.85rem;
  }
  
  .overlay-icon {
    font-size: 2rem !important;
  }
}

@media (max-width: 480px) {
  .main-container {
    padding: 0.5rem;
  }
  
  .page-title {
    font-size: 1.8rem;
  }
  
  .intro-text {
    font-size: 0.9rem;
  }
  
  .header-section {
    padding: 1rem 0;
  }
  
  .values-grid {
    margin: 0 -4px;
  }
  
  .value-col {
    padding: 0.25rem;
  }
  
  .card-content {
    padding: 0.75rem;
  }
  
  .value-title {
    font-size: 0.9rem;
  }
  
  .value-index {
    font-size: 0.7rem;
    padding: 0.3rem 0.6rem;
  }
  
  .overlay-content {
    padding: 1rem;
  }
  
  .overlay-text {
    font-size: 0.8rem;
  }
  
  .overlay-icon {
    font-size: 1.5rem !important;
    margin-bottom: 0.5rem;
  }
}

/* Touch-friendly improvements */
@media (hover: none) {
  .value-card:hover {
    transform: none;
  }
  
  .card-overlay {
    position: static;
    background: linear-gradient(135deg, rgba(0, 0, 0, 0.7) 0%, rgba(255, 215, 0, 0.2) 100%);
    padding: 1rem;
  }
}

/* Reduced motion support */
@media (prefers-reduced-motion: reduce) {
  .value-card {
    animation: none;
  }
  
  .value-card:hover .value-image {
    transform: none;
  }
  
  .value-col {
    animation: none;
    opacity: 1;
  }
}
</style>