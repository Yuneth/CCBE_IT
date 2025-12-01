<template>
  <div class="kalutara-branch-page">
    <NavBar></NavBar>
    <v-container class="main-container">
      <!-- Header Section -->
      <section class="header-section">
        <h1 class="page-title" data-aos="fade-up" data-aos-duration="3000">
          Welcome to <span class="highlight">Kalutara College</span>
        </h1>
      </section>

      <v-divider class="section-divider"></v-divider>

      <!-- Contact Section -->
      <section class="content-section">
        <h2 class="section-title" data-aos="fade-up" data-aos-duration="3000">CONTACT</h2>
        <v-row justify="center" class="fill-height">
          <v-col cols="12" md="8" lg="6" class="branch-card mt-3">
            <div class="branch-info">
              <p class="contact-item">
                <v-icon class="address-icon">mdi-map-marker</v-icon>
                No 85, Maha Waskaduwa, 12580
              </p>
              <p class="contact-item">
                <v-icon class="contact-icon map-icon" @click="openGoogleMaps" style="cursor: pointer;">mdi-map-marker</v-icon>
                Google Map
              </p>
              <p class="contact-item">
                <v-icon class="contact-icon">mdi-phone</v-icon>
                <a href="tel:0342121210" class="contact-link">0342 121 210</a>
              </p>
              <p class="contact-item">
                <v-icon class="contact-icon">mdi-email</v-icon>
                <a href="mailto:kalutaraccbe@gmail.com" class="contact-link">kalutaraccbe@gmail.com</a>
              </p>
              <div class="social-links">
                <a href="https://www.facebook.com/profile.php?id=61575104380343" target="_blank" rel="noopener noreferrer" class="social-link">
                  <v-icon class="social-icon" color="#1877F2">mdi-facebook</v-icon>
                </a>
                <a href="https://www.youtube.com/@cambridgecollegeofbritishe9360" target="_blank" rel="noopener noreferrer" class="social-link">
                  <v-icon class="social-icon" color="#FF0000">mdi-youtube</v-icon>
                </a>
                <a href="https://www.instagram.com/ccbeamb" target="_blank" rel="noopener noreferrer" class="social-link">
                  <v-icon class="social-icon" color="#E4405F">mdi-instagram</v-icon>
                </a>
                <a href="https://www.tiktok.com/@cambridgecollege9" target="_blank" rel="noopener noreferrer" class="social-link">
                  <v-icon class="social-icon" color="#000000">mdi-music-note</v-icon>
                </a>
              </div>
              <a href="https://wa.me/+94711715666?text=Hello%20Kalutara%20Branch" target="_blank" class="whatsapp-button">
                <img src="https://upload.wikimedia.org/wikipedia/commons/6/6b/WhatsApp.svg" alt="WhatsApp" />
                <strong>Chat Via WhatsApp</strong>
              </a>
            </div>
          </v-col>
        </v-row>
      </section>

      <v-divider class="section-divider"></v-divider>

      <!-- Gallery Section -->
      <section class="content-section">
        <h2 class="section-title" data-aos="fade-up" data-aos-duration="3000">Gallery</h2>
        
        <div class="gallery-container">
          <v-row>
            <!-- Virtual Tour Items -->
            <v-col v-for="(item, index) in contentItems" :key="'tour-' + index" cols="12" sm="6" md="4">
              <v-card class="gallery-card" data-aos="fade-up" :data-aos-duration="1000 + (index * 200)">
                <iframe 
                  width="100%" 
                  height="200px" 
                  frameborder="0" 
                  :src="item.iframeSrc" 
                  allowfullscreen
                  class="gallery-iframe"
                  loading="lazy"
                ></iframe>
                <v-card-subtitle class="gallery-subtitle">
                  {{ item.subtitle }}
                </v-card-subtitle>
                <v-card-text class="gallery-description">
                  <div>{{ item.description }}</div>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
          
          <!-- Image Gallery -->
          <v-row>
            <v-col 
              v-for="(image, index) in images" 
              :key="'image-' + index" 
              cols="12" sm="6" md="4" lg="3"
            >
              <v-card class="image-card" data-aos="zoom-in" :data-aos-duration="1200 + (index * 200)">
                <v-img 
                  :src="image.src" 
                  aspect-ratio="1" 
                  class="gallery-image" 
                  cover
                  gradient="to bottom, rgba(0,0,0,0.1), rgba(0,0,0,0.3)"
                >
                  <template v-slot:placeholder>
                    <v-row align="center" class="fill-height ma-0" justify="center">
                      <v-progress-circular color="grey-lighten-5" indeterminate></v-progress-circular>
                    </v-row>
                  </template>
                </v-img>
              </v-card>
            </v-col>
          </v-row>
        </div>
      </section>
    </v-container>
    
    <ArrowButton></ArrowButton>
    <ChatBot></ChatBot>
    <FooterPage></FooterPage>
  </div>
</template>

<script>
import NavBar from '../NavBar.vue';
import FooterPage from '../FooterPage.vue';
import ChatBot from '../ChatBot.vue'
import ArrowButton from '../ArrowButton.vue';

// AOS Transition
import AOS from 'aos';
import 'aos/dist/aos.css';

export default {
  name: 'KalutaraBranch',
  components: {
    NavBar,
    FooterPage,
    ChatBot,
    ArrowButton
  },
  data() {
    return {
      contentItems: [{
        iframeSrc: "https://momento360.com/e/u/4e0567c60ff04f2399663f0331bf84d5?utm_campaign=embed&utm_source=other&heading=0&pitch=0&field-of-view=75&size=medium&display-plan=true",
        subtitle: "Explore Kalutara Branch in 360",
        description: "Immerse yourself in a virtual tour of our vibrant learning spaces at the Kalutara Branch.",
      }, 
      {
        iframeSrc: "https://momento360.com/e/u/494aacf6a10642b983445a4a13f7e490?utm_campaign=embed&utm_source=other&heading=0&pitch=0&field-of-view=98&size=medium&display-plan=true",
        subtitle: "360° Virtual Tour of Smart Classroom",
        description: "Explore the innovative learning environment equipped with cutting-edge technology for interactive education.",
      }, 
      {
        iframeSrc: "https://momento360.com/e/u/e31cd13a27db483d8795e8ce1f822f30?utm_campaign=embed&utm_source=other&heading=0&pitch=0&field-of-view=75&size=medium&display-plan=true",
        subtitle: "360° Virtual Tour of the Auditorium",
        description: "Experience every angle of our state-of-the-art auditorium from the comfort of your screen.",
      }, 
    ],
      images: [
        {
          src: 'https://ik.imagekit.io/u3wbiya66/Ambalangoda/Kalutara.jpg?updatedAt=1746770889100',
        },
        {
          src: 'https://ik.imagekit.io/u3wbiya66/PXL_20250117_094732824.jpg?updatedAt=1737789273936',
        },
        {
          src: 'https://ik.imagekit.io/u3wbiya66/Ambalangoda/CV8.jpg?updatedAt=1737874746020',
        },
        {
          src: 'https://images.unsplash.com/photo-1523050854058-8df90110c9f1?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80',
        }
      ],
    };
  },
  mounted() {
    window.scrollTo(0, 0);
    AOS.init();
  },
  methods: {
    openGoogleMaps() {
      window.open('https://maps.app.goo.gl/XyQqiD5g3hwMpMtXA?g_st=com.google.maps.preview.copy', '_blank');
    },
  },
};
</script>

<style scoped>
.kalutara-branch-page {
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
  font-family: "Inter", "Poppins", sans-serif;
  font-size: 2rem;
  font-weight: 800;
  color: black;
  margin-bottom: 1.5rem;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.highlight {
  background: linear-gradient(135deg, #ffd700 0%, #ffa500 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  position: relative;
}

.highlight::after {
  content: "";
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, #ffd700, transparent);
  opacity: 0.7;
}

/* Section Divider */
.section-divider {
  border-color: '';
  margin: 3rem 0;
  background: linear-gradient(90deg, transparent, #ffd700, transparent);
  height: 2px;
}

/* Content Sections */
.content-section {
  margin: 3rem 0;
}

.section-title {
  font-family: "Inter", "Poppins", sans-serif;
  font-size: 2rem;
  font-weight: 700;
  text-align: center;
  color: black;
  margin-bottom: 2rem;
}

/* Contact Section */
.branch-card {
  background: linear-gradient(135deg, white 0%, white 100%);
  border-radius: 16px;
  padding: 2.5rem;
  margin: 1rem auto;
  transition: all 0.4s ease;
  position: relative;
  overflow: hidden;
  text-align: center;
}

.branch-card::before {
  content: "";
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    90deg,
    transparent,
    rgba(255, 215, 0, 0.1),
    transparent
  );
  transition: left 0.6s ease;
  z-index: 1;
}

.branch-card:hover::before {
  left: 100%;
}

.branch-info {
  position: relative;
  z-index: 2;
}

.contact-item {
  font-family: "Inter", sans-serif;
  font-size: 1.1rem;
  color: black;
  margin: 1.2rem 0;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.8rem;
}

.contact-icon {
  color: blue;
  font-size: 1.4rem;
  flex-shrink: 0;
}

.address-icon {
  color: black;
  font-size: 1.4rem;
  flex-shrink: 0;
}

.map-icon {
  cursor: pointer;
  transition: all 0.3s ease;
  color:green;
}

.map-icon:hover {
  color: #ffa500;
  transform: scale(1.1);
}

.contact-link {
  color: black;
  text-decoration: none;
  transition: all 0.3s ease;
  font-weight: 500;
}

.contact-link:hover {
  color: #ffa500;
  text-decoration: underline;
}

.social-links {
  display: flex;
  justify-content: center;
  gap: 1.2rem;
  margin: 2rem 0;
}

.social-link {
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.1);
}

.social-link:hover {
  transform: scale(1.2);
  background: rgba(255, 215, 0, 0.2);
}

.social-icon {
  font-size: 1.8rem !important;
}

/* WhatsApp Button */
.whatsapp-button {
  display: inline-flex;
  align-items: center;
  background: linear-gradient(135deg, #25d366 0%, #128C7E 100%);
  color: white;
  padding: 14px 28px;
  border-radius: 30px;
  text-decoration: none;
  font-size: 1.1rem;
  font-weight: 600;
  box-shadow: 0 6px 20px rgba(37, 211, 102, 0.4);
  transition: all 0.3s ease;
  margin-top: 1.5rem;
  border: 2px solid transparent;
}

.whatsapp-button img {
  width: 32px;
  height: 32px;
  margin-right: 12px;
  border-radius: 50%;
}

.whatsapp-button:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 30px rgba(37, 211, 102, 0.6);
  background: linear-gradient(135deg, #128C7E 0%, #25d366 100%);
  border-color: #fff;
}

/* Gallery Section */
.gallery-container {
  margin-top: 2rem;
}

.gallery-card {
  background: linear-gradient(135deg, #2d2d2d 0%, #1a1a1a 100%);
  border: 2px solid #333;
  border-radius: 16px;
  transition: all 0.4s ease;
  position: relative;
  overflow: hidden;
  height: 100%;
  margin-bottom: 1.5rem;
}

.gallery-card::before {
  content: "";
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    90deg,
    transparent,
    rgba(255, 215, 0, 0.1),
    transparent
  );
  transition: left 0.6s ease;
  z-index: 1;
}

.gallery-card:hover::before {
  left: 100%;
}

.gallery-card:hover {
  transform: translateY(-8px);
  border-color: #ffd700;
  box-shadow: 0 15px 35px rgba(255, 215, 0, 0.25);
}

.gallery-iframe {
  border-radius: 12px 12px 0 0;
  border: none;
}

.gallery-subtitle {
  font-family: "Inter", sans-serif;
  font-size: 1.2rem !important;
  font-weight: 700 !important;
  color: #ffd700 !important;
  text-align: center;
  margin-top: 1rem;
  padding: 0 1rem;
}

.gallery-description {
  font-family: "Inter", sans-serif;
  font-size: 1rem;
  color: #e0e0e0;
  text-align: center;
  line-height: 1.6;
  padding: 0 1rem 1rem;
}

.image-card {
  background: linear-gradient(135deg, #2d2d2d 0%, #1a1a1a 100%);
  border: 2px solid #333;
  border-radius: 16px;
  transition: all 0.4s ease;
  position: relative;
  overflow: hidden;
  margin-bottom: 1.5rem;
}

.image-card::before {
  content: "";
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    90deg,
    transparent,
    rgba(255, 215, 0, 0.1),
    transparent
  );
  transition: left 0.6s ease;
  z-index: 1;
}

.image-card:hover::before {
  left: 100%;
}

.image-card:hover {
  transform: translateY(-8px);
  border-color: #ffd700;
  box-shadow: 0 15px 35px rgba(255, 215, 0, 0.25);
}

.gallery-image {
  border-radius: 12px;
  transition: transform 0.4s ease;
}

.image-card:hover .gallery-image {
  transform: scale(1.05);
}

/* Floating Animation */
.branch-card, .gallery-card, .image-card {
  animation: float 6s ease-in-out infinite;
}

.branch-card:nth-child(odd), .gallery-card:nth-child(odd), .image-card:nth-child(odd) {
  animation-delay: 0s;
}

.branch-card:nth-child(even), .gallery-card:nth-child(even), .image-card:nth-child(even) {
  animation-delay: 1.5s;
}

@keyframes float {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-8px);
  }
}

.branch-card:hover, .gallery-card:hover, .image-card:hover {
  animation: none;
}

/* Additional Effects */
.branch-card::after, .gallery-card::after, .image-card::after {
  content: "";
  position: absolute;
  top: -2px;
  left: -2px;
  right: -2px;
  bottom: -2px;
  background: linear-gradient(45deg, #ffd700, #ffa500, #ffd700);
  border-radius: 18px;
  z-index: -1;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.branch-card:hover::after, .gallery-card:hover::after, .image-card:hover::after {
  opacity: 0.3;
}

/* Responsive Design */
@media (max-width: 960px) {
  .page-title {
    font-size: 2.2rem;
  }

  .section-title {
    font-size: 1.8rem;
  }

  .contact-item {
    font-size: 1rem;
  }

  .branch-card {
    padding: 2rem;
  }
}

@media (max-width: 600px) {
  .page-title {
    font-size: 1.8rem;
  }

  .section-title {
    font-size: 1.5rem;
  }

  .header-section {
    padding: 2rem 0;
  }

  .contact-item {
    font-size: 0.9rem;
    flex-direction: column;
    text-align: center;
    gap: 0.5rem;
    margin: 1rem 0;
  }

  .social-links {
    gap: 0.8rem;
  }

  .social-link {
    width: 45px;
    height: 45px;
  }

  .social-icon {
    font-size: 1.6rem !important;
  }

  .whatsapp-button {
    padding: 12px 24px;
    font-size: 1rem;
  }

  .whatsapp-button img {
    width: 28px;
    height: 28px;
  }

  .branch-card {
    padding: 1.5rem;
  }
}

/* Content Animation Enhancement */
.content-section {
  perspective: 1000px;
}
</style>