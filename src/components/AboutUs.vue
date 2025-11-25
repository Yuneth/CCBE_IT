<template>
  <div class="about-page">
    <NavBar></NavBar>
    <v-container class="main-container">
      <!-- Logo Section -->
      <div class="logo-container" data-aos="zoom-in-up" data-aos-duration="2000">
        <img :src="logo" alt="Company Logo" class="logo-image">
      </div>
      
      <!-- Main Title -->
      <h1 class="page-title" data-aos="fade-up" data-aos-duration="3000">
        ABOUT <span class="highlight">CCIT</span>
      </h1>
      
      <br>
      
      <!-- About Content -->
      <div class="content-section">
        <v-row class="about-row">
          <v-col cols="12" lg="6" class="image-col">
            <v-img 
              data-aos="zoom-out" 
              data-aos-duration="2000" 
              src="https://ik.imagekit.io/u3wbiya66/Board.jpg?updatedAt=1737883142390" 
              class="about-image"
              alt="CCBE Board"
            ></v-img>
          </v-col>
          <v-col cols="12" lg="6" class="text-col">
            <p class="paragraph" data-aos="fade-up" data-aos-duration="3000">
              Established on September 3rd, 2015, our institution proudly functions as a distinguished
              Cambridge English Exam Preparation Centre (CELA Centre). Recognized as a designated Cambridge Qualifications
              registration center for the esteemed British Council in Colombo, Sri Lanka, we specialize in facilitating
              University of Cambridge Examinations.
              With a steadfast commitment to academic excellence, we provide comprehensive and tailored
              preparatory programs to empower individuals seeking success in Cambridge English exams. Our longstanding
              association with the British Council underscores our dedication to upholding the highest standards in
              education, ensuring that our students are well-equipped to excel in their academic pursuits.
            </p>
          </v-col>
        </v-row>
      </div>

      <v-divider class="section-divider"></v-divider>

      <!-- Vision & Mission Section -->
      <div class="vision-mission-section">
        <h1 class="section-title" data-aos="fade-up" data-aos-duration="3000">
          OUR <span class="highlight">VISION</span> & <span class="highlight">MISSION</span>
        </h1>
      </div>
    </v-container>

    <!-- Parallax Section -->
    <v-parallax class="parallax-section" src='@/assets/BC1.jpg'>
      <div class="parallax-content">
        <div class="mission-vision-container">
          <div class="text-card" data-aos="fade-up" data-aos-duration="3000">
            <h3 class="card-title">Our Mission</h3>
            <p class="card-text">
              To excel as a premier Cambridge English Assessment preparation center in Sri Lanka. We are dedicated to providing an exceptional learning experience, fostering language proficiency, critical thinking, and global awareness. Through innovative teaching and a commitment to student success, we aim to be the preferred choice for effective Cambridge English Assessment preparation, making a lasting impact on our students' academic and personal growth.
            </p>
          </div>
          
          <div class="text-card" data-aos="fade-up" data-aos-duration="3000" data-aos-delay="200">
            <h3 class="card-title">Our Vision</h3>
            <p class="card-text">
              To lead as the top Cambridge English Assessment preparation center in Sri Lanka, dedicated to fostering excellence in language proficiency and academic success. We aim to provide an inspiring learning environment, utilizing innovative teaching methods and resources to empower students for success in a globalized world.
            </p>
          </div>
        </div>
      </div>
    </v-parallax>

    <v-container class="main-container">
      <v-divider class="section-divider"></v-divider>
      
      <!-- Branch Network Section -->
      <section class="branch-section">
        <h1 class="section-title" data-aos="fade-up" data-aos-duration="3000">
          OUR <span class="highlight">BRANCH NETWORK</span>
        </h1>

        <div class="branch-map-container">
          <!-- Image Container -->
          <div class="image-container" data-aos="zoom-in" data-aos-duration="2000">
            <!-- Main Image -->
            <v-img 
              class="branch-map" 
              src="@/assets/Branch_Network.png" 
              alt="Branch Network"
            ></v-img>
            
            <!-- Interactive Points -->
            <div 
              class="branch-point" 
              v-tooltip:start="'Ambalangoda College'" 
              :style="{ top: '72%', left: '34%' }" 
              @click="navigateTo('/about/ambalangoda')"
            ></div>
            <div 
              class="branch-point" 
              v-tooltip:start="'Galle College'" 
              :style="{ top: '80%', left: '40%' }" 
              @click="navigateTo('/about/galle')"
            ></div>
            <div 
              class="branch-point" 
              v-tooltip:start="'Matara College'" 
              :style="{ top: '79%', left: '55%' }" 
              @click="navigateTo('/about/matara')"
            ></div>
            <div 
              class="branch-point" 
              v-tooltip:start="'Piliyandala College'" 
              :style="{ top: '63%', left: '35%' }" 
              @click="navigateTo('/about/piliyandala')"
            ></div>
            <div 
              class="branch-point" 
              v-tooltip:start="'Horana College'" 
              :style="{ top: '67%', left: '32%' }" 
              @click="navigateTo('/about/horana')"
            ></div>
            <div 
              class="branch-point" 
              v-tooltip:start="'Kalutara College'" 
              :style="{ top: '63%', left: '28%' }" 
              @click="navigateTo('/about/kalutara')"
            ></div>
          </div>
        </div>

        <!-- Selected Office Info -->
        <div v-if="selectedOffice" class="office-info" data-aos="fade-up">
          <h3 class="office-name">{{ selectedOffice.name }}</h3>
          <p class="office-detail">{{ selectedOffice.address }}</p>
          <p class="office-detail">{{ selectedOffice.phone }}</p>
        </div>

        <!-- Branch Buttons -->
        <div class="branch-buttons">
          <v-row justify="center" class="button-row">
            <v-btn 
              v-for="(office, index) in offices" 
              :key="index" 
              class="branch-btn"
              data-aos="zoom-out" 
              data-aos-duration="2000"
              :data-aos-delay="index * 100"
              rounded="xl" 
              size="large" 
              @click="selectOffice(office)"
            >
              {{ office.name }}
            </v-btn>
          </v-row>
        </div>
      </section>

      <v-divider class="section-divider"></v-divider>
    </v-container>

    <ArrowButton></ArrowButton>
    <ChatBot></ChatBot>
    <FooterPage></FooterPage>
  </div>
</template>

<script>
import NavBar from './NavBar.vue'
import FooterPage from './FooterPage.vue'
import ChatBot from './ChatBot.vue';
import ArrowButton from './ArrowButton.vue';
import AOS from 'aos';
import 'aos/dist/aos.css';

export default {
  name: 'AboutPage',
  components: {
    NavBar,
    FooterPage,
    ChatBot,
    ArrowButton
  },
  mounted() {
    AOS.init();
  },
  methods: {
    selectOffice(office) {
      this.selectedOffice = office;
    },
    navigateTo(link) {
      console.log('Navigating to:', link);
      if (link) {
        this.$router.push(link);
      } else {
        console.warn("No link provided for this point.");
      }
    },
  },
  data() {
    return {
      logo: require('@/assets/CCIT - logo.png'),
      offices: [
        {
          name: "Galle College",
          address: "118, Old Matara Rd, Galle, 80000",
          phone: "+94 91 22 37373"
        },
        {
          name: "Ambalangoda College",
          address: "No 97, New Rd, Ambalangoda, 80300",
          phone: "+94 91 2252 452"
        },
        {
          name: "Matara College",
          address: "No 352, Kumarathunga Mw, Matara, 81000",
          phone: "+94 41 2050 200"
        },
        {
          name: "Piliyandala College",
          address: "No Moratuwa Rd, Suwarapola, Piliyandala, 10300",
          phone: "+94 11 2 180 008"
        },
        {
          name: "Horana College",
          address: "No 149, Graceland Circular Rd, Horana, 12400",
          phone: "+94 2 180 008"
        },
        {
          name: "Kalutara College",
          address: "No 85, Maha Waskaduwa, 12580",
          phone: "0342 121 210"
        },
      ],
      selectedOffice: null,
    }
  },
}
</script>

<style scoped>
.about-page {
  background: linear-gradient(135deg, #0a0a0a 0%, #1a1a1a 100%);
  min-height: 100vh;
  color: #ffffff;
}

.main-container {
  background: transparent;
  padding: 2rem 1rem;
}

/* Logo Section */
.logo-container {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1rem 0;
}

.logo-image {
  width: 200px;
  height: 150px;
  transition: transform 0.3s ease;
}

.logo-image:hover {
  transform: scale(1.05);
}

/* Typography */
.page-title {
  font-family: 'Inter', 'Poppins', sans-serif;
  font-size: 3rem;
  font-weight: 800;
  text-align: center;
  color: #ffffff;
  margin-bottom: 1rem;
}

.section-title {
  font-family: 'Inter', 'Poppins', sans-serif;
  font-size: 2.5rem;
  font-weight: 700;
  text-align: center;
  color: #ffffff;
  margin-bottom: 2rem;
}

.highlight {
  background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

/* Content Section */
.content-section {
  margin: 2rem 0;
}

.about-row {
  align-items: center;
}

.about-image {
  border-radius: 12px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
  transition: transform 0.3s ease;
}

.about-image:hover {
  transform: scale(1.02);
}

.paragraph {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  line-height: 1.8;
  color: #e0e0e0;
  text-align: justify;
}

/* Section Divider */
.section-divider {
  border-color: #333;
  margin: 3rem 0;
  background: linear-gradient(90deg, transparent, #FFD700, transparent);
  height: 2px;
}

/* Vision & Mission Section */
.vision-mission-section {
  padding: 2rem 0;
}

/* Parallax Section */
.parallax-section {
  height: 600px;
  position: relative;
}

.parallax-section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.7);
  z-index: 1;
}

.parallax-content {
  position: relative;
  z-index: 2;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.mission-vision-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
  gap: 2rem;
  max-width: 1200px;
  width: 90%;
  padding: 2rem;
}

.text-card {
  background: linear-gradient(135deg, rgba(26, 26, 26, 0.9) 0%, rgba(45, 45, 45, 0.9) 100%);
  padding: 2.5rem;
  border-radius: 16px;
  border: 2px solid #FFD700;
  box-shadow: 0 15px 35px rgba(255, 215, 0, 0.2);
  transition: transform 0.3s ease;
}

.text-card:hover {
  transform: translateY(-5px);
}

.card-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.8rem;
  font-weight: 700;
  color: #FFD700;
  margin-bottom: 1.5rem;
  text-align: center;
}

.card-text {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  line-height: 1.7;
  color: #e0e0e0;
  text-align: center;
}

/* Branch Network Section */
.branch-section {
  padding: 3rem 0;
}

.branch-map-container {
  display: flex;
  justify-content: center;
  margin: 3rem 0;
}

.image-container {
  position: relative;
  max-width: 600px;
  width: 100%;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.4);
  border: 2px solid #333;
}

.branch-map {
  width: 100%;
  height: auto;
  display: block;
}

.branch-point {
  position: absolute;
  width: 20px;
  height: 20px;
  background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  cursor: pointer;
  z-index: 10;
  animation: pulse-grow 2s infinite;
  box-shadow: 0 0 20px rgba(255, 215, 0, 0.8);
  transition: all 0.3s ease;
}

.branch-point:hover {
  transform: translate(-50%, -50%) scale(1.3);
  box-shadow: 0 0 30px rgba(255, 215, 0, 1);
}

.branch-point::before,
.branch-point::after {
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  border: 2px solid #FFD700;
  border-radius: 50%;
  top: 0;
  left: 0;
  transform: scale(1);
  animation: wave 2s infinite;
}

.branch-point::after {
  animation-delay: 1s;
}

@keyframes pulse-grow {
  0%, 100% {
    transform: translate(-50%, -50%) scale(1);
  }
  50% {
    transform: translate(-50%, -50%) scale(1.2);
  }
}

@keyframes wave {
  0% {
    opacity: 1;
    transform: scale(1);
  }
  100% {
    opacity: 0;
    transform: scale(3);
  }
}

/* Office Info */
.office-info {
  background: linear-gradient(135deg, #2d2d2d 0%, #1a1a1a 100%);
  padding: 2rem;
  border-radius: 12px;
  border: 1px solid #FFD700;
  margin: 2rem auto;
  max-width: 500px;
  text-align: center;
}

.office-name {
  font-family: 'Inter', sans-serif;
  font-size: 1.5rem;
  font-weight: 700;
  color: #FFD700;
  margin-bottom: 1rem;
}

.office-detail {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  color: #e0e0e0;
  margin: 0.5rem 0;
}

/* Branch Buttons */
.branch-buttons {
  margin: 2rem 0;
}

.button-row {
  gap: 1rem;
}

.branch-btn {
  background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%) !important;
  color: #000000 !important;
  font-weight: 600 !important;
  font-family: 'Inter', sans-serif !important;
  border: 2px solid transparent !important;
  transition: all 0.3s ease !important;
}

.branch-btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 25px rgba(255, 215, 0, 0.4) !important;
  border-color: #FFD700 !important;
}

/* Responsive Design */
@media (max-width: 960px) {
  .page-title {
    font-size: 2.5rem;
  }
  
  .section-title {
    font-size: 2rem;
  }
  
  .mission-vision-container {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }
  
  .text-card {
    padding: 2rem;
  }
  
  .card-title {
    font-size: 1.5rem;
  }
  
  .card-text {
    font-size: 1rem;
  }
}

@media (max-width: 600px) {
  .page-title {
    font-size: 2rem;
  }
  
  .section-title {
    font-size: 1.8rem;
  }
  
  .logo-image {
    width: 160px;
    height: 120px;
  }
  
  .paragraph {
    font-size: 1rem;
    text-align: left;
  }
  
  .mission-vision-container {
    padding: 1rem;
  }
  
  .text-card {
    padding: 1.5rem;
  }
  
  .branch-point {
    width: 15px;
    height: 15px;
  }
  
  .button-row {
    flex-direction: column;
    align-items: center;
  }
  
  .branch-btn {
    width: 100%;
    max-width: 250px;
  }
}

/* Additional Animations */
.content-section, .vision-mission-section, .branch-section {
  opacity: 0;
  animation: fadeInUp 1s ease forwards;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>