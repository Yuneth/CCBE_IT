<template>
  <div class="testimonials-page">
    <v-container class="main-container">
      <!-- Header Section -->
      <section class="header-section">
        <!-- <h1 class="page-title" data-aos="fade-up" data-aos-duration="3000">
          STUDENT <span class="highlight">TESTIMONIALS</span>
        </h1> -->
        <p class="intro-text" data-aos="fade-up" data-aos-duration="3000">
          Hear from our students about their transformative learning experiences. 
          These testimonials reflect the impact of our comprehensive English programmes 
          and the success stories that inspire us to continue delivering excellence.
        </p>
      </section>

      <!-- Testimonials Carousel Section -->
      <section class="testimonials-section">
        <div class="carousel-container">
          <div class="testimonials-carousel">
            <button @click="prevSlide" class="nav-button nav-left">
              <v-icon>mdi-chevron-left</v-icon>
            </button>
            
            <div class="testimonials-grid">
              <div 
                v-for="(testimonial, index) in visibleTestimonials" 
                :key="index" 
                class="testimonial-card"
                data-aos="fade-up" 
                :data-aos-delay="(index + 1) * 100"
                data-aos-duration="3000"
              >
                <!-- Image Container -->
                <div class="image-container">
                  <img 
                    :src="testimonial.userAvatar" 
                    alt="User Avatar" 
                    class="testimonial-avatar" 
                  />
                  <div class="card-overlay">
                    <v-icon class="overlay-icon">mdi-account</v-icon>
                    <span class="overlay-text">{{ testimonial.userRole }}</span>
                  </div>
                </div>
                
                <!-- Card Content -->
                <div class="card-content">
                  <div class="testimonial-badge">Student</div>
                  <h3 class="testimonial-title">{{ testimonial.userName }}</h3>
                  <p class="testimonial-text">
                    "{{ testimonial.text }}"
                  </p>
                </div>
                
                <!-- Card Actions -->
                <div class="card-actions">
                  <v-btn 
                    class="learn-more-btn" 
                    variant="outlined" 
                    :href="testimonial.link" 
                    target="_blank" 
                    rel="noopener noreferrer"
                  >
                    Watch Video
                    <v-icon right>mdi-play-circle</v-icon>
                  </v-btn>
                </div>
              </div>
            </div>
            
            <button @click="nextSlide" class="nav-button nav-right">
              <v-icon>mdi-chevron-right</v-icon>
            </button>
          </div>

          <!-- Pagination Dots -->
          <div class="pagination-dots">
            <button 
              v-for="page in totalPages" 
              :key="page" 
              :class="['pagination-dot', { active: currentSlide === (page - 1) * testimonialsPerPage }]"
              @click="goToPage(page)"
            ></button>
          </div>
        </div>
      </section>

      <!-- Video Section -->
      <section class="video-section">
        <h2 class="section-title" data-aos="fade-up" data-aos-duration="3000">
          WATCH THEIR <span class="highlight">STORIES</span>
        </h2>
        <p class="section-subtitle" data-aos="fade-up" data-aos-duration="3000">
          Experience the journey through their own words
        </p>
        
        <v-row class="videos-grid">
          <v-col 
            v-for="(video, index) in videos" 
            :key="index" 
            cols="12" 
            md="6" 
            lg="4"
            data-aos="fade-up" 
            :data-aos-delay="(index + 1) * 100"
            data-aos-duration="3000"
          >
            <div class="video-card">
              <div class="video-container">
                <iframe 
                  :src="video.link" 
                  frameborder="0" 
                  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
                  allowfullscreen
                  class="video-iframe"
                ></iframe>
              </div>
            </div>
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
import ChatBot from './ChatBot.vue';
import ArrowButton from './ArrowButton.vue';
import AOS from 'aos';
import 'aos/dist/aos.css';
import StudentIcon from '@/assets/icons/User Ave.png'

export default {
  name: 'TestimonialsPage',
  components: {
    ChatBot,
    ArrowButton
  },
  data() {
    return {
      currentSlide: 0,
      testimonialsPerPage: 3,
      testimonials: [
        {
          text: "English became as natural to me as my mother tongue. Apart from the syllabus, they taught me many valuable life lessons and prepared me with the armor of English.",
          userName: "Thilina Chamod",
          userRole: "Key Intake",
          userAvatar: StudentIcon,
          link: "https://www.youtube.com/watch?v=Xb9PO6GwpYE&list=PLnra1_c-Y6TiQiBCk1clsy80PVAp9Z1q3&index=1"
        },
        {
          text: "I was able to improve my language skills, including reading, writing, listening, and speaking. The practice exams helped us achieve good grades in the British Council exam.",
          userName: "Rishini Hansani",
          userRole: "IKEY002",
          userAvatar: StudentIcon,
          link: "https://www.youtube.com/watch?v=QgsrB9n_EVQ&list=PLnra1_c-Y6TiQiBCk1clsy80PVAp9Z1q3&index=2"
        },
        {
          text: "Through the four-month course, we were able to improve the four essential language skills: reading, writing, listening, and speaking.",
          userName: "Hasanga Bingusara",
          userRole: "IKEY002",
          userAvatar: StudentIcon,
          link: "https://www.youtube.com/watch?v=X3URJtpSRNc&list=PLnra1_c-Y6TiQiBCk1clsy80PVAp9Z1q3&index=3"
        },
        {
          text: "The dedicated instructors, comprehensive study materials, and interactive learning environment helped me achieve my desired score. I highly recommend it to anyone looking to excel in the IELTS exam",
          userName: "Ranmina Navoth",
          userRole: "IELTS",
          userAvatar: StudentIcon,
          link: "https://www.youtube.com/watch?v=5a-CoElEByk&list=PLnra1_c-Y6TiQiBCk1clsy80PVAp9Z1q3&index=4"
        },
        {
          text: "I prefer to recommend the IELTS Fast Track programm in Ambalangoda CCBE as the better place to boots the band who wish to sit the IELTS examination.",
          userName: "Prabhashini Chathurika",
          userRole: "IELTS",
          userAvatar: StudentIcon,
          link: "https://www.youtube.com/watch?v=16SXO8RDb4k&list=PLnra1_c-Y6TiQiBCk1clsy80PVAp9Z1q3&index=5"
        },
        {
          text: "During the course we were able to do lot of activities in English and we could in our four language skills such as reading,writing listning & speaking the evolutions.",
          userName: "Kushani Umanda",
          userRole: "IKEY002",
          userAvatar: StudentIcon,
          link: "https://www.youtube.com/watch?v=-nBqEGHpnQs&list=PLnra1_c-Y6TiQiBCk1clsy80PVAp9Z1q3&index=6"
        },
        {
          text: "I wanted to improve my speaking skills as I'm expecting to go abroad for my highest studies at CCBE. I was given the best guidance we learn in a stressfree environment.",
          userName: "Jayani Bawathma",
          userRole: "IKF004",
          userAvatar: StudentIcon,
          link: "https://www.youtube.com/watch?v=iN5WZINOmrk&list=PLnra1_c-Y6TiQiBCk1clsy80PVAp9Z1q3&index=7"
        },
        {
          text: "We could learn and make learned language skills through various academic activities the students entered classrooms help us to improve our confidence in English.",
          userName: "Vinuji Mallawa Arachchi",
          userRole: "IPET002",
          userAvatar: StudentIcon,
          link: "https://www.youtube.com/watch?v=ZEyR-mUGTAs&list=PLnra1_c-Y6TiQiBCk1clsy80PVAp9Z1q3&index=8"
        },
        {
          text: "End of the course I faced Cambridge assessment exams confidently. Thanks to all the preparation sessions. I would really recommend CCBE to anyone out there come joing CCBE without hesitation.",
          userName: "Naduni Abeynayaka",
          userRole: "FCE Intake",
          userAvatar: StudentIcon,
          link: "https://www.youtube.com/watch?v=Lsl_qzKhMjY&list=PLnra1_c-Y6TiQiBCk1clsy80PVAp9Z1q3&index=9"
        },
      ],
      videos: [
        {
          link: "https://www.youtube.com/embed/uSr4JjCtge4?si=64lVPGcTuj4s4C-K",
        },
        {
          link: "https://www.youtube.com/embed/V_riM5h2pOQ?si=LufQypwbQLuMPFF1",
        },
        {
          link: "https://www.youtube.com/embed/uTyP39sO-Q0?si=OvU_rVvdvIeGqNOV",
        },
      ],
    };
  },
  computed: {
    visibleTestimonials() {
      return this.testimonials.slice(this.currentSlide, this.currentSlide + this.testimonialsPerPage);
    },
    totalPages() {
      return Math.ceil(this.testimonials.length / this.testimonialsPerPage);
    }
  },
  methods: {
    nextSlide() {
      if (this.currentSlide < this.testimonials.length - this.testimonialsPerPage) {
        this.currentSlide += this.testimonialsPerPage;
      } else {
        this.currentSlide = 0;
      }
    },
    prevSlide() {
      if (this.currentSlide > 0) {
        this.currentSlide -= this.testimonialsPerPage;
      } else {
        this.currentSlide = this.testimonials.length - this.testimonialsPerPage;
      }
    },
    goToPage(page) {
      this.currentSlide = (page - 1) * this.testimonialsPerPage;
    }
  },
  mounted() {
    AOS.init();
  }
};
</script>

<style scoped>
.testimonials-page {
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

/* Testimonials Section */
.testimonials-section {
  padding: 2rem 0;
}

.carousel-container {
  position: relative;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.testimonials-carousel {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
  margin-bottom: 3rem;
}

.testimonials-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
  flex: 1;
}

/* Testimonial Card */
.testimonial-card {
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

.testimonial-card::before {
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

.testimonial-card:hover::before {
  left: 100%;
}

.testimonial-card:hover {
  transform: translateY(-15px);
  border-color: #FFD700;
  box-shadow: 0 25px 50px rgba(255, 215, 0, 0.25);
}

/* Image Container */
.image-container {
  position: relative;
  overflow: hidden;
  height: 200px;
}

.testimonial-avatar {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.4s ease;
}

.testimonial-card:hover .testimonial-avatar {
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

.testimonial-badge {
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

.testimonial-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.4rem;
  font-weight: 700;
  color: #ffffff;
  line-height: 1.3;
  margin-bottom: 1rem;
  min-height: 3.5rem;
}

.testimonial-text {
  font-family: 'Inter', sans-serif;
  font-size: 0.95rem;
  line-height: 1.6;
  color: #e0e0e0;
  margin-bottom: 0;
  flex: 1;
  font-style: italic;
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

/* Pagination Dots */
.pagination-dots {
  display: flex;
  justify-content: center;
  gap: 12px;
  margin-top: 2rem;
}

.pagination-dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: #333;
  border: none;
  cursor: pointer;
  transition: all 0.3s ease;
}

.pagination-dot.active {
  background: #FFD700;
  transform: scale(1.2);
  box-shadow: 0 0 0 2px rgba(255, 215, 0, 0.3);
}

.pagination-dot:hover {
  background: #FFA500;
}

/* Video Section */
.video-section {
  padding: 4rem 0;
  text-align: center;
}

.section-title {
  font-family: 'Inter', 'Poppins', sans-serif;
  font-size: 2.5rem;
  font-weight: 700;
  color: #ffffff;
  margin-bottom: 1rem;
  text-transform: uppercase;
}

.section-subtitle {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  color: #e0e0e0;
  margin-bottom: 3rem;
}

.videos-grid {
  margin: 0 -12px;
}

.video-card {
  background: linear-gradient(135deg, #2d2d2d 0%, #1a1a1a 100%);
  border: 2px solid #333;
  border-radius: 20px;
  overflow: hidden;
  transition: all 0.4s ease;
  position: relative;
}

.video-card:hover {
  transform: translateY(-10px);
  border-color: #FFD700;
  box-shadow: 0 20px 40px rgba(255, 215, 0, 0.2);
}

.video-container {
  position: relative;
  width: 100%;
  height: 250px;
  overflow: hidden;
}

.video-iframe {
  width: 100%;
  height: 100%;
  border: none;
  transition: transform 0.4s ease;
}

.video-card:hover .video-iframe {
  transform: scale(1.05);
}

.video-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, rgba(255, 215, 0, 0.1) 0%, rgba(255, 165, 0, 0.1) 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.video-card:hover .video-overlay {
  opacity: 1;
}

.play-icon {
  font-size: 3rem !important;
  color: #FFD700 !important;
  opacity: 0.8;
}

/* Floating Animation */
.testimonial-card, .video-card {
  animation: float 6s ease-in-out infinite;
}

.testimonial-card:nth-child(odd), .video-card:nth-child(odd) {
  animation-delay: 0s;
}

.testimonial-card:nth-child(even), .video-card:nth-child(even) {
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

.testimonial-card:hover, .video-card:hover {
  animation: none;
}

/* Additional Effects */
.testimonial-card::after, .video-card::after {
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

.testimonial-card:hover::after, .video-card:hover::after {
  opacity: 0.3;
}

/* Responsive Design */
@media (max-width: 960px) {
  .page-title {
    font-size: 2.8rem;
  }
  
  .intro-text {
    font-size: 1.1rem;
  }
  
  .testimonials-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 1.5rem;
  }
  
  .testimonial-title {
    font-size: 1.2rem;
    min-height: auto;
  }
  
  .section-title {
    font-size: 2.2rem;
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
  
  .testimonials-grid {
    grid-template-columns: 1fr;
    gap: 1rem;
  }
  
  .card-content {
    padding: 1.5rem;
  }
  
  .testimonial-title {
    font-size: 1.1rem;
  }
  
  .testimonial-text {
    font-size: 0.9rem;
  }
  
  .card-actions {
    padding: 0 1.5rem 1.5rem;
  }
  
  .carousel-container {
    padding: 0 16px;
  }
  
  .nav-button {
    width: 48px;
    height: 48px;
  }
  
  .section-title {
    font-size: 1.8rem;
  }
  
  .section-subtitle {
    font-size: 1rem;
  }
  
  .video-container {
    height: 200px;
  }
}
</style>