<template>
  <div class="home-page">
    <!-- Hero Section -->
    <section class="hero-section">
      <div class="container">
        <div class="row align-items-center">
          <div class="col-lg-6">
            <h1 class="hero-title">Shape Your Future with <span class="highlight">CCIT</span></h1>
            <p class="hero-subtitle">
              The national IT school that hones your child's ICT skills with 
              <strong>100% PRACTICAL</strong> content that goes beyond the subject.
            </p>
            <div class="hero-buttons">
              <router-link to="/courses" class="btn btn-primary btn-lg">
                Explore Courses
              </router-link>
              <router-link to="/contact" class="btn btn-outline-primary btn-lg">
                Contact Us
              </router-link>
            </div>
          </div>
          <div class="col-lg-6">
            <div class="hero-image">
              <div class="image-placeholder">
                <i class="fas fa-laptop-code"></i>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Features Section -->
    <section class="features-section py-5">
      <div class="container">
        <h2 class="section-title text-center mb-5">Why Choose CCIT?</h2>
        <div class="row">
          <div class="col-md-4 mb-4" v-for="(feature, index) in features" :key="index">
            <div class="feature-card card-theme">
              <div class="feature-icon">
                <i :class="feature.icon"></i>
              </div>
              <h3>{{ feature.title }}</h3>
              <p>{{ feature.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Courses Preview -->
    <section class="courses-section py-5 bg-secondary">
      <div class="container">
        <h2 class="section-title text-center mb-5">Popular Courses</h2>
        <div class="row">
          <div class="col-md-4 mb-4" v-for="(course, index) in courses" :key="index">
            <div class="course-card card-theme">
              <div class="course-badge">{{ course.level }}</div>
              <h3>{{ course.title }}</h3>
              <p>{{ course.description }}</p>
              <ul class="course-features">
                <li v-for="(feature, idx) in course.features" :key="idx">
                  <i class="fas fa-check"></i> {{ feature }}
                </li>
              </ul>
              <router-link :to="`/courses#${course.id}`" class="btn btn-accent">
                Learn More
              </router-link>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact CTA -->
    <section class="contact-cta py-5">
      <div class="container text-center">
        <h2 class="section-title mb-4">Ready to Start Your IT Journey?</h2>
        <p class="mb-4">Contact us today to learn more about our programs and enrollment.</p>
        <div class="cta-buttons">
          <a :href="`tel:${mobile}`" class="btn btn-primary btn-lg">
            <i class="fas fa-phone"></i> Call Now
          </a>
          <a :href="`https://wa.me/${whatsapp.replace('+', '')}`" target="_blank" class="btn btn-success btn-lg">
            <i class="fab fa-whatsapp"></i> WhatsApp
          </a>
          <a :href="`mailto:${email}`" class="btn btn-outline-primary btn-lg">
            <i class="fas fa-envelope"></i> Email Us
          </a>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  name: 'HomeView',
  setup() {
    const mobile = '0718861234'
    const whatsapp = '+94707205126'
    const email = 'email.ccit@gmail.com'
    
    const features = ref([
      {
        icon: 'fas fa-laptop-code',
        title: '100% Practical Training',
        description: 'Hands-on experience with real-world projects and industry-standard tools.'
      },
      {
        icon: 'fas fa-chalkboard-teacher',
        title: 'Expert Instructors',
        description: 'Learn from industry professionals with years of teaching experience.'
      },
      {
        icon: 'fas fa-certificate',
        title: 'Certification Programs',
        description: 'Internationally recognized certifications upon course completion.'
      }
    ])
    
    const courses = ref([
      {
        id: 'programming',
        title: 'Programming Fundamentals',
        level: 'Beginner',
        description: 'Learn coding basics with Python, Java, and web development.',
        features: ['Python Basics', 'Web Development', 'Problem Solving', '3 Months Duration']
      },
      {
        id: 'web-dev',
        title: 'Full Stack Web Development',
        level: 'Intermediate',
        description: 'Master modern web technologies for frontend and backend development.',
        features: ['HTML/CSS/JS', 'Vue.js', 'Node.js', 'Database Design', '6 Months Duration']
      },
      {
        id: 'cyber',
        title: 'Cybersecurity Essentials',
        level: 'Advanced',
        description: 'Learn to protect systems and networks from digital threats.',
        features: ['Network Security', 'Ethical Hacking', 'Risk Management', '4 Months Duration']
      }
    ])
    
    return {
      mobile,
      whatsapp,
      email,
      features,
      courses
    }
  }
}
</script>

<style scoped>
.hero-section {
  padding: 100px 0;
  background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
  color: white;
}

.hero-title {
  font-size: 3.5rem;
  font-weight: 700;
  margin-bottom: 1.5rem;
}

.highlight {
  color: var(--accent-color);
}

.hero-subtitle {
  font-size: 1.2rem;
  margin-bottom: 2rem;
  opacity: 0.9;
}

.hero-buttons {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}

.hero-image {
  text-align: center;
}

.image-placeholder {
  background: rgba(255, 255, 255, 0.1);
  border-radius: 20px;
  padding: 60px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.image-placeholder i {
  font-size: 8rem;
  color: var(--accent-color);
}

.section-title {
  color: var(--text-primary);
  font-weight: 700;
  font-size: 2.5rem;
  margin-bottom: 3rem;
}

.feature-card {
  padding: 2rem;
  border-radius: 15px;
  text-align: center;
  height: 100%;
  transition: transform 0.3s ease;
}

.feature-card:hover {
  transform: translateY(-10px);
}

.feature-icon {
  font-size: 3rem;
  color: var(--accent-color);
  margin-bottom: 1.5rem;
}

.feature-card h3 {
  color: var(--text-primary);
  margin-bottom: 1rem;
  font-size: 1.5rem;
}

.feature-card p {
  color: var(--text-secondary);
  line-height: 1.6;
}

.course-card {
  padding: 2rem;
  border-radius: 15px;
  position: relative;
  height: 100%;
  display: flex;
  flex-direction: column;
}

.course-badge {
  position: absolute;
  top: -10px;
  right: 20px;
  background: var(--accent-color);
  color: white;
  padding: 5px 15px;
  border-radius: 20px;
  font-weight: 600;
  font-size: 0.8rem;
}

.course-card h3 {
  color: var(--text-primary);
  margin-bottom: 1rem;
  font-size: 1.8rem;
}

.course-card p {
  color: var(--text-secondary);
  margin-bottom: 1.5rem;
  flex-grow: 1;
}

.course-features {
  list-style: none;
  padding: 0;
  margin-bottom: 1.5rem;
}

.course-features li {
  color: var(--text-secondary);
  margin-bottom: 0.5rem;
  display: flex;
  align-items: center;
}

.course-features i {
  color: var(--accent-color);
  margin-right: 10px;
}

.btn-accent {
  background: var(--accent-color);
  color: white;
  border: none;
  padding: 10px 25px;
  border-radius: 25px;
  font-weight: 600;
  text-decoration: none;
  display: inline-block;
  transition: all 0.3s ease;
}

.btn-accent:hover {
  background: var(--primary-color);
  color: white;
  transform: translateY(-2px);
}

.contact-cta {
  background: linear-gradient(135deg, var(--secondary-color) 0%, var(--primary-color) 100%);
  color: white;
}

.cta-buttons {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}

.btn-success {
  background-color: #25d366 !important;
  border-color: #25d366 !important;
}

@media (max-width: 768px) {
  .hero-title {
    font-size: 2.5rem;
  }
  
  .hero-buttons {
    flex-direction: column;
  }
  
  .cta-buttons {
    flex-direction: column;
    align-items: center;
  }
}
</style>