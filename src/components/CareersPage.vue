<template>
  <div class="careers-page">
    <NavBar></NavBar>
    
    <!-- Hero Section -->
    <section class="hero-section">
      <div class="hero-overlay">
        <div class="hero-content">
          <h1 class="hero-title" data-aos="fade-up" data-aos-duration="800">
            Join Our <span class="highlight">Team</span>
          </h1>
          <p class="hero-subtitle" data-aos="fade-up" data-aos-duration="800" data-aos-delay="200">
            Shape the Future of English Education
          </p>
          <p class="hero-description" data-aos="fade-up" data-aos-duration="800" data-aos-delay="400">
            Be part of a prestigious institution that prioritizes academic excellence and nurtures a thriving community of dedicated professionals. Together, we inspire confidence, build futures, and redefine success.
          </p>
          <div class="hero-actions" data-aos="fade-up" data-aos-duration="800" data-aos-delay="600">
            <button class="hero-btn primary" @click="scrollToOpenings">
              View Open Positions
            </button>
            <button class="hero-btn secondary" @click="openApplicationDialog">
              Quick Apply
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- Why Join Us Section -->
    <section class="benefits-section">
      <div class="container">
        <div class="section-header" data-aos="fade-up">
          <h2 class="section-title">Why Join <span class="highlight">CCBE</span></h2>
          <p class="section-subtitle">A Workplace That Values Growth and Excellence</p>
        </div>

        <div class="benefits-grid">
          <div class="benefit-card" v-for="(benefit, index) in benefits" :key="index" data-aos="fade-up" :data-aos-delay="index * 100">
            <div class="benefit-icon">
              <component :is="benefit.icon" />
            </div>
            <h3 class="benefit-title">{{ benefit.title }}</h3>
            <p class="benefit-description">{{ benefit.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Career Openings Section -->
    <section class="openings-section" ref="openingsSection">
      <div class="container">
        <div class="section-header" data-aos="fade-up">
          <h2 class="section-title">Current <span class="highlight">Openings</span></h2>
          <p class="section-subtitle">Explore Exciting Career Opportunities</p>
        </div>

        <!-- Career Cards Grid -->
        <div class="careers-grid">
          <div 
            v-for="(career, index) in careers" 
            :key="index" 
            class="career-card-wrapper"
            :data-aos="index % 2 === 0 ? 'fade-right' : 'fade-left'"
            :data-aos-delay="(index % 4) * 100"
          >
            <div class="career-card">
              <!-- Image Preview -->
              <div class="card-preview" @click="openImageModal(career.image)">
                <v-img 
                  :src="career.image" 
                  cover
                  class="career-image"
                  :alt="`Career opportunity at CCBE - ${career.title}`"
                  loading="lazy"
                ></v-img>
                <div class="preview-overlay">
                  <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M15 12C15 13.6569 13.6569 15 12 15C10.3431 15 9 13.6569 9 12C9 10.3431 10.3431 9 12 9C13.6569 9 15 10.3431 15 12Z" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M2 12C2 12 5 4 12 4C19 4 22 12 22 12C22 12 19 20 12 20C5 20 2 12 2 12Z" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  </svg>
                  <span>View Details</span>
                </div>
              </div>

              <!-- Card Content -->
              <div class="card-content">
                <div class="card-header">
                  <div class="position-badge">{{ career.type }}</div>
                  <div class="location-badge">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                      <path d="M21 10C21 17 12 23 12 23C12 23 3 17 3 10C3 7.61305 3.94821 5.32387 5.63604 3.63604C7.32387 1.94821 9.61305 1 12 1C14.3869 1 16.6761 1.94821 18.364 3.63604C20.0518 5.32387 21 7.61305 21 10Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                      <path d="M12 13C13.6569 13 15 11.6569 15 10C15 8.34315 13.6569 7 12 7C10.3431 7 9 8.34315 9 10C9 11.6569 10.3431 13 12 13Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    </svg>
                    <span>{{ career.location }}</span>
                  </div>
                </div>
                
                <h3 class="position-title">{{ career.title }}</h3>
                <p class="position-description">{{ career.description }}</p>
                
                <div class="position-details">
                  <div class="detail-item">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                      <path d="M12 22C17.5228 22 22 17.5228 22 12C22 6.47715 17.5228 2 12 2C6.47715 2 2 6.47715 2 12C2 17.5228 6.47715 22 12 22Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                      <path d="M12 6V12L16 14" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    </svg>
                    <span>{{ career.duration }}</span>
                  </div>
                  <div class="detail-item">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                      <path d="M12 1V23" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                      <path d="M17 5H9.5C8.57174 5 7.6815 5.36875 7.02513 6.02513C6.36875 6.6815 6 7.57174 6 8.5C6 9.42826 6.36875 10.3185 7.02513 10.9749C7.6815 11.6313 8.57174 12 9.5 12H14.5C15.4283 12 16.3185 12.3687 16.9749 13.0251C17.6313 13.6815 18 14.5717 18 15.5C18 16.4283 17.6313 17.3185 16.9749 17.9749C16.3185 18.6313 15.4283 19 14.5 19H6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    </svg>
                    <span>{{ career.salary }}</span>
                  </div>
                </div>
              </div>

              <!-- Card Footer -->
              <div class="card-footer">
                <button class="apply-btn" @click="applyForPosition(career)">
                  Apply Now
                  <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M5 12H19" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M12 5L19 12L12 19" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  </svg>
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Application CTA Section -->
    <section class="application-cta">
      <div class="container">
        <div class="cta-card" data-aos="fade-up">
          <div class="cta-content">
            <h2 class="cta-title">Ready to Join Our Team?</h2>
            <p class="cta-description">
              Submit your application today and take the first step towards a rewarding career at Cambridge College of British English.
            </p>
            <div class="cta-actions">
              <button class="cta-btn primary" @click="openApplicationDialog">
                Start Your Application
              </button>
              <a href="mailto:careers@ccbe.lk" class="cta-btn secondary">
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M4 4H20C21.1 4 22 4.9 22 6V18C22 19.1 21.1 20 20 20H4C2.9 20 2 19.1 2 18V6C2 4.9 2.9 4 4 4Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  <path d="M22 6L12 13L2 6" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
                <span>Email Us</span>
              </a>
            </div>
          </div>
          <div class="cta-image">
            <img src="https://ik.imagekit.io/u3wbiya66/Careers/C1.jpg?updatedAt=1760439871391" alt="Team Collaboration">
          </div>
        </div>
      </div>
    </section>

    <ArrowButton></ArrowButton>
    <ChatBot></ChatBot>
    <FooterPage></FooterPage>

    <!-- Image Modal -->
    <div v-if="showImageModal" class="image-modal" @click="closeImageModal">
      <div class="modal-content" @click.stop>
        <button class="modal-close" @click="closeImageModal">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M18 6L6 18" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            <path d="M6 6L18 18" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </button>
        <img :src="currentImage" alt="Career Details" class="modal-image">
      </div>
    </div>

    <!-- Application Modal -->
    <div v-if="showApplicationModal" class="application-modal" @click="closeApplicationModal">
      <div class="modal-content application-content" @click.stop>
        <div class="modal-header">
          <h2 class="modal-title">Apply for Position</h2>
          <p class="modal-subtitle">{{ selectedPosition?.title || 'General Application' }}</p>
          <button class="modal-close" @click="closeApplicationModal">
            <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M18 6L6 18" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
              <path d="M6 6L18 18" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </button>
        </div>

        <form class="application-form" @submit.prevent="submitApplication">
          <div class="form-grid">
            <div class="form-group">
              <label for="name">Full Name *</label>
              <input type="text" id="name" v-model="applicationForm.name" required>
            </div>
            <div class="form-group">
              <label for="email">Email Address *</label>
              <input type="email" id="email" v-model="applicationForm.email" required>
            </div>
            <div class="form-group">
              <label for="phone">Phone Number *</label>
              <input type="tel" id="phone" v-model="applicationForm.phone" required>
            </div>
            <div class="form-group">
              <label for="position">Position Applying For *</label>
              <input type="text" id="position" v-model="applicationForm.position" required>
            </div>
            <div class="form-group">
              <label for="experience">Years of Experience *</label>
              <select id="experience" v-model="applicationForm.experience" required>
                <option value="">Select experience</option>
                <option value="0-2">0-2 years</option>
                <option value="2-5">2-5 years</option>
                <option value="5-10">5-10 years</option>
                <option value="10+">10+ years</option>
              </select>
            </div>
            <div class="form-group">
              <label for="qualification">Highest Qualification *</label>
              <select id="qualification" v-model="applicationForm.qualification" required>
                <option value="">Select qualification</option>
                <option value="Diploma">Diploma</option>
                <option value="Bachelor's">Bachelor's Degree</option>
                <option value="Master's">Master's Degree</option>
                <option value="PhD">PhD</option>
              </select>
            </div>
            <div class="form-group full-width">
              <label for="coverLetter">Cover Letter *</label>
              <textarea id="coverLetter" v-model="applicationForm.coverLetter" rows="4" required placeholder="Tell us why you're interested in this position..."></textarea>
            </div>
            <div class="form-group full-width">
              <label for="resume">Upload Resume/CV *</label>
              <div class="file-upload">
                <input type="file" id="resume" @change="handleFileUpload" accept=".pdf,.doc,.docx" required>
                <label for="resume" class="file-label">
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M21 15V19C21 19.5304 20.7893 20.0391 20.4142 20.4142C20.0391 20.7893 19.5304 21 19 21H5C4.46957 21 3.96086 20.7893 3.58579 20.4142C3.21071 20.0391 3 19.5304 3 19V15" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M17 8L12 3L7 8" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    <path d="M12 3V15" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                  </svg>
                  <span>{{ applicationForm.resume ? applicationForm.resume.name : 'Choose file' }}</span>
                </label>
              </div>
            </div>
          </div>

          <div class="form-footer">
            <button type="button" class="cancel-btn" @click="closeApplicationModal">Cancel</button>
            <button type="submit" class="submit-btn" :disabled="isSubmitting">
              {{ isSubmitting ? 'Submitting...' : 'Submit Application' }}
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import NavBar from "./NavBar.vue";
import FooterPage from "./FooterPage.vue";
import ChatBot from "./ChatBot.vue";
import ArrowButton from './ArrowButton.vue';
import AOS from "aos";
import emailjs from "emailjs-com";

// SVG Icons
const GrowthIcon = {
  template: `
    <svg width="48" height="48" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M7 17L12 12L17 17" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M7 7L12 12L17 7" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M1 12H23" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
  `
};

const TrainingIcon = {
  template: `
    <svg width="48" height="48" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M12 19C15.866 19 19 15.866 19 12C19 8.13401 15.866 5 12 5C8.13401 5 5 8.13401 5 12C5 15.866 8.13401 19 12 19Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M9.09 9C9.3251 8.33167 9.78915 7.76811 10.4 7.40913C11.0108 7.05016 11.7289 6.91894 12.4272 7.03871C13.1255 7.15849 13.7588 7.52152 14.2151 8.06353C14.6713 8.60553 14.9211 9.29152 14.92 10C14.92 12 11.92 13 11.92 13" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M12 17H12.01" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
  `
};

const SupportIcon = {
  template: `
    <svg width="48" height="48" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M18 8C18 6.4087 17.3679 4.88258 16.2426 3.75736C15.1174 2.63214 13.5913 2 12 2C10.4087 2 8.88258 2.63214 7.75736 3.75736C6.63214 4.88258 6 6.4087 6 8C6 15 3 17 3 17H21C21 17 18 15 18 8Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M13.73 21C13.5542 21.3031 13.3019 21.5547 12.9982 21.7295C12.6946 21.9044 12.3504 21.9965 12 21.9965C11.6496 21.9965 11.3054 21.9044 11.0018 21.7295C10.6982 21.5547 10.4458 21.3031 10.27 21" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
  `
};

const CultureIcon = {
  template: `
    <svg width="48" height="48" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M17 21V19C17 17.9391 16.5786 16.9217 15.8284 16.1716C15.0783 15.4214 14.0609 15 13 15H5C3.93913 15 2.92172 15.4214 2.17157 16.1716C1.42143 16.9217 1 17.9391 1 19V21" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M9 11C11.2091 11 13 9.20914 13 7C13 4.79086 11.2091 3 9 3C6.79086 3 5 4.79086 5 7C5 9.20914 6.79086 11 9 11Z" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M23 21V19C22.9993 18.1137 22.7044 17.2528 22.1614 16.5523C21.6184 15.8519 20.8581 15.3516 20 15.13" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M16 3.13C16.8604 3.35031 17.623 3.85071 18.1676 4.55232C18.7122 5.25392 19.0078 6.11683 19.0078 7.005C19.0078 7.89318 18.7122 8.75608 18.1676 9.45769C17.623 10.1593 16.8604 10.6597 16 10.88" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
    </svg>
  `
};

export default {
  name: "CareersPage",
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
      showImageModal: false,
      showApplicationModal: false,
      currentImage: '',
      selectedPosition: null,
      isSubmitting: false,
      benefits: [
        {
          icon: GrowthIcon,
          title: "Professional Growth",
          description: "Continuous learning opportunities and clear career progression paths"
        },
        {
          icon: TrainingIcon,
          title: "Training & Development",
          description: "Regular workshops, certifications, and skill enhancement programs"
        },
        {
          icon: SupportIcon,
          title: "Supportive Environment",
          description: "Collaborative culture with mentorship and team support"
        },
        {
          icon: CultureIcon,
          title: "Positive Culture",
          description: "Inclusive workplace with regular team-building activities"
        }
      ],
      careers: [
        {
          image: "https://ik.imagekit.io/u3wbiya66/Careers/C1.jpg?updatedAt=1760439871391",
          title: "English Language Instructor",
          type: "Teaching",
          location: "Multiple Locations",
          description: "Deliver engaging English language lessons to students of all levels",
          duration: "Full-time",
          salary: "Competitive Salary"
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/Careers/C2.jpg?updatedAt=1760439871237",
          title: "Academic Coordinator",
          type: "Administration",
          location: "Galle Branch",
          description: "Oversee academic programs and ensure quality standards",
          duration: "Full-time",
          salary: "Attractive Package"
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/Careers/WhatsApp%20Image%202025-08-22%20at%2008.47.25_0277efb2.jpg?updatedAt=1755832794043",
          title: "Student Counselor",
          type: "Support",
          location: "Matara Branch",
          description: "Guide and support students in their educational journey",
          duration: "Full-time",
          salary: "Market Competitive"
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/Careers/WhatsApp%20Image%202025-08-22%20at%2008.46.00_3a637631.jpg?updatedAt=1755832782647",
          title: "IELTS Trainer",
          type: "Specialized Teaching",
          location: "All Branches",
          description: "Prepare students for IELTS exams with expert guidance",
          duration: "Part-time/Full-time",
          salary: "Based on Experience"
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/Careers/2.png?updatedAt=1755833509742",
          title: "Branch Manager",
          type: "Management",
          location: "Colombo",
          description: "Lead and manage branch operations and team performance",
          duration: "Full-time",
          salary: "Executive Package"
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0006.jpg?updatedAt=1737434201584",
          title: "Marketing Executive",
          type: "Marketing",
          location: "Head Office",
          description: "Promote our programs and engage with the community",
          duration: "Full-time",
          salary: "Commission Based"
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0011.jpg?updatedAt=1737435218639",
          title: "Content Developer",
          type: "Development",
          location: "Remote/On-site",
          description: "Create engaging educational materials and resources",
          duration: "Contract",
          salary: "Project Based"
        },
        {
          image: "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0009.jpg?updatedAt=1737435218715",
          title: "Administrative Assistant",
          type: "Support",
          location: "Piliyandala",
          description: "Provide administrative support and manage office operations",
          duration: "Full-time",
          salary: "Competitive"
        }
      ],
      applicationForm: {
        name: '',
        email: '',
        phone: '',
        position: '',
        experience: '',
        qualification: '',
        coverLetter: '',
        resume: null
      }
    };
  },
  methods: {
    scrollToOpenings() {
      this.$refs.openingsSection.scrollIntoView({ behavior: 'smooth' });
    },
    openImageModal(imageUrl) {
      this.currentImage = imageUrl;
      this.showImageModal = true;
      document.body.style.overflow = 'hidden';
    },
    closeImageModal() {
      this.showImageModal = false;
      document.body.style.overflow = '';
    },
    openApplicationDialog(position = null) {
      this.selectedPosition = position;
      this.showApplicationModal = true;
      document.body.style.overflow = 'hidden';
      
      // Reset the form first
      this.resetApplicationForm();
      
      // If a position is provided, set it in the form
      if (position) {
        this.applicationForm.position = position.title;
      }
    },
    closeApplicationModal() {
      this.showApplicationModal = false;
      document.body.style.overflow = '';
      this.resetApplicationForm();
    },
    applyForPosition(position) {
      this.openApplicationDialog(position);
    },
    handleFileUpload(event) {
      const file = event.target.files[0];
      if (file) {
        // Validate file type
        const validTypes = ['application/pdf', 'application/msword', 'application/vnd.openxmlformats-officedocument.wordprocessingml.document'];
        if (!validTypes.includes(file.type)) {
          alert('Please upload a PDF or Word document');
          return;
        }
        
        // Validate file size (5MB max)
        if (file.size > 5 * 1024 * 1024) {
          alert('File size should be less than 5MB');
          return;
        }
        
        this.applicationForm.resume = file;
      }
    },
    resetApplicationForm() {
      this.applicationForm = {
        name: '',
        email: '',
        phone: '',
        position: '',
        experience: '',
        qualification: '',
        coverLetter: '',
        resume: null
      };
    },
    async submitApplication() {
      this.isSubmitting = true;
      
      try {
        // Prepare template parameters
        const templateParams = {
          to_email: 'careers@ccbe.lk',
          from_name: this.applicationForm.name,
          from_email: this.applicationForm.email,
          phone: this.applicationForm.phone,
          position: this.applicationForm.position,
          experience: this.applicationForm.experience,
          qualification: this.applicationForm.qualification,
          cover_letter: this.applicationForm.coverLetter,
          message: `New Job Application - ${this.applicationForm.position}`
        };

        // Send email using EmailJS
        await emailjs.send(
          'service_s33obqe',
          'template_mz5d1yg',
          templateParams,
          'WIB0bG1OPslsktqa2'
        );

        // Open Google Form in new tab
        window.open(
          "https://docs.google.com/forms/d/e/1FAIpQLSco34ONLHBhIu6kfET6PNMynrJ-R5x9qRLIfGrYSquXd9tmwQ/viewform?fbzx=5328050623112666009",
          "_blank"
        );

        // Show success message
        alert('Application submitted successfully! Please complete the Google Form.');
        
        // Reset form and close modal
        this.closeApplicationModal();
        
      } catch (error) {
        console.error('Error submitting application:', error);
        alert('There was an error submitting your application. Please try again or email us directly.');
      } finally {
        this.isSubmitting = false;
      }
    }
  }
};
</script>

<style scoped>
.careers-page {
  background: #ffffff;
  min-height: 100vh;
  color: #333;
}

/* Hero Section */
.hero-section {
  height: 70vh;
  min-height: 600px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
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
}

.highlight {
  background: linear-gradient(135deg, #ffd166 0%, #ffb347 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-subtitle {
  font-family: 'Inter', sans-serif;
  font-size: 1.2rem;
  font-weight: 500;
  margin-bottom: 1.5rem;
  color: rgba(255,255,255,0.95);
  text-transform: uppercase;
  letter-spacing: 3px;
}

.hero-description {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  line-height: 1.6;
  color: rgba(255,255,255,0.9);
  max-width: 600px;
  margin: 0 auto 2rem;
}

.hero-actions {
  display: flex;
  gap: 1rem;
  justify-content: center;
  margin-top: 2rem;
}

.hero-btn {
  padding: 1rem 2rem;
  border-radius: 12px;
  font-family: 'Inter', sans-serif;
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
  transition: all 0.3s ease;
  border: none;
}

.hero-btn.primary {
  background: linear-gradient(135deg, #ffd166 0%, #ffb347 100%);
  color: #1a1a1a;
}

.hero-btn.primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 30px rgba(255, 209, 102, 0.3);
}

.hero-btn.secondary {
  background: transparent;
  color: white;
  border: 2px solid rgba(255,255,255,0.3);
}

.hero-btn.secondary:hover {
  background: rgba(255,255,255,0.1);
  border-color: white;
}

/* Container */
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
}

/* Benefits Section */
.benefits-section {
  padding: 6rem 1rem;
  background: #f8f9ff;
}

.section-header {
  text-align: center;
  margin-bottom: 4rem;
}

.section-title {
  font-family: 'Inter', sans-serif;
  font-size: 2.5rem;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 1rem;
}

.section-subtitle {
  font-family: 'Inter', sans-serif;
  font-size: 1.1rem;
  color: #666;
  font-weight: 400;
}

.benefits-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
  max-width: 1000px;
  margin: 0 auto;
}

.benefit-card {
  background: white;
  border-radius: 20px;
  padding: 2.5rem;
  text-align: center;
  box-shadow: 0 10px 40px rgba(0,0,0,0.08);
  border: 1px solid rgba(102,126,234,0.1);
  transition: all 0.3s ease;
}

.benefit-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 60px rgba(102,126,234,0.15);
}

.benefit-icon {
  color: #667eea;
  margin-bottom: 1.5rem;
  display: flex;
  justify-content: center;
}

.benefit-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.3rem;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 1rem;
}

.benefit-description {
  font-family: 'Inter', sans-serif;
  font-size: 0.95rem;
  line-height: 1.6;
  color: #555;
}

/* Openings Section */
.openings-section {
  padding: 6rem 1rem;
  background: white;
}

.careers-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 2rem;
}

.career-card-wrapper {
  perspective: 1000px;
}

.career-card {
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

.career-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 20px 60px rgba(102,126,234,0.15);
}

/* Card Preview */
.card-preview {
  position: relative;
  height: 200px;
  overflow: hidden;
  cursor: pointer;
}

.career-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.6s ease;
}

.career-card:hover .career-image {
  transform: scale(1.05);
}

.preview-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(to top, rgba(0,0,0,0.7), transparent 50%);
  display: flex;
  align-items: flex-end;
  padding: 1.5rem;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.card-preview:hover .preview-overlay {
  opacity: 1;
}

.preview-overlay svg {
  margin-right: 0.5rem;
}

.preview-overlay span {
  font-family: 'Inter', sans-serif;
  font-size: 0.9rem;
  color: white;
  font-weight: 500;
}

/* Card Content */
.card-content {
  padding: 1.5rem;
  flex: 1;
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 1rem;
}

.position-badge {
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

.location-badge {
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

.location-badge svg {
  color: #667eea;
}

.position-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.3rem;
  font-weight: 700;
  color: #1a1a1a;
  margin-bottom: 0.75rem;
  line-height: 1.3;
}

.position-description {
  font-family: 'Inter', sans-serif;
  font-size: 0.95rem;
  line-height: 1.6;
  color: #555;
  margin-bottom: 1.5rem;
}

.position-details {
  display: flex;
  gap: 1.5rem;
  margin-top: auto;
}

.detail-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-family: 'Inter', sans-serif;
  font-size: 0.85rem;
  color: #666;
}

.detail-item svg {
  color: #667eea;
  flex-shrink: 0;
}

/* Card Footer */
.card-footer {
  padding: 1.5rem;
  border-top: 1px solid rgba(102,126,234,0.1);
}

.apply-btn {
  width: 100%;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border: none;
  padding: 1rem 1.5rem;
  border-radius: 12px;
  font-family: 'Inter', sans-serif;
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.75rem;
}

.apply-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(102,126,234,0.3);
  gap: 1rem;
}

/* Application CTA */
.application-cta {
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

.cta-actions {
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
  text-decoration: none;
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

/* Image Modal */
.image-modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0,0,0,0.9);
  z-index: 1000;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
}

.modal-content {
  position: relative;
  max-width: 90vw;
  max-height: 90vh;
}

.modal-close {
  position: absolute;
  top: -40px;
  right: 0;
  background: rgba(255,255,255,0.1);
  border: none;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  color: white;
  transition: background 0.3s ease;
}

.modal-close:hover {
  background: rgba(255,255,255,0.2);
}

.modal-image {
  max-width: 100%;
  max-height: 90vh;
  object-fit: contain;
  border-radius: 8px;
}

/* Application Modal */
.application-modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0,0,0,0.8);
  z-index: 1001;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1rem;
  backdrop-filter: blur(5px);
}

.application-content {
  background: white;
  border-radius: 20px;
  max-width: 800px;
  max-height: 90vh;
  overflow-y: auto;
  width: 100%;
}

.modal-header {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 2rem;
  position: relative;
}

.modal-title {
  font-family: 'Inter', sans-serif;
  font-size: 1.8rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
}

.modal-subtitle {
  font-family: 'Inter', sans-serif;
  font-size: 1rem;
  opacity: 0.9;
}

.modal-header .modal-close {
  top: 1rem;
  right: 1rem;
  background: rgba(255,255,255,0.2);
}

.modal-header .modal-close:hover {
  background: rgba(255,255,255,0.3);
}

.application-form {
  padding: 2rem;
}

.form-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 1.5rem;
  margin-bottom: 2rem;
}

.form-group {
  display: flex;
  flex-direction: column;
}

.form-group.full-width {
  grid-column: 1 / -1;
}

.form-group label {
  font-family: 'Inter', sans-serif;
  font-size: 0.9rem;
  font-weight: 600;
  color: #555;
  margin-bottom: 0.5rem;
}

.form-group input,
.form-group select,
.form-group textarea {
  padding: 0.75rem 1rem;
  border: 2px solid rgba(102,126,234,0.2);
  border-radius: 8px;
  font-family: 'Inter', sans-serif;
  font-size: 1rem;
  transition: all 0.3s ease;
}

.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #667eea;
  box-shadow: 0 0 0 3px rgba(102,126,234,0.1);
}

.form-group textarea {
  resize: vertical;
  min-height: 100px;
}

.file-upload {
  position: relative;
}

.file-upload input[type="file"] {
  position: absolute;
  width: 0.1px;
  height: 0.1px;
  opacity: 0;
  overflow: hidden;
  z-index: -1;
}

.file-label {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.75rem 1.5rem;
  background: #f8f9ff;
  border: 2px dashed rgba(102,126,234,0.3);
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s ease;
  font-family: 'Inter', sans-serif;
  color: #667eea;
  font-weight: 500;
}

.file-label:hover {
  background: #f0f4ff;
  border-color: #667eea;
}

.file-label svg {
  color: #667eea;
}

.form-footer {
  display: flex;
  justify-content: flex-end;
  gap: 1rem;
  padding-top: 2rem;
  border-top: 1px solid rgba(0,0,0,0.1);
}

.cancel-btn {
  padding: 0.75rem 2rem;
  background: white;
  color: #666;
  border: 2px solid rgba(0,0,0,0.2);
  border-radius: 8px;
  font-family: 'Inter', sans-serif;
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.cancel-btn:hover {
  background: #f5f5f5;
  border-color: #666;
}

.submit-btn {
  padding: 0.75rem 2rem;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border: none;
  border-radius: 8px;
  font-family: 'Inter', sans-serif;
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.submit-btn:hover:not(:disabled) {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(102,126,234,0.3);
}

.submit-btn:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

/* Responsive Design */
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
  
  .form-grid {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 768px) {
  .hero-section {
    height: 60vh;
    min-height: 500px;
  }
  
  .hero-title {
    font-size: 2.2rem;
  }
  
  .hero-subtitle {
    font-size: 1rem;
    letter-spacing: 2px;
  }
  
  .hero-actions {
    flex-direction: column;
    align-items: center;
  }
  
  .hero-btn {
    width: 100%;
    max-width: 300px;
  }
  
  .section-title {
    font-size: 2rem;
  }
  
  .careers-grid {
    grid-template-columns: 1fr;
    max-width: 500px;
    margin: 0 auto;
  }
  
  .cta-actions {
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
  
  .benefits-grid {
    grid-template-columns: 1fr;
  }
  
  .benefit-card {
    padding: 2rem;
  }
  
  .application-content {
    margin: 0;
    border-radius: 0;
    height: 100vh;
  }
  
  .modal-header {
    padding: 1.5rem;
  }
  
  .application-form {
    padding: 1.5rem;
  }
  
  .form-footer {
    flex-direction: column;
  }
  
  .cancel-btn,
  .submit-btn {
    width: 100%;
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

.career-card-wrapper {
  animation: fadeInUp 0.6s ease forwards;
  opacity: 0;
}

/* Stagger animations */
.career-card-wrapper:nth-child(1) { animation-delay: 0.1s; }
.career-card-wrapper:nth-child(2) { animation-delay: 0.2s; }
.career-card-wrapper:nth-child(3) { animation-delay: 0.3s; }
.career-card-wrapper:nth-child(4) { animation-delay: 0.4s; }
.career-card-wrapper:nth-child(5) { animation-delay: 0.5s; }
.career-card-wrapper:nth-child(6) { animation-delay: 0.6s; }
.career-card-wrapper:nth-child(7) { animation-delay: 0.7s; }
.career-card-wrapper:nth-child(8) { animation-delay: 0.8s; }
</style>