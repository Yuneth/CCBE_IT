<template>
    <nav class="navbar-creative">
        <div class="nav-container">
            <!-- Logo and Brand Section -->
            <div class="brand-section">
                <div class="brand-wrapper">
                    <div class="logo-container">
                        <div class="logo-glow"></div>
                        <img :src="logoPath" alt="Cambridge College of Information Technology" class="brand-logo" />
                    </div>
                    <div class="brand-text">
                        <h1 class="brand-title">CCIT</h1>
                        <p class="brand-subtitle">Cambridge College of Information Technology</p>
                    </div>
                </div>
                  <!-- Action Buttons -->
                <div class="nav-actions">
                    <a href="https://classroom.google.com/" target="_blank" class="action-btn lms-btn">
                        <div class="btn-glow"></div>
                        <v-icon class="action-icon">mdi-monitor-dashboard</v-icon>
                        <span class="action-text">LMS Portal</span>
                    </a>
                    <button class="action-btn payment-btn" @click="openPaymentDialog">
                        <div class="btn-glow"></div>
                        <v-icon class="action-icon">mdi-credit-card-outline</v-icon>
                        <span class="action-text">Make Payment</span>
                    </button>
                </div>

                <!-- Mobile Toggler -->
                <button class="navbar-toggler creative-toggler" type="button" @click="toggleMobileMenu" 
                        :class="{ 'toggler-active': isMenuOpen }">
                    <span class="toggler-line toggler-line-1"></span>
                    <span class="toggler-line toggler-line-2"></span>
                    <span class="toggler-line toggler-line-3"></span>
                </button>
            </div>

            <!-- Desktop Navigation -->
            <div class="nav-content" :class="{ 'nav-content-open': isMenuOpen }">
                <!-- Animated Background for Mobile -->
                <div class="nav-background" v-if="isMenuOpen"></div>
                
                <!-- Main Navigation Menu -->
                <ul class="nav-menu">
                    <li class="nav-item" v-for="(item, index) in navItems" :key="index">
                        <router-link :to="item.link" class="nav-link creative-link" @click="closeMobileMenu">
                            <div class="link-content">
                                <v-icon class="nav-icon">{{ item.icon }}</v-icon>
                                <span class="nav-text">{{ item.text }}</span>
                            </div>
                            <div class="link-hover-effect"></div>
                            <div class="link-underline"></div>
                        </router-link>
                    </li>
                </ul>

              

                <!-- Quick Actions -->
                <div class="quick-actions">
                    <button class="quick-btn contact-btn" @click="openInquiryDialog">
                        <v-icon class="quick-icon">mdi-message-text</v-icon>
                        <span class="quick-text">Quick Inquiry</span>
                    </button>
                    <router-link to="/contact" class="quick-btn inquiry-btn" @click="closeMobileMenu">
                        <v-icon class="quick-icon">mdi-phone-in-talk</v-icon>
                        <span class="quick-text">Contact Us</span>
                    </router-link>
                </div>
            </div>
        </div>

        <!-- Floating Notification -->
        <div class="floating-notification" :class="{ 'notification-visible': showNotification }">
            <v-icon class="notification-icon">mdi-bell-outline</v-icon>
            <span>Welcome to CCIT - Excellence in IT Education</span>
        </div>
    </nav>

    <!-- Enhanced Dialogs -->
    
    <!-- Inquiry Dialog -->
    <v-dialog v-model="dialogInq" max-width="600" class="creative-dialog">
        <v-card class="dialog-card inquiry-card">
            <div class="dialog-header-glow"></div>
            <div class="dialog-header">
                <div class="dialog-icon-container">
                    <v-icon class="dialog-icon">mdi-message-text-outline</v-icon>
                </div>
                <div class="dialog-title-section">
                    <h3 class="dialog-title">Get In Touch</h3>
                    <p class="dialog-subtitle">We'll respond within 24 hours</p>
                </div>
            </div>
            
            <v-card-text class="dialog-body">
                <v-row dense>
                    <v-col cols="12" md="6">
                        <v-text-field 
                            label="Your Name" 
                            v-model="formData.name" 
                            required
                            variant="outlined"
                            density="comfortable"
                            class="creative-field"
                            prepend-inner-icon="mdi-account-outline"
                        ></v-text-field>
                    </v-col>
                    <v-col cols="12" md="6">
                        <v-text-field 
                            label="Contact Number" 
                            v-model="formData.contact"
                            variant="outlined"
                            density="comfortable"
                            class="creative-field"
                            prepend-inner-icon="mdi-phone-outline"
                        ></v-text-field>
                    </v-col>
                    <v-col cols="12" md="6">
                        <v-select 
                            :items="['Ambalangoda', 'Galle', 'Horana', 'Matara', 'Piliyandala', 'Kalutara']"
                            label="Preferred Branch" 
                            v-model="formData.branch" 
                            required 
                            variant="outlined"
                            density="comfortable"
                            class="creative-field"
                            prepend-inner-icon="mdi-map-marker-outline"
                        ></v-select>
                    </v-col>
                    <v-col cols="12" md="6">
                        <v-select 
                            :items="['Social Media', 'Website', 'Friend/Referral', 'Newspaper', 'Other']"
                            label="How did you hear about us?" 
                            v-model="formData.source" 
                            required
                            variant="outlined"
                            density="comfortable"
                            class="creative-field"
                            prepend-inner-icon="mdi-information-outline"
                        ></v-select>
                    </v-col>
                    <v-col cols="12">
                        <v-textarea 
                            label="Your Message" 
                            v-model="formData.message" 
                            required
                            variant="outlined"
                            rows="4"
                            class="creative-field"
                            prepend-inner-icon="mdi-pencil-outline"
                            placeholder="Tell us about your inquiry..."
                        ></v-textarea>
                    </v-col>
                </v-row>
                <div class="form-footer">
                    <small class="field-caption">* Required fields</small>
                    <div class="privacy-notice">
                        <v-icon small>mdi-shield-check-outline</v-icon>
                        <span>Your information is secure and protected</span>
                    </div>
                </div>
            </v-card-text>
            
            <v-divider class="dialog-divider"></v-divider>
            
            <v-card-actions class="dialog-actions">
                <v-btn 
                    text="Cancel" 
                    variant="outlined" 
                    @click="dialogInq = false"
                    class="action-btn cancel-btn"
                >
                    <v-icon left>mdi-close</v-icon>
                    Cancel
                </v-btn>
                <v-btn 
                    color="primary" 
                    @click="sendInquiry"
                    class="action-btn submit-btn creative-submit"
                >
                    <v-icon left>mdi-send</v-icon>
                    Send Inquiry
                    <div class="btn-sparkle"></div>
                </v-btn>
            </v-card-actions>
        </v-card>
    </v-dialog>

    <!-- Success Dialog -->
    <v-dialog v-model="successDialog" max-width="500" class="creative-dialog">
        <v-card class="dialog-card success-card">
            <div class="success-glow"></div>
            <div class="success-icon-container">
                <div class="success-circle">
                    <v-icon class="success-icon">mdi-check</v-icon>
                </div>
            </div>
            <v-card-title class="success-title">Message Sent Successfully!</v-card-title>
            <v-card-text class="success-message">
                Thank you for contacting Cambridge College of IT. Our team will get back to you within 24 hours.
            </v-card-text>
            <v-divider class="dialog-divider"></v-divider>
            <v-card-actions class="dialog-actions">
                <v-btn 
                    text="Close" 
                    color="primary" 
                    variant="flat"
                    @click="successDialog = false"
                    class="action-btn success-close-btn"
                >
                    <v-icon left>mdi-check</v-icon>
                    Got It
                </v-btn>
            </v-card-actions>
        </v-card>
    </v-dialog>
</template>

<script>
import { ref, onMounted } from 'vue'

export default {
    name: 'CreativeNavBar',
    setup() {
        const isMenuOpen = ref(false)
        const dialogInq = ref(false)
        const successDialog = ref(false)
        const showNotification = ref(false)
        
        const logoPath = require("@/assets/CCIT - logo.png")

        const navItems = [
            { 
                text: "Home", 
                link: "/",
                icon: "mdi-home-outline"
            },
            { 
                text: "Programmes", 
                link: "/courses",
                icon: "mdi-book-education-outline"
            },
            { 
                text: "Values", 
                link: "/corevalues",
                icon: "mdi-heart-outline"
            },
            { 
                text: "About", 
                link: "/about",
                icon: "mdi-information-outline"
            },
            { 
                text: "News", 
                link: "/news",
                icon: "mdi-newspaper-variant-outline"
            },
            { 
                text: "Careers", 
                link: "/careers",
                icon: "mdi-briefcase-outline"
            }
        ]

        const formData = ref({
            name: "",
            contact: "",
            branch: "",
            source: "",
            message: "",
        })

        const toggleMobileMenu = () => {
            isMenuOpen.value = !isMenuOpen.value
        }

        const closeMobileMenu = () => {
            isMenuOpen.value = false
        }

        const openInquiryDialog = () => {
            dialogInq.value = true
            closeMobileMenu()
        }

        const openPaymentDialog = () => {
            // Payment dialog logic here
            console.log("Open payment dialog")
        }

        const sendInquiry = async () => {
            if (!formData.value.name || !formData.value.branch || !formData.value.message) {
                alert("Please fill out all required fields.");
                return;
            }
            
            // Simulate successful inquiry submission
            console.log("Inquiry submitted:", formData.value);
            
            // Clear form and show success
            formData.value = {
                name: "",
                contact: "",
                branch: "",
                source: "",
                message: "",
            }
            
            dialogInq.value = false
            successDialog.value = true
        }

        // Show welcome notification
        onMounted(() => {
            setTimeout(() => {
                showNotification.value = true
                setTimeout(() => {
                    showNotification.value = false
                }, 4000)
            }, 1000)
        })

        return {
            isMenuOpen,
            dialogInq,
            successDialog,
            showNotification,
            logoPath,
            navItems,
            formData,
            toggleMobileMenu,
            closeMobileMenu,
            openInquiryDialog,
            openPaymentDialog,
            sendInquiry
        }
    }
}
</script>

<style scoped>
/* Creative Navbar Styles - Enhanced Dark Yellow & Black Theme */
.navbar-creative {
    background: linear-gradient(135deg, #0a0a0a 0%, #1a1a1a 50%, #0f0f0f 100%);
    padding: 0.5rem 0;
    box-shadow: 0 8px 40px rgba(0, 0, 0, 0.5);
    position: relative;
    z-index: 1000;
    border-bottom: 1px solid rgba(255, 215, 0, 0.3);
    backdrop-filter: blur(20px);
}

.navbar-creative::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, #FFD700, transparent);
    opacity: 0.6;
}

.nav-container {
    max-width: 1400px;
    margin: 0 auto;
    padding: 0 2rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
}

/* Brand Section */
.brand-section {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    position: relative;
}

.brand-wrapper {
    display: flex;
    align-items: center;
    gap: 1.5rem;
}

.logo-container {
    position: relative;
    padding: 0.5rem;
}

.logo-glow {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 80px;
    height: 80px;
    background: radial-gradient(circle, rgba(255, 215, 0, 0.3) 0%, transparent 70%);
    border-radius: 50%;
    animation: pulseGlow 3s ease-in-out infinite;
}

@keyframes pulseGlow {
    0%, 100% { opacity: 0.3; transform: translate(-50%, -50%) scale(1); }
    50% { opacity: 0.6; transform: translate(-50%, -50%) scale(1.1); }
}

.brand-logo {
    width: 200px;
    height: 120px;
    object-fit: contain;
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    position: relative;
    z-index: 2;
}

.brand-logo:hover {
    transform: scale(1.05) rotate(-1deg);
}

.brand-text {
    display: flex;
    flex-direction: column;
    gap: 0.25rem;
}

.brand-title {
    font-family: 'Inter', 'Poppins', sans-serif;
    font-weight: 800;
    font-size: 2rem;
    background: linear-gradient(135deg, #FFD700 0%, #FFA500 50%, #FFD700 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin: 0;
    letter-spacing: -0.5px;
    text-shadow: 0 2px 20px rgba(255, 215, 0, 0.3);
    position: relative;
}

.brand-title::after {
    content: '';
    position: absolute;
    bottom: -4px;
    left: 0;
    width: 100%;
    height: 2px;
    background: linear-gradient(90deg, transparent, #FFD700, transparent);
    opacity: 0.8;
}

.brand-subtitle {
    font-family: 'Inter', sans-serif;
    font-size: 0.75rem;
    color: #888;
    margin: 0;
    font-weight: 500;
    letter-spacing: 0.5px;
}

/* Creative Toggler */
.creative-toggler {
    background: rgba(255, 215, 0, 0.1);
    border: 1px solid rgba(255, 215, 0, 0.3);
    border-radius: 8px;
    padding: 0.75rem;
    cursor: pointer;
    display: none;
    flex-direction: column;
    gap: 0.35rem;
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    position: relative;
    overflow: hidden;
}

.creative-toggler::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255, 215, 0, 0.2), transparent);
    transition: left 0.6s ease;
}

.creative-toggler:hover::before {
    left: 100%;
}

.creative-toggler:hover {
    border-color: rgba(255, 215, 0, 0.6);
    background: rgba(255, 215, 0, 0.15);
    box-shadow: 0 0 20px rgba(255, 215, 0, 0.3);
    transform: scale(1.05);
}

.toggler-line {
    width: 24px;
    height: 2px;
    background: #FFD700;
    border-radius: 2px;
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    transform-origin: center;
}

.toggler-active .toggler-line-1 {
    transform: rotate(45deg) translate(6px, 6px);
}

.toggler-active .toggler-line-2 {
    opacity: 0;
    transform: scale(0);
}

.toggler-active .toggler-line-3 {
    transform: rotate(-45deg) translate(6px, -6px);
}

/* Navigation Content */
.nav-content {
    display: flex;
    align-items: center;
    gap: 2rem;
    flex: 1;
    justify-content: space-between;
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.nav-background {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: linear-gradient(135deg, #1a1a1a 0%, #2d2d2d 100%);
    opacity: 0.98;
    z-index: -1;
}

/* Main Navigation Menu */
.nav-menu {
    display: flex;
    list-style: none;
    margin: 0;
    padding: 0;
    gap: 0.5rem;
    flex: 1;
    justify-content: center;
}

.nav-item {
    position: relative;
}

.creative-link {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 0.75rem 1.5rem;
    color: #ffffff !important;
    text-decoration: none;
    font-family: 'Inter', 'Poppins', sans-serif;
    font-weight: 600;
    font-size: 0.95rem;
    border-radius: 12px;
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    background: rgba(255, 255, 255, 0.03);
    backdrop-filter: blur(10px);
    border: 1px solid rgba(255, 215, 0, 0.1);
    position: relative;
    overflow: hidden;
}

.link-content {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    position: relative;
    z-index: 2;
}

.link-hover-effect {
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255, 215, 0, 0.1), transparent);
    transition: left 0.6s ease;
}

.creative-link:hover .link-hover-effect {
    left: 100%;
}

.creative-link:hover {
    background: rgba(255, 215, 0, 0.1);
    transform: translateY(-3px);
    box-shadow: 0 8px 25px rgba(255, 215, 0, 0.2);
    border-color: rgba(255, 215, 0, 0.4);
}

.creative-link.router-link-active {
    background: rgba(255, 215, 0, 0.15);
    border-color: rgba(255, 215, 0, 0.6);
    box-shadow: 0 6px 20px rgba(255, 215, 0, 0.3);
}

.creative-link.router-link-active .link-underline {
    width: 80%;
    background: #FFA500;
    box-shadow: 0 0 15px rgba(255, 215, 0, 0.6);
}

.nav-icon {
    color: #FFD700 !important;
    font-size: 1.3rem !important;
    transition: all 0.4s ease;
}

.creative-link:hover .nav-icon {
    color: #FFA500 !important;
    transform: scale(1.2) rotate(5deg);
}

.link-underline {
    position: absolute;
    bottom: 0.5rem;
    left: 50%;
    width: 0;
    height: 2px;
    background: #FFD700;
    border-radius: 2px;
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    transform: translateX(-50%);
}

.creative-link:hover .link-underline {
    width: 60%;
}

/* Action Buttons */
.nav-actions {
    display: flex;
    gap: 1rem;
    align-items: center;
}

.action-btn {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    padding: 0.75rem 1.5rem;
    border: 1px solid;
    border-radius: 10px;
    text-decoration: none;
    font-family: 'Inter', 'Poppins', sans-serif;
    font-weight: 600;
    font-size: 0.9rem;
    transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    cursor: pointer;
    position: relative;
    overflow: hidden;
}

.btn-glow {
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
    transition: left 0.6s ease;
}

.action-btn:hover .btn-glow {
    left: 100%;
}

.lms-btn {
    background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%);
    color: #000000 !important;
    border-color: transparent;
    font-weight: 700;
    box-shadow: 0 4px 15px rgba(255, 215, 0, 0.3);
}

.lms-btn:hover {
    background: linear-gradient(135deg, #FFA500 0%, #FF8C00 100%);
    transform: translateY(-3px);
    box-shadow: 0 8px 25px rgba(255, 215, 0, 0.4);
}

.payment-btn {
    background: rgba(255, 215, 0, 0.1);
    color: #FFD700 !important;
    border-color: #FFD700;
    backdrop-filter: blur(10px);
}

.payment-btn:hover {
    background: rgba(255, 215, 0, 0.2);
    border-color: #FFA500;
    color: #FFA500 !important;
    transform: translateY(-3px);
    box-shadow: 0 8px 25px rgba(255, 215, 0, 0.3);
}

.action-icon {
    font-size: 1.3rem !important;
    transition: transform 0.3s ease;
}

.action-btn:hover .action-icon {
    transform: scale(1.1);
}

/* Quick Actions */
.quick-actions {
    display: flex;
    gap: 0.75rem;
    align-items: center;
}

.quick-btn {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.6rem 1rem;
    color: #FFD700 !important;
    text-decoration: none;
    font-family: 'Inter', 'Poppins', sans-serif;
    font-weight: 500;
    font-size: 0.85rem;
    border-radius: 8px;
    transition: all 0.3s ease;
    background: rgba(255, 215, 0, 0.08);
    border: 1px solid rgba(255, 215, 0, 0.2);
    cursor: pointer;
}

.quick-btn:hover {
    background: rgba(255, 215, 0, 0.15);
    border-color: rgba(255, 215, 0, 0.4);
    transform: translateY(-2px);
    box-shadow: 0 4px 15px rgba(255, 215, 0, 0.2);
}

.quick-icon {
    font-size: 1.1rem !important;
    color: #FFD700 !important;
}

/* Floating Notification */
.floating-notification {
    position: fixed;
    top: -100px;
    right: 2rem;
    background: linear-gradient(135deg, #1a1a1a 0%, #2d2d2d 100%);
    border: 1px solid rgba(255, 215, 0, 0.3);
    border-radius: 12px;
    padding: 1rem 1.5rem;
    display: flex;
    align-items: center;
    gap: 0.75rem;
    color: #FFD700;
    font-family: 'Inter', sans-serif;
    font-weight: 500;
    box-shadow: 0 8px 30px rgba(0, 0, 0, 0.4);
    backdrop-filter: blur(20px);
    transition: all 0.6s cubic-bezier(0.4, 0, 0.2, 1);
    z-index: 1001;
}

.notification-visible {
    top: 6rem;
}

.notification-icon {
    color: #FFD700 !important;
    animation: ring 2s ease-in-out infinite;
}

@keyframes ring {
    0%, 100% { transform: rotate(0deg); }
    25% { transform: rotate(15deg); }
    75% { transform: rotate(-15deg); }
}

/* Enhanced Dialog Styles */
.creative-dialog {
    font-family: 'Inter', 'Poppins', sans-serif;
}

.dialog-card {
    border-radius: 16px;
    overflow: hidden;
    box-shadow: 0 30px 60px rgba(0, 0, 0, 0.5);
    border: 1px solid rgba(255, 215, 0, 0.4);
    background: linear-gradient(135deg, #1a1a1a 0%, #2d2d2d 100%);
    position: relative;
}

.dialog-header-glow {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 4px;
    background: linear-gradient(90deg, #FFD700, #FFA500, #FFD700);
    opacity: 0.8;
}

.dialog-header {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 2.5rem 2.5rem 1.5rem;
    background: transparent;
    color: #FFD700;
    border-bottom: 1px solid rgba(255, 215, 0, 0.2);
}

.dialog-icon-container {
    background: rgba(255, 215, 0, 0.1);
    border-radius: 12px;
    padding: 1rem;
    border: 1px solid rgba(255, 215, 0, 0.3);
}

.dialog-icon {
    font-size: 2.5rem !important;
    color: #FFD700 !important;
}

.dialog-title-section {
    display: flex;
    flex-direction: column;
    gap: 0.25rem;
}

.dialog-title {
    font-weight: 700;
    font-size: 1.6rem;
    margin: 0;
    letter-spacing: -0.25px;
    background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
}

.dialog-subtitle {
    color: #888;
    font-size: 0.9rem;
    margin: 0;
    font-weight: 500;
}

.dialog-body {
    padding: 2rem 2.5rem;
    background: transparent;
}

.dialog-divider {
    margin: 0 2.5rem;
    border-color: rgba(255, 215, 0, 0.2);
}

.dialog-actions {
    padding: 1.5rem 2.5rem;
    display: flex;
    gap: 1rem;
    justify-content: flex-end;
    background: rgba(0, 0, 0, 0.3);
    border-top: 1px solid rgba(255, 215, 0, 0.1);
}

/* Enhanced Form Fields */
.creative-field {
    border-radius: 10px;
}

.creative-field :deep(.v-field) {
    border-radius: 10px;
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 255, 255, 0.1);
    color: #ffffff;
    transition: all 0.3s ease;
}

.creative-field :deep(.v-field:hover) {
    border-color: rgba(255, 215, 0, 0.5);
    background: rgba(255, 255, 255, 0.08);
}

.creative-field :deep(.v-field--focused) {
    border-color: #FFD700;
    background: rgba(255, 255, 255, 0.1);
    box-shadow: 0 0 0 2px rgba(255, 215, 0, 0.2);
}

.creative-field :deep(.v-label) {
    color: #999 !important;
}

.creative-field :deep(.v-field__input) {
    color: #ffffff !important;
}

.creative-field :deep(.v-icon) {
    color: #FFD700 !important;
}

.form-footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 1rem;
}

.field-caption {
    color: #666;
    font-size: 0.875rem;
}

.privacy-notice {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    color: #888;
    font-size: 0.8rem;
}

.privacy-notice .v-icon {
    color: #4caf50 !important;
    font-size: 1rem !important;
}

/* Enhanced Buttons */
.creative-submit {
    position: relative;
    overflow: hidden;
    background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%) !important;
    color: #000000 !important;
    font-weight: 700;
    border: none !important;
}

.btn-sparkle {
    position: absolute;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: radial-gradient(circle, rgba(255, 255, 255, 0.8) 0%, transparent 60%);
    opacity: 0;
    transition: opacity 0.3s ease;
}

.creative-submit:hover .btn-sparkle {
    opacity: 0.6;
}

/* Success Dialog Enhancements */
.success-glow {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: radial-gradient(circle at center, rgba(255, 215, 0, 0.1) 0%, transparent 70%);
    opacity: 0.6;
}

.success-icon-container {
    padding: 2rem 2rem 1rem;
    position: relative;
    z-index: 2;
}

.success-circle {
    width: 80px;
    height: 80px;
    background: linear-gradient(135deg, #4caf50, #45a049);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0 auto;
    box-shadow: 0 8px 25px rgba(76, 175, 80, 0.4);
    animation: successPulse 2s ease-in-out infinite;
}

@keyframes successPulse {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.05); }
}

.success-icon {
    font-size: 2.5rem !important;
    color: white !important;
}

.success-title {
    justify-content: center;
    font-weight: 700;
    color: #FFD700;
    font-size: 1.5rem !important;
    font-family: 'Inter', sans-serif;
    text-align: center;
}

.success-message {
    text-align: center;
    color: #ccc;
    font-size: 1rem;
    font-family: 'Inter', sans-serif;
    line-height: 1.6;
}

.success-close-btn {
    background: linear-gradient(135deg, #FFD700 0%, #FFA500 100%) !important;
    color: #000000 !important;
    font-weight: 700;
}

/* Mobile Responsive Design */
@media (max-width: 1200px) {
    .nav-container {
        padding: 0 1.5rem;
    }
    
    .brand-logo {
        width: 160px;
        height: 50px;
    }
    
    .brand-title {
        font-size: 1.8rem;
    }
    
    .nav-menu {
        gap: 0.25rem;
    }
    
    .creative-link {
        padding: 0.6rem 1.25rem;
        font-size: 0.9rem;
    }
}

@media (max-width: 991.98px) {
    .creative-toggler {
        display: flex;
    }
    
    .nav-content {
        flex-direction: column;
        align-items: stretch;
        gap: 1.5rem;
        display: none;
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background: linear-gradient(135deg, #0a0a0a 0%, #1a1a1a 100%);
        padding: 2rem;
        box-shadow: 0 0 50px rgba(0, 0, 0, 0.8);
        z-index: 999;
        overflow-y: auto;
    }
    
    .nav-content-open {
        display: flex;
    }
    
    .nav-menu {
        flex-direction: column;
        gap: 0.75rem;
    }
    
    .nav-actions {
        justify-content: center;
        order: -1;
    }
    
    .quick-actions {
        justify-content: center;
        order: -2;
    }
    
    .brand-title {
        font-size: 1.6rem;
    }
    
    .brand-logo {
        width: 140px;
        height: 45px;
    }
    
    .floating-notification {
        right: 1rem;
        left: 1rem;
    }
}

@media (max-width: 575.98px) {
    .nav-container {
        padding: 0 1rem;
    }
    
    .brand-title {
        font-size: 1.4rem;
    }
    
    .brand-subtitle {
        font-size: 0.7rem;
    }
    
    .brand-logo {
        width: 120px;
        height: 40px;
    }
    
    .nav-content {
        padding: 1.5rem;
    }
    
    .action-btn,
    .quick-btn {
        padding: 0.75rem 1rem;
        font-size: 0.85rem;
    }
    
    .dialog-header {
        padding: 2rem 1.5rem 1rem;
    }
    
    .dialog-body {
        padding: 1.5rem;
    }
    
    .dialog-actions {
        padding: 1rem 1.5rem;
        flex-direction: column;
    }
    
    .action-btn {
        width: 100%;
    }
}

/* Enhanced Animations */
.navbar-creative {
    animation: slideDownEnhanced 0.6s cubic-bezier(0.4, 0, 0.2, 1);
}

@keyframes slideDownEnhanced {
    from {
        transform: translateY(-100%);
        opacity: 0;
    }
    to {
        transform: translateY(0);
        opacity: 1;
    }
}

.nav-item {
    animation: fadeInUpEnhanced 0.8s cubic-bezier(0.4, 0, 0.2, 1) forwards;
    opacity: 0;
}

@keyframes fadeInUpEnhanced {
    from {
        opacity: 0;
        transform: translateY(30px) scale(0.9);
    }
    to {
        opacity: 1;
        transform: translateY(0) scale(1);
    }
}

/* Stagger animation delays */
.nav-item:nth-child(1) { animation-delay: 0.1s; }
.nav-item:nth-child(2) { animation-delay: 0.2s; }
.nav-item:nth-child(3) { animation-delay: 0.3s; }
.nav-item:nth-child(4) { animation-delay: 0.4s; }
.nav-item:nth-child(5) { animation-delay: 0.5s; }
.nav-item:nth-child(6) { animation-delay: 0.6s; }

/* Focus states for accessibility */
.creative-link:focus,
.action-btn:focus,
.quick-btn:focus,
.creative-toggler:focus {
    outline: 2px solid #FFD700;
    outline-offset: 3px;
    border-radius: 8px;
}

/* Loading states */
.action-btn:disabled {
    opacity: 0.5;
    cursor: not-allowed;
    transform: none !important;
}

/* Premium glow effects for active state */
.creative-link.router-link-active {
    position: relative;
}

.creative-link.router-link-active::after {
    content: '';
    position: absolute;
    top: -2px;
    left: -2px;
    right: -2px;
    bottom: -2px;
    background: linear-gradient(135deg, #FFD700, #FFA500, #FFD700);
    border-radius: 14px;
    z-index: -1;
    opacity: 0.4;
    animation: enhancedGlow 3s ease-in-out infinite alternate;
}

@keyframes enhancedGlow {
    from {
        opacity: 0.3;
        filter: blur(5px);
    }
    to {
        opacity: 0.6;
        filter: blur(8px);
    }
}

/* Smooth scrolling for mobile */
.nav-content {
    -webkit-overflow-scrolling: touch;
}

/* Performance optimizations */
.navbar-creative {
    will-change: transform;
}

.creative-link, .action-btn {
    will-change: transform, box-shadow;
}
</style>