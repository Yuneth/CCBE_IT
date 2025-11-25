<template>
  <div class="careers-page">
    <NavBar></NavBar>
    <v-container class="main-container">
      <!-- Header Section -->
      <section class="header-section">
        <h1 class="page-title" data-aos="fade-up" data-aos-duration="3000">
          JOIN OUR <span class="highlight">TEAM</span>
        </h1>
        <p class="intro-text" data-aos="fade-up" data-aos-duration="3000">
          <b>Cambridge College of British English (CCBE)</b> Careers is your gateway to a world of possibilities and a launchpad for your professional aspirations. Be part of a prestigious institution that not only prioritizes academic excellence but also nurtures a thriving community of dedicated professionals. Together, we inspire confidence, build futures, and redefine what it means to succeed.
          Your career journey begins here at Cambridge College of British English!
        </p>
      </section>

      <!-- Careers Grid Section -->
      <section class="careers-section">
        <v-row class="careers-grid">
          <v-col 
            v-for="(career, index) in careers" 
            :key="index" 
            cols="12" 
            sm="6" 
            md="4" 
            lg="3"
          >
            <v-card 
              class="career-card" 
              data-aos="fade-up" 
              :data-aos-delay="(index % 4) * 100"
              data-aos-duration="3000"
            >
              <!-- Image Container -->
              <div class="image-container">
                <v-img 
                  :src="career.image" 
                  height="300" 
                  width= auto
                  cover
                  class="career-image"
                ></v-img>
                <div class="card-overlay">
                  <v-icon class="overlay-icon">mdi-account-tie</v-icon>
                  <span class="overlay-text">Career</span>
                </div>
              </div>
              
              <!-- Card Content -->
              <v-card-text class="card-content">
                <div class="career-badge">Opportunity</div>
                <h3 class="career-title">Join Our Team</h3>
              </v-card-text>
              
              <!-- Card Actions -->
              <v-card-actions class="card-actions">
                <v-btn 
                  class="apply-now-btn" 
                  variant="outlined" 
                  @click="openApplicationDialog"
                  block
                >
                  Apply Now
                  <v-icon right>mdi-arrow-right</v-icon>
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </section>

      <!-- Call to Action Section -->
      <section class="cta-section" data-aos="fade-up" data-aos-duration="3000">
        <div class="cta-content">
          <h2 class="cta-title">Ready to Start Your Journey?</h2>
          <p class="cta-description">
            Join our prestigious institution and be part of a team that's transforming English education.
          </p>
          <v-btn class="cta-button" size="large" @click="openApplicationDialog">
            Start Your Application
            <v-icon right>mdi-rocket-launch</v-icon>
          </v-btn>
        </div>
      </section>
    </v-container>

    <ChatBot></ChatBot>
    <FooterPage></FooterPage>

    <!-- Application Dialog -->
    <div class="text-center">
      <v-dialog v-model="dialog" max-width="800" persistent>
        <v-card class="application-dialog">
          <div class="dialog-header">
            <v-icon class="dialog-icon">mdi-briefcase-outline</v-icon>
            <h2 class="dialog-title">Career Application</h2>
          </div>
          
          <v-card-text class="dialog-content">
            <v-row dense>
              <v-col cols="12" md="6">
                <v-text-field 
                  label="Your Name" 
                  v-model="formData.name" 
                  required 
                  variant="outlined"
                  color="#FFD700"
                ></v-text-field>
              </v-col>
              <v-col cols="12" md="6">
                <v-select 
                  :items="['Teaching', 'Administration', 'Management', 'Marketing', 'Development', 'Business Development']" 
                  v-model="formData.position" 
                  label="Apply For" 
                  required 
                  variant="outlined"
                  color="#FFD700"
                ></v-select>
              </v-col>
              <v-col cols="12" md="6">
                <v-select 
                  :items="['Ambalangoda', 'Galle', 'Horana', 'Matara', 'Piliyandala']" 
                  v-model="formData.branch" 
                  label="Nearest Branch" 
                  required 
                  variant="outlined"
                  color="#FFD700"
                ></v-select>
              </v-col>
              <v-col cols="12" md="6">
                <v-select 
                  :items="['Masters', 'Bachelors', 'HND', 'Diploma', 'Certificate']" 
                  v-model="formData.qualifications" 
                  label="Highest Qualifications" 
                  required 
                  variant="outlined"
                  color="#FFD700"
                ></v-select>
              </v-col>
              <v-col cols="12" md="6">
                <v-select 
                  :items="['No Experience', '<2 Years', '<3 Years', '<4 Years', '4+ Years']" 
                  v-model="formData.experience" 
                  label="Experience" 
                  required 
                  variant="outlined"
                  color="#FFD700"
                ></v-select>
              </v-col>
              <v-col cols="12" md="6">
                <v-select 
                  :items="['Social Media', 'Website', 'Friend/Referral', 'Other']" 
                  v-model="formData.source" 
                  label="How did you hear about us?" 
                  required 
                  variant="outlined"
                  color="#FFD700"
                ></v-select>
              </v-col>
              <v-col cols="12" md="6">
                <v-text-field 
                  label="Contact Number" 
                  v-model="formData.contact" 
                  variant="outlined"
                  color="#FFD700"
                ></v-text-field>
              </v-col>
              <v-col cols="12" md="6">
                <v-text-field 
                  label="Email" 
                  v-model="formData.email" 
                  type="email" 
                  variant="outlined"
                  color="#FFD700"
                ></v-text-field>
              </v-col>
            </v-row>
            <small class="text-caption required-note">*indicates required field</small>
          </v-card-text>
          
          <v-divider></v-divider>
          
          <v-card-actions class="dialog-actions">
            <v-btn 
              class="cancel-btn" 
              variant="outlined" 
              @click="dialog = false"
            >
              <v-icon left>mdi-close-circle</v-icon>
              Cancel
            </v-btn>
            <v-btn 
              class="submit-btn" 
              variant="flat" 
              @click="sendInquiry"
              :loading="loading"
            >
              <v-icon left>mdi-check-circle</v-icon>
              Submit Application
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>

      <!-- Success Message Dialog -->
      <v-dialog v-model="successDialog" max-width="500">
        <v-card class="success-dialog">
          <v-card-title class="success-title">
            <v-icon color="#FFD700" size="48" class="mr-3">mdi-check-circle</v-icon>
            Application Sent Successfully
          </v-card-title>
          <v-card-text class="success-content text-center">
            <p>Your application has been successfully sent. Thank you for applying to join our team!</p>
            <p class="success-note">We will review your application and contact you shortly.</p>
          </v-card-text>
          <v-divider></v-divider>
          <v-card-actions class="success-actions">
            <v-spacer></v-spacer>
            <v-btn 
              class="close-success-btn" 
              variant="flat" 
              @click="successDialog = false"
            >
              Close
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </div>
  </div>
</template>

<script>
import NavBar from './NavBar.vue';
import FooterPage from './FooterPage.vue';
import ChatBot from './ChatBot.vue';
import AOS from 'aos';
import emailjs from "emailjs-com";

export default {
    name: 'CareersPage',
    data() {
        return {
            dialog: false,
            successDialog: false,
            loading: false,
            formData: {
                name: "",
                position: "",
                branch: "",
                qualifications: "",
                experience: "",
                source: "",
                contact: "",
                email: "",
            },
            careers: [
                {
                    image: "https://ik.imagekit.io/u3wbiya66/Careers/C1.jpg?updatedAt=1760439871391",
                },
                {
                    image: "https://ik.imagekit.io/u3wbiya66/Careers/C2.jpg?updatedAt=1760439871237",
                },
                {
                    image: "https://ik.imagekit.io/u3wbiya66/Careers/WhatsApp%20Image%202025-08-22%20at%2008.47.25_0277efb2.jpg?updatedAt=1755832794043",
                },
                {
                    image: "https://ik.imagekit.io/u3wbiya66/Careers/WhatsApp%20Image%202025-08-22%20at%2008.46.00_3a637631.jpg?updatedAt=1755832782647",
                },
                {
                    image: "https://ik.imagekit.io/u3wbiya66/Careers/2.png?updatedAt=1755833509742",
                },
                {
                    image: "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0006.jpg?updatedAt=1737434201584",
                },
                {
                    image: "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0011.jpg?updatedAt=1737435218639",
                },
                {
                    image: "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0009.jpg?updatedAt=1737435218715",
                },
                {
                    image: "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0007.jpg?updatedAt=1737435218724",
                },
                {
                    image: "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0010.jpg?updatedAt=1737435218885",
                },
                {
                    image: "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0012.jpg?updatedAt=1737435219022",
                },
                {
                    image: "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0008.jpg?updatedAt=1737435219045",
                },
                {
                    image: "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0015.jpg?updatedAt=1737435219046",
                },
                {
                    image: "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0014.jpg?updatedAt=1737435219125",
                },
            ],
        };
    },
    components: {
        NavBar,
        FooterPage,
        ChatBot,
    },
    mounted() {
        AOS.init();
    },
    methods: {
        openApplicationDialog() {
            this.dialog = true;
        },
        async sendInquiry() {
            this.loading = true;
            const formData = this.formData;

            try {
                // Send first email to info@ccbe.lk
                await emailjs.send('service_s33obqe', 'template_mz5d1yg', formData, 'WIB0bG1OPslsktqa2');
                console.log('First email sent successfully');

                // Send second email to Jobs@ccbe.lk
                await emailjs.send('service_eypw2ip', 'template_ygw1cnq', formData, 'sW9PkDNeVewlET9FF');
                console.log('Second email sent successfully');

                // Show success dialog
                this.successDialog = true;
                this.dialog = false;

                // Open Google Form in new tab
                window.open('https://docs.google.com/forms/d/e/1FAIpQLSco34ONLHBhIu6kfET6PNMynrJ-R5x9qRLIfGrYSquXd9tmwQ/viewform?fbzx=5328050623112666009', '_blank');

                // Reset the form
                this.clearForm();

            } catch (error) {
                console.error('Error sending emails:', error);
            } finally {
                this.loading = false;
            }
        },
        clearForm() {
            this.formData = {
                name: "",
                position: "",
                branch: "",
                qualifications: "",
                experience: "",
                source: "",
                contact: "",
                email: "",
            };
        },
    },
};
</script>

<style scoped>
.careers-page {
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
  max-width: 1000px;
  margin: 0 auto;
  text-align: center;
}

/* Careers Section */
.careers-section {
  padding: 2rem 0;
}

.careers-grid {
  margin: 0 -12px;
}

/* Career Card */
.career-card {
  background: linear-gradient(135deg, #2d2d2d 0%, #1a1a1a 100%);
  border: 2px solid #333;
  border-radius: 20px;
  overflow: hidden;
  transition: all 0.4s ease;
  height: 100%;
  position: relative;
  margin-bottom: 2rem;
}

.career-card::before {
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

.career-card:hover::before {
  left: 100%;
}

.career-card:hover {
  transform: translateY(-15px);
  border-color: #FFD700;
  box-shadow: 0 25px 50px rgba(255, 215, 0, 0.25);
}

/* Image Container */
.image-container {
  position: relative;
  overflow: hidden;
}

.career-image {
  transition: transform 0.4s ease;
  position: relative;
}

.career-card:hover .career-image {
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
}

.career-badge {
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

.career-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.4rem;
  font-weight: 700;
  color: #ffffff;
  line-height: 1.3;
  margin-bottom: 1rem;
  min-height: 3.5rem;
}

.career-description {
  font-family: 'Inter', sans-serif;
  font-size: 0.95rem;
  line-height: 1.6;
  color: #e0e0e0;
  margin-bottom: 0;
}

/* Card Actions */
.card-actions {
  padding: 0 2rem 2rem;
  display: flex;
  justify-content: center;
}

.apply-now-btn {
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

.apply-now-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(255, 215, 0, 0.4) !important;
  border-color: #FFD700 !important;
}

/* CTA Section */
.cta-section {
  text-align: center;
  padding: 4rem 0;
  margin-top: 2rem;
}

.cta-content {
  max-width: 600px;
  margin: 0 auto;
}

.cta-title {
  font-family: 'Inter', sans-serif;
  font-size: 2.5rem;
  font-weight: 700;
  color: #ffffff;
  margin-bottom: 1rem;
}

.cta-description {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  line-height: 1.6;
  color: #e0e0e0;
  margin-bottom: 2rem;
}

.cta-button {
  background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%) !important;
  color: #000000 !important;
  font-weight: 700 !important;
  font-family: 'Inter', sans-serif !important;
  border: 2px solid transparent !important;
  border-radius: 30px !important;
  padding: 1rem 3rem !important;
  text-transform: none !important;
  transition: all 0.3s ease !important;
  font-size: 1.1rem !important;
  box-shadow: 0 8px 25px rgba(255, 215, 0, 0.3) !important;
}

.cta-button:hover {
  transform: translateY(-3px);
  box-shadow: 0 12px 30px rgba(255, 215, 0, 0.4) !important;
  border-color: #FFD700 !important;
}

/* Dialog Styles */
.application-dialog {
  background: linear-gradient(135deg, #1a1a1a 0%, #2d2d2d 100%) !important;
  border: 2px solid #333;
  border-radius: 20px;
  overflow: hidden;
}

.dialog-header {
  background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%);
  padding: 2rem;
  text-align: center;
  color: #000000;
}

.dialog-icon {
  font-size: 3rem !important;
  margin-bottom: 1rem;
}

.dialog-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.8rem;
  font-weight: 700;
  margin: 0;
}

.dialog-content {
  color: white !important;
  padding: 2rem !important;
}

.required-note {
  color: #FFD700 !important;
  font-weight: 600;
}

.dialog-actions {
  padding: 1.5rem 2rem !important;
  display: flex;
  justify-content: space-between;
  gap: 1rem;
}

.cancel-btn {
  color: #ff6b6b !important;
  border-color: #ff6b6b !important;
  font-weight: 600;
}

.submit-btn {
  background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%) !important;
  color: #000000 !important;
  font-weight: 600;
}

/* Success Dialog */
.success-dialog {
  background: linear-gradient(135deg, #1a1a1a 0%, #2d2d2d 100%) !important;
  border: 2px solid #333;
  border-radius: 20px;
  overflow: hidden;
}

.success-title {
  background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%);
  color: #000000 !important;
  font-family: 'Inter', sans-serif;
  font-weight: 700;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
}

.success-content {
  padding: 2rem !important;
  color: #e0e0e0;
  font-family: 'Inter', sans-serif;
}

.success-note {
  color: #FFD700;
  font-weight: 600;
  margin-top: 1rem;
}

.success-actions {
  padding: 1.5rem 2rem !important;
}

.close-success-btn {
  background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%) !important;
  color: #000000 !important;
  font-weight: 600;
}

/* Floating Animation */
.career-card {
  animation: float 6s ease-in-out infinite;
}

.career-card:nth-child(4n+1) {
  animation-delay: 0s;
}

.career-card:nth-child(4n+2) {
  animation-delay: 1.5s;
}

.career-card:nth-child(4n+3) {
  animation-delay: 3s;
}

.career-card:nth-child(4n+4) {
  animation-delay: 4.5s;
}

@keyframes float {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}

.career-card:hover {
  animation: none;
}

/* Additional Effects */
.career-card::after {
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

.career-card:hover::after {
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
  
  .career-title {
    font-size: 1.2rem;
    min-height: auto;
  }
  
  .cta-title {
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
  
  .card-content {
    padding: 1.5rem;
  }
  
  .career-title {
    font-size: 1.1rem;
  }
  
  .career-description {
    font-size: 0.9rem;
  }
  
  .card-actions {
    padding: 0 1.5rem 1.5rem;
  }
  
  .cta-title {
    font-size: 1.8rem;
  }
  
  .cta-description {
    font-size: 1rem;
  }
  
  .dialog-actions {
    flex-direction: column;
  }
}
</style>