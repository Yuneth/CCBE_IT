<template>
  <div class="contact-page">
    <NavBar></NavBar>
    <v-container class="main-container">
      <!-- Logo Section -->
      <div class="logo-container" data-aos="zoom-in-up" data-aos-duration="2000">
        <img :src="logo" alt="Company Logo" class="logo-image">
      </div>
      
      <!-- Main Title -->
      <h1 class="page-title" data-aos="fade-up" data-aos-duration="3000">
        CONTACT <span class="highlight">US</span>
      </h1>
      
      <!-- Subtitle -->
      <h4 class="subtitle" data-aos="fade-up" data-aos-duration="2000">
        At the heart of our commitment to communication and service lies our dedication to ensuring every interaction is meaningful, responsive, and supportive.
      </h4>

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
              :style="{ top: '79%', left: '34%' }" 
              @click="navigateTo('/about/ambalangoda')"
            ></div>
            <div 
              class="branch-point" 
              v-tooltip:start="'Galle College'" 
              :style="{ top: '88%', left: '40%' }" 
              @click="navigateTo('/about/galle')"
            ></div>
            <div 
              class="branch-point" 
              v-tooltip:start="'Matara College'" 
              :style="{ top: '86%', left: '55%' }" 
              @click="navigateTo('/about/matara')"
            ></div>
            <div 
              class="branch-point" 
              v-tooltip:start="'Piliyandala College'" 
              :style="{ top: '66.5%', left: '35%' }" 
              @click="navigateTo('/about/piliyandala')"
            ></div>
            <div 
              class="branch-point" 
              v-tooltip:start="'Horana College'" 
              :style="{ top: '70.7%', left: '32%' }" 
              @click="navigateTo('/about/horana')"
            ></div>
            <div 
              class="branch-point" 
              v-tooltip:start="'Kalutara College'" 
              :style="{ top: '66.2%', left: '28.4%' }" 
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

    <ChatBot></ChatBot>
    <FooterPage></FooterPage>
  </div>
</template>

<script>
import NavBar from "./NavBar.vue";
import FooterPage from "./FooterPage.vue";
import ChatBot from "./ChatBot.vue";

// Import AOS for animations
import AOS from "aos";
import "aos/dist/aos.css";

export default {
    name: "ContactUs",
    components: {
        NavBar,
        FooterPage,
        ChatBot
    },
    mounted() {
        AOS.init(); // Initialize AOS animations when the component is mounted
    },
    methods: {
        formatPhone(phone) {
            // Format the phone number in a readable format
            return phone.replace(/(\d{2})(\d{3})(\d{3})(\d{2})/, "+$1 $2 $3 $4");
        },
        navigateTo(route) {
            this.$router.push(route);
        },
        selectOffice(office) {
            this.selectedOffice = office;
        }
    },
    data() {
        return {
            logo: require('@/assets/logo-New.png'),
            offices: [{
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
                    phone: "+342 121 210"
                },
            ],
            selectedOffice: null,
        };
    },
};
</script>

<style scoped>
.contact-page {
  background: linear-gradient(135deg, #ffffff 0%, #ffffff 100%);
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
  width: 300px;
  height: 200px;
  transition: transform 0.3s ease;
}

.logo-image:hover {
  transform: scale(1.05);
}

/* Typography */
.page-title {
  font-family: 'Inter', 'Poppins', sans-serif;
  font-size: 2rem;
  font-weight: 800;
  text-align: center;
  color: #0c0c0c;
  margin-bottom: 1rem;
}

.section-title {
  font-family: 'Inter', 'Poppins', sans-serif;
  font-size: 2rem;
  font-weight: 700;
  text-align: center;
  color: #0f0f0f;
  margin-bottom: 2rem;
}

.highlight {
  background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.subtitle {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  line-height: 1.6;
  color: #555;
  text-align: center;
  margin: 2rem 0;
  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
}

/* Section Divider */
.section-divider {
  border-color: '';
  margin: 3rem 0;
  background: linear-gradient(90deg, transparent, #FFD700, transparent);
  height: 2px;
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
  max-width: 400px;
  width: 100%;
  height: auto;
  border-radius: 16px;
  overflow: hidden;
  
}

.branch-map {
  width: 100%;
  height: auto;
  display: block;
}

.branch-point {
  position: absolute;
  width: 15px;
  height: 15px;
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
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
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
  box-shadow: 0 4px 15px rgba(255, 215, 0, 0.3) !important;
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
  
  .subtitle {
    font-size: 1.1rem;
    padding: 0 1rem;
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
  
  .subtitle {
    font-size: 1rem;
    text-align: left;
    padding: 0 0.5rem;
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
  
  .office-info {
    margin: 1rem;
    padding: 1.5rem;
  }
  
  .office-name {
    font-size: 1.3rem;
  }
  
  .office-detail {
    font-size: 1rem;
  }
}

/* Additional Animations */
.branch-section {
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

/* Center container for branch map */
.center-container-Branch {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  width: 100%;
  margin: 0 auto;
}
</style>