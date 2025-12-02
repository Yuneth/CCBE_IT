<template>
  <div class="contact-view">
    <!-- Hero Section -->
    <section class="contact-hero py-5">
      <div class="container">
        <div class="row align-items-center">
          <div class="col-lg-6">
            <h1 class="hero-title">Contact <span class="highlight">Us</span> </h1>
            <p class="lead">
              Get in touch with Cambridge College of Information Technology. 
              We're here to answer all your questions.
            </p>
          </div>
          <div class="col-lg-6 text-center">
            <div class="hero-icon">
              <i class="fas fa-headset"></i>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Info & Form -->
    <section class="contact-main py-5">
      <div class="container">
        <div class="row">
          <!-- Contact Information -->
          <div class="col-lg-5 mb-5 mb-lg-0">
            <div class="contact-info card-theme p-4 h-100">
              <h2 class="mb-4">Get in Touch</h2>
              
              <div class="contact-item mb-4">
                <div class="contact-icon">
                  <i class="fas fa-map-marker-alt"></i>
                </div>
                <div class="contact-details">
                  <h4>Visit Our Campus</h4>
                  <p>{{ address }}</p>
                </div>
              </div>
              
              <div class="contact-item mb-4">
                <div class="contact-icon">
                  <i class="fas fa-phone"></i>
                </div>
                <div class="contact-details">
                  <h4>Call Us</h4>
                  <p>
                    <a :href="`tel:${mobile}`">{{ mobile }}</a>
                  </p>
                </div>
              </div>
              
              <div class="contact-item mb-4">
                <div class="contact-icon">
                  <i class="fab fa-whatsapp"></i>
                </div>
                <div class="contact-details">
                  <h4>WhatsApp</h4>
                  <p>
                    <a :href="`https://wa.me/${whatsapp.replace('+', '')}`" target="_blank">
                      {{ whatsapp }}
                    </a>
                  </p>
                </div>
              </div>
              
              <div class="contact-item mb-4">
                <div class="contact-icon">
                  <i class="fas fa-envelope"></i>
                </div>
                <div class="contact-details">
                  <h4>Email Us</h4>
                  <p>
                    <a :href="`mailto:${email}`">{{ email }}</a>
                  </p>
                </div>
              </div>
              
              <div class="contact-item mb-4">
                <div class="contact-icon">
                  <i class="fas fa-clock"></i>
                </div>
                <div class="contact-details">
                  <h4>Business Hours</h4>
                  <p>Monday - Friday: 8:00 AM - 6:00 PM</p>
                  <p>Saturday: 8:00 AM - 1:00 PM</p>
                  <p>Sunday: Closed</p>
                </div>
              </div>
              
              <div class="social-links mt-5">
                <h4 class="mb-3">Follow Us</h4>
                <div class="d-flex gap-3">
                  <a href="#" class="social-link">
                    <i class="fab fa-facebook-f"></i>
                  </a>
                  <a href="#" class="social-link">
                    <i class="fab fa-youtube"></i>
                  </a>
                  <a href="#" class="social-link">
                    <i class="fab fa-linkedin-in"></i>
                  </a>
                  <a href="#" class="social-link">
                    <i class="fab fa-instagram"></i>
                  </a>
                </div>
              </div>
            </div>
          </div>
          
          <!-- Contact Form -->
          <div class="col-lg-7">
            <div class="contact-form card-theme p-4">
              <h2 class="mb-4">Send Us a Message</h2>
              
              <form @submit.prevent="submitForm" id="contactForm">
                <div v-if="formSuccess" class="alert alert-success">
                  <i class="fas fa-check-circle"></i> {{ formSuccess }}
                </div>
                
                <div v-if="formError" class="alert alert-danger">
                  <i class="fas fa-exclamation-circle"></i> {{ formError }}
                </div>
                
                <div class="row">
                  <div class="col-md-6 mb-3">
                    <label for="name" class="form-label">Full Name *</label>
                    <input 
                      type="text" 
                      class="form-control" 
                      id="name" 
                      v-model="form.name"
                      required
                    >
                  </div>
                  
                  <div class="col-md-6 mb-3">
                    <label for="phone" class="form-label">Phone Number *</label>
                    <input 
                      type="tel" 
                      class="form-control" 
                      id="phone" 
                      v-model="form.phone"
                      required
                    >
                  </div>
                </div>
                
                <div class="mb-3">
                  <label for="email" class="form-label">Email Address *</label>
                  <input 
                    type="email" 
                    class="form-control" 
                    id="email" 
                    v-model="form.email"
                    required
                  >
                </div>
                
                <div class="mb-3">
                  <label for="subject" class="form-label">Subject *</label>
                  <select class="form-select" id="subject" v-model="form.subject" required>
                    <option value="">Select a subject</option>
                    <option value="course">Course Inquiry</option>
                    <option value="admission">Admission Process</option>
                    <option value="schedule">Schedule & Timing</option>
                    <option value="fees">Fee Structure</option>
                    <option value="other">Other</option>
                  </select>
                </div>
                
                <div class="mb-3">
                  <label for="course" class="form-label">Course Interested In</label>
                  <select class="form-select" id="course" v-model="form.course">
                    <option value="">Select a course</option>
                    <option value="fundamentals">Computer Fundamentals</option>
                    <option value="python">Programming with Python</option>
                    <option value="web">Web Development</option>
                    <option value="fullstack">Full Stack Development</option>
                    <option value="cyber">Cybersecurity</option>
                    <option value="ccna">CISCO CCNA</option>
                  </select>
                </div>
                
                <div class="mb-3">
                  <label for="message" class="form-label">Message *</label>
                  <textarea 
                    class="form-control" 
                    id="message" 
                    rows="5"
                    v-model="form.message"
                    required
                  ></textarea>
                </div>
                
                <div class="mb-3">
                  <div class="form-check">
                    <input 
                      class="form-check-input" 
                      type="checkbox" 
                      id="newsletter"
                      v-model="form.newsletter"
                    >
                    <label class="form-check-label" for="newsletter">
                      Subscribe to our newsletter for updates and offers
                    </label>
                  </div>
                </div>
                
                <button 
                  type="submit" 
                  class="btn btn-primary btn-lg w-100"
                  :disabled="formSubmitting"
                >
                  <span v-if="formSubmitting">
                    <i class="fas fa-spinner fa-spin"></i> Sending...
                  </span>
                  <span v-else>
                    <i class="fas fa-paper-plane"></i> Send Message
                  </span>
                </button>
              </form>
            </div>
          </div>
        </div>
      </div>
    </section>
    
    <!-- Map Section -->
    <section class="map-section py-5 bg-light">
      <div class="container">
        <h2 class="section-title text-center mb-5">Find <span class="highlight">Our College</span></h2>
        <div class="map-container card-theme overflow-hidden">
          <!-- In a real application, you would embed Google Maps here -->
          <div class="map-placeholder text-center py-5">
            <i class="fas fa-map-marked-alt fa-4x mb-3"></i>
            <h3>Location Map</h3>
            <p class="mb-0">{{ address }}</p>
            <div class="mt-4">
              <a 
                href="https://www.google.com/maps?q=No+26/B,+New+Road,+Ambalangoda,+Sri+Lanka+80300" 
                target="_blank"
                class="btn btn-primary"
              >
                <i class="fas fa-map-marker-alt"></i> Open in Google Maps
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>
    
    <!-- FAQ Section -->
    <section class="faq-section py-5">
      <div class="container">
        <h2 class="section-title text-center mb-5">Frequently Asked Questions</h2>
        
        <div class="accordion" id="faqAccordion">
          <div class="accordion-item" v-for="(faq, index) in faqs" :key="index">
            <h3 class="accordion-header">
              <button 
                class="accordion-button" 
                type="button" 
                :class="{ 'collapsed': index !== 0 }"
                :data-bs-target="`#faq${index}`"
                data-bs-toggle="collapse"
                :aria-expanded="index === 0 ? 'true' : 'false'"
              >
                {{ faq.question }}
              </button>
            </h3>
            <div 
              :id="`faq${index}`" 
              class="accordion-collapse collapse"
              :class="{ 'show': index === 0 }"
              :data-bs-parent="'#faqAccordion'"
            >
              <div class="accordion-body">
                {{ faq.answer }}
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
/* eslint-disable vue/multi-word-component-names */
export default {
  name: 'ContactView',
  data() {
    return {
      address: 'No 26/B, New Rd, Ambalangoda, Sri Lanka',
      mobile: '071 886 4477',
      whatsapp: '+94 70 520 5666',
      email: 'email.ccit@gmail.com',
      form: {
        name: '',
        phone: '',
        email: '',
        subject: '',
        course: '',
        message: '',
        newsletter: false
      },
      formSubmitting: false,
      formSuccess: '',
      formError: '',
      faqs: [
        {
          question: 'What are your operating hours?',
          answer: 'We are open Monday to Friday from 8:00 AM to 6:00 PM, and Saturdays from 8:00 AM to 1:00 PM. We are closed on Sundays and public holidays.'
        },
        {
          question: 'How can I enroll in a course?',
          answer: 'You can enroll by visiting our campus, calling us, or filling out the contact form above. We recommend scheduling a consultation first to discuss your goals and suitable courses.'
        },
        {
          question: 'Do you offer payment plans?',
          answer: 'Yes, we offer flexible payment plans for most courses. You can pay in monthly installments. Please contact us for specific payment options for your chosen course.'
        },
        {
          question: 'Are there any prerequisites for courses?',
          answer: 'Beginner courses have no prerequisites. Intermediate and advanced courses may require basic computer knowledge or completion of prerequisite courses. Contact us for specific requirements.'
        },
        {
          question: 'Do you provide certificates?',
          answer: 'Yes, upon successful completion of any course, you will receive a recognized certificate from Cambridge College of Information Technology. Some courses also prepare you for international certifications.'
        },
        {
          question: 'Can I visit the campus before enrolling?',
          answer: 'Absolutely! We encourage prospective students to visit our campus, see our facilities, and meet our instructors. Please call ahead to schedule a campus tour.'
        }
      ]
    }
  },
  methods: {
    async submitForm() {
      this.formSubmitting = true
      this.formSuccess = ''
      this.formError = ''
      
      try {
        // Simulate API call - In real app, use emailjs-com or backend API
        await new Promise(resolve => setTimeout(resolve, 1500))
        
        // For demo purposes, show success message
        this.formSuccess = 'Thank you for your message! We will contact you within 24 hours.'
        
        // Reset form
        this.form = {
          name: '',
          phone: '',
          email: '',
          subject: '',
          course: '',
          message: '',
          newsletter: false
        }
        
        // Reset form validation
        const form = document.getElementById('contactForm')
        if (form) {
          form.reset()
        }
        
      } catch (error) {
        console.error('Error sending message:', error)
        this.formError = 'Sorry, there was an error sending your message. Please try again or contact us directly.'
      } finally {
        this.formSubmitting = false
      }
    }
  }
}
</script>

<style scoped>
.contact-hero {
  background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
  color: white;
}

.hero-title {
  font-size: 2.8rem;
  font-weight: 700;
  margin-bottom: 1rem;
}

.highlight {
  background: linear-gradient(135deg, #ff6b35 0%, #ffa500 50%, #ff8c00 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  position: relative;
  display: inline-block;
}

.hero-icon {
  font-size: 6rem;
  color: var(--accent-color);
}

.contact-item {
  display: flex;
  align-items: flex-start;
  gap: 15px;
}

.contact-icon {
  width: 40px;
  height: 40px;
  background: var(--primary-color);
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.contact-details h4 {
  color: var(--text-primary);
  margin-bottom: 5px;
  font-size: 1.1rem;
}

.contact-details p {
  color: var(--text-secondary);
  margin: 0;
}

.contact-details a {
  color: var(--text-secondary);
  text-decoration: none;
  transition: color 0.3s ease;
}

.contact-details a:hover {
  color: var(--accent-color);
}

.social-link {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  background: var(--primary-color);
  color: white;
  border-radius: 50%;
  text-decoration: none;
  transition: all 0.3s ease;
}

.social-link:hover {
  background: var(--accent-color);
  transform: translateY(-3px);
}

.contact-form .form-label {
  color: var(--text-primary);
  font-weight: 500;
}

.contact-form .form-control,
.contact-form .form-select {
  background-color: var(--bg-primary);
  border-color: var(--border-color);
  color: var(--text-primary);
  transition: all 0.3s ease;
}

.contact-form .form-control:focus,
.contact-form .form-select:focus {
  border-color: var(--accent-color);
  box-shadow: 0 0 0 0.25rem rgba(0, 188, 212, 0.25);
}

.contact-form .alert {
  border: none;
  border-radius: 10px;
}

.alert-success {
  background-color: rgba(76, 175, 80, 0.1);
  border-left: 4px solid #4CAF50;
}

.alert-danger {
  background-color: rgba(244, 67, 54, 0.1);
  border-left: 4px solid #F44336;
}

.alert i {
  margin-right: 10px;
}

.btn-primary:disabled {
  opacity: 0.7;
  cursor: not-allowed;
}

.map-container {
  border-radius: 15px;
  height: 400px;
}

.map-placeholder {
  color: var(--text-secondary);
}

.map-placeholder i {
  color: var(--accent-color);
}

.section-title {
  color: var(--text-primary);
  font-weight: 700;
  font-size: 2.2rem;
  margin-bottom: 3rem;
}

.accordion-item {
  background-color: var(--card-bg);
  border-color: var(--border-color);
  margin-bottom: 10px;
  border-radius: 10px !important;
  overflow: hidden;
}

.accordion-button {
  background-color: var(--card-bg);
  color: var(--text-primary);
  font-weight: 600;
  border: none;
}

.accordion-button:not(.collapsed) {
  background-color: var(--primary-color);
  color: white;
  box-shadow: none;
}

.accordion-button:focus {
  border-color: var(--accent-color);
  box-shadow: 0 0 0 0.25rem rgba(0, 188, 212, 0.25);
}

.accordion-body {
  background-color: var(--bg-primary);
  color: var(--text-secondary);
}

@media (max-width: 768px) {
  .hero-title {
    font-size: 2rem;
  }
  
  .hero-icon {
    font-size: 4rem;
  }
  
  .contact-item {
    flex-direction: column;
    align-items: flex-start;
  }
}
</style>