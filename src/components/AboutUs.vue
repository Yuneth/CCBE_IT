<template>
  <div class="about-page">
    <NavBar></NavBar>
    
    <!-- Hero Section -->
    <section class="hero-section">
      <div class="hero-overlay">
        <div class="hero-content">
          <div class="logo-container" data-aos="zoom-in" data-aos-duration="800">
            <img :src="logo" alt="Company Logo" class="logo-image">
          </div>
          
          <h1 class="hero-title" data-aos="fade-up" data-aos-duration="1000">
            ABOUT <span class="highlight">CCIT</span>
          </h1>
          
          <p class="hero-subtitle" data-aos="fade-up" data-aos-duration="1000" data-aos-delay="200">
            Excellence in Information Technology Education Since 2015
          </p>
        </div>
      </div>
    </section>

    <!-- Main Content -->
    <v-container class="main-container">
      <!-- About Section -->
      <section class="about-section">
        <div class="section-header" data-aos="fade-up">
          <h2 class="section-title">
            Our <span class="highlight">Story</span>
          </h2>
          <p class="section-subtitle">A Legacy of Academic Excellence</p>
        </div>

        <div class="about-content">
          <v-row class="about-row" align="center">
            <v-col cols="12" lg="6" class="image-col" data-aos="fade-right">
              <div class="image-wrapper">
                <v-img 
                  src="https://ik.imagekit.io/u3wbiya66/Board.jpg?updatedAt=1737883142390" 
                  class="about-image"
                  alt="CCBE Board"
                  cover
                ></v-img>
                <div class="image-overlay"></div>
                <div class="year-badge">
                  <span>Since 2015</span>
                </div>
              </div>
            </v-col>
            
            <v-col cols="12" lg="6" class="text-col" data-aos="fade-left" data-aos-delay="200">
              <div class="text-content">
                <p class="paragraph">
                  Established on September 3rd, 2015, our institution proudly functions as a distinguished
                  Cambridge English Exam Preparation Centre (CELA Centre). Recognized as a designated Cambridge Qualifications
                  registration center for the esteemed British Council in Colombo, Sri Lanka, we specialize in facilitating
                  University of Cambridge Examinations.
                </p>
                
                <div class="achievement-stats">
                  <div class="stat-item">
                    <h3>8+</h3>
                    <p>Years of Excellence</p>
                  </div>
                  <div class="stat-item">
                    <h3>6</h3>
                    <p>Branches</p>
                  </div>
                  <div class="stat-item">
                    <h3>1000+</h3>
                    <p>Students Empowered</p>
                  </div>
                </div>
                
                <p class="paragraph">
                  With a steadfast commitment to academic excellence, we provide comprehensive and tailored
                  preparatory programs to empower individuals seeking success in Cambridge English exams. Our longstanding
                  association with the British Council underscores our dedication to upholding the highest standards in
                  education.
                </p>
              </div>
            </v-col>
          </v-row>
        </div>
      </section>

      <!-- Vision & Mission Cards -->
      <section class="vision-mission-section">
        <div class="section-header" data-aos="fade-up">
          <h2 class="section-title">
            Our <span class="highlight">Vision</span> & <span class="highlight">Mission</span>
          </h2>
          <p class="section-subtitle">Guiding Principles for Educational Excellence</p>
        </div>

        <div class="cards-container">
          <div class="card-wrapper" data-aos="fade-up" data-aos-duration="800">
            <div class="modern-card mission-card">
              <div class="card-icon">
                <svg width="48" height="48" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M12 22C17.5228 22 22 17.5228 22 12C22 6.47715 17.5228 2 12 2C6.47715 2 2 6.47715 2 12C2 17.5228 6.47715 22 12 22Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  <path d="M12 6V12L16 14" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
              </div>
              <h3 class="card-title">Our Mission</h3>
              <p class="card-text">
                To excel as a premier Cambridge English Assessment preparation center in Sri Lanka. We are dedicated to providing an exceptional learning experience, fostering language proficiency, critical thinking, and global awareness.
              </p>
              <div class="card-footer">
                <span class="tag">Innovation</span>
                <span class="tag">Excellence</span>
                <span class="tag">Growth</span>
              </div>
            </div>
          </div>

          <div class="card-wrapper" data-aos="fade-up" data-aos-duration="800" data-aos-delay="200">
            <div class="modern-card vision-card">
              <div class="card-icon">
                <svg width="48" height="48" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M1 12C1 12 5 4 12 4C19 4 23 12 23 12C23 12 19 20 12 20C5 20 1 12 1 12Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  <path d="M12 15C13.6569 15 15 13.6569 15 12C15 10.3431 13.6569 9 12 9C10.3431 9 9 10.3431 9 12C9 13.6569 10.3431 15 12 15Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
              </div>
              <h3 class="card-title">Our Vision</h3>
              <p class="card-text">
                To lead as the top Cambridge English Assessment preparation center in Sri Lanka, dedicated to fostering excellence in language proficiency and academic success.
              </p>
              <div class="card-footer">
                <span class="tag">Leadership</span>
                <span class="tag">Innovation</span>
                <span class="tag">Global</span>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Branch Network Section -->
      <section class="branch-section">
        <div class="section-header" data-aos="fade-up">
          <h2 class="section-title">
            Our <span class="highlight">Network</span>
          </h2>
          <p class="section-subtitle">Strategic Locations Across Sri Lanka</p>
        </div>

        <div class="branch-content">
          <div class="map-container" data-aos="zoom-in">
            <div class="map-wrapper">
              <v-img 
                class="branch-map" 
                src="@/assets/Branch_Network.png" 
                alt="Branch Network"
              ></v-img>
              
              <!-- Interactive Points -->
              <div 
                v-for="(office, index) in offices" 
                :key="index"
                class="branch-point" 
                :class="{ 'active': selectedOffice === office }"
                :style="getPointPosition(index)"
                @click="selectOffice(office)"
                @mouseenter="hoverOffice = office"
                @mouseleave="hoverOffice = null"
              >
                <div class="point-tooltip">
                  {{ office.name }}
                </div>
              </div>
            </div>
          </div>

          <!-- Office Details -->
          <div class="office-details" data-aos="fade-up" data-aos-delay="300">
            <div class="details-card" v-if="selectedOffice">
              <h3 class="office-name">{{ selectedOffice.name }}</h3>
              <div class="office-info">
                <div class="info-item">
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M20 10C20 16 12 22 12 22C12 22 4 16 4 10C4 7.87827 4.84285 5.84344 6.34315 4.34315C7.84344 2.84285 9.87827 2 12 2C14.1217 2 16.1566 2.84285 17.6569 4.34315C19.1571 5.84344 20 7.87827 20 10Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M12 13C13.6569 13 15 11.6569 15 10C15 8.34315 13.6569 7 12 7C10.3431 7 9 8.34315 9 10C9 11.6569 10.3431 13 12 13Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  </svg>
                  <span>{{ selectedOffice.address }}</span>
                </div>
                <div class="info-item">
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M22 16.92V19.92C22 20.47 21.55 20.92 21 20.92H19C18.45 20.92 18 20.47 18 19.92V16.92C18 16.37 17.55 15.92 17 15.92H15C14.45 15.92 14 15.47 14 14.92V6.92001C14 6.37001 14.45 5.92001 15 5.92001H19C19.55 5.92001 20 6.37001 20 6.92001V14.92C20 15.47 19.55 15.92 19 15.92H17C16.45 15.92 16 16.37 16 16.92V19.92" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M2 16.92V19.92C2 20.47 2.45 20.92 3 20.92H5C5.55 20.92 6 20.47 6 19.92V16.92C6 16.37 6.45 15.92 7 15.92H9C9.55 15.92 10 15.47 10 14.92V6.92001C10 6.37001 9.55 5.92001 9 5.92001H5C4.45 5.92001 4 6.37001 4 6.92001V14.92C4 15.47 4.45 15.92 5 15.92H7C7.55 15.92 8 16.37 8 16.92V19.92" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  </svg>
                  <span>{{ selectedOffice.phone }}</span>
                </div>
              </div>
              <button class="contact-btn" @click="navigateToBranch(selectedOffice)">
                Contact Branch
              </button>
            </div>
            
            <div class="empty-state" v-else>
              <svg width="64" height="64" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M21 10C21 17 12 23 12 23C12 23 3 17 3 10C3 7.61305 3.94821 5.32387 5.63604 3.63604C7.32387 1.94821 9.61305 1 12 1C14.3869 1 16.6761 1.94821 18.364 3.63604C20.0518 5.32387 21 7.61305 21 10Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                <path d="M12 13C13.6569 13 15 11.6569 15 10C15 8.34315 13.6569 7 12 7C10.3431 7 9 8.34315 9 10C9 11.6569 10.3431 13 12 13Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
              <h4>Select a Branch</h4>
              <p>Click on any location point or button below to view details</p>
            </div>
          </div>
        </div>

        <!-- Branch Buttons Grid -->
        <div class="branch-grid" data-aos="fade-up" data-aos-delay="400">
          <button 
            v-for="(office, index) in offices" 
            :key="index" 
            class="branch-tab"
            :class="{ 'active': selectedOffice === office }"
            @click="selectOffice(office)"
          >
            <span class="branch-name">{{ office.name }}</span>
            <span class="branch-location">{{ office.address.split(',')[1]?.trim() || office.address }}</span>
          </button>
        </div>
      </section>
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
    AOS.init({
      duration: 800,
      once: true,
      offset: 100
    });
  },
  methods: {
    selectOffice(office) {
      this.selectedOffice = office;
    },
    navigateToBranch(office) {
      console.log('Navigating to:', office.name);
      // Add navigation logic here
    },
    getPointPosition(index) {
      const positions = [
        { top: '79%', left: '34%' },   // Ambalangoda
        { top: '88%', left: '40%' },   // Galle
        { top: '86%', left: '55%' },   // Matara
        { top: '66.5%', left: '35%' }, // Piliyandala
        { top: '70.7%', left: '32%' }, // Horana
        { top: '66.2%', left: '28.4%' } // Kalutara
      ];
      return positions[index] || positions[0];
    }
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
      hoverOffice: null
    }
  },
}
</script>

<style scoped>
.about-page {
  background: #ffffff;
  min-height: 100vh;
  color: #333;
}

/* Hero Section */
.hero-section {
  height: 70vh;
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
  background: linear-gradient(white, white);
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
}

.logo-container {
  margin-bottom: 2rem;
}

.logo-image {
  width: 200px;
  height: 170px;
  filter: drop-shadow(0 4px 20px rgba(0,0,0,0.2));
}

.hero-title {
  font-family: 'Inter', 'Poppins', sans-serif;
  font-size: 3.5rem;
  font-weight: 800;
  color: black;
  margin-bottom: 1rem;
  letter-spacing: 1px;
}

.hero-subtitle {
  font-family: 'Inter', sans-serif;
  font-size: 1.2rem;
  color: rgba(255,255,255,0.9);
  font-weight: 300;
  letter-spacing: 2px;
  text-transform: uppercase;
}

/* Main Container */
.main-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 4rem 1rem;
}

/* Section Styles */
.section-header {
  text-align: center;
  margin-bottom: 4rem;
}

.section-title {
  font-family: 'Inter', sans-serif;
  font-size: 2.5rem;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 1rem;
}

.section-subtitle {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  color: #666;
  font-weight: 400;
}

.highlight {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

/* About Section */
.about-section {
  margin-bottom: 6rem;
}

.about-content {
  background: white;
  border-radius: 24px;
  overflow: hidden;
  box-shadow: 0 20px 60px rgba(0,0,0,0.08);
}

.image-wrapper {
  position: relative;
  border-radius: 16px;
  overflow: hidden;
  height: 100%;
  min-height: 400px;
}

.image-wrapper::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, rgba(102,126,234,0.1) 0%, rgba(118,75,162,0.1) 100%);
  z-index: 1;
}

.about-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.6s ease;
}

.image-wrapper:hover .about-image {
  transform: scale(1.05);
}

.year-badge {
  position: absolute;
  top: 20px;
  left: 20px;
  background: rgba(255,255,255,0.95);
  padding: 0.75rem 1.5rem;
  border-radius: 50px;
  z-index: 2;
  backdrop-filter: blur(10px);
}

.year-badge span {
  font-family: 'Inter', sans-serif;
  font-weight: 600;
  color: #667eea;
  font-size: 0.9rem;
}

.text-content {
  padding: 3rem;
}

.paragraph {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  line-height: 1.8;
  color: #444;
  margin-bottom: 2rem;
}

.achievement-stats {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
  margin: 2.5rem 0;
}

.stat-item {
  text-align: center;
  padding: 1.5rem;
  background: linear-gradient(135deg, #f6f9ff 0%, #f0f4ff 100%);
  border-radius: 12px;
  border: 1px solid rgba(102,126,234,0.1);
}

.stat-item h3 {
  font-family: 'Inter', sans-serif;
  font-size: 2rem;
  font-weight: 700;
  color: #667eea;
  margin-bottom: 0.5rem;
}

.stat-item p {
  font-family: 'Inter', sans-serif;
  font-size: 0.9rem;
  color: #666;
  font-weight: 500;
}

/* Vision & Mission Cards */
.vision-mission-section {
  margin-bottom: 6rem;
}

.cards-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
  max-width: 900px;
  margin: 0 auto;
}

.card-wrapper {
  perspective: 1000px;
}

.modern-card {
  background: white;
  border-radius: 20px;
  padding: 2.5rem;
  height: 100%;
  box-shadow: 0 10px 40px rgba(0,0,0,0.08);
  transition: all 0.4s ease;
  border: 1px solid rgba(102,126,234,0.1);
  position: relative;
  overflow: hidden;
}

.modern-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.modern-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 60px rgba(102,126,234,0.15);
}

.card-icon {
  margin-bottom: 1.5rem;
  color: #667eea;
}

.card-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.5rem;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 1.5rem;
}

.card-text {
  font-family: 'Inter', sans-serif;
  font-size: 1rem;
  line-height: 1.7;
  color: #555;
  margin-bottom: 2rem;
}

.card-footer {
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
}

.tag {
  background: linear-gradient(135deg, rgba(102,126,234,0.1) 0%, rgba(118,75,162,0.1) 100%);
  color: #667eea;
  padding: 0.5rem 1rem;
  border-radius: 50px;
  font-family: 'Inter', sans-serif;
  font-size: 0.85rem;
  font-weight: 500;
}

/* Branch Network */
.branch-section {
  margin-top: 4rem;
}

.branch-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
  margin-bottom: 3rem;
}

.map-container {
  position: relative;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 20px 60px rgba(0,0,0,0.1);
}

.map-wrapper {
  position: relative;
  width: 100%;
  height: 100%;
  min-height: 400px;
}

.branch-map {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.branch-point {
  position: absolute;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: white;
  border: 3px solid #667eea;
  cursor: pointer;
  transform: translate(-50%, -50%);
  transition: all 0.3s ease;
  z-index: 10;
}

.branch-point::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 40px;
  height: 40px;
  background: rgba(102,126,234,0.2);
  border-radius: 50%;
  transform: translate(-50%, -50%);
  animation: pulse 2s infinite;
  z-index: -1;
}

.branch-point:hover {
  transform: translate(-50%, -50%) scale(1.3);
  background: #667eea;
}

.branch-point.active {
  background: #667eea;
  transform: translate(-50%, -50%) scale(1.2);
}

.branch-point.active::before {
  background: rgba(102,126,234,0.4);
}

.point-tooltip {
  position: absolute;
  bottom: 100%;
  left: 50%;
  transform: translateX(-50%);
  background: rgba(0,0,0,0.8);
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 8px;
  font-family: 'Inter', sans-serif;
  font-size: 0.85rem;
  white-space: nowrap;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.3s ease;
}

.branch-point:hover .point-tooltip {
  opacity: 1;
}

.office-details {
  display: flex;
  align-items: center;
  justify-content: center;
}

.details-card {
  background: white;
  border-radius: 20px;
  padding: 2.5rem;
  box-shadow: 0 10px 40px rgba(0,0,0,0.08);
  border: 1px solid rgba(102,126,234,0.1);
  width: 100%;
  max-width: 400px;
}

.office-name {
  font-family: 'Inter', sans-serif;
  font-size: 1.8rem;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 1.5rem;
}

.office-info {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-bottom: 2rem;
}

.info-item {
  display: flex;
  align-items: center;
  gap: 1rem;
  color: #555;
}

.info-item svg {
  color: #667eea;
}

.info-item span {
  font-family: 'Inter', sans-serif;
  font-size: 1rem;
  line-height: 1.5;
}

.contact-btn {
  width: 100%;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border: none;
  padding: 1rem 2rem;
  border-radius: 12px;
  font-family: 'Inter', sans-serif;
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.contact-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 30px rgba(102,126,234,0.3);
}

.empty-state {
  text-align: center;
  padding: 3rem;
  color: #999;
}

.empty-state svg {
  margin-bottom: 1rem;
  color: #ddd;
}

.empty-state h4 {
  font-family: 'Inter', sans-serif;
  font-size: 1.2rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
  color: #666;
}

.empty-state p {
  font-family: 'Inter', sans-serif;
  font-size: 0.95rem;
  color: #888;
}

.branch-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1rem;
  margin-top: 3rem;
}

.branch-tab {
  background: white;
  border: 2px solid rgba(102,126,234,0.1);
  border-radius: 12px;
  padding: 1.5rem;
  cursor: pointer;
  transition: all 0.3s ease;
  text-align: left;
}

.branch-tab:hover {
  border-color: #667eea;
  transform: translateY(-3px);
  box-shadow: 0 10px 30px rgba(102,126,234,0.1);
}

.branch-tab.active {
  background: linear-gradient(135deg, rgba(102,126,234,0.1) 0%, rgba(118,75,162,0.1) 100%);
  border-color: #667eea;
}

.branch-name {
  display: block;
  font-family: 'Inter', sans-serif;
  font-size: 1rem;
  font-weight: 600;
  color: #1a1a1a;
  margin-bottom: 0.25rem;
}

.branch-location {
  display: block;
  font-family: 'Inter', sans-serif;
  font-size: 0.9rem;
  color: #666;
}

/* Animations */
@keyframes pulse {
  0% {
    transform: translate(-50%, -50%) scale(1);
    opacity: 1;
  }
  100% {
    transform: translate(-50%, -50%) scale(2);
    opacity: 0;
  }
}

/* Responsive Design */
@media (max-width: 960px) {
  .hero-title {
    font-size: 2.5rem;
  }
  
  .section-title {
    font-size: 2rem;
  }
  
  .branch-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }
  
  .achievement-stats {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 600px) {
  .hero-section {
    height: 50vh;
  }
  
  .hero-title {
    font-size: 2rem;
  }
  
  .hero-subtitle {
    font-size: 1rem;
  }
  
  .logo-image {
    width: 150px;
    height: 105px;
  }
  
  .section-title {
    font-size: 1.8rem;
  }
  
  .text-content {
    padding: 1.5rem;
  }
  
  .cards-container {
    grid-template-columns: 1fr;
  }
  
  .achievement-stats {
    grid-template-columns: 1fr;
  }
  
  .modern-card {
    padding: 2rem;
  }
  
  .details-card {
    padding: 1.5rem;
  }
  
  .branch-grid {
    grid-template-columns: 1fr;
  }
}

/* Smooth Scrolling */
html {
  scroll-behavior: smooth;
}

/* Custom Scrollbar */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #f1f1f1;
}

::-webkit-scrollbar-thumb {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: linear-gradient(135deg, #5a6fd8 0%, #6a4a95 100%);
}
</style>