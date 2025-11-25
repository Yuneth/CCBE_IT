<template>
  <div class="awards-page">
    <v-container class="main-container">
      <!-- Header Section -->
      <section class="header-section">
        <h1 class="page-title" data-aos="fade-up" data-aos-duration="3000">
          OUR <span class="highlight">AWARDS</span>
        </h1>
        <p class="intro-text" data-aos="fade-up" data-aos-duration="3000">
          Celebrating our achievements and recognition in English language education. 
          These prestigious awards reflect our commitment to excellence, innovation, 
          and outstanding performance in delivering world-class English education.
        </p>
      </section>

      <!-- Awards Carousel Section -->
      <section class="awards-section">
        <div class="carousel-container">
          <swiper
            :modules="[Autoplay, Navigation, Pagination]"
            :slides-per-view="1"
            :space-between="30"
            :loop="true"
            :autoplay="{
              delay: 4000,
              disableOnInteraction: false,
              pauseOnMouseEnter: true
            }"
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
              640: {
                slidesPerView: 1,
                spaceBetween: 20
              },
              768: {
                slidesPerView: 2,
                spaceBetween: 30
              },
              1024: {
                slidesPerView: 3,
                spaceBetween: 30
              }
            }"
            class="awards-carousel"
          >
            <swiper-slide v-for="(award, index) in awards" :key="index">
              <v-card 
                class="award-card" 
                data-aos="fade-up" 
                :data-aos-delay="(index + 1) * 100"
                data-aos-duration="3000"
              >
                <!-- Image Container -->
                <div class="image-container">
                  <v-img
                    :src="award.src"
                    :alt="award.title"
                    height="250"
                    cover
                    class="award-image"
                  ></v-img>
                  <div class="card-overlay">
                    <v-icon class="overlay-icon">mdi-trophy</v-icon>
                    <span class="overlay-text">{{ award.category }}</span>
                  </div>
                </div>
                
                <!-- Card Content -->
                <v-card-text class="card-content">
                  <div class="award-badge">{{ award.year }}</div>
                  <h3 class="award-title">{{ award.title }}</h3>
                  <p class="award-description">
                    {{ award.description }}
                  </p>
                </v-card-text>
                
                <!-- Card Actions -->
                <v-card-actions class="card-actions">
                   <div class="programme-badge">British Council</div>
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
      </section>
    </v-container>
  </div>
</template>

<script>
import { Swiper, SwiperSlide } from 'swiper/vue';
import { Autoplay, Navigation, Pagination } from 'swiper/modules';
import 'swiper/css';
import 'swiper/css/navigation';
import 'swiper/css/pagination';
import 'swiper/css/autoplay';

export default {
  name: "AwardsSection",
  components: {
    Swiper,
    SwiperSlide
  },
  data() {
    return {
      awards: [
        { 
          src: "https://ik.imagekit.io/u3wbiya66/Awards/Platinum.jpg?updatedAt=1757935994777", 
          title: "Excellence Beyond Gold", 
          description: "Awarded by the British Council for outstanding performance and exclusivity as a Cambridge English registration centre.",
          year: "2025",
          category: "Platinum"
        },
        { 
          src: "https://ik.imagekit.io/u3wbiya66/Awards/Gold.jpg?updatedAt=1757647128110", 
          title: "Excellence in Performance", 
          description: "Honoured by the British Council for exceptional achievements as a Cambridge English registration centre.",
          year: "2024",
          category: "Gold"
        },
        { 
          src: "https://ik.imagekit.io/u3wbiya66/Awards/Southern.jpg?updatedAt=1757647127985", 
          title: "Highest Regional Contribution", 
          description: "Recognized by the British Council for the highest regional contribution in Cambridge English registrations.",
          year: "2025",
          category: "Regional"
        },
        { 
          src: "https://ik.imagekit.io/u3wbiya66/Awards/Star.jpg?updatedAt=1757937143732", 
          title: "Emerging Star of the Year Award", 
          description: "Recognized as an Emerging Star at the 2023 Annual Coordinators' Conference for outstanding growth in Cambridge English.",
          year: "2023",
          category: "Emerging"
        },
      ],
    };
  },
  methods: {
    // viewAwardDetails(award) {
    //   // You can implement award details view logic here
    //   console.log('Viewing award details:', award);
    // }
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
    };
  }
}
</script>

<style scoped>
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

.awards-page {
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

/* Awards Section */
.awards-section {
  padding: 2rem 0;
}

.carousel-container {
  position: relative;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.awards-carousel {
  padding: 20px 10px 80px;
  width: 100%;
}

.awards-carousel .swiper-slide {
  height: auto;
  display: flex;
}

/* Award Card */
.award-card {
  background: linear-gradient(135deg, #2d2d2d 0%, #1a1a1a 100%);
  border: 2px solid #333;
  border-radius: 20px;
  overflow: hidden;
  transition: all 0.4s ease;
  height: 100%;
  position: relative;
  margin-bottom: 2rem;
  display: flex;
  flex-direction: column;
}

.award-card::before {
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

.award-card:hover::before {
  left: 100%;
}

.award-card:hover {
  transform: translateY(-15px);
  border-color: #FFD700;
  box-shadow: 0 25px 50px rgba(255, 215, 0, 0.25);
}

/* Image Container */
.image-container {
  position: relative;
  overflow: hidden;
}

.award-image {
  transition: transform 0.4s ease;
  position: relative;
}

.award-card:hover .award-image {
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

.award-badge {
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

.award-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.4rem;
  font-weight: 700;
  color: #ffffff;
  line-height: 1.3;
  margin-bottom: 1rem;
  min-height: 3.5rem;
}

.award-description {
  font-family: 'Inter', sans-serif;
  font-size: 0.95rem;
  line-height: 1.6;
  color: #e0e0e0;
  margin-bottom: 0;
  flex: 1;
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
.award-card {
  animation: float 6s ease-in-out infinite;
}

.award-card:nth-child(odd) {
  animation-delay: 0s;
}

.award-card:nth-child(even) {
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

.award-card:hover {
  animation: none;
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

/* Additional Effects */
.award-card::after {
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

.award-card:hover::after {
  opacity: 0.3;
}

/* Scroll Animation Enhancement */
.awards-section {
  perspective: 1000px;
}

.award-card {
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
  
  .award-title {
    font-size: 1.2rem;
    min-height: auto;
  }
  
  .awards-carousel {
    padding: 20px 10px 70px;
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
  
  .award-title {
    font-size: 1.1rem;
  }
  
  .award-description {
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
}
</style>