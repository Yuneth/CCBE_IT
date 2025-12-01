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
            :space-between="20"
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
                    height="200"
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
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
}

/* Highlights Section */
.highlights-section {
  padding: 1rem 0;
}

.carousel-container {
  position: relative;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 15px;
}

.highlights-swiper {
  padding: 15px 5px 60px;
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
  border-radius: 15px;
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
  transform: translateY(-10px);
  border-color: #FFD700;
  box-shadow: 0 20px 40px rgba(255, 215, 0, 0.25);
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
  top: 0.75rem;
  right: 0.75rem;
  background: linear-gradient(135deg, rgba(255, 215, 0, 0.9) 0%, rgba(255, 165, 0, 0.9) 100%);
  padding: 0.4rem 0.8rem;
  border-radius: 15px;
  display: flex;
  align-items: center;
  gap: 0.4rem;
  backdrop-filter: blur(10px);
}

.overlay-icon {
  color: #000000 !important;
  font-size: 1rem !important;
}

.overlay-text {
  font-family: 'Inter', sans-serif;
  font-size: 0.7rem;
  font-weight: 600;
  color: #000000;
  text-transform: uppercase;
}

/* Card Content */
.card-content {
  padding: 1.5rem;
  position: relative;
  z-index: 2;
  flex: 1;
  display: flex;
  flex-direction: column;
}

.highlight-badge {
  font-family: 'Inter', sans-serif;
  font-size: 0.7rem;
  font-weight: 700;
  color: #FFD700;
  background: rgba(255, 215, 0, 0.1);
  padding: 0.3rem 0.8rem;
  border-radius: 12px;
  display: inline-block;
  margin-bottom: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  align-self: flex-start;
}

.highlight-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  font-weight: 700;
  color: #ffffff;
  line-height: 1.3;
  margin-bottom: 0.75rem;
  min-height: 2.8rem;
}

.highlight-description {
  font-family: 'Inter', sans-serif;
  font-size: 0.9rem;
  line-height: 1.5;
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
  padding: 0 1.5rem 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 0.75rem;
}

.learn-more-btn {
  background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%) !important;
  color: #000000 !important;
  font-weight: 600 !important;
  font-family: 'Inter', sans-serif !important;
  border: 2px solid transparent !important;
  border-radius: 20px !important;
  padding: 0.6rem 1.5rem !important;
  text-transform: none !important;
  transition: all 0.3s ease !important;
  flex: 1;
}

.learn-more-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 15px rgba(255, 215, 0, 0.4) !important;
  border-color: #FFD700 !important;
}

.social-icons {
  display: flex;
  gap: 0.4rem;
}

.icon-btn {
  transition: all 0.3s ease !important;
}

.icon-btn:hover {
  transform: translateY(-1px);
  background: rgba(255, 215, 0, 0.1) !important;
}

/* Carousel Navigation */
.carousel-navigation {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
  position: relative;
}

.swiper-button {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background: linear-gradient(135deg, white 0%, white 100%);
  
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.3);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.3s ease;
  color: black;
  position: relative;
  z-index: 10;
  margin: 0 15px; 
}

.swiper-button:hover {
  background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%);
  color: #000000;
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(255, 215, 0, 0.3);
  border-color: #FFD700;
}

/* Pagination */
.custom-pagination-wrapper {
  position: absolute;
  bottom: -50px;
  left: 0;
  width: 100%;
  display: flex;
  justify-content: center;
}

:deep(.custom-pagination) {
  display: flex;
  justify-content: center;
  gap: 6px;
  position: relative;
  z-index: 5;
}

:deep(.custom-bullet) {
  width: 10px;
  height: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

:deep(.bullet-inner) {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: #333;
  transition: all 0.3s ease;
}

:deep(.swiper-pagination-bullet-active .bullet-inner) {
  width: 10px;
  height: 10px;
  background: #FFD700;
  box-shadow: 0 0 0 2px rgba(255, 215, 0, 0.3);
}

/* View All Button */
.view-all-container {
  text-align: center;
  margin-top: 3rem;
}

.view-all-btn {
  background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%) !important;
  color: #000000 !important;
  font-weight: 700 !important;
  font-family: 'Inter', sans-serif !important;
  border: 2px solid transparent !important;
  border-radius: 25px !important;
  padding: 0.875rem 2.5rem !important;
  text-transform: none !important;
  transition: all 0.3s ease !important;
  font-size: 1rem !important;
  box-shadow: 0 6px 20px rgba(255, 215, 0, 0.3) !important;
}

.view-all-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 25px rgba(255, 215, 0, 0.4) !important;
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
    transform: translateY(-8px);
  }
}

.highlight-card:hover {
  animation: none;
}

/* Additional Effects */
.highlight-card::after {
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
    font-size: 2.2rem;
  }
  
  .intro-text {
    font-size: 1rem;
  }
  
  .highlight-title {
    font-size: 1rem;
    min-height: 2.5rem;
  }
  
  .highlights-swiper {
    padding: 15px 5px 50px;
  }
  
  .card-actions {
    flex-direction: column;
    align-items: stretch;
    gap: 0.75rem;
  }
  
  .social-icons {
    justify-content: center;
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
  
  .card-content {
    padding: 1.25rem;
  }
  
  .highlight-title {
    font-size: 0.95rem;
  }
  
  .highlight-description {
    font-size: 0.85rem;
  }
  
  .card-actions {
    padding: 0 1.25rem 0.75rem;
  }
  
  .carousel-container {
    padding: 0 10px;
  }
  
  .carousel-navigation {
    gap: 15px;
  }
  
  .swiper-button {
    width: 42px;
    height: 42px;
  }
  
  .custom-pagination-wrapper {
    bottom: -45px;
  }
  
  .view-all-btn {
    padding: 0.75rem 2rem !important;
    font-size: 0.95rem !important;
  }
  
  .highlight-image {
    height: 180px;
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
  
  .card-content {
    padding: 1rem;
  }
  
  .highlight-title {
    font-size: 0.9rem;
    min-height: auto;
  }
  
  .highlight-description {
    font-size: 0.8rem;
  }
  
  .card-actions {
    padding: 0 1rem 0.5rem;
  }
  
  .carousel-container {
    padding: 0 5px;
  }
  
  .carousel-navigation {
    gap: 12px;
  }
  
  .swiper-button {
    width: 38px;
    height: 38px;
  }
  
  .custom-pagination-wrapper {
    bottom: -40px;
  }
  
  .view-all-btn {
    padding: 0.625rem 1.75rem !important;
    font-size: 0.9rem !important;
  }
  
  .highlight-badge {
    font-size: 0.65rem;
    padding: 0.25rem 0.6rem;
  }
  
  .overlay-text {
    font-size: 0.6rem;
  }
  
  .overlay-icon {
    font-size: 0.8rem !important;
  }
  
  .card-overlay {
    padding: 0.3rem 0.6rem;
  }
  
  .highlight-image {
    height: 160px;
  }
}

/* Touch-friendly improvements */
@media (hover: none) {
  .highlight-card:hover {
    transform: none;
  }
  
  .highlight-card:hover .highlight-image {
    transform: none;
  }
  
  .swiper-button:hover {
    transform: none;
  }
  
  .view-all-btn:hover {
    transform: none;
  }
}

/* Reduced motion support */
@media (prefers-reduced-motion: reduce) {
  .highlight-card {
    animation: none;
  }
  
  .highlight-card:hover .highlight-image {
    transform: none;
  }
}
</style>