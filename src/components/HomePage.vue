<template>
  <div class="homepage">
    <NavBar></NavBar>
    <CaroselPage></CaroselPage>

    <!-- Main Content -->
    <div class="main-content">
      <!-- Logo Section -->
      <div
        class="logo-container"
        data-aos="zoom-in-up"
        data-aos-duration="3000"
      >
        <img :src="logo" alt="Company Logo" class="logo-image" />
      </div>

      <!-- Welcome Section -->
      <section class="welcome-section">
        <h1 class="title" data-aos="fade-up" data-aos-duration="3000">
          Welcome to
          <span class="highlight"
            >Cambridge College of Information Technology</span
          >
        </h1>

        <div class="content-wrapper">
          <p class="paragraph" data-aos="fade-up" data-aos-duration="3000">
            <b>Cambridge College of Information Technology (CCIT)</b> is renowned for
            its commitment to providing world-class English courses tailored to
            individuals of all ages, from 5-year-old children to adults. With a
            dedicated mission to foster proficiency in reading, writing,
            listening, and speaking English, CCBE stands as a beacon of
            excellence in language education. Through innovative teaching
            methods and a nurturing environment, students embark on a
            transformative journey towards linguistic mastery. Whether honing
            the basics or delving into advanced concepts, CCBE ensures that each
            learner receives personalized attention and support to achieve their
            language learning goals.
          </p>

          <p
            class="paragraph call-to-action"
            data-aos="fade-up"
            data-aos-duration="3000"
          >
            <b>Join CCBE and unlock your potential for academic success!</b>
          </p>
        </div>
      </section>

      <v-container class="container-wrapper">
        <!-- <v-divider class="section-divider"></v-divider> -->

        <!-- Statistics Section -->
        <section class="stats-section" ref="statsSection">
          <h1 class="section-title" data-aos="fade-up" data-aos-duration="2000">
            OUR <span class="highlight">STRENGTH</span>
          </h1>

          <v-container>
            <v-row
              justify="center"
              align="center"
              class="stats-row"
              spacing="3"
            >
              <!-- Card 1: Happy Students -->
              <v-col
                cols="6"
                sm="3"
                md="3"
                class="text-center"
                data-aos="fade-down"
                data-aos-duration="1000"
              >
                <v-card class="stat-card">
                  <div class="stat-header">
                    <p class="stat-label">Happy Students</p>
                  </div>
                  <v-row justify="center">
                    <v-col cols="auto">
                      <v-img
                        src="@/assets/icons/Student.png"
                        class="stat-icon"
                      ></v-img>
                    </v-col>
                  </v-row>
                  <v-list-item-title class="stat-value-container">
                    <h3 class="stat-value">{{ happyStudents }} +</h3>
                  </v-list-item-title>
                </v-card>
              </v-col>

              <!-- Card 2: Qualified Teachers -->
              <v-col
                cols="6"
                sm="3"
                md="3"
                class="text-center"
                data-aos="fade-down"
                data-aos-duration="1500"
              >
                <v-card class="stat-card">
                  <div class="stat-header">
                    <p class="stat-label">Teachers</p>
                  </div>
                  <v-row justify="center">
                    <v-col cols="auto">
                      <v-img
                        src="@/assets/icons/Teacher.png"
                        class="stat-icon"
                      ></v-img>
                    </v-col>
                  </v-row>
                  <v-list-item-title class="stat-value-container">
                    <h3 class="stat-value">{{ qualifiedTeachers }} +</h3>
                  </v-list-item-title>
                </v-card>
              </v-col>

              <!-- Card 3: Years In The Field -->
              <v-col
                cols="6"
                sm="3"
                md="3"
                class="text-center"
                data-aos="fade-down"
                data-aos-duration="2000"
              >
                <v-card class="stat-card">
                  <div class="stat-header">
                    <p class="stat-label">Years In The Field</p>
                  </div>
                  <v-row justify="center">
                    <v-col cols="auto">
                      <v-img
                        src="@/assets/icons/Year.png"
                        class="stat-icon"
                      ></v-img>
                    </v-col>
                  </v-row>
                  <v-list-item-title class="stat-value-container">
                    <h3 class="stat-value">{{ yearsInField }} +</h3>
                  </v-list-item-title>
                </v-card>
              </v-col>

              <!-- Card 4: Branches -->
              <v-col
                cols="6"
                sm="3"
                md="3"
                class="text-center"
                data-aos="fade-down"
                data-aos-duration="2500"
              >
                <v-card class="stat-card">
                  <div class="stat-header">
                    <p class="stat-label">Branches</p>
                  </div>
                  <v-row justify="center">
                    <v-col cols="auto">
                      <v-img
                        src="@/assets/icons/Building.png"
                        class="stat-icon"
                      ></v-img>
                    </v-col>
                  </v-row>
                  <v-list-item-title class="stat-value-container">
                    <h3 class="stat-value">{{ branches }}</h3>
                  </v-list-item-title>
                </v-card>
              </v-col>
            </v-row>
          </v-container>
        </section>

        <!-- <v-divider class="section-divider"></v-divider> -->

        <!-- Awards Section -->
        <AwardsSection></AwardsSection>

        <!-- <v-divider class="section-divider"></v-divider> -->

        <!-- News Feed Section -->
        <NewsSliderPage></NewsSliderPage>

        <!-- <v-divider class="section-divider"></v-divider> -->

        <!-- Testimonials Section -->
        <section class="testimonials-section">
          <!-- <h1 class="section-title" data-aos="fade-up" data-aos-duration="3000">
            <span class="highlight">TESTIMONIALS</span>
          </h1> -->
          <TestimologyPage></TestimologyPage>
        </section>
      </v-container>
    </div>

    <ArrowButton></ArrowButton>
    <ChatBot></ChatBot>
    <FooterPage></FooterPage>
  </div>
</template>

<script>
import CaroselPage from "./CaroselPage.vue";
import NavBar from "./NavBar.vue";
import FooterPage from "./FooterPage.vue";
import ChatBot from "./ChatBot.vue";
import NewsSliderPage from "./NewsSliderPage.vue";
import TestimologyPage from "./TestimologyPage.vue";
import ArrowButton from "./ArrowButton.vue";
import AwardsSection from "./AwardsSection.vue";

export default {
  name: "HomePage",
  components: {
    CaroselPage,
    NavBar,
    FooterPage,
    ChatBot,
    NewsSliderPage,
    TestimologyPage,
    ArrowButton,
    AwardsSection,
  },
  data() {
    return {
      happyStudents: 0,
      qualifiedTeachers: 0,
      yearsInField: 9,
      branches: 6,
      logo: require("@/assets/CCIT - logo.png"),
    };
  },
  mounted() {
    this.initializeAnimations();
  },
  methods: {
    initializeAnimations() {
      const options = {
        root: null,
        rootMargin: "0px",
        threshold: 0.3,
      };

      const observer = new IntersectionObserver((entries, observer) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            this.animateCount("happyStudents", 10000, 2000);
            this.animateCount("qualifiedTeachers", 150, 1500);
            this.animateCount("yearsInField", 9, 1000);
            this.animateCount("branches", 6, 800);
            observer.disconnect();
          }
        });
      }, options);

      if (this.$refs.statsSection) {
        observer.observe(this.$refs.statsSection);
      }
    },

    animateCount(property, target, duration) {
      const start = this[property];
      const increment = (target - start) / (duration / 16);
      let current = start;

      const timer = setInterval(() => {
        current += increment;
        if (current >= target) {
          this[property] = target;
          clearInterval(timer);
        } else {
          this[property] = Math.round(current);
        }
      }, 16);
    },
  },
};
</script>

<style scoped>
.homepage {
  background: white;
  min-height: 100vh;
}

.main-content {
  background: linear-gradient(135deg, white 0%, white 100%);
}

/* Logo Section */
.logo-container {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1.5rem 0;
}

.logo-image {
  width: 250px;
  height: 200px;
  transition: transform 0.3s ease;
}

.logo-image:hover {
  transform: scale(1.05);
}

/* Welcome Section */
.welcome-section {
  
  text-align: center;
  background: white;
}

.title {
  font-size: 2rem;
  font-weight: 800;
  color: black;
  margin-bottom: 1.5rem;
  font-family: "Inter", "Poppins", sans-serif;
}

.highlight {
  background: linear-gradient(135deg, #ff6b35 0%, #ffa500 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.content-wrapper {
  max-width: 800px;
  margin: 0 auto;
}

.paragraph {
  font-family: "Inter", sans-serif;
  font-size: 1.1rem;
  line-height: 1.7;
  color: black;
  margin-bottom: 1.25rem;
  text-align: center;
}

.call-to-action {
  font-size: 1.3rem;
  color: black;
  font-weight: 700;
}

/* Container Wrapper */
.container-wrapper {
  background: white;
  padding: 0;
}

.section-divider {
  border-color: '';
  margin: 1.5rem 0;
}

/* Statistics Section */
.stats-section {
  padding: 3rem 0;
  background: linear-gradient(135deg, white 0%, white 100%);
}

.section-title {
  font-family: "Inter", "Poppins", sans-serif;
  font-size: 2rem;
  font-weight: 800;
  color: black;
  text-align: center;
  margin-bottom: 2.5rem;
  text-transform: uppercase;
}

.stat-card {
  background: linear-gradient(135deg, #2d2d2d 0%, #1a1a1a 100%);
  border: 2px solid #333;
  border-radius: 12px;
  padding: 1.5rem 0.75rem;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  height: 100%;
}

.stat-card::before {
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
}

.stat-card:hover::before {
  left: 100%;
}

.stat-card:hover {
  transform: translateY(-8px);
  border-color: #ffd700;
  box-shadow: 0 12px 25px rgba(255, 215, 0, 0.2);
}

.stat-header {
  margin-bottom: 1rem;
}

.stat-label {
  color: white;
  font-weight: 700;
  font-size: 1.1rem;
  font-family: "Inter", sans-serif;
  margin: 0;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.stat-icon {
  width: 60px;
  height: 60px;
  margin: 0.75rem auto;
  transition: transform 0.3s ease;
}

.stat-card:hover .stat-icon {
  transform: scale(1.1);
}

.stat-value-container {
  margin-top: 0.75rem;
}

.stat-value {
  font-size: 2rem;
  font-weight: 800;
  background: linear-gradient(135deg, #ffd700 0%, #ffa500 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  margin: 0;
  font-family: "Inter", sans-serif;
}

/* Testimonials Section */
.testimonials-section {
  padding: 2rem 0;
  background: linear-gradient(135deg, white 0%, white 100%);
}

/* Responsive Design */
@media (max-width: 960px) {
  .title {
    font-size: 2rem;
  }

  .section-title {
    font-size: 2.2rem;
  }

  .paragraph {
    font-size: 1rem;
  }

  .stat-value {
    font-size: 1.8rem;
  }

  .stat-label {
    font-size: 1rem;
  }

  .logo-image {
    width: 160px;
    height: 120px;
  }
}

@media (max-width: 768px) {
  .title {
    font-size: 1.8rem;
  }

  .section-title {
    font-size: 2rem;
  }

  .logo-image {
    width: 140px;
    height: 110px;
  }

  .stat-card {
    padding: 1.25rem 0.5rem;
  }

  .stat-value {
    font-size: 1.6rem;
  }

  .stat-label {
    font-size: 0.95rem;
  }

  .stat-icon {
    width: 50px;
    height: 50px;
  }

  .welcome-section {
    padding: 1.5rem 0.75rem;
  }

  .stats-section {
    padding: 2rem 0;
  }

  .testimonials-section {
    padding: 2rem 0;
  }
}

@media (max-width: 480px) {
  .title {
    font-size: 1.6rem;
  }

  .section-title {
    font-size: 1.8rem;
  }

  .logo-image {
    width: 120px;
    height: 90px;
  }

  .stat-card {
    padding: 1rem 0.5rem;
  }

  .stat-value {
    font-size: 1.4rem;
  }

  .stat-label {
    font-size: 0.9rem;
  }

  .stat-icon {
    width: 45px;
    height: 45px;
  }

  .paragraph {
    font-size: 0.95rem;
  }

  .call-to-action {
    font-size: 1.1rem;
  }

  .stats-row {
    margin: 0 -4px;
  }
}

/* Animation enhancements */
.stat-card {
  animation: float 3s ease-in-out infinite;
}

@keyframes float {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-4px);
  }
}

/* Glow effects for premium feel */
.highlight {
  position: relative;
}

.highlight::after {
  content: "";
  position: absolute;
  bottom: -1px;
  left: 0;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, #ffd700, transparent);
  opacity: 0.7;
}

/* Touch-friendly improvements */
@media (hover: none) {
  .stat-card:hover {
    transform: none;
  }
  
  .stat-card:hover .stat-icon {
    transform: none;
  }
}

/* Reduced motion support */
@media (prefers-reduced-motion: reduce) {
  .stat-card {
    animation: none;
  }
}
</style>