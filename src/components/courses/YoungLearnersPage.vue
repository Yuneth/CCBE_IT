<template>
  <div class="young-learners-page">
    <NavBar></NavBar>
    <v-container class="main-container">
      <!-- Header Section -->
      <section class="header-section">
        <h1 class="page-title" data-aos="fade-up" data-aos-duration="3000">
          <span class="highlight">YOUNG LEARNERS</span>
        </h1>
        <!-- <p class="intro-text" data-aos="fade-up" data-aos-duration="3000">
          This programme for primary school students builds children's English skills to prepare them for academic excellence and beyond. Through engaging topics and interactive activities, we inspire young learners to develop confidence in their English abilities.
        </p> -->
      </section>

      <v-divider class="section-divider"></v-divider>

      <!-- Course Overview Section -->
      <section class="content-section">
        <h1 class="section-title" data-aos="fade-up" data-aos-duration="3000">
          Course Overview
        </h1>
        <v-row class="about-row">
          <v-col cols="12" lg="6" class="image-col">
            <v-img
              data-aos="zoom-out"
              data-aos-duration="2000"
              src="https://ik.imagekit.io/u3wbiya66/PXL_20250128_092657658-EDIT.jpg?updatedAt=1738392311029"
              class="content-image"
              alt="Young Learners Classroom"
            ></v-img>
          </v-col>
          <v-col cols="12" lg="6" class="text-col">
            <p class="paragraph" data-aos="fade-up" data-aos-duration="3000">
              This programme for primary school students builds children's English skills to prepare them for academic excellence and beyond. The topics were developed to inspire young learners through fun and fascinating information about the real world. We keep children motivated to learn through songs, games, video activities, language presentations, and group projects.

              Children will improve their language abilities step by step in a friendly and co-operative environment that builds their confidence in their English. They will learn how to communicate and become little storytellers while striving for success in different areas of their lives.
            </p>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12">
            <p class="paragraph mt-2" data-aos="fade-up" data-aos-duration="3000">
              Lessons from each level are based on subjects and activities that are relatable to all children, regardless of their first language. The programme leads to a series of tests from Cambridge English that are tailored for children who may not be used to taking exams. With no pass or fail grades, the tests provide every student with a reward for their efforts.
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
          <v-col cols="12" lg="6" class="text-col">
            <p class="paragraph" data-aos="fade-up" data-aos-duration="3000">
              For primary schoolers, our learning outcomes are meticulously crafted to encompass a holistic approach to education, nurturing their academic, social, and emotional development. Through a diverse curriculum, students engage in a range of subjects and activities designed to cultivate critical thinking skills, creativity, and a thirst for knowledge.

              Additionally, our curriculum emphasizes the importance of character development, fostering qualities such as empathy, resilience, and responsibility. Through collaborative projects, extracurricular activities, and community involvement, our students gain valuable life skills and a sense of global citizenship.
            </p>
          </v-col>
          <v-col cols="12" lg="6" class="image-col">
            <v-img
              data-aos="zoom-out"
              data-aos-duration="2000"
              src="https://ik.imagekit.io/u3wbiya66/2024_11_07_15_33_IMG_8396.jpg?updatedAt=1737709328196"
              class="content-image"
              alt="Learning Activities"
            ></v-img>
          </v-col>
        </v-row>
        
        <!-- Skills Cards -->
        <v-row align="center" justify="center" dense class="skills-row">
          <v-col cols="12" md="6" data-aos="fade-right" data-aos-duration="3000">
            <v-card class="skill-card" color="#2d2d2d">
              <v-card-title class="skill-title">
                <v-icon left color="#ffd700">mdi-book</v-icon>
                Reading
              </v-card-title>
              <v-card-text class="skill-text">
                Starting with recognizing simple words and phrases, children will progress towards reading and understanding full sentences and stories with confidence.
              </v-card-text>
            </v-card>
          </v-col>
          <v-col cols="12" md="6" data-aos="fade-right" data-aos-duration="3000">
            <v-card class="skill-card" color="#2d2d2d">
              <v-card-title class="skill-title">
                <v-icon left color="#ffd700">mdi-pencil</v-icon>
                Writing
              </v-card-title>
              <v-card-text class="skill-text">
                Starting with writing and spelling simple words, children will then progress to learning how to write short stories.
              </v-card-text>
            </v-card>
          </v-col>
          <v-col cols="12" md="6" data-aos="fade-left" data-aos-duration="3000">
            <v-card class="skill-card" color="#2d2d2d">
              <v-card-title class="skill-title">
                <v-icon left color="#ffd700">mdi-speaker</v-icon>
                Listening
              </v-card-title>
              <v-card-text class="skill-text">
                Starting with listening to short conversations, children will progress to being able to understand simple English stories.
              </v-card-text>
            </v-card>
          </v-col>
          <v-col cols="12" md="6" data-aos="fade-left" data-aos-duration="3000">
            <v-card class="skill-card" color="#2d2d2d">
              <v-card-title class="skill-title">
                <v-icon left color="#ffd700">mdi-chat</v-icon>
                Speaking
              </v-card-title>
              <v-card-text class="skill-text">
                Starting with answering simple questions, children will progress towards expressing themselves fluently through speech.
              </v-card-text>
            </v-card>
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
              clas2="text-center d-flex justify-center"
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
                  <p class="detail-text">06 - 12 Years</p>
                </v-row>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </section>

      <v-divider class="section-divider"></v-divider>

      <!-- Programme Levels Section -->
      <section class="content-section">
        <h1 class="section-title" data-aos="fade-up" data-aos-duration="3000">
          Programme Levels
        </h1>
        <div class="center-container">
          <v-container>
            <v-row justify="center" align="center">
              <v-timeline side="end" class="timeline-custom">
                <v-timeline-item dot-color="#FF5722" size="small">
                  <v-card class="level-card" color="#2d2d2d" elevation="10" data-aos="fade-left" data-aos-duration="1500">
                    <v-card-title class="level-title" style="color: #FF5722">
                      Beginner Level (Starters)
                    </v-card-title>
                    <v-card-text class="level-text">
                      In the beginner level, children will be able to:
                      <ul class="bullet-list">
                        <li>Read and write simple sentences</li>
                        <li>Spell simple words</li>
                        <li>Understand short conversations</li>
                      </ul>
                    </v-card-text>
                  </v-card>
                </v-timeline-item>
                <v-timeline-item dot-color="#FF9800" size="small">
                  <v-card class="level-card" color="#2d2d2d" elevation="10" data-aos="fade-left" data-aos-duration="2000">
                    <v-card-title class="level-title" style="color: #FF9800">
                      Intermediate Level (Movers)
                    </v-card-title>
                    <v-card-text class="level-text">
                      In the intermediate level, children will be able to:
                      <ul class="bullet-list">
                        <li>Understand simple English stories</li>
                        <li>Write and understand simple sentences</li>
                        <li>Answer basic questions using correct expressions</li>
                      </ul>
                    </v-card-text>
                  </v-card>
                </v-timeline-item>
                <v-timeline-item dot-color="#4CAF50" size="small">
                  <v-card class="level-card" color="#2d2d2d" elevation="10" data-aos="fade-left" data-aos-duration="2500">
                    <v-card-title class="level-title" style="color: #4CAF50">
                      Higher Level (Flyers)
                    </v-card-title>
                    <v-card-text class="level-text">
                      In the higher levels, children will be able to:
                      <ul class="bullet-list">
                        <li>Understand longer texts about everyday topics</li>
                        <li>Write short stories and short messages</li>
                        <li>Tell a story using their own ideas</li>
                      </ul>
                    </v-card-text>
                  </v-card>
                </v-timeline-item>
              </v-timeline>
            </v-row>
          </v-container>
        </div>
      </section>

      <v-divider class="section-divider"></v-divider>

      <!-- YLE Exams Section -->
      <section class="content-section">
        <h1 class="section-title" data-aos="fade-up" data-aos-duration="3000">
          Young Learners English (YLE) Exams
        </h1>
        <v-row class="about-row">
          <v-col cols="12" lg="6" class="image-col">
            <v-img
              data-aos="zoom-out"
              data-aos-duration="2000"
              src="https://ik.imagekit.io/u3wbiya66/6.jpg?updatedAt=1737779168033"
              class="content-image"
              alt="YLE Exams"
            ></v-img>
          </v-col>
          <v-col cols="12" lg="6" class="text-col">
            <p class="paragraph" data-aos="fade-up" data-aos-duration="3000">
              The Young Learners English (YLE) exams serve as a valuable assessment tool for young language learners, offering a comprehensive evaluation of their English proficiency. Tailored specifically for children, these exams provide a supportive and engaging environment where students can demonstrate their language skills with confidence.

              Divided into three levels—Pre A1 Starters, A1 Movers and A2 Flyers—the YLE exams cover a range of language competencies, including listening, speaking, reading, and writing. By preparing for and successfully completing these exams, young learners not only gain a sense of accomplishment but also develop essential language skills that will serve them well in future academic and professional pursuits.

              Moreover, the YLE exams provide teachers and parents with valuable insights into students' progress and areas for improvement, ensuring a tailored and effective approach to language education.
            </p>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12">
            <p class="paragraph mt-2" data-aos="fade-up" data-aos-duration="3000">
              Lessons from each level are based on subjects and activities that are relatable to all children, regardless of their first language. The programme leads to a series of tests from Cambridge English that are tailored for children who may not be used to taking exams. With no pass or fail grades, the tests provide every student with a reward for their efforts.
            </p>
          </v-col>
        </v-row>
      </section>

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
            Before enrolling, all children will take a Placement Test to
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
    name: 'YoungLearnersPage',
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
        }
    },
}
</script>

<style scoped>
.young-learners-page {
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
  color: #ffffff;
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

/* Skills Cards */
.skills-row {
  margin-top: 2rem;
}

.skill-card {
  border-radius: 16px;
  margin-bottom: 1.5rem;
  transition: all 0.4s ease;
  border: 2px solid #333;
  position: relative;
  overflow: hidden;
}

.skill-card::before {
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

.skill-card:hover::before {
  left: 100%;
}

.skill-card:hover {
  transform: translateY(-8px);
  border-color: #ffd700;
  box-shadow: 0 12px 25px rgba(255, 215, 0, 0.2);
}

.skill-title {
  font-family: "Inter", sans-serif;
  font-weight: 700;
  color: #ffd700;
  padding: 1.5rem 1.5rem 0.5rem;
  font-size: 1.2rem;
}

.skill-text {
  font-family: "Inter", sans-serif;
  font-size: 1rem;
  color: #e0e0e0;
  padding: 0 1.5rem 1.5rem;
  line-height: 1.6;
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

/* Programme Levels */
.timeline-custom {
  padding: 2rem 0;
}

.level-card {
  border-radius: 16px;
  margin: 1rem 0;
  border: 2px solid #333;
  transition: all 0.4s ease;
  position: relative;
  overflow: hidden;
}

.level-card::before {
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

.level-card:hover::before {
  left: 100%;
}

.level-card:hover {
  transform: translateX(5px);
  border-color: #ffd700;
  box-shadow: 0 10px 25px rgba(255, 215, 0, 0.2);
}

.level-title {
  font-family: "Inter", sans-serif;
  font-weight: 700;
  padding: 1.5rem 1.5rem 0.5rem;
  font-size: 1.3rem;
}

.level-text {
  font-family: "Inter", sans-serif;
  font-size: 1rem;
  color: #e0e0e0;
  padding: 0 1.5rem 1.5rem;
  line-height: 1.6;
}

.bullet-list {
  list-style-type: disc;
  padding-left: 20px;
  margin-top: 0.5rem;
}

.bullet-list li {
  margin-bottom: 0.5rem;
  line-height: 1.5;
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
.detail-card, .skill-card, .level-card {
  animation: float 6s ease-in-out infinite;
}

.detail-card:nth-child(odd), .skill-card:nth-child(odd), .level-card:nth-child(odd) {
  animation-delay: 0s;
}

.detail-card:nth-child(even), .skill-card:nth-child(even), .level-card:nth-child(even) {
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

.detail-card:hover, .skill-card:hover, .level-card:hover {
  animation: none;
}

/* Additional Effects */
.detail-card::after, .skill-card::after, .level-card::after {
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

.detail-card:hover::after, .skill-card:hover::after, .level-card:hover::after {
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

  .skill-title, .level-title {
    font-size: 1.1rem;
    padding: 1rem 1rem 0.5rem;
  }

  .skill-text, .level-text {
    padding: 0 1rem 1rem;
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