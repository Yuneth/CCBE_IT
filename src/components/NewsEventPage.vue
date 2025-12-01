<template>
  <div class="news-events-page">
    <NavBar></NavBar>
    
    <!-- Hero Section -->
    <section class="hero-section">
      <div class="hero-overlay">
        <div class="hero-content">
          <h1 class="hero-title" data-aos="fade-up" data-aos-duration="800">
            News <span class="highlight">&</span> Events
          </h1>
          <p class="hero-subtitle" data-aos="fade-up" data-aos-duration="800" data-aos-delay="200">
            Celebrating Our Community & Achievements
          </p>
          <p class="hero-description" data-aos="fade-up" data-aos-duration="800" data-aos-delay="400">
            Stay updated with our latest achievements, community events, and inspiring stories from Cambridge College of British English.
          </p>
        </div>
      </div>
    </section>

    <!-- News & Events Section -->
    <section class="news-events-section">
      <div class="container">
        <!-- Featured Event -->
        <div class="featured-section" v-if="featuredEvent">
          <div class="featured-card" data-aos="fade-up">
            <div class="featured-image">
              <v-img 
                :src="featuredEvent.image" 
                cover
                class="featured-img"
                :alt="featuredEvent.title"
              ></v-img>
              <div class="featured-badge">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M18 8C18 6.4087 17.3679 4.88258 16.2426 3.75736C15.1174 2.63214 13.5913 2 12 2C10.4087 2 8.88258 2.63214 7.75736 3.75736C6.63214 4.88258 6 6.4087 6 8C6 15 3 17 3 17H21C21 17 18 15 18 8Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  <path d="M13.73 21C13.5542 21.3031 13.3019 21.5547 12.9982 21.7295C12.6946 21.9044 12.3504 21.9965 12 21.9965C11.6496 21.9965 11.3054 21.9044 11.0018 21.7295C10.6982 21.5547 10.4458 21.3031 10.27 21" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
                <span>Featured Event</span>
              </div>
            </div>
            <div class="featured-content">
              <div class="featured-header">
                <div class="event-date">
                  <span class="date-day">NOW</span>
                  <span class="date-text">Featured</span>
                </div>
                <div class="event-category">Community Initiative</div>
              </div>
              <h2 class="featured-title">{{ featuredEvent.title }}</h2>
              <p class="featured-description">{{ featuredEvent.subtitle }}</p>
              <p class="featured-full">{{ featuredEvent.content }}</p>
              <div class="featured-tags">
                <span class="tag">Environment</span>
                <span class="tag">Community</span>
                <span class="tag">Growth</span>
              </div>
              <button class="featured-btn" @click="openEventModal(featuredEvent)">
                Learn More
                <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M5 12H19" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  <path d="M12 5L19 12L12 19" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
              </button>
            </div>
          </div>
        </div>

        <!-- Events Filter -->
        <div class="filter-section" data-aos="fade-up">
          <div class="filter-tabs">
            <button 
              v-for="tab in tabs" 
              :key="tab.id"
              class="filter-tab"
              :class="{ 'active': activeTab === tab.id }"
              @click="setActiveTab(tab.id)"
            >
              <component :is="tab.icon" />
              <span>{{ tab.label }}</span>
            </button>
          </div>
        </div>

        <!-- Events Grid -->
        <div class="events-grid">
          <div 
            v-for="(event, index) in filteredEvents" 
            :key="index"
            class="event-card-wrapper"
            :data-aos="index % 2 === 0 ? 'fade-right' : 'fade-left'"
            :data-aos-delay="(index % 4) * 100"
          >
            <div class="event-card">
              <div class="card-image">
                <v-img 
                  :src="event.image" 
                  cover
                  class="event-image"
                  :alt="event.title"
                ></v-img>
                <div class="image-overlay"></div>
                <div class="event-badge">
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M20 21V19C20 17.9391 19.5786 16.9217 18.8284 16.1716C18.0783 15.4214 17.0609 15 16 15H8C6.93913 15 5.92172 15.4214 5.17157 16.1716C4.42143 16.9217 4 17.9391 4 19V21" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M12 11C14.2091 11 16 9.20914 16 7C16 4.79086 14.2091 3 12 3C9.79086 3 8 4.79086 8 7C8 9.20914 9.79086 11 12 11Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  </svg>
                  <span>Event</span>
                </div>
              </div>

              <div class="card-content">
                <div class="card-header">
                  <div class="event-date">
                    <span class="date-day">{{ getEventDate(index) }}</span>
                    <span class="date-month">Latest</span>
                  </div>
                  <div class="event-category">{{ event.category }}</div>
                </div>
                
                <h3 class="event-title">{{ event.title }}</h3>
                <p class="event-subtitle">{{ event.subtitle }}</p>
                
                <div class="event-description">
                  <p>{{ truncateText(event.content, 120) }}</p>
                </div>

                <div class="event-actions">
                  <button class="read-btn" @click="toggleEvent(index)">
                    {{ event.expanded ? 'Show Less' : 'Read More' }}
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                      <path d="M6 9L12 15L18 9" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    </svg>
                  </button>
                  <button class="share-btn" @click="shareEvent(event)">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                      <path d="M4 12V20C4 20.5304 4.21071 21.0391 4.58579 21.4142C4.96086 21.7893 5.46957 22 6 22H18C18.5304 22 19.0391 21.7893 19.4142 21.4142C19.7893 21.0391 20 20.5304 20 20V12" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                      <path d="M16 6L12 2L8 6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                      <path d="M12 2V15" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    </svg>
                  </button>
                </div>

                <div v-if="event.expanded" class="expanded-content">
                  <p class="full-content">{{ event.content }}</p>
                  <div class="event-tags">
                    <span class="tag" v-for="(tag, i) in event.tags" :key="i">{{ tag }}</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Newsletter Section -->
    <section class="newsletter-section">
      <div class="container">
        <div class="newsletter-card" data-aos="fade-up">
          <div class="newsletter-content">
            <h2 class="newsletter-title">Stay Updated</h2>
            <p class="newsletter-description">
              Subscribe to our newsletter and never miss important announcements, upcoming events, and student achievements.
            </p>
            <form class="newsletter-form" @submit.prevent="subscribeNewsletter">
              <div class="input-group">
                <input 
                  type="email" 
                  v-model="email" 
                  placeholder="Enter your email" 
                  required
                  class="newsletter-input"
                >
                <button type="submit" class="subscribe-btn">
                  Subscribe
                  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M22 2L11 13" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M22 2L15 22L11 13L2 9L22 2Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  </svg>
                </button>
              </div>
              <p class="newsletter-note">We respect your privacy. Unsubscribe at any time.</p>
            </form>
          </div>
        </div>
      </div>
    </section>

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

// SVG Icons
const AllIcon = {
  template: `
    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M3 9H21" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M9 21V9" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M21 3H3V21H21V3Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
  `
};

const EventsIcon = {
  template: `
    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M8 2V6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M16 2V6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M3 10H21" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M19 4H5C3.89543 4 3 4.89543 3 6V20C3 21.1046 3.89543 22 5 22H19C20.1046 22 21 21.1046 21 20V6C21 4.89543 20.1046 4 19 4Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
  `
};

const AchievementsIcon = {
  template: `
    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M12 15C15.866 15 19 11.866 19 8C19 4.13401 15.866 1 12 1C8.13401 1 5 4.13401 5 8C5 11.866 8.13401 15 12 15Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M8.21 13.89L7 23L12 20L17 23L15.79 13.88" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
  `
};

const CommunityIcon = {
  template: `
    <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M17 21V19C17 17.9391 16.5786 16.9217 15.8284 16.1716C15.0783 15.4214 14.0609 15 13 15H5C3.93913 15 2.92172 15.4214 2.17157 16.1716C1.42143 16.9217 1 17.9391 1 19V21" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M9 11C11.2091 11 13 9.20914 13 7C13 4.79086 11.2091 3 9 3C6.79086 3 5 4.79086 5 7C5 9.20914 6.79086 11 9 11Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M23 21V19C22.9993 18.1137 22.7044 17.2528 22.1614 16.5523C21.6184 15.8519 20.8581 15.3516 20 15.13" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M16 3.13C16.8604 3.35031 17.623 3.85071 18.1676 4.55232C18.7122 5.25392 19.0078 6.11683 19.0078 7.005C19.0078 7.89318 18.7122 8.75608 18.1676 9.45769C17.623 10.1593 16.8604 10.6597 16 10.88" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
  `
};

export default {
  name: 'NewsEventsPage',
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
  data() {
    return {
      activeTab: 'all',
      email: '',
      tabs: [
        { id: 'all', label: 'All', icon: AllIcon },
        { id: 'events', label: 'Events', icon: EventsIcon },
        { id: 'achievements', label: 'Achievements', icon: AchievementsIcon },
        { id: 'community', label: 'Community', icon: CommunityIcon }
      ],
      featuredEvent: {
        image: "https://ik.imagekit.io/u3wbiya66/News&Events/WhatsApp%20Image%202025-06-08%20at%2010.12.15_fb599a49.jpg?updatedAt=1749452636230",
        title: "🌿 Husma Fluit Plant Dansal 2025",
        subtitle: "Thank You for Being a Part of the Husma Project 2025",
        content: "The Husma Project, first launched by our CCBE Galle branch in 2024 with just 500 plants, has grown into a beautiful island-wide movement. In 2025, thanks to the amazing support from all our branches, the project has flourished reaching 5,000 plants across the country. This initiative reflects our shared commitment to a greener tomorrow and the strength of working together as one. Thank you for being a part of this journey. Together, we breathe life into the future."
      },
      events: [
        {
          image: "https://ik.imagekit.io/u3wbiya66/_MG_9895.jpg?updatedAt=1745842133941",
          title: "Cambrians Awrudu Udanaya",
          subtitle: "The Cambrians Awurudu Udanaya 2025",
          content: "A vibrant day filled with traditional games, colorful festivities, cultural performances, and joyful togetherness awaits. Let's come together to honor our rich heritage and create unforgettable memories.",
          category: "Cultural Event",
          tags: ["Culture", "Festival", "Community"],
          type: "events",
          expanded: false
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/481082092_601994946155124_2299747182221281091_n.jpg?updatedAt=1745841751881",
          title: "MasterChef Kitchen in Action!",
          subtitle: "Culinary Creations, Teamwork, and Speaking Skills",
          content: "MasterChef Kitchen in Action! Our talented students stepped into the spotlight to showcase their favorite meals in an exciting culinary event! This wasn't just about cooking—it was an opportunity to blend creativity, teamwork, and communication skills. From sharing their unique recipes to presenting their culinary masterpieces with confidence, the event was a flavorful journey of learning, collaboration, and fun.",
          category: "Student Activity",
          tags: ["Cooking", "Teamwork", "Skills"],
          type: "events",
          expanded: false
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/IMG_6630.JPG?updatedAt=1745842202604",
          title: "Welcoming 2025 with Warmth and Positivity",
          subtitle: "A Heartfelt New Year Celebration Marking New Beginnings",
          content: "As we step into 2025, our Galle branch hosted a celebration that radiated warmth and positivity. The event was more than just a New Year gathering—it was a heartfelt occasion filled with joy, reflection, and a shared vision for the year ahead.",
          category: "Celebration",
          tags: ["New Year", "Celebration", "Team"],
          type: "community",
          expanded: false
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/News&Events/FB_IMG_1738984651465.jpg?updatedAt=1738985253696",
          title: "Spreading Festive Cheer with a Secret Santa Celebration",
          subtitle: "A Joyful Day of Togetherness at Cambridge College of British English",
          content: "We brought the festive cheer to Cambridge College of British English with a delightful Secret Santa celebration! Our team shared laughter, exchanged thoughtful gifts, and created heartwarming memories that truly captured the spirit of togetherness.",
          category: "Festive Event",
          tags: ["Christmas", "Team Building", "Fun"],
          type: "community",
          expanded: false
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/News&Events/FB_IMG_1738984882674.jpg?updatedAt=1738985253221",
          title: "Celebrating Student Success",
          subtitle: "Congratulations to Our Students on Achieving A2 Flyers Level!",
          content: "Exciting News from Cambridge College of British English! A big congratulations to our incredible students for achieving the Cambridge English Assessment A2 Flyers Level! Your hard work and dedication continue to inspire us every day.",
          category: "Achievement",
          tags: ["Success", "Students", "Cambridge"],
          type: "achievements",
          expanded: false
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/News&Events/FB_IMG_1738984825665.jpg?updatedAt=1738985254002",
          title: "Fit to Fight 2024",
          subtitle: "Our 9th Annual Event a Huge Success!",
          content: "Heartfelt thanks to everyone who contributed to and supported our 9th annual Fit to Fight event! Your unwavering generosity and dedication have once again demonstrated the power of community and compassion.",
          category: "Charity Event",
          tags: ["Charity", "Community", "Health"],
          type: "community",
          expanded: false
        }
      ]
    };
  },
  computed: {
    filteredEvents() {
      if (this.activeTab === 'all') {
        return this.events;
      }
      return this.events.filter(event => event.type === this.activeTab);
    }
  },
  methods: {
    setActiveTab(tabId) {
      this.activeTab = tabId;
    },
    toggleEvent(index) {
      this.events[index].expanded = !this.events[index].expanded;
    },
    truncateText(text, length) {
      if (text.length <= length) return text;
      return text.substring(0, length) + '...';
    },
    getEventDate(index) {
      const days = ['01', '02', '03', '04', '05', '06', '07'];
      return days[index] || '01';
    },
    openEventModal(event) {
      // Implement modal opening logic
      console.log('Opening modal for:', event.title);
    },
    shareEvent(event) {
      if (navigator.share) {
        navigator.share({
          title: event.title,
          text: event.subtitle,
          url: window.location.href,
        });
      } else {
        // Fallback for browsers that don't support Web Share API
        navigator.clipboard.writeText(`${event.title} - ${event.subtitle}`);
        alert('Event link copied to clipboard!');
      }
    },
    subscribeNewsletter() {
      if (this.email) {
        console.log('Subscribing email:', this.email);
        alert('Thank you for subscribing to our newsletter!');
        this.email = '';
      }
    }
  }
};
</script>

<style scoped>
.news-events-page {
  background: #ffffff;
  min-height: 100vh;
  color: #333;
}

/* Hero Section */
.hero-section {
  height: 60vh;
  min-height: 500px;
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
  background: 
    radial-gradient(circle at 20% 80%, rgba(255,255,255,0.1) 0%, transparent 50%),
    radial-gradient(circle at 80% 20%, rgba(255,255,255,0.1) 0%, transparent 50%);
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
  color: white;
}

.hero-title {
  font-family: 'Inter', 'Poppins', sans-serif;
  font-size: 3.5rem;
  font-weight: 800;
  margin-bottom: 1rem;
  letter-spacing: -0.5px;
  color: black;
  
}

.highlight {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-subtitle {
  font-family: 'Inter', sans-serif;
  font-size: 1.2rem;
  font-weight: 500;
  margin-bottom: 1.5rem;
  color: black;
  text-transform: uppercase;
  letter-spacing: 3px;
}

.hero-description {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  line-height: 1.6;
  color: black;
  max-width: 600px;
  margin: 0 auto;
}

/* Main Container */
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
}

/* Featured Section */
.featured-section {
  margin: 4rem 0;
}

.featured-card {
  background: white;
  border-radius: 24px;
  overflow: hidden;
  box-shadow: 0 20px 60px rgba(0,0,0,0.08);
  border: 1px solid rgba(102,126,234,0.1);
  display: grid;
  grid-template-columns: 1fr 1fr;
  align-items: stretch;
}

.featured-image {
  position: relative;
  height: 100%;
  min-height: 400px;
  overflow: hidden;
}

.featured-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.6s ease;
}

.featured-card:hover .featured-img {
  transform: scale(1.05);
}

.featured-badge {
  position: absolute;
  top: 1.5rem;
  left: 1.5rem;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 0.75rem 1.5rem;
  border-radius: 50px;
  display: flex;
  align-items: center;
  gap: 0.75rem;
  font-family: 'Inter', sans-serif;
  font-weight: 600;
  font-size: 0.9rem;
  z-index: 2;
}

.featured-badge svg {
  color: white;
}

.featured-content {
  padding: 3rem;
  display: flex;
  flex-direction: column;
}

.featured-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1.5rem;
}

.event-date {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.date-day {
  font-family: 'Inter', sans-serif;
  font-size: 1.8rem;
  font-weight: 700;
  color: #667eea;
  line-height: 1;
}

.date-text {
  font-family: 'Inter', sans-serif;
  font-size: 0.8rem;
  color: #666;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.event-category {
  font-family: 'Inter', sans-serif;
  font-size: 0.85rem;
  font-weight: 600;
  color: #667eea;
  background: rgba(102,126,234,0.1);
  padding: 0.4rem 1rem;
  border-radius: 50px;
}

.featured-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.8rem;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 1rem;
  line-height: 1.3;
}

.featured-description {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  line-height: 1.6;
  color: #555;
  margin-bottom: 1.5rem;
  font-weight: 500;
}

.featured-full {
  font-family: 'Inter', sans-serif;
  font-size: 1rem;
  line-height: 1.6;
  color: #666;
  margin-bottom: 2rem;
  flex: 1;
}

.featured-tags {
  display: flex;
  gap: 0.75rem;
  margin-bottom: 2rem;
  flex-wrap: wrap;
}

.tag {
  font-family: 'Inter', sans-serif;
  font-size: 0.85rem;
  color: #667eea;
  background: rgba(102,126,234,0.1);
  padding: 0.4rem 1rem;
  border-radius: 50px;
  font-weight: 500;
}

.featured-btn {
  align-self: flex-start;
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
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.featured-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 30px rgba(102,126,234,0.3);
  gap: 1rem;
}

/* Filter Section */
.filter-section {
  margin-bottom: 3rem;
}

.filter-tabs {
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
  justify-content: center;
}

.filter-tab {
  background: white;
  border: 2px solid rgba(102,126,234,0.1);
  border-radius: 12px;
  padding: 0.75rem 1.5rem;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  gap: 0.75rem;
  font-family: 'Inter', sans-serif;
  font-weight: 600;
  color: #666;
  font-size: 0.95rem;
}

.filter-tab:hover {
  border-color: #667eea;
  color: #667eea;
}

.filter-tab.active {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border-color: transparent;
}

.filter-tab svg {
  color: currentColor;
}

/* Events Grid */
.events-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
  gap: 2rem;
  margin-bottom: 4rem;
}

.event-card-wrapper {
  perspective: 1000px;
}

.event-card {
  background: white;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 10px 40px rgba(0,0,0,0.08);
  border: 1px solid rgba(102,126,234,0.1);
  transition: all 0.3s ease;
  height: 100%;
}

.event-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 60px rgba(102,126,234,0.15);
}

.card-image {
  position: relative;
  height: 200px;
  overflow: hidden;
}

.event-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.6s ease;
}

.event-card:hover .event-image {
  transform: scale(1.05);
}

.image-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(to bottom, transparent 50%, rgba(0,0,0,0.1) 100%);
}

.event-badge {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: rgba(0,0,0,0.8);
  color: white;
  padding: 0.4rem 0.8rem;
  border-radius: 50px;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-family: 'Inter', sans-serif;
  font-size: 0.75rem;
  font-weight: 600;
  z-index: 2;
}

.event-badge svg {
  color: white;
}

.card-content {
  padding: 1.5rem;
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 1rem;
}

.event-date {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.date-day {
  font-family: 'Inter', sans-serif;
  font-size: 1.2rem;
  font-weight: 700;
  color: #667eea;
  line-height: 1;
}

.date-month {
  font-family: 'Inter', sans-serif;
  font-size: 0.7rem;
  color: #666;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.event-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.2rem;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 0.5rem;
  line-height: 1.3;
}

.event-subtitle {
  font-family: 'Inter', sans-serif;
  font-size: 0.9rem;
  color: #667eea;
  font-weight: 500;
  margin-bottom: 1rem;
}

.event-description {
  font-family: 'Inter', sans-serif;
  font-size: 0.9rem;
  line-height: 1.6;
  color: #555;
  margin-bottom: 1.5rem;
}

.event-actions {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
}

.read-btn {
  background: white;
  color: #667eea;
  border: 2px solid rgba(102,126,234,0.3);
  border-radius: 8px;
  padding: 0.5rem 1rem;
  font-family: 'Inter', sans-serif;
  font-weight: 600;
  font-size: 0.85rem;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.read-btn:hover {
  background: rgba(102,126,234,0.05);
  border-color: #667eea;
  gap: 0.75rem;
}

.share-btn {
  background: white;
  color: #666;
  border: 2px solid rgba(0,0,0,0.1);
  border-radius: 8px;
  padding: 0.5rem;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
}

.share-btn:hover {
  color: #667eea;
  border-color: rgba(102,126,234,0.3);
  transform: rotate(45deg);
}

/* Expanded Content */
.expanded-content {
  border-top: 1px solid rgba(102,126,234,0.1);
  padding-top: 1rem;
  margin-top: 1rem;
}

.full-content {
  font-family: 'Inter', sans-serif;
  font-size: 0.9rem;
  line-height: 1.6;
  color: #555;
  margin-bottom: 1rem;
  white-space: pre-line;
}

.event-tags {
  display: flex;
  gap: 0.5rem;
  flex-wrap: wrap;
}

/* Newsletter Section */
.newsletter-section {
  padding: 6rem 1rem;
  background: linear-gradient(135deg, #f6f9ff 0%, #f0f4ff 100%);
}

.newsletter-card {
  background: white;
  border-radius: 24px;
  padding: 4rem;
  box-shadow: 0 20px 60px rgba(0,0,0,0.08);
  border: 1px solid rgba(102,126,234,0.1);
  text-align: center;
}

.newsletter-content {
  max-width: 600px;
  margin: 0 auto;
}

.newsletter-title {
  font-family: 'Inter', sans-serif;
  font-size: 2.2rem;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 1rem;
}

.newsletter-description {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  line-height: 1.6;
  color: #555;
  margin-bottom: 2rem;
}

.newsletter-form {
  max-width: 500px;
  margin: 0 auto;
}

.input-group {
  display: flex;
  gap: 1rem;
  margin-bottom: 1rem;
}

.newsletter-input {
  flex: 1;
  padding: 1rem 1.5rem;
  border: 2px solid rgba(102,126,234,0.3);
  border-radius: 12px;
  font-family: 'Inter', sans-serif;
  font-size: 1rem;
  transition: all 0.3s ease;
}

.newsletter-input:focus {
  outline: none;
  border-color: #667eea;
  box-shadow: 0 0 0 3px rgba(102,126,234,0.1);
}

.subscribe-btn {
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
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.subscribe-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 30px rgba(102,126,234,0.3);
  gap: 1rem;
}

.newsletter-note {
  font-family: 'Inter', sans-serif;
  font-size: 0.85rem;
  color: #888;
  margin-top: 0.5rem;
}

/* Responsive Design */
@media (max-width: 992px) {
  .hero-title {
    font-size: 2.8rem;
  }
  
  .featured-card {
    grid-template-columns: 1fr;
  }
  
  .featured-image {
    min-height: 300px;
    order: -1;
  }
  
  .featured-content {
    padding: 2rem;
  }
}

@media (max-width: 768px) {
  .hero-section {
    height: 50vh;
    min-height: 400px;
  }
  
  .hero-title {
    font-size: 2.2rem;
  }
  
  .hero-subtitle {
    font-size: 1rem;
    letter-spacing: 2px;
  }
  
  .featured-title {
    font-size: 1.5rem;
  }
  
  .featured-content {
    padding: 1.5rem;
  }
  
  .events-grid {
    grid-template-columns: 1fr;
    max-width: 500px;
    margin: 0 auto 4rem;
  }
  
  .newsletter-card {
    padding: 2rem;
  }
  
  .input-group {
    flex-direction: column;
  }
  
  .subscribe-btn {
    width: 100%;
    justify-content: center;
  }
}

@media (max-width: 480px) {
  .hero-title {
    font-size: 1.8rem;
  }
  
  .hero-subtitle {
    font-size: 0.9rem;
    letter-spacing: 1px;
  }
  
  .filter-tabs {
    justify-content: flex-start;
    overflow-x: auto;
    padding-bottom: 0.5rem;
  }
  
  .filter-tab {
    white-space: nowrap;
  }
  
  .featured-badge {
    padding: 0.5rem 1rem;
    font-size: 0.8rem;
  }
  
  .event-card {
    margin: 0;
  }
}

/* Animations */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.event-card-wrapper {
  animation: fadeInUp 0.6s ease forwards;
  opacity: 0;
}

/* Stagger animations */
.event-card-wrapper:nth-child(1) { animation-delay: 0.1s; }
.event-card-wrapper:nth-child(2) { animation-delay: 0.2s; }
.event-card-wrapper:nth-child(3) { animation-delay: 0.3s; }
.event-card-wrapper:nth-child(4) { animation-delay: 0.4s; }
.event-card-wrapper:nth-child(5) { animation-delay: 0.5s; }
.event-card-wrapper:nth-child(6) { animation-delay: 0.6s; }

/* Smooth transitions */
.expanded-content {
  transition: all 0.3s ease;
}
</style>