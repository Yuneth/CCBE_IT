<template>
  <div class="programmes-page">
    <NavBar></NavBar>
    
    <!-- Hero Section -->
    <section class="hero-section">
      <div class="hero-overlay">
        <div class="hero-content">
          <h1 class="hero-title" data-aos="fade-up" data-aos-duration="800">
            Our <span class="highlight">Programmes</span>
          </h1>
          <p class="hero-subtitle" data-aos="fade-up" data-aos-duration="800" data-aos-delay="200">
            Comprehensive English Education Pathways
          </p>
          <p class="hero-description" data-aos="fade-up" data-aos-duration="800" data-aos-delay="400">
            From early childhood foundations to advanced professional certifications, we provide tailored 
            learning experiences that empower students at every stage of their educational journey.
          </p>
        </div>
      </div>
    </section>

    <!-- Programmes Section -->
    <section class="programmes-section">
      <div class="container">
        <!-- Programme Categories -->
        <div class="categories-section">
          <h2 class="section-title" data-aos="fade-up">Educational Pathways</h2>
          <div class="categories-grid" data-aos="fade-up" data-aos-delay="200">
            <div 
              v-for="category in categories" 
              :key="category.id"
              class="category-card"
              :class="{ 'active': activeCategory === category.id }"
              @click="setActiveCategory(category.id)"
            >
              <div class="category-icon">
                <component :is="category.icon" />
              </div>
              <h3 class="category-title">{{ category.title }}</h3>
              <p class="category-description">{{ category.description }}</p>
            </div>
          </div>
        </div>

        <!-- Programme Cards Grid -->
        <div class="programmes-grid">
          <div 
            v-for="(programme, index) in filteredProgrammes" 
            :key="index"
            class="programme-card-wrapper"
            :data-aos="index % 2 === 0 ? 'fade-right' : 'fade-left'"
            :data-aos-delay="(index % 4) * 100"
          >
            <div class="programme-card">
              <!-- Card Header -->
              <div class="card-header">
                <div class="level-badge">{{ programme.level }}</div>
                <div class="age-badge">
                  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M12 22C17.5228 22 22 17.5228 22 12C22 6.47715 17.5228 2 12 2C6.47715 2 2 6.47715 2 12C2 17.5228 6.47715 22 12 22Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M12 6V12L16 14" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  </svg>
                  <span>{{ programme.age }}</span>
                </div>
              </div>

              <!-- Card Image -->
              <div class="card-image">
                <v-img 
                  :src="programme.image" 
                  cover
                  class="programme-image"
                  :alt="programme.title"
                ></v-img>
                <div class="image-overlay"></div>
                <div class="image-gradient"></div>
              </div>

              <!-- Card Content -->
              <div class="card-content">
                <div class="programme-category">{{ programme.category }}</div>
                <h3 class="programme-title">{{ programme.title }}</h3>
                <p class="programme-description">{{ programme.description }}</p>
                
                <!-- Programme Features -->
                <div class="programme-features">
                  <div class="feature" v-for="(feature, i) in programme.features" :key="i">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                      <path d="M22 11.08V12C21.9988 14.1564 21.3005 16.2547 20.0093 17.9818C18.7182 19.709 16.9033 20.9725 14.8354 21.5839C12.7674 22.1953 10.5573 22.1219 8.53447 21.3746C6.51168 20.6273 4.78465 19.2461 3.61096 17.4371C2.43727 15.628 1.87979 13.4881 2.02168 11.3363C2.16356 9.18457 2.99721 7.13633 4.39828 5.49707C5.79935 3.85782 7.69279 2.71538 9.79619 2.24015C11.8996 1.76491 14.1003 1.98234 16.07 2.86" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                      <path d="M22 4L12 14.01L9 11.01" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    </svg>
                    <span>{{ feature }}</span>
                  </div>
                </div>
              </div>

              <!-- Card Footer -->
              <div class="card-footer">
                <router-link :to="programme.route" class="details-btn">
                  <span>View Details</span>
                  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M5 12H19" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M12 5L19 12L12 19" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  </svg>
                </router-link>
                <button class="enquiry-btn" @click="openEnquiry(programme.title)">
                  <span>Make Enquiry</span>
                  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M21 11.5C21 16.75 16.75 21 11.5 21C6.25 21 2 16.75 2 11.5C2 6.25 6.25 2 11.5 2C16.75 2 21 6.25 21 11.5Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M11.5 15.5V11.5" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M11.5 7.5H11.51" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  </svg>
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Call to Action -->
    <section class="cta-section">
      <div class="container">
        <div class="cta-card">
          <div class="cta-content">
            <h2 class="cta-title">Need Guidance Choosing a Programme?</h2>
            <p class="cta-description">
              Our education advisors are here to help you select the perfect programme 
              based on your goals, current level, and learning preferences.
            </p>
            <div class="cta-buttons">
              <button class="cta-btn primary" @click="openEnquiry('General Programme Guidance')">
                Book a Consultation
              </button>
              <button class="cta-btn secondary" @click="callNow">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M22 16.92V19.92C22 20.47 21.55 20.92 21 20.92H19C18.45 20.92 18 20.47 18 19.92V16.92C18 16.37 17.55 15.92 17 15.92H15C14.45 15.92 14 15.47 14 14.92V6.92001C14 6.37001 14.45 5.92001 15 5.92001H19C19.55 5.92001 20 6.37001 20 6.92001V14.92C20 15.47 19.55 15.92 19 15.92H17C16.45 15.92 16 16.37 16 16.92V19.92" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  <path d="M2 16.92V19.92C2 20.47 2.45 20.92 3 20.92H5C5.55 20.92 6 20.47 6 19.92V16.92C6 16.37 6.45 15.92 7 15.92H9C9.55 15.92 10 15.47 10 14.92V6.92001C10 6.37001 9.55 5.92001 9 5.92001H5C4.45 5.92001 4 6.37001 4 6.92001V14.92C4 15.47 4.45 15.92 5 15.92H7C7.55 15.92 8 16.37 8 16.92V19.92" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
                <span>Call Now</span>
              </button>
            </div>
          </div>
          <div class="cta-image">
            <img src="https://ik.imagekit.io/u3wbiya66/PXL_20250127_083713735-EDIT.jpg?updatedAt=1738393428664" alt="Student Consultation">
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

// Import SVG icons as components
const SchoolIcon = {
  template: `
    <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M22 9L12 2L2 9L12 16L22 9Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M2 9V21" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M6 16V12" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M22 9V21" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M18 16V12" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M12 16V12" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
  `
};

const ChildIcon = {
  template: `
    <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M12 2C13.1 2 14 2.9 14 4C14 5.1 13.1 6 12 6C10.9 6 10 5.1 10 4C10 2.9 10.9 2 12 2Z" fill="currentColor"/>
      <path d="M15.89 8.11C15.5 7.72 14.83 7 13.53 7C13.32 7 12.11 7 10.99 7C8.24 7 6 9.24 6 12V15H10V22H14V15H18V12C18 10.39 17.22 8.98 15.89 8.11Z" fill="currentColor"/>
    </svg>
  `
};

const ExamIcon = {
  template: `
    <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M19 4H5C3.89543 4 3 4.89543 3 6V20C3 21.1046 3.89543 22 5 22H19C20.1046 22 21 21.1046 21 20V6C21 4.89543 20.1046 4 19 4Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M16 2V6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M8 2V6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M3 10H21" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M8 14H8.01" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M12 14H12.01" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M16 14H16.01" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M8 18H8.01" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M12 18H12.01" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M16 18H16.01" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
  `
};

const GlobalIcon = {
  template: `
    <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M12 22C17.5228 22 22 17.5228 22 12C22 6.47715 17.5228 2 12 2C6.47715 2 2 6.47715 2 12C2 17.5228 6.47715 22 12 22Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M2 12H22" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M12 2C14.5013 4.73835 15.9228 8.29203 16 12C15.9228 15.708 14.5013 19.2616 12 22C9.49872 19.2616 8.07725 15.708 8 12C8.07725 8.29203 9.49872 4.73835 12 2Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
  `
};

export default {
  name: 'ProgrammesPage',
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
      activeCategory: 'all',
      categories: [
        {
          id: 'all',
          title: 'All Programmes',
          description: 'View our complete range of English programmes',
          icon: SchoolIcon
        },
        {
          id: 'foundation',
          title: 'Foundation',
          description: 'Early childhood and primary education',
          icon: ChildIcon
        },
        {
          id: 'secondary',
          title: 'Secondary',
          description: 'Middle school and high school programmes',
          icon: SchoolIcon
        },
        {
          id: 'exam',
          title: 'Exam Preparation',
          description: 'O/L, A/L and international exams',
          icon: ExamIcon
        },
        {
          id: 'professional',
          title: 'Professional',
          description: 'International certifications and advanced courses',
          icon: GlobalIcon
        }
      ],
      programmes: [
        {
          title: 'Pre Schoolers',
          level: 'Foundation',
          category: 'Foundation',
          age: 'Ages 3-5',
          image: 'https://ik.imagekit.io/u3wbiya66/PXL_20250117_094732824.jpg?updatedAt=1737789273936',
          description: 'Build foundational language skills through interactive and engaging activities for young learners starting their English journey.',
          features: ['Interactive Learning', 'Basic Reading Skills', 'Fun Activities', 'Small Class Sizes'],
          route: '/courses/preschool'
        },
        {
          title: 'Young Learners',
          level: 'Elementary',
          category: 'Foundation',
          age: 'Ages 6-12',
          image: 'https://ik.imagekit.io/u3wbiya66/PXL_20250128_092657658-EDIT.jpg?updatedAt=1738392311029',
          description: 'Develop strong English foundations through creative lessons and age-appropriate materials for elementary students.',
          features: ['Creative Activities', 'Grammar Fundamentals', 'Vocabulary Building', 'Speaking Practice'],
          route: '/courses/younglearners'
        },
        {
          title: 'For Schools',
          level: 'Secondary',
          category: 'Secondary',
          age: 'Ages 13-18',
          image: 'https://ik.imagekit.io/u3wbiya66/IMG-20250127-WA0071.jpg?updatedAt=1737967718437',
          description: 'Comprehensive English programme focusing on academic skills and communication for secondary school students.',
          features: ['Academic English', 'Communication Skills', 'Exam Preparation', 'Critical Thinking'],
          route: '/courses/forschool'
        },
        {
          title: 'English Skills For O/L\'s',
          level: 'Exam Prep',
          category: 'Exam Preparation',
          age: 'O/L Students',
          image: 'https://ik.imagekit.io/u3wbiya66/PXL_20250131_073049442-EDIT.jpg?updatedAt=1738389378296',
          description: 'Specialized preparation focusing on all language components for Ordinary Level examinations.',
          features: ['Comprehensive Syllabus', 'Practice Tests', 'Skill Development', 'Exam Strategies'],
          route: '/courses/ol'
        },
        {
          title: 'English Skills For A/L\'s',
          level: 'Advanced',
          category: 'Exam Preparation',
          age: 'A/L Students',
          image: 'https://ik.imagekit.io/u3wbiya66/PXL_20250127_083713735-EDIT.jpg?updatedAt=1738393428664',
          description: 'Advanced programme emphasizing critical thinking and academic writing for higher education preparation.',
          features: ['Advanced Writing', 'Critical Analysis', 'Research Skills', 'University Prep'],
          route: '/courses/al'
        },
        {
          title: 'IELTS Preparation',
          level: 'Professional',
          category: 'Professional',
          age: 'All Ages',
          image: 'https://ik.imagekit.io/u3wbiya66/IELTS.jpg?updatedAt=1738050317311',
          description: 'Comprehensive IELTS preparation with expert guidance and strategies for achieving desired band scores.',
          features: ['All Test Components', 'Practice Tests', 'Expert Guidance', 'Score Guarantee'],
          route: '/courses/ielts'
        }
      ]
    };
  },
  computed: {
    filteredProgrammes() {
      if (this.activeCategory === 'all') {
        return this.programmes;
      }
      return this.programmes.filter(programme => 
        programme.category.toLowerCase() === this.activeCategory
      );
    }
  },
  methods: {
    setActiveCategory(categoryId) {
      this.activeCategory = categoryId;
    },
    openEnquiry(programme) {
      // Implement enquiry modal or redirect
      console.log('Opening enquiry for:', programme);
      // You can trigger a modal or navigate to contact page
      this.$router.push({ path: '/contact', query: { programme } });
    },
    callNow() {
      // Implement call functionality
      window.location.href = 'tel:+94112233445';
    }
  }
};
</script>

<style scoped>
.programmes-page {
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

/* Programmes Section */
.programmes-section {
  padding: 6rem 1rem;
  background: #f8f9ff;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

/* Categories Section */
.categories-section {
  margin-bottom: 4rem;
}

.section-title {
  font-family: 'Inter', sans-serif;
  font-size: 2.5rem;
  font-weight: 700;
  color: #1a1a1a;
  text-align: center;
  margin-bottom: 3rem;
}

.categories-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1.5rem;
  margin-bottom: 3rem;
}

.category-card {
  background: white;
  border: 2px solid rgba(102,126,234,0.1);
  border-radius: 16px;
  padding: 1.5rem;
  cursor: pointer;
  transition: all 0.3s ease;
  text-align: center;
}

.category-card:hover {
  border-color: #667eea;
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(102,126,234,0.1);
}

.category-card.active {
  background: linear-gradient(135deg, rgba(102,126,234,0.1) 0%, rgba(118,75,162,0.1) 100%);
  border-color: #667eea;
}

.category-icon {
  color: #667eea;
  margin-bottom: 1rem;
  display: flex;
  justify-content: center;
}

.category-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  font-weight: 600;
  color: #1a1a1a;
  margin-bottom: 0.5rem;
}

.category-description {
  font-family: 'Inter', sans-serif;
  font-size: 0.85rem;
  color: #666;
  line-height: 1.4;
}

/* Programmes Grid */
.programmes-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
  gap: 2rem;
}

.programme-card-wrapper {
  perspective: 1000px;
}

.programme-card {
  background: white;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 10px 40px rgba(0,0,0,0.08);
  border: 1px solid rgba(102,126,234,0.1);
  transition: all 0.3s ease;
  height: 100%;
  display: flex;
  flex-direction: column;
}

.programme-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 60px rgba(102,126,234,0.15);
}

/* Card Header */
.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem 1.5rem 1rem;
}

.level-badge {
  font-family: 'Inter', sans-serif;
  font-size: 0.8rem;
  font-weight: 600;
  color: #667eea;
  background: rgba(102,126,234,0.1);
  padding: 0.4rem 1rem;
  border-radius: 50px;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.age-badge {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-family: 'Inter', sans-serif;
  font-size: 0.85rem;
  color: #666;
  background: rgba(0,0,0,0.05);
  padding: 0.4rem 0.8rem;
  border-radius: 50px;
}

.age-badge svg {
  color: #667eea;
}

/* Card Image */
.card-image {
  position: relative;
  height: 180px;
  overflow: hidden;
}

.programme-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.6s ease;
}

.programme-card:hover .programme-image {
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

.image-gradient {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 60px;
  background: linear-gradient(to top, rgba(255,255,255,0.8), transparent);
}

/* Card Content */
.card-content {
  padding: 1.5rem;
  flex: 1;
}

.programme-category {
  font-family: 'Inter', sans-serif;
  font-size: 0.85rem;
  font-weight: 600;
  color: #667eea;
  margin-bottom: 0.5rem;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.programme-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.3rem;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 1rem;
  line-height: 1.3;
}

.programme-description {
  font-family: 'Inter', sans-serif;
  font-size: 0.95rem;
  line-height: 1.6;
  color: #555;
  margin-bottom: 1.5rem;
}

.programme-features {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
  margin-top: 1.5rem;
}

.feature {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  font-family: 'Inter', sans-serif;
  font-size: 0.9rem;
  color: #666;
}

.feature svg {
  color: #667eea;
  flex-shrink: 0;
}

/* Card Footer */
.card-footer {
  padding: 1.5rem;
  display: flex;
  gap: 1rem;
  border-top: 1px solid rgba(102,126,234,0.1);
}

.details-btn,
.enquiry-btn {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  padding: 0.75rem 1.5rem;
  border-radius: 12px;
  font-family: 'Inter', sans-serif;
  font-weight: 600;
  font-size: 0.9rem;
  cursor: pointer;
  transition: all 0.3s ease;
  text-decoration: none;
}

.details-btn {
  background: white;
  color: #667eea;
  border: 2px solid rgba(102,126,234,0.3);
}

.details-btn:hover {
  background: rgba(102,126,234,0.05);
  border-color: #667eea;
  gap: 0.75rem;
}

.enquiry-btn {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border: none;
}

.enquiry-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(102,126,234,0.3);
  gap: 0.75rem;
}

/* CTA Section */
.cta-section {
  padding: 6rem 1rem;
  background: linear-gradient(135deg, #f6f9ff 0%, #f0f4ff 100%);
}

.cta-card {
  background: white;
  border-radius: 24px;
  overflow: hidden;
  box-shadow: 0 20px 60px rgba(0,0,0,0.08);
  display: grid;
  grid-template-columns: 1fr 1fr;
  align-items: center;
}

.cta-content {
  padding: 4rem;
}

.cta-title {
  font-family: 'Inter', sans-serif;
  font-size: 2.2rem;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 1.5rem;
  line-height: 1.2;
}

.cta-description {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  line-height: 1.6;
  color: #555;
  margin-bottom: 2.5rem;
}

.cta-buttons {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}

.cta-btn {
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

.cta-btn.primary {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border: none;
}

.cta-btn.primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 30px rgba(102,126,234,0.3);
}

.cta-btn.secondary {
  background: white;
  color: #667eea;
  border: 2px solid rgba(102,126,234,0.3);
}

.cta-btn.secondary:hover {
  background: rgba(102,126,234,0.05);
  border-color: #667eea;
}

.cta-image {
  height: 100%;
  min-height: 400px;
  overflow: hidden;
}

.cta-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* Responsive Design */
@media (max-width: 1200px) {
  .programmes-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 992px) {
  .hero-title {
    font-size: 2.8rem;
  }
  
  .cta-card {
    grid-template-columns: 1fr;
  }
  
  .cta-content {
    padding: 3rem;
  }
  
  .cta-image {
    order: -1;
    min-height: 300px;
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
  
  .section-title {
    font-size: 2rem;
  }
  
  .programmes-grid {
    grid-template-columns: 1fr;
    max-width: 500px;
    margin: 0 auto;
  }
  
  .categories-grid {
    grid-template-columns: repeat(2, 1fr);
  }
  
  .card-footer {
    flex-direction: column;
  }
  
  .cta-buttons {
    flex-direction: column;
  }
  
  .cta-btn {
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
  
  .section-title {
    font-size: 1.8rem;
  }
  
  .categories-grid {
    grid-template-columns: 1fr;
  }
  
  .programme-title {
    font-size: 1.2rem;
  }
  
  .cta-title {
    font-size: 1.8rem;
  }
  
  .cta-content {
    padding: 2rem;
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

.programme-card-wrapper {
  animation: fadeInUp 0.6s ease forwards;
  opacity: 0;
}

/* Stagger animations */
.programme-card-wrapper:nth-child(1) { animation-delay: 0.1s; }
.programme-card-wrapper:nth-child(2) { animation-delay: 0.2s; }
.programme-card-wrapper:nth-child(3) { animation-delay: 0.3s; }
.programme-card-wrapper:nth-child(4) { animation-delay: 0.4s; }
.programme-card-wrapper:nth-child(5) { animation-delay: 0.5s; }
.programme-card-wrapper:nth-child(6) { animation-delay: 0.6s; }
</style>