<template>
  <div class="news-events-page">
    <NavBar></NavBar>
    <v-container class="main-container">
      <!-- Header Section -->
      <section class="header-section">
        <h1 class="page-title" data-aos="fade-up" data-aos-duration="3000">
          NEWS <span class="highlight">& EVENTS</span>
        </h1>
        <p class="intro-text" data-aos="fade-up" data-aos-duration="3000">
          <b>At Cambridge College of British English (CCBE)</b>, we are constantly evolving to offer our students the best learning experiences. Our upcoming events include language workshops, cultural exchange programs, and exciting new course launches designed to meet the needs of learners of all ages. Whether you're interested in expanding your vocabulary, improving your accent, or exploring advanced language techniques, our events offer unique opportunities for growth. Stay tuned for announcements on our seasonal events, student achievements, and exciting collaborations with language experts. At CCBE, every moment is a chance to learn, connect, and celebrate the joy of mastering English.
        </p>
      </section>

      <!-- News & Events Grid -->
      <section class="news-events-section">
        <v-row class="news-events-grid">
          <v-col 
            v-for="(card, index) in cards" 
            :key="index" 
            cols="12" 
            sm="6" 
            md="4" 
            lg="4"
          >
            <v-card 
              class="news-card" 
              data-aos="fade-up" 
              :data-aos-delay="(index % 3) * 100"
              data-aos-duration="3000"
            >
              <!-- Image Container -->
              <div class="image-container">
                <v-img 
                  :src="card.image" 
                  height="250" 
                  cover
                  class="news-image"
                ></v-img>
                <div class="card-overlay">
                  <v-icon class="overlay-icon">mdi-newspaper</v-icon>
                  <span class="overlay-text">Event</span>
                </div>
              </div>
              
              <!-- Card Content -->
              <v-card-text class="card-content">
                <div class="news-badge">Latest</div>
                <h3 class="news-title">{{ card.title }}</h3>
                <p class="news-subtitle">{{ card.subtitle }}</p>
                
                <!-- Expandable Content -->
                <v-expand-transition>
                  <div v-show="card.show" class="expanded-content">
                    <v-divider class="content-divider"></v-divider>
                    <p class="news-content">{{ card.content }}</p>
                  </div>
                </v-expand-transition>
              </v-card-text>
              
              <!-- Card Actions -->
              <v-card-actions class="card-actions">
                <v-btn 
                  class="read-more-btn" 
                  variant="text" 
                  @click="toggleCard(index)"
                  :icon="card.show ? 'mdi-chevron-up' : 'mdi-chevron-down'"
                >
                  {{ card.show ? 'Show Less' : 'Read More' }}
                  <v-icon right>{{ card.show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
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
import AOS from 'aos';
import NavBar from './NavBar.vue';
import FooterPage from './FooterPage.vue';
import ChatBot from './ChatBot.vue'
import ArrowButton from './ArrowButton.vue';

export default {
  name: 'NewsEventPage',
  components: {
    NavBar,
    FooterPage,
    ChatBot,
    ArrowButton
  },
  data() {
    return {
      cards: [
        {
          image: "https://ik.imagekit.io/u3wbiya66/News&Events/WhatsApp%20Image%202025-06-08%20at%2010.12.15_fb599a49.jpg?updatedAt=1749452636230",
          title: "🌿 Husma Fluit Plant Dansal 2025",
          subtitle: "Thank You for Being a Part of the Husma Project 2025",
          content: "The Husma Project, first launched by our CCBE Galle branch in 2024 with just 500 plants, has grown into a beautiful island-wide movement. In 2025, thanks to the amazing support from all our branches, the project has flourished reaching 5,000 plants across the country. This initiative reflects our shared commitment to a greener tomorrow and the strength of working together as one. Thank you for being a part of this journey. Together, we breathe life into the future.",
          show: false,
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/_MG_9895.jpg?updatedAt=1745842133941",
          title: "Cambrians Awrudu Udanaya",
          subtitle: "The Cambrians Awurudu Udanaya 2025",
          content: "A vibrant day filled with traditional games, colorful festivities, cultural performances, and joyful togetherness awaits. Let's come together to honor our rich heritage and create unforgettable memories.",
          show: false,
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/481082092_601994946155124_2299747182221281091_n.jpg?updatedAt=1745841751881",
          title: "MasterChef Kitchen in Action!",
          subtitle: "Culinary Creations, Teamwork, and Speaking Skills",
          content: "MasterChef Kitchen in Action! 👨‍🍳🍴 Our talented students stepped into the spotlight to showcase their favorite meals in an exciting culinary event! This wasn't just about cooking—it was an opportunity to blend creativity, teamwork, and communication skills. From sharing their unique recipes to presenting their culinary masterpieces with confidence, the event was a flavorful journey of learning, collaboration, and fun. Students worked together seamlessly, demonstrating their ability to combine flavors and ideas while honing their public speaking skills. It was inspiring to witness their passion, teamwork, and creativity come to life in the kitchen. Here's to more delicious moments and skill-building adventures in the future! Stay tuned for highlights, photos, and recipes from this vibrant event! 🌟✨",
          show: false,
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/IMG_6630.JPG?updatedAt=1745842202604",
          title: "Welcoming 2025 with Warmth and Positivity",
          subtitle: "A Heartfelt New Year Celebration Marking New Beginnings",
          content: "✨ As we step into 2025, our Galle branch hosted a celebration that radiated warmth and positivity. The event was more than just a New Year gathering—it was a heartfelt occasion filled with joy, reflection, and a shared vision for the year ahead. 🌟 The team came together to embrace the opportunities and challenges that 2025 will bring. With a sense of unity and optimism, we reflected on the accomplishments of the past year while setting our sights on continued growth and success. This celebration was a reminder of the strong bonds that connect us, and the meaningful impact we aim to make as we move forward, together. Here's to embracing new opportunities, pursuing excellence, and creating a year filled with meaningful moments. Cheers to a fantastic 2025! 🌱",
          show: false,
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/News&Events/FB_IMG_1738984651465.jpg?updatedAt=1738985253696",
          title: "Spreading Festive Cheer with a Secret Santa Celebration",
          subtitle: "A Joyful Day of Togetherness at Cambridge College of British English",
          content: "🎅✨ We brought the festive cheer to Cambridge College of British English with a delightful Secret Santa celebration! 🎁❤️ Our team shared laughter, exchanged thoughtful gifts, and created heartwarming memories that truly captured the spirit of togetherness. It was a day filled with joy, surprises, and the magic of giving! 🎄🎉",
          show: false,
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/News&Events/FB_IMG_1738984743534.jpg?updatedAt=1738985253864",
          title: "Throwback to Unforgettable Moments from Our Annual Trip",
          subtitle: "Breathtaking Views, Adventures, and Team Bonding",
          content: "Throwback to the unforgettable moments from our annual trip! 🌟 From breathtaking views and laughter-filled adventures to team bonding and endless joy, every memory is a treasure we'll cherish forever. Here's to more journeys, stronger connections, and creating magic together! 🏞️✨",
          show: false,
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/News&Events/FB_IMG_1738984882674.jpg?updatedAt=1738985253221",
          title: "Celebrating Success at Cambridge College of British English",
          subtitle: "Congratulations to Our Students on Achieving A2 Flyers Level!",
          content: "🎉 Exciting News from Cambridge College of British English 📚 A big congratulations to our incredible students for achieving the Cambridge English Assessment A2 Flyers Level! 🏆✨ Your hard work and dedication continue to inspire us every day. This milestone is just the beginning of your amazing language-learning journey! 🌟🙌 Keep aiming high and chasing your dreams! 🚀✨",
          show: false,
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/News&Events/FB_IMG_1738984825665.jpg?updatedAt=1738985254002",
          title: "Fit to Fight 2024",
          subtitle: "Our 9th Annual Event a Huge Success!",
          content: "Heartfelt thanks to everyone who contributed to and supported our 9th annual Fit to Fight event! Your unwavering generosity and dedication have once again demonstrated the power of community and compassion. This year's event was a remarkable success, with participants, sponsors, and volunteers coming together to support a noble cause. The funds raised during this event will directly benefit the Cancer Hospital in Karapitiya, providing vital resources for patients and their families. Together, we have shown that strength lies in unity, and with your support, we have made a meaningful difference in the lives of those who need it most. Thank you for being a part of this incredible journey. Here's to continuing the fight and spreading hope, one step at a time! Stay tuned for updates, photos, and highlights from the event!",
          show: false,
        },
      ],
    };
  },
  methods: {
    toggleCard(index) {
      this.cards[index].show = !this.cards[index].show;
    },
  },
  mounted() {
    AOS.init();
  }
};
</script>

<style scoped>
.news-events-page {
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
  max-width: 1200px;
  margin: 0 auto;
  text-align: center;
}

/* News & Events Section */
.news-events-section {
  padding: 2rem 0;
}

.news-events-grid {
  margin: 0 -12px;
}

/* News Card */
.news-card {
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

.news-card::before {
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

.news-card:hover::before {
  left: 100%;
}

.news-card:hover {
  transform: translateY(-15px);
  border-color: #FFD700;
  box-shadow: 0 25px 50px rgba(255, 215, 0, 0.25);
}

/* Image Container */
.image-container {
  position: relative;
  overflow: hidden;
}

.news-image {
  transition: transform 0.4s ease;
  position: relative;
}

.news-card:hover .news-image {
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

.news-badge {
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

.news-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.3rem;
  font-weight: 700;
  color: #ffffff;
  line-height: 1.4;
  margin-bottom: 0.75rem;
  min-height: 3.5rem;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.news-subtitle {
  font-family: 'Inter', sans-serif;
  font-size: 0.95rem;
  line-height: 1.5;
  color: #e0e0e0;
  margin-bottom: 1rem;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
  flex: 1;
}

/* Expanded Content */
.expanded-content {
  margin-top: 1rem;
}

.content-divider {
  border-color: #333;
  margin-bottom: 1rem;
}

.news-content {
  font-family: 'Inter', sans-serif;
  font-size: 0.9rem;
  line-height: 1.6;
  color: #e0e0e0;
  white-space: pre-line;
}

/* Card Actions */
.card-actions {
  padding: 0 2rem 1.5rem;
  display: flex;
  justify-content: center;
}

.read-more-btn {
  color: #FFD700 !important;
  font-weight: 600 !important;
  font-family: 'Inter', sans-serif !important;
  text-transform: none !important;
  transition: all 0.3s ease !important;
}

.read-more-btn:hover {
  color: #FFA500 !important;
  transform: translateY(-2px);
}

/* Floating Animation */
.news-card {
  animation: float 6s ease-in-out infinite;
}

.news-card:nth-child(3n+1) {
  animation-delay: 0s;
}

.news-card:nth-child(3n+2) {
  animation-delay: 1.5s;
}

.news-card:nth-child(3n+3) {
  animation-delay: 3s;
}

@keyframes float {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}

.news-card:hover {
  animation: none;
}

/* Additional Effects */
.news-card::after {
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

.news-card:hover::after {
  opacity: 0.3;
}

/* Scroll Animation Enhancement */
.news-events-section {
  perspective: 1000px;
}

.news-card {
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
  
  .news-title {
    font-size: 1.2rem;
    min-height: auto;
  }
  
  .news-subtitle {
    font-size: 0.9rem;
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
  
  .news-title {
    font-size: 1.1rem;
  }
  
  .news-subtitle {
    font-size: 0.85rem;
  }
  
  .news-content {
    font-size: 0.85rem;
  }
  
  .card-actions {
    padding: 0 1.5rem 1.5rem;
  }
  
  .news-events-grid {
    margin: 0 -8px;
  }
}

/* Smooth transitions for expandable content */
.v-expand-transition {
  transition: all 0.3s ease !important;
}

/* Ensure proper text wrapping and readability */
:deep(.v-card-text) {
  white-space: normal;
  word-wrap: break-word;
}

/* Improve the expand transition */
:deep(.v-expand-transition-enter-active),
:deep(.v-expand-transition-leave-active) {
  transition: all 0.3s ease !important;
}

:deep(.v-expand-transition-enter-from),
:deep(.v-expand-transition-leave-to) {
  opacity: 0;
  transform: translateY(-10px);
}
</style>