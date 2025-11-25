<template>
  <div class="highlights-page">
    <v-container class="main-container">
      <!-- Header Section -->
      <section class="header-section">
        <h1 class="page-title" data-aos="fade-up" data-aos-duration="3000">
          OUR <span class="highlight">HIGHLIGHTS</span>
        </h1>
        <p class="intro-text" data-aos="fade-up" data-aos-duration="3000">
          Celebrating our memorable moments, achievements, and special events that showcase 
          our commitment to excellence in English education and community engagement.
        </p>
      </section>

      <!-- Highlights Carousel Section -->
      <section class="highlights-section">
        <div class="carousel-container">
          <swiper
            :modules="[Autoplay, Navigation, Pagination]"
            :slides-per-view="1"
            :space-between="30"
            :loop="true"
            :autoplay="{ delay: 4000, disableOnInteraction: false }"
            :pagination="{
              clickable: true,
              el: '.custom-pagination',
              renderBullet: renderCustomBullet
            }"
            :navigation="{ 
              nextEl: '.swiper-button-next', 
              prevEl: '.swiper-button-prev' 
            }"
            :breakpoints="{
              640: { slidesPerView: 1 },
              768: { slidesPerView: 2 },
              1024: { slidesPerView: 3 }
            }"
            class="highlights-swiper"
          >
            <swiper-slide v-for="(highlight, index) in highlights" :key="index">
              <v-card 
                class="highlight-card"
                data-aos="fade-up" 
                :data-aos-delay="(index + 1) * 100"
                data-aos-duration="3000"
              >
                <!-- Image Container -->
                <div class="image-container">
                  <v-img
                    :src="highlight.src"
                    :alt="highlight.title"
                    height="250"
                    cover
                    class="highlight-image"
                  ></v-img>
                  <div class="card-overlay">
                    <v-icon class="overlay-icon">mdi-star-circle</v-icon>
                    <span class="overlay-text">Event</span>
                  </div>
                </div>
                
                <!-- Card Content -->
                <v-card-text class="card-content">
                  <div class="highlight-badge">2025</div>
                  <h3 class="highlight-title">{{ highlight.title }}</h3>
                  <p class="highlight-description">
                    {{ highlight.description }}
                  </p>
                </v-card-text>
                
                <!-- Card Actions -->
                <v-card-actions class="card-actions">
                  <div class="social-icons">
                    <v-btn 
                      class="icon-btn"  
                      icon 
                      variant="text" 
                      size="small"
                      color="#FFD700"
                    >
                      <v-icon>mdi-facebook</v-icon>
                    </v-btn>
                    <v-btn 
                      class="icon-btn" 
                      icon 
                      variant="text" 
                      size="small"
                      color="#FFD700"
                    >
                      <v-icon>mdi-twitter</v-icon>
                    </v-btn>
                  </div>
                </v-card-actions>
              </v-card>
            </swiper-slide>
          </swiper>

          <!-- Custom Navigation -->
          <div class="carousel-navigation">
            <button class="swiper-button swiper-button-prev">
              <v-icon>mdi-chevron-left</v-icon>
            </button>
            
            <!-- Custom Pagination -->
            <div class="custom-pagination-wrapper">
              <div class="custom-pagination"></div>
            </div>
            
            <button class="swiper-button swiper-button-next">
              <v-icon>mdi-chevron-right</v-icon>
            </button>
          </div>
        </div>

        <!-- View All Button -->
        <div class="view-all-container">
          <v-btn class="view-all-btn" size="large">
            View All Highlights
            <v-icon right>mdi-arrow-right</v-icon>
          </v-btn>
        </div>
      </section>
    </v-container>
    
    <ArrowButton></ArrowButton>
    <ChatBot></ChatBot>
    <FooterPage></FooterPage>
  </div>
</template>

<script>
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Autoplay, Navigation, Pagination } from 'swiper/modules'
import 'swiper/css'
import 'swiper/css/navigation'
import 'swiper/css/pagination'
import ChatBot from './ChatBot.vue';
import ArrowButton from './ArrowButton.vue';
import AOS from 'aos';
import 'aos/dist/aos.css';

export default {
  name: 'NewsSliderPage',
  components: {
    Swiper,
    SwiperSlide,
    ChatBot,
    ArrowButton
  },
  data() {
    return {
      highlights: [
        { 
          src: "https://ik.imagekit.io/u3wbiya66/Highlights/1.jpg?updatedAt=1760438874157", 
          title: "Children's Day Awareness", 
          description: "Collaboration with Sri Lanka Police for a 'Good Touch and Bad Touch' session to help children learn, understand, and stay confident in their safety."
        },
        { 
          src: "https://ik.imagekit.io/u3wbiya66/Highlights/4.jpg?updatedAt=1760438873819", 
          title: "Happy Children's Day!", 
          description: "To our bright, kind, and curious little stars — keep dreaming big and believing in yourself every step of the way."
        },
        { 
          src: "https://ik.imagekit.io/u3wbiya66/Highlights/3.jpg?updatedAt=1760438873618", 
          title: "Honoring Our Everyday Heroes", 
          description: "To all our teachers who inspire, guide, and ignite dreams — we thank you today and always for your dedication and passion."
        },
        { 
          src: "https://ik.imagekit.io/u3wbiya66/Highlights/2.jpg?updatedAt=1760438875073", 
          title: "A Decade of Dedication", 
          description: "Marking ten years of excellence, our institute held a Pirith Chanting and Almsgiving ceremony with the blessings of the Maha Sangha."
        },
        { 
          src: "https://ik.imagekit.io/u3wbiya66/Highlights/5.jpg?updatedAt=1760438875365", 
          title: "Cambridge English Awards 2025", 
          description: "Celebrating our High Achievers and Top Achievers — a night of pride, passion, and excellence that truly lit up the stage."
        },
      ]
    }
  },
  methods: {
    viewHighlightDetails(highlight) {
      // You can implement highlight details view logic here
      console.log('Viewing highlight details:', highlight);
    }
  },
  setup() {
    const renderCustomBullet = (index, className) => {
      return `<span class="${className} custom-bullet">
                <span class="bullet-inner"></span>
              </span>`;
    };
    
    return {
      Autoplay,
      Navigation,
      Pagination,
      renderCustomBullet
    }
  },
  mounted() {
    AOS.init();
  }
}
</script>

<style scoped>
.highlights-page {
  background: linear-gradient(135deg, #0a0a0a 0%, #1a1a1a 100%);
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
  font-size: 3.5rem;
  font-weight: 800;
  color: #ffffff;
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
  font-size: 1.2rem;
  line-height: 1.7;
  color: #e0e0e0;
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
}

/* Highlights Section */
.highlights-section {
  padding: 2rem 0;
}

.carousel-container {
  position: relative;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.highlights-swiper {
  padding: 20px 10px 80px;
  width: 100%;
}

.highlights-swiper .swiper-slide {
  height: auto;
  display: flex;
}

/* Highlight Card */
.highlight-card {
  background: linear-gradient(135deg, #2d2d2d 0%, #1a1a1a 100%);
  border: 2px solid #333;
  border-radius: 20px;
  overflow: hidden;
  transition: all 0.4s ease;
  height: 100%;
  position: relative;
  display: flex;
  flex-direction: column;
}

.highlight-card::before {
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

.highlight-card:hover::before {
  left: 100%;
}

.highlight-card:hover {
  transform: translateY(-15px);
  border-color: #FFD700;
  box-shadow: 0 25px 50px rgba(255, 215, 0, 0.25);
}

/* Image Container */
.image-container {
  position: relative;
  overflow: hidden;
}

.highlight-image {
  transition: transform 0.4s ease;
  position: relative;
}

.highlight-card:hover .highlight-image {
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
  text-transform: uppercase;
}

/* Card Content */
.card-content {
  padding: 2rem;
  position: relative;
  z-index: 2;
  flex: 1;
  display: flex;
  flex-direction: column;
}

.highlight-badge {
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
  align-self: flex-start;
}

.highlight-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.4rem;
  font-weight: 700;
  color: #ffffff;
  line-height: 1.3;
  margin-bottom: 1rem;
  min-height: 3.5rem;
}

.highlight-description {
  font-family: 'Inter', sans-serif;
  font-size: 0.95rem;
  line-height: 1.6;
  color: #e0e0e0;
  margin-bottom: 0;
  flex: 1;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

/* Card Actions */
.card-actions {
  padding: 0 2rem 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
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
  flex: 1;
}

.learn-more-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(255, 215, 0, 0.4) !important;
  border-color: #FFD700 !important;
}

.social-icons {
  display: flex;
  gap: 0.5rem;
}

.icon-btn {
  transition: all 0.3s ease !important;
}

.icon-btn:hover {
  transform: translateY(-2px);
  background: rgba(255, 215, 0, 0.1) !important;
}

/* Carousel Navigation */
.carousel-navigation {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 24px;
  position: relative;
}

.swiper-button {
  width: 56px;
  height: 56px;
  border-radius: 50%;
  background: linear-gradient(135deg, #2d2d2d 0%, #1a1a1a 100%);
  border: 2px solid #333;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.3s ease;
  color: #FFD700;
  position: relative;
  z-index: 10;
}

.swiper-button:hover {
  background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%);
  color: #000000;
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(255, 215, 0, 0.3);
  border-color: #FFD700;
}

/* Pagination */
.custom-pagination-wrapper {
  position: absolute;
  bottom: -60px;
  left: 0;
  width: 100%;
  display: flex;
  justify-content: center;
}

:deep(.custom-pagination) {
  display: flex;
  justify-content: center;
  gap: 8px;
  position: relative;
  z-index: 5;
}

:deep(.custom-bullet) {
  width: 12px;
  height: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

:deep(.bullet-inner) {
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: #333;
  transition: all 0.3s ease;
}

:deep(.swiper-pagination-bullet-active .bullet-inner) {
  width: 12px;
  height: 12px;
  background: #FFD700;
  box-shadow: 0 0 0 2px rgba(255, 215, 0, 0.3);
}

/* View All Button */
.view-all-container {
  text-align: center;
  margin-top: 4rem;
}

.view-all-btn {
  background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%) !important;
  color: #000000 !important;
  font-weight: 700 !important;
  font-family: 'Inter', sans-serif !important;
  border: 2px solid transparent !important;
  border-radius: 30px !important;
  padding: 1rem 3rem !important;
  text-transform: none !important;
  transition: all 0.3s ease !important;
  font-size: 1.1rem !important;
  box-shadow: 0 8px 25px rgba(255, 215, 0, 0.3) !important;
}

.view-all-btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 12px 30px rgba(255, 215, 0, 0.4) !important;
  border-color: #FFD700 !important;
}

/* Floating Animation */
.highlight-card {
  animation: float 6s ease-in-out infinite;
}

.highlight-card:nth-child(odd) {
  animation-delay: 0s;
}

.highlight-card:nth-child(even) {
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

.highlight-card:hover {
  animation: none;
}

/* Additional Effects */
.highlight-card::after {
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

.highlight-card:hover::after {
  opacity: 0.3;
}

/* Scroll Animation Enhancement */
.highlights-section {
  perspective: 1000px;
}

.highlight-card {
  transform-style: preserve-3d;
}

/* Responsive Design */
@media (max-width: 960px) {
  .page-title {
    font-size: 2.8rem;
  }
  
  .intro-text {
    font-size: 1.1rem;
  }
  
  .highlight-title {
    font-size: 1.2rem;
    min-height: auto;
  }
  
  .highlights-swiper {
    padding: 20px 10px 70px;
  }
  
  .card-actions {
    flex-direction: column;
    align-items: stretch;
    gap: 1rem;
  }
  
  .social-icons {
    justify-content: center;
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
  
  .highlight-title {
    font-size: 1.1rem;
  }
  
  .highlight-description {
    font-size: 0.9rem;
  }
  
  .card-actions {
    padding: 0 1.5rem 1.5rem;
  }
  
  .carousel-container {
    padding: 0 16px;
  }
  
  .carousel-navigation {
    gap: 16px;
  }
  
  .swiper-button {
    width: 48px;
    height: 48px;
  }
  
  .custom-pagination-wrapper {
    bottom: -50px;
  }
  
  .view-all-btn {
    padding: 0.875rem 2.5rem !important;
    font-size: 1rem !important;
  }
}
</style>