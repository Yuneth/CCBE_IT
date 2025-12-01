<template>
  <div class="ielts-page">
    <NavBar></NavBar>
    <v-container class="main-container">

      <!-- Header Section -->
      <section class="header-section">
        <h1 class="page-title" data-aos="fade-up" data-aos-duration="3000">
          <span class="highlight">IELTS</span>
        </h1>
      </section>

      <v-divider class="section-divider"></v-divider>

      <!-- What is IELTS Section -->
      <section class="content-section">
        <h2 class="section-title" data-aos="fade-up" data-aos-duration="3000">
          What is <span class="highlight">IELTS?</span>
        </h2>
        <v-row class="about-row">
          <v-col cols="12">
            <p class="paragraph" data-aos="fade-up" data-aos-duration="3000">
              The International English Language Testing System (IELTS) is an exam that measures the language proficiency of people who want to study, work or live abroad in English speaking countries. IELTS is the standard test used for university entry in Australia, New Zealand, Canada, United Kingdom (UK) and the United States (US).
              At CCBE, we have a course to prepare you for the IELTS exams in order to gain access to international colleges or universities, improve career opportunities or for migration purposes in English-speaking countries.
            </p>
          </v-col>
        </v-row>
      </section>

      <v-divider class="section-divider"></v-divider>

      <!-- Learning Outcomes Section -->
      <section class="content-section">
        <h1 class="section-title" data-aos="fade-up" data-aos-duration="3000">
          Learning Outcomes
        </h1>
        <v-row class="about-row">
          <v-col cols="12">
            <p class="paragraph" data-aos="fade-up" data-aos-duration="3000">
              With IELTS you can gain access to universities or colleges, improve employment prospects or migrate to English-speaking countries throughout the world.
            </p>
            <p class="paragraph" data-aos="fade-up" data-aos-duration="3000">
              We can provide you with the appropriate materials to study effectively for the IELTS at a comfortable pace. <strong>Mindset for IELTS</strong> is a comprehensive course designed to develop the learner's language, vocabulary, and grammar skills in an in-depth manner.
            </p>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12">
            <p class="paragraph mt-2" data-aos="fade-up" data-aos-duration="3000">
              Learners can take the Cambridge English exams as they progress through this programme and upon passing, will be awarded valuable certificates that will help open doors to the best colleges, universities and careers worldwide. Starting from a basic English skill level to the highest level, these courses train students on the use of language in real life through meaningful communication. At the end of this programme, students will be able to read, write, listen and speak at a high level of English fluency.
            </p>
          </v-col>
        </v-row>
      </section>

      <v-divider class="section-divider"></v-divider>

      <!-- Course Details Section -->
      <section class="course-details-section">
        <h2 class="section-title" data-aos="fade-up" data-aos-duration="3000">
          Course Details
        </h2>
        <v-container>
          <v-row justify="center" align="center" class="details-row">
            <v-col
              cols="8"
              sm="4"
              md="2"
              class="text-center d-flex justify-center"
            >
              <v-card
                class="detail-card"
                data-aos="fade-down"
                data-aos-easing="linear"
                data-aos-duration="1500"
              >
                <v-row justify="center" align="center">
                  <v-img
                    data-aos="zoom-out"
                    class="detail-icon"
                    src="@/assets/animation/timer.gif"
                    max-width="100"
                    height="100"
                  ></v-img>
                </v-row>
                <h5 class="detail-title"><b>Course Duration</b></h5>
                <p class="detail-text">12 Months</p>
              </v-card>
            </v-col>
            <v-col
              cols="8"
              sm="4"
              md="2"
              class="text-center d-flex justify-center"
            >
              <v-card
                class="detail-card"
                data-aos="fade-down"
                data-aos-easing="linear"
                data-aos-duration="1500"
              >
                <v-row justify="center" align="center">
                  <v-img
                    data-aos="zoom-out"
                    class="detail-icon"
                    src="@/assets/animation/calender.gif"
                    max-width="100"
                    height="100"
                  ></v-img>
                </v-row>
                <h5 class="detail-title"><b>Class Duration</b></h5>
                <p class="detail-text">Contact us to find out</p>
              </v-card>
            </v-col>
            <v-col
              cols="8"
              sm="4"
              md="2"
              class="text-center d-flex justify-center"
            >
              <v-card
                class="detail-card"
                data-aos="fade-down"
                data-aos-easing="linear"
                data-aos-duration="1500"
              >
                <v-row justify="center" align="center">
                  <v-img
                    data-aos="zoom-out"
                    class="detail-icon"
                    src="@/assets/animation/fee.gif"
                    max-width="100"
                    height="100"
                  ></v-img>
                </v-row>
                <h5 class="detail-title"><b>Course Fee</b></h5>
                <p class="detail-text">Contact us to find out</p>
              </v-card>
            </v-col>
            <v-col
              cols="8"
              sm="4"
              md="2"
              class="text-center d-flex justify-center"
            >
              <v-card
                class="detail-card"
                data-aos="fade-down"
                data-aos-easing="linear"
                data-aos-duration="1500"
              >
                <v-row justify="center" align="center">
                  <h1 class="detail-age-icon"><b>Age</b></h1>
                </v-row>
                <v-row justify="center" align="center">
                  <h5 class="detail-title"><b>Age Group</b></h5>
                </v-row>
                <v-row justify="center" align="center">
                  <p class="detail-text">16 and above</p>
                </v-row>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </section>

      <v-divider class="section-divider"></v-divider>

      <!-- Contact Button Section -->
      <section class="contact-section">
        <v-row justify="center" align="center" class="my-5">
          <v-btn
            class="contact-btn"
            rounded="xl"
            size="large"
            to="/contact"
            data-aos="zoom-in"
            data-aos-duration="2000"
          >
            <v-icon left>mdi-phone</v-icon>
            Contact Us
          </v-btn>
        </v-row>
      </section>

      <!-- Important Notice Section -->
      <section class="notice-section">
        <v-row justify="center" align="center" class="my-5">
          <h1 class="notice-title" data-aos="fade-up">IMPORTANT</h1>
        </v-row>
        <v-row justify="center" class="my-5">
          <h5 class="notice-text" data-aos="fade-up" data-aos-delay="200">
            Before enrolling, all students will take a Placement Test to
            determine which course is best-suited to their level of English
            language proficiency.
          </h5>
        </v-row>
      </section>
    </v-container>

    <ArrowButton></ArrowButton>
    <ChatBot></ChatBot>
    <FooterPage></FooterPage>
  </div>
</template>

<script>
import NavBar from '../NavBar.vue'
import FooterPage from '../FooterPage.vue'
import ChatBot from '../ChatBot.vue';
import ArrowButton from '../ArrowButton.vue';

// AOS Transition
import AOS from 'aos';
import 'aos/dist/aos.css';

export default {
    name: 'IELTSPage',
    components: {
        NavBar,
        FooterPage,
        ChatBot,
        ArrowButton
    },
    mounted() {
        window.scrollTo(0, 0);
        AOS.init(); // Initialize AOS when the component is mounted
    },
    data() {
        return {
            logo: require('@/assets/Logo.png'),
            show1: false,
        }
    },
}
</script>

<style scoped>
.ielts-page {
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

.intro-text {
  font-family: "Inter", sans-serif;
  font-size: 1.1rem;
  line-height: 1.7;
  color: #e0e0e0;
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
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

.about-row {
  align-items: center;
}

.content-image {
  border-radius: 16px;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
  transition: transform 0.3s ease;
}

.content-image:hover {
  transform: scale(1.02);
}

.paragraph {
  font-family: "Inter", sans-serif;
  font-size: 1.1rem;
  line-height: 1.8;
  color: black;
  text-align: justify;
}

/* Course Details Section */
.course-details-section {
  padding: 3rem 0;
}

.details-row {
  gap: 2rem;
}

.detail-card {
  background: linear-gradient(135deg, white 0%, white 100%);
  border: 2px solid #333;
  border-radius: 16px;
  padding: 2rem 1rem;
  width: 100%;
  max-width: 280px;
  height: 280px;
  transition: all 0.4s ease;
  position: relative;
  overflow: hidden;
}

.detail-card::before {
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

.detail-card:hover::before {
  left: 100%;
}

.detail-card:hover {
  transform: translateY(-10px);
  border-color: #ffd700;
  box-shadow: 0 15px 35px rgba(255, 215, 0, 0.25);
}

.detail-icon {
  margin-bottom: 1rem;
}

.detail-age-icon {
  font-family: "Inter", sans-serif;
  font-size: 2rem;
  color: black;
  margin-bottom: 1rem;
}

.detail-title {
  font-family: "Inter", sans-serif;
  font-size: 1.1rem;
  font-weight: 700;
  color: black;
  margin-bottom: 0.5rem;
}

.detail-text {
  font-family: "Inter", sans-serif;
  font-size: 1rem;
  color: black;
  margin: 0;
}

/* Contact Button */
.contact-section {
  padding: 2rem 0;
}

.contact-btn {
  background: linear-gradient(135deg, #ffd700 0%, #ffa500 100%) !important;
  color: #000000 !important;
  font-weight: 700 !important;
  font-family: "Inter", sans-serif !important;
  border: 2px solid transparent !important;
  border-radius: 30px !important;
  padding: 1rem 3rem !important;
  text-transform: none !important;
  transition: all 0.3s ease !important;
  font-size: 1.1rem !important;
}

.contact-btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 12px 30px rgba(255, 215, 0, 0.4) !important;
  border-color: #ffd700 !important;
}

/* Notice Section */
.notice-section {
  padding: 2rem 0;
  text-align: center;
}

.notice-title {
  font-family: "Inter", sans-serif;
  font-size: 2rem;
  font-weight: 800;
  color: #ff4444;
  margin-bottom: 1rem;
}

.notice-text {
  font-family: "Inter", sans-serif;
  font-size: 1.2rem;
  color: black;
  text-align: center;
  max-width: 800px;
  margin: 0 auto;
  line-height: 1.6;
}

/* Floating Animation */
.detail-card {
  animation: float 6s ease-in-out infinite;
}

.detail-card:nth-child(odd) {
  animation-delay: 0s;
}

.detail-card:nth-child(even) {
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

.detail-card:hover {
  animation: none;
}

/* Additional Effects */
.detail-card::after {
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

.detail-card:hover::after {
  opacity: 0.3;
}

/* Responsive Design */
@media (max-width: 960px) {
  .page-title {
    font-size: 2.8rem;
  }

  .section-title {
    font-size: 2rem;
  }

  .intro-text {
    font-size: 1.1rem;
  }

  .paragraph {
    font-size: 1rem;
  }

  .details-row {
    gap: 1.5rem;
  }
}

@media (max-width: 600px) {
  .page-title {
    font-size: 2.2rem;
  }

  .section-title {
    font-size: 1.8rem;
  }

  .intro-text {
    font-size: 1rem;
    text-align: left;
  }

  .header-section {
    padding: 2rem 0;
  }

  .paragraph {
    font-size: 0.95rem;
    text-align: left;
  }

  .detail-card {
    max-width: 250px;
    height: 250px;
    padding: 1.5rem 1rem;
  }

  .notice-title {
    font-size: 1.8rem;
  }

  .notice-text {
    font-size: 1rem;
    padding: 0 1rem;
  }

  .contact-btn {
    padding: 0.9rem 2.5rem !important;
    font-size: 1rem !important;
  }
}

/* Content Animation Enhancement */
.content-section {
  perspective: 1000px;
}

.about-row {
  transform-style: preserve-3d;
}

.center-container {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>