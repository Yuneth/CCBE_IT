<template>
  <div class="for-schools-page">
    <NavBar></NavBar>
    <v-container class="main-container">
      <!-- Header Section -->
      <section class="header-section">
        <h1 class="page-title" data-aos="fade-up" data-aos-duration="3000">
          For Schools <span class="highlight">(Age 13-18)</span>
        </h1>
        <!-- <p class="intro-text" data-aos="fade-up" data-aos-duration="3000">
          This programme is suitable for secondary school students and provides better academic, social and career opportunities through English mastery. We provide learners with a friendly learning space where they can improve their language abilities through the four core skills.
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
              src="@/assets/course/PS1.jpg"
              class="content-image"
              alt="Secondary School Classroom"
            ></v-img>
          </v-col>
          <v-col cols="12" lg="6" class="text-col">
            <p class="paragraph" data-aos="fade-up" data-aos-duration="3000">
              This programme is suitable for secondary school students and provides better academic, social and career opportunities through English mastery. We provide learners with a friendly learning space where they can improve their language abilities through the four core skills of reading, writing, speaking and listening. This programme teaches learners to discover their own voices to communicate effortlessly.

              We use materials which provide learners with the language, vocabulary, grammar and the skills to do well in the Cambridge English examinations. We also encourage plenty of speaking practice in order to increase the learner's confidence in their English skills.
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

      <!-- Learning Outcomes Section -->
      <section class="content-section">
        <h1 class="section-title" data-aos="fade-up" data-aos-duration="3000">
          Learning Outcomes
        </h1>
        <v-row class="about-row">
          <v-col cols="12" lg="6" class="text-col">
            <p class="paragraph" data-aos="fade-up" data-aos-duration="3000">
              For secondary schoolers studying English, our learning outcomes are structured to cultivate a comprehensive proficiency in the language across multiple dimensions. Through a diverse curriculum encompassing literature analysis, writing proficiency, oral communication skills, and critical thinking, students develop a deep understanding of the English language and its application in various contexts.

              students will have demonstrated mastery in reading comprehension, literary analysis, and effective written expression. Moreover, they will have honed their verbal communication skills through presentations, discussions, and debates.
            </p>
          </v-col>
          <v-col cols="12" lg="6" class="image-col">
            <v-img
              data-aos="zoom-out"
              data-aos-duration="2000"
              src="@/assets/course/PS3.jpg"
              class="content-image"
              alt="Learning Activities"
            ></v-img>
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
                    src="@/assets/animation/exam.gif"
                    max-width="100"
                    height="100"
                  ></v-img>
                </v-row>
                <h5 class="detail-title"><b>Exams</b></h5>
                <p class="detail-text">A2,B1,B2,C1,C2 Proficiency</p>
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
                  <p class="detail-text">13 - 18 Years</p>
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
        <v-row class="levels-row">
          <v-col cols="12">
            <v-card class="level-card" color="#2d2d2d" elevation="10" data-aos="fade-left" data-aos-duration="1500">
              <v-card-title class="level-title" style="color: #ffd700">
                Elementary Level (A2 Key)
              </v-card-title>
              <v-card-text class="level-text">
                <b>This course is for beginners with basic English skills who are able to communicate in simple situations and is designed to prepare learners for the A2 KEY exam. By the end of this course,</b>
                <br><br>
                students will be able to:
                <ul class="bullet-list">
                  <li>Understand straightforward information and begin to express oneself in familiar topics</li>
                  <li>Understand basic sentences about relevant topics: family, shopping, local geography, etc.</li>
                  <li>Communicate regarding simple and routine tasks.</li>
                  <li>Describe in simple terms his/her background, environment and immediate needs.</li>
                </ul>
              </v-card-text>
            </v-card>
          </v-col>
          <v-col cols="12">
            <v-card class="level-card" color="#2d2d2d" elevation="10" data-aos="fade-right" data-aos-duration="2000">
              <v-card-title class="level-title" style="color: #ffa500">
                Pre-Intermediate Level (B1 Preliminary)
              </v-card-title>
              <v-card-text class="level-text">
                <b>This course is for learners who have fully mastered basic English and have practical language skills for everyday use. By the end of this course, learners will be taking the B1 Preliminary exam.</b>
                <br><br>
                By the end of this course, students will be able to:
                <ul class="bullet-list">
                  <li>Express oneself in a simple and general way in familiar situations.</li>
                  <li>Understand the main points of familiar matters (e.g. school, family, leisure).</li>
                  <li>Deal with most situations related to travelling in English speaking countries.</li>
                  <li>Describe experiences and events, dreams, hopes & ambitions with explanations.</li>
                </ul>
              </v-card-text>
            </v-card>
          </v-col>
          <v-col cols="12">
            <v-card class="level-card" color="#2d2d2d" elevation="10" data-aos="fade-left" data-aos-duration="2500">
              <v-card-title class="level-title" style="color: #4CAF50">
                Upper-Intermediate Level (B2 First)
              </v-card-title>
              <v-card-text class="level-text">
                <b>This course is for learners who know how to use English in a variety of situations in the real world and are able to take a course of study in English. This level effectively prepares them for the B2 First exam.</b>
                <br><br>
                By the end of this course, students will be able to:
                <ul class="bullet-list">
                  <li>Understand the main ideas of complex texts on concrete and abstract concepts</li>
                  <li>Interact and socialise with native English speakers smoothly</li>
                  <li>Produce clear, detailed texts on a wide range of subjects</li>
                </ul>
              </v-card-text>
            </v-card>
          </v-col>
          <v-col cols="12">
            <v-card class="level-card" color="#2d2d2d" elevation="10" data-aos="fade-right" data-aos-duration="3000">
              <v-card-title class="level-title" style="color: #2196F3">
                Advanced Level (C1 Advanced)
              </v-card-title>
              <v-card-text class="level-text">
                <b>This course is for learners who wish to use English for professional or higher education study purposes. By the end of this course, learners can take the C1 Advanced exam that meets the English language entrance requirements for many colleges, universities and companies worldwide.</b>
                <br><br>
                By the end of this course, students will be able to:
                <ul class="bullet-list">
                  <li>Understand a wide range of demanding and lengthy texts</li>
                  <li>Recognise meanings that are not straightforward</li>
                  <li>Express himself/herself spontaneously and fluently</li>
                  <li>Use language flexibly for social, academic or professional purposes</li>
                </ul>
              </v-card-text>
            </v-card>
          </v-col>
          <v-col cols="12">
            <v-card class="level-card" color="#2d2d2d" elevation="10" data-aos="fade-left" data-aos-duration="3000">
              <v-card-title class="level-title" style="color: #E91E63">
                Proficient Level (C2 Proficiency)
              </v-card-title>
              <v-card-text class="level-text">
                <b>This course is designed to prepare students for the final level of the Cambridge English exams, C2 Proficiency, where learners will reach the highest level of English proficiency. Universities and colleges throughout the world accept C2 Proficiency as a suitable English language entry requirement to courses of higher education or post-graduate study. It is also internationally recognised by many companies as an indication of a high level of competence in English. At this level, learners are approaching a standard of English similar to that of an educated native speaker.</b>
                <br><br>
                By the end of this course, students will be able to:
                <ul class="bullet-list">
                  <li>Understand virtually everything heard or read with ease</li>
                  <li>Read, write, understand and speak at native English speakers' level</li>
                  <li>Express himself/herself spontaneously and fluently</li>
                </ul>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </section>

      <v-divider class="section-divider"></v-divider>

      <!-- Learners Exams Section -->
      <section class="content-section">
        <h1 class="section-title" data-aos="fade-up" data-aos-duration="3000">
          Learners Exams
        </h1>
        <div class="exams-container">
          <v-expansion-panels class="exams-panels" variant="popout">
            <v-expansion-panel>
              <template #title>
                <span class="exam-title"><b>A2 Key Exam</b></span>
              </template>
              <template #text>
                <div class="exam-content">
                  <p>The A2 Key examination is an elementary-level exam that tests learner ability to deal with basic written and spoken communications in simple situations.</p>
                  <p>An A2 certificate demonstrates that the learner can:</p>
                  <ul>
                    <li>Understand and use basic phrases and expressions</li>
                    <li>Understand basic written English</li>
                    <li>Communicate with English speakers at a basic level</li>
                  </ul>
                  <p>A2 Key has 3 components:</p>
                  <ul>
                    <li>Reading and Writing (60 Minutes)</li>
                    <li>Listening (30 Minutes)</li>
                    <li>Speaking(8-10 Minutes)</li>
                  </ul>
                  <p>Each component contributes to a profile which defines the candidate's overall communicative language ability at this level.</p>
                </div>
              </template>
            </v-expansion-panel>
            <v-expansion-panel>
              <template #title>
                <span class="exam-title"><b>B1 Preliminary Exam</b></span>
              </template>
              <template #text>
                <div class="exam-content">
                  <p>The B1 Preliminary examination is for candidates who can use every day written and spoken English at an intermediate level.</p>
                  <p>A B1 Preliminary certificate demonstrates that the learner can:</p>
                  <ul>
                    <li>Read simple textbooks and articles in English</li>
                    <li>Write emails & articles on real-life subjects</li>
                    <li>Understand factual information</li>
                    <li>Show awareness of opinions and mood in spoken and written English.</li>
                  </ul>
                  <p>B1 Preliminary has 4 components:</p>
                  <ul>
                    <li>Reading (45 Minutes)</li>
                    <li>Writing (45 Minutes)</li>
                    <li>Listening (30 Minutes)</li>
                    <li>Speaking (12 Minutes)</li>
                  </ul>
                  <p>Each of the four test components contributes to a profile which defines the candidate's overall communicative language ability at this level.</p>
                </div>
              </template>
            </v-expansion-panel>
            <v-expansion-panel>
              <template #title>
                <span class="exam-title"><b>B2 First Exam</b></span>
              </template>
              <template #text>
                <div class="exam-content">
                  <p>The B2 First examination is for candidates who has practical language skills for everyday written and spoken situations.</p>
                  <p>With a B2 First qualification, learners will be prepared to:</p>
                  <ul>
                    <li>Start working in an English-speaking environment</li>
                    <li>Study at an upper-intermediate level, such as foundation or pathway courses</li>
                    <li>Live independently in an English-speaking country</li>
                  </ul>
                  <p>B2 First has 4 components:</p>
                  <ul>
                    <li>Reading and Use of English (75 Minutes)</li>
                    <li>Writing (80 Minutes)</li>
                    <li>Listening (40 Minutes)</li>
                    <li>Speaking(14 Minutes)</li>
                  </ul>
                  <p>Each of the four test components contributes to a profile which defines the candidate's overall communicative language ability at this level.</p>
                </div>
              </template>
            </v-expansion-panel>
            <v-expansion-panel>
              <template #title>
                <span class="exam-title"><b>C1 Advanced Exam</b></span>
              </template>
              <template #text>
                <div class="exam-content">
                  <p>The C1 Advanced examination is for candidates who can communicate in English at an advanced level and wish to pursue a managerial or professional career, or to follow a course of academic study.</p>
                  <p>C1 Advanced is aimed at learners who need to show that they can:</p>
                  <ul>
                    <li>Enrol for an academic course at university level</li>
                    <li>Effectively interact with people at managerial or professional level</li>
                    <li>Conduct challenging research</li>
                  </ul>
                  <p>C1 Advanced has 4 components:</p>
                  <ul>
                    <li>Reading and Use of English (90 Minutes)</li>
                    <li>Writing (90 Minutes)</li>
                    <li>Listening (40 Minutes)</li>
                    <li>Speaking(15 Minutes)</li>
                  </ul>
                  <p>Each of the four test components contributes to a profile which defines the candidate's overall communicative language ability at this level.</p>
                </div>
              </template>
            </v-expansion-panel>
            <v-expansion-panel>
              <template #title>
                <span class="exam-title"><b>C2 Proficiency Exam</b></span>
              </template>
              <template #text>
                <div class="exam-content">
                  <p>The C2 Proficiency examination is for candidates who have an appropriate level of educational and personal maturity and can use English for study or professional purposes. Success at this very advanced level exam represents a significant personal achievement.</p>
                  <p>C2 Proficiency is aimed for learners who need to show that they can:</p>
                  <ul>
                    <li>Follow a high level academic course and participate confidently in seminars and tutorials related to it</li>
                    <li>Lead and conduct research.</li>
                    <li>Partake in negotiation and persuasion at managerial and professional levels.</li>
                  </ul>
                  <p>C2 Proficiency has 4 components:</p>
                  <ul>
                    <li>Reading and Use of English (90 Minutes)</li>
                    <li>Writing (90 Minutes)</li>
                    <li>Listening (40 Minutes)</li>
                    <li>Speaking (16 Minutes)</li>
                  </ul>
                  <p>Each test components contributes to a profile which defines the candidate's overall communicative language ability at this level.</p>
                </div>
              </template>
            </v-expansion-panel>
          </v-expansion-panels>
        </div>
        <v-row>
          <v-col cols="12">
            <p class="paragraph mt-2" data-aos="fade-up" data-aos-duration="3000">
              By preparing for and successfully completing these exams, young learners not only gain a sense of accomplishment but also develop essential language skills that will serve them well in future academic and professional pursuits.
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
    name: 'ForSchoolPage',
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
.for-schools-page {
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

/* Programme Levels */
.levels-row {
  gap: 1.5rem;
}

.level-card {
  border-radius: 16px;
  margin-bottom: 1.5rem;
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
  transform: translateY(-8px);
  border-color: #ffd700;
  box-shadow: 0 12px 25px rgba(255, 215, 0, 0.2);
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

/* Exams Section */
.exams-container {
  margin: 2rem 0;
}

.exams-panels {
  width: 100%;
}

.exam-title {
  font-family: "Inter", sans-serif;
  font-size: 1.1rem;
  font-weight: 600;
  color: black;
}

.exam-content {
  font-family: "Inter", sans-serif;
  font-size: 1rem;
  color: black;
  line-height: 1.6;
}

.exam-content ul {
  list-style-type: disc;
  padding-left: 20px;
  margin: 0.5rem 0;
}

.exam-content li {
  margin-bottom: 0.3rem;
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
.detail-card, .level-card {
  animation: float 6s ease-in-out infinite;
}

.detail-card:nth-child(odd), .level-card:nth-child(odd) {
  animation-delay: 0s;
}

.detail-card:nth-child(even), .level-card:nth-child(even) {
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

.detail-card:hover, .level-card:hover {
  animation: none;
}

/* Additional Effects */
.detail-card::after, .level-card::after {
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

.detail-card:hover::after, .level-card:hover::after {
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

  .level-title {
    font-size: 1.1rem;
    padding: 1rem 1rem 0.5rem;
  }

  .level-text {
    padding: 0 1rem 1rem;
  }

  .exam-title {
    font-size: 1rem;
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