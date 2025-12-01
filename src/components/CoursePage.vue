<template>
  <div class="programmes-page">
    <NavBar></NavBar>
    <v-container class="main-container">
      <!-- Header Section -->
      <section class="header-section">
        <h1 class="page-title" data-aos="fade-up" data-aos-duration="3000">
          OUR <span class="highlight">PROGRAMMES</span>
        </h1>
        <p class="intro-text" data-aos="fade-up" data-aos-duration="3000">
          Discover our comprehensive range of English language programmes designed to empower learners of all ages 
          and backgrounds. From early childhood education to advanced professional certifications, we provide 
          tailored learning experiences that foster excellence and confidence.
        </p>
      </section>

      <!-- Programmes Grid -->
      <section class="programmes-section">
        <v-row class="programmes-grid">
          <!-- Pre Schoolers -->
          <v-col cols="12" lg="4" md="6">
            <v-card 
              class="programme-card" 
              data-aos="fade-up" 
              data-aos-duration="3000"
              data-aos-delay="100"
            >
              <div class="image-container">
                <v-img 
                  class="programme-image" 
                  height="200" 
                  src="https://ik.imagekit.io/u3wbiya66/PXL_20250117_094732824.jpg?updatedAt=1737789273936" 
                  cover
                ></v-img>
                <div class="card-overlay">
                  <v-icon class="overlay-icon">mdi-school</v-icon>
                  <span class="overlay-text">Ages 3-5</span>
                </div>
              </div>
              
              <v-card-text class="card-content">
                <div class="programme-badge">Foundation</div>
                <h3 class="programme-title">Pre Schoolers</h3>
                <p class="programme-description">
                  This program is for children who know their ABCs and are just starting to read or have some familiarity with English. We focus on building foundational language skills through interactive and engaging activities.
                </p>
              </v-card-text>
              
              <v-card-actions class="card-actions">
                <v-btn 
                  class="learn-more-btn" 
                  variant="outlined" 
                  to="/courses/preschool"
                >
                  Learn More
                  <v-icon right>mdi-arrow-right</v-icon>
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-col>

          <!-- Young Learners -->
          <v-col cols="12" lg="4" md="6">
            <v-card 
              class="programme-card" 
              data-aos="fade-up" 
              data-aos-duration="3000"
              data-aos-delay="200"
            >
              <div class="image-container">
                <v-img 
                  class="programme-image" 
                  height="200" 
                  src="https://ik.imagekit.io/u3wbiya66/PXL_20250128_092657658-EDIT.jpg?updatedAt=1738392311029" 
                  cover
                ></v-img>
                <div class="card-overlay">
                  <v-icon class="overlay-icon">mdi-account-child</v-icon>
                  <span class="overlay-text">Ages 6-12</span>
                </div>
              </div>
              
              <v-card-text class="card-content">
                <div class="programme-badge">Elementary</div>
                <h3 class="programme-title">Young Learners</h3>
                <p class="programme-description">
                  Designed for elementary school students, this programme builds strong English foundations through 
                  interactive lessons, creative activities, and age-appropriate learning materials.
                </p>
              </v-card-text>
              
              <v-card-actions class="card-actions">
                <v-btn 
                  class="learn-more-btn" 
                  variant="outlined" 
                  to="/courses/younglearners"
                >
                  Learn More
                  <v-icon right>mdi-arrow-right</v-icon>
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-col>

          <!-- For Schools -->
          <v-col cols="12" lg="4" md="6">
            <v-card 
              class="programme-card" 
              data-aos="fade-up" 
              data-aos-duration="3000"
              data-aos-delay="300"
            >
              <div class="image-container">
                <v-img 
                  class="programme-image" 
                  height="200" 
                  src="https://ik.imagekit.io/u3wbiya66/IMG-20250127-WA0071.jpg?updatedAt=1737967718437" 
                  cover
                ></v-img>
                <div class="card-overlay">
                  <v-icon class="overlay-icon">mdi-account-group</v-icon>
                  <span class="overlay-text">Ages 13-18</span>
                </div>
              </div>
              
              <v-card-text class="card-content">
                <div class="programme-badge">Secondary</div>
                <h3 class="programme-title">For Schools</h3>
                <p class="programme-description">
                  Comprehensive English programme for secondary school students, focusing on academic English, 
                  communication skills, and exam preparation to support their educational journey.
                </p>
              </v-card-text>
              
              <v-card-actions class="card-actions">
                <v-btn 
                  class="learn-more-btn" 
                  variant="outlined" 
                  to="/courses/forschool"
                >
                  Learn More
                  <v-icon right>mdi-arrow-right</v-icon>
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-col>

          <!-- O/L English Skills -->
          <v-col cols="12" lg="4" md="6">
            <v-card 
              class="programme-card" 
              data-aos="fade-up" 
              data-aos-duration="3000"
              data-aos-delay="400"
            >
              <div class="image-container">
                <v-img 
                  class="programme-image" 
                  height="200" 
                  src="https://ik.imagekit.io/u3wbiya66/PXL_20250131_073049442-EDIT.jpg?updatedAt=1738389378296" 
                  cover
                ></v-img>
                <div class="card-overlay">
                  <v-icon class="overlay-icon">mdi-certificate</v-icon>
                  <span class="overlay-text">O/L Exam</span>
                </div>
              </div>
              
              <v-card-text class="card-content">
                <div class="programme-badge">Exam Prep</div>
                <h3 class="programme-title">English Skills For O/L's</h3>
                <p class="programme-description">
                  Specialized preparation for Ordinary Level examinations with focused training on all language 
                  components including reading, writing, listening, and speaking skills.
                </p>
              </v-card-text>
              
              <v-card-actions class="card-actions">
                <v-btn 
                  class="learn-more-btn" 
                  variant="outlined" 
                  to="/courses/ol"
                >
                  Learn More
                  <v-icon right>mdi-arrow-right</v-icon>
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-col>

          <!-- A/L English Skills -->
          <v-col cols="12" lg="4" md="6">
            <v-card 
              class="programme-card" 
              data-aos="fade-up" 
              data-aos-duration="3000"
              data-aos-delay="500"
            >
              <div class="image-container">
                <v-img 
                  class="programme-image" 
                  height="200" 
                  src="https://ik.imagekit.io/u3wbiya66/PXL_20250127_083713735-EDIT.jpg?updatedAt=1738393428664" 
                  cover
                ></v-img>
                <div class="card-overlay">
                  <v-icon class="overlay-icon">mdi-certificate-outline</v-icon>
                  <span class="overlay-text">A/L Exam</span>
                </div>
              </div>
              
              <v-card-text class="card-content">
                <div class="programme-badge">Advanced</div>
                <h3 class="programme-title">English Skills For A/L's</h3>
                <p class="programme-description">
                  Advanced English programme for Advanced Level students, emphasizing critical thinking, 
                  academic writing, and sophisticated communication skills for higher education.
                </p>
              </v-card-text>
              
              <v-card-actions class="card-actions">
                <v-btn 
                  class="learn-more-btn" 
                  variant="outlined" 
                  to="/courses/al"
                >
                  Learn More
                  <v-icon right>mdi-arrow-right</v-icon>
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-col>

          <!-- IELTS -->
          <v-col cols="12" lg="4" md="6">
            <v-card 
              class="programme-card" 
              data-aos="fade-up" 
              data-aos-duration="3000"
              data-aos-delay="600"
            >
              <div class="image-container">
                <v-img 
                  class="programme-image" 
                  height="200" 
                  src="https://ik.imagekit.io/u3wbiya66/IELTS.jpg?updatedAt=1738050317311" 
                  cover
                ></v-img>
                <div class="card-overlay">
                  <v-icon class="overlay-icon">mdi-earth</v-icon>
                  <span class="overlay-text">International</span>
                </div>
              </div>
              
              <v-card-text class="card-content">
                <div class="programme-badge">Professional</div>
                <h3 class="programme-title">IELTS Preparation</h3>
                <p class="programme-description">
                  Comprehensive IELTS preparation programme covering all test components with expert guidance, 
                  practice tests, and strategies to achieve your desired band score for global opportunities.
                </p>
              </v-card-text>
              
              <v-card-actions class="card-actions">
                <v-btn 
                  class="learn-more-btn" 
                  variant="outlined" 
                  to="/courses/ielts"
                >
                  Learn More
                  <v-icon right>mdi-arrow-right</v-icon>
                </v-btn>
              </v-card-actions>
            </v-card>
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
  name: 'CoursePage',
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
    return {};
  }
};
</script>

<style scoped>
.programmes-page {
  background: linear-gradient(135deg, white 0%, white 100%);
  min-height: 100vh;
  color: #ffffff;
}

.main-container {
  background: transparent;
  padding: 2rem 1rem;
}

/* Header Section */
.header-section {
  text-align: center;
  padding: 3rem 0;
  margin-bottom: 3rem;
}

.page-title {
  font-family: 'Inter', 'Poppins', sans-serif;
  font-size: 2rem;
  font-weight: 800;
  color: black;
  margin-bottom: 1.5rem;
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
  bottom: -5px;
  left: 0;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, #FFD700, transparent);
  opacity: 0.7;
}

.intro-text {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  line-height: 1.7;
  color: black;
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
}

/* Programmes Section */
.programmes-section {
  padding: 2rem 0;
}

.programmes-grid {
  margin: 0 -12px;
}

/* Programme Card */
.programme-card {
  background: linear-gradient(135deg, #2d2d2d 0%, #1a1a1a 100%);
  border: 2px solid #333;
  border-radius: 20px;
  overflow: hidden;
  transition: all 0.4s ease;
  height: 100%;
  position: relative;
  margin-bottom: 2rem;
}

.programme-card::before {
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

.programme-card:hover::before {
  left: 100%;
}

.programme-card:hover {
  transform: translateY(-15px);
  border-color: #FFD700;
  box-shadow: 0 25px 50px rgba(255, 215, 0, 0.25);
}

/* Image Container */
.image-container {
  position: relative;
  overflow: hidden;
}

.programme-image {
  transition: transform 0.4s ease;
  position: relative;
}

.programme-card:hover .programme-image {
  transform: scale(1.1);
}

.card-overlay {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: linear-gradient(135deg, rgba(255, 215, 0, 0.9) 0%, rgba(255, 165, 0, 0.9) 100%);
  padding: 0.5rem 1rem;
  border-radius: 20px;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  backdrop-filter: blur(10px);
}

.overlay-icon {
  color: #000000 !important;
  font-size: 1.2rem !important;
}

.overlay-text {
  font-family: 'Inter', sans-serif;
  font-size: 0.8rem;
  font-weight: 600;
  color: #000000;
}

/* Card Content */
.card-content {
  padding: 2rem;
  position: relative;
  z-index: 2;
}

.programme-badge {
  font-family: 'Inter', sans-serif;
  font-size: 0.8rem;
  font-weight: 700;
  color: #FFD700;
  background: rgba(255, 215, 0, 0.1);
  padding: 0.4rem 1rem;
  border-radius: 15px;
  display: inline-block;
  margin-bottom: 1rem;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.programme-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.4rem;
  font-weight: 700;
  color: #ffffff;
  line-height: 1.3;
  margin-bottom: 1rem;
  min-height: 3.5rem;
}

.programme-description {
  font-family: 'Inter', sans-serif;
  font-size: 0.95rem;
  line-height: 1.6;
  color: #e0e0e0;
  margin-bottom: 0;
}

/* Card Actions */
.card-actions {
  padding: 0 2rem 2rem;
  display: flex;
  justify-content: center;
}

.learn-more-btn {
  background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%) !important;
  color: #000000 !important;
  font-weight: 600 !important;
  font-family: 'Inter', sans-serif !important;
  border: 2px solid transparent !important;
  border-radius: 25px !important;
  padding: 0.75rem 2rem !important;
  text-transform: none !important;
  transition: all 0.3s ease !important;
}

.learn-more-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(255, 215, 0, 0.4) !important;
  border-color: #FFD700 !important;
}

/* Floating Animation */
.programme-card {
  animation: float 6s ease-in-out infinite;
}

.programme-card:nth-child(odd) {
  animation-delay: 0s;
}

.programme-card:nth-child(even) {
  animation-delay: 1.5s;
}

@keyframes float {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}

.programme-card:hover {
  animation: none;
}

/* Responsive Design */
@media (max-width: 960px) {
  .page-title {
    font-size: 2.8rem;
  }
  
  .intro-text {
    font-size: 1.1rem;
  }
  
  .programme-title {
    font-size: 1.2rem;
    min-height: auto;
  }
  
  .programmes-grid {
    margin: 0 -8px;
  }
}

@media (max-width: 600px) {
  .page-title {
    font-size: 2.2rem;
  }
  
  .intro-text {
    font-size: 1rem;
    text-align: left;
  }
  
  .header-section {
    padding: 2rem 0;
  }
  
  .card-content {
    padding: 1.5rem;
  }
  
  .programme-title {
    font-size: 1.1rem;
  }
  
  .programme-description {
    font-size: 0.9rem;
  }
  
  .card-actions {
    padding: 0 1.5rem 1.5rem;
  }
}

/* Additional Effects */
.programme-card::after {
  content: '';
  position: absolute;
  top: -2px;
  left: -2px;
  right: -2px;
  bottom: -2px;
  background: linear-gradient(45deg, #FFD700, #FFA500, #FFD700);
  border-radius: 22px;
  z-index: -1;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.programme-card:hover::after {
  opacity: 0.3;
}

/* Scroll Animation Enhancement */
.programmes-section {
  perspective: 1000px;
}

.programme-card {
  transform-style: preserve-3d;
}
</style>