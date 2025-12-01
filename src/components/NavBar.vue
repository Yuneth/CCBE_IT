<template>
    <!-- Elegant Navigation Bar -->
    <nav class="elegant-navbar">
        <!-- Top Navigation Bar -->
        <div class="top-nav">
            <div class="nav-container">
                <!-- Logo & Brand -->
                <div class="brand-section">
                    <div class="logo-container">
                        <img :src="logoPath" alt="CCBE Logo" class="brand-logo" />
                    </div>
                    <div class="brand-text">
                        <h1 class="brand-name">CCIT</h1>
                        <p class="brand-tagline">Cambridge College of Information Technology</p>
                    </div>
                </div>

                <!-- Top Action Buttons -->
                <div class="top-actions">
                    <a href="https://classroom.google.com/" target="_blank" class="top-action-btn lms-btn">
                        <v-icon class="btn-icon">mdi-monitor-dashboard</v-icon>
                        <span>LMS Portal</span>
                    </a>
                    <a href="https://pay.ccbe.lk/" target="_blank" class="top-action-btn payment-btn">
                        <v-icon class="btn-icon">mdi-credit-card-outline</v-icon>
                        <span>Make Payment</span>
                    </a>
                    <button class="top-action-btn contact-btn" @click="openContact">
                        <v-icon class="btn-icon">mdi-email-outline</v-icon>
                        <span>Contact</span>
                    </button>
                    <button class="top-action-btn inquiry-btn" @click="dialogInq = true">
                        <v-icon class="btn-icon">mdi-help-circle-outline</v-icon>
                        <span>Inquiry</span>
                    </button>
                </div>

                <!-- Mobile Menu Toggle -->
                <button class="mobile-toggle" @click="toggleMobileMenu" :class="{ 'active': mobileMenuOpen }">
                    <span class="toggle-line"></span>
                    <span class="toggle-line"></span>
                    <span class="toggle-line"></span>
                </button>
            </div>
        </div>

        <!-- Bottom Navigation Menu -->
        <div class="bottom-nav">
            <div class="nav-container">
                <ul class="main-menu">
                    <li class="menu-item" v-for="(item, index) in menuItems" :key="index">
                        <a :href="item.link" class="menu-link" @mouseenter="setActiveItem(index)">
                            <span class="menu-icon">
                                <v-icon small>{{ item.icon }}</v-icon>
                            </span>
                            <span class="menu-text">{{ item.text }}</span>
                            <div class="menu-indicator" :class="{ 'active': activeItem === index }"></div>
                        </a>
                    </li>
                </ul>
            </div>
        </div>

        <!-- Mobile Navigation Menu -->
        <div class="mobile-menu" :class="{ 'active': mobileMenuOpen }">
            <div class="mobile-menu-container">
                <!-- Mobile Header -->
                <div class="mobile-header">
                    <div class="mobile-brand">
                        <img :src="logoPath" alt="CCBE Logo" class="mobile-logo" />
                        <div class="mobile-brand-text">
                            <h2>CCBE</h2>
                            <p>Cambridge College</p>
                        </div>
                    </div>
                    <button class="mobile-close" @click="closeMobileMenu">
                        <v-icon>mdi-close</v-icon>
                    </button>
                </div>

                <!-- Mobile Menu Items -->
                <div class="mobile-content">
                    <!-- Top Actions in Mobile -->
                    <div class="mobile-top-actions">
                        <a href="https://classroom.google.com/" target="_blank" class="mobile-top-action-btn lms-btn" @click="closeMobileMenu">
                            <v-icon>mdi-monitor-dashboard</v-icon>
                            <span>LMS Portal</span>
                        </a>
                        <a href="https://pay.ccbe.lk/" target="_blank" class="mobile-top-action-btn payment-btn" @click="closeMobileMenu">
                            <v-icon>mdi-credit-card-outline</v-icon>
                            <span>Make Payment</span>
                        </a>
                        <button class="mobile-top-action-btn contact-btn" @click="openContact; closeMobileMenu();">
                            <v-icon>mdi-email-outline</v-icon>
                            <span>Contact</span>
                        </button>
                        <button class="mobile-top-action-btn inquiry-btn" @click="dialogInq = true; closeMobileMenu();">
                            <v-icon>mdi-help-circle-outline</v-icon>
                            <span>Inquiry</span>
                        </button>
                    </div>

                    <!-- Main Menu Items -->
                    <div class="mobile-menu-section">
                        <h3 class="mobile-section-title">Main Menu</h3>
                        <ul class="mobile-nav-items">
                            <li class="mobile-nav-item" v-for="(item, index) in menuItems" :key="index">
                                <a :href="item.link" class="mobile-nav-link" @click="closeMobileMenu">
                                    <v-icon class="mobile-nav-icon">{{ item.icon }}</v-icon>
                                    <span class="mobile-nav-text">{{ item.text }}</span>
                                </a>
                            </li>
                        </ul>
                    </div>

                    <!-- Mobile Contact Info -->
                    <div class="mobile-contact">
                        <div class="contact-item">
                            <v-icon small>mdi-phone</v-icon>
                            <span>071 3 999 666</span>
                        </div>
                        <div class="contact-item">
                            <v-icon small>mdi-email</v-icon>
                            <span>info@ccbe.lk</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </nav>

    <!-- Inquiry Dialog -->
    <v-dialog v-model="dialogInq" max-width="600" class="inquiry-dialog">
        <v-card class="dialog-card">
            <v-card-header class="dialog-header">
                <div class="header-content">
                    <div class="icon-container">
                        <v-icon class="header-icon">mdi-chat-question</v-icon>
                    </div>
                    <div class="header-text">
                        <v-card-title class="dialog-title">Get In Touch With Us</v-card-title>
                        <v-card-subtitle class="dialog-subtitle">We'll respond within 24 hours</v-card-subtitle>
                    </div>
                </div>
            </v-card-header>

            <v-card-text class="dialog-body">
                <v-form ref="inquiryForm" class="inquiry-form">
                    <v-row>
                        <v-col cols="12" md="6">
                            <v-text-field
                                v-model="formData.name"
                                label="Full Name *"
                                variant="outlined"
                                color="#2962ff"
                                :rules="[v => !!v || 'Name is required']"
                                required
                            ></v-text-field>
                        </v-col>
                        <v-col cols="12" md="6">
                            <v-text-field
                                v-model="formData.contact"
                                label="Contact Number"
                                variant="outlined"
                                color="#2962ff"
                            ></v-text-field>
                        </v-col>
                        <v-col cols="12" md="6">
                            <v-select
                                v-model="formData.branch"
                                :items="branchOptions"
                                label="Select Branch *"
                                variant="outlined"
                                color="#2962ff"
                                :rules="[v => !!v || 'Branch is required']"
                                required
                            ></v-select>
                        </v-col>
                        <v-col cols="12" md="6">
                            <v-select
                                v-model="formData.source"
                                :items="sourceOptions"
                                label="How did you hear about us?"
                                variant="outlined"
                                color="#2962ff"
                            ></v-select>
                        </v-col>
                        <v-col cols="12">
                            <v-textarea
                                v-model="formData.message"
                                label="Your Message *"
                                variant="outlined"
                                color="#2962ff"
                                rows="4"
                                :rules="[v => !!v || 'Message is required']"
                                required
                                placeholder="Tell us about your inquiry..."
                            ></v-textarea>
                        </v-col>
                    </v-row>
                </v-form>
                <small class="required-note">* indicates required field</small>
            </v-card-text>

            <v-divider></v-divider>

            <v-card-actions class="dialog-actions">
                <v-btn
                    variant="outlined"
                    @click="dialogInq = false"
                    class="cancel-btn"
                    size="large"
                >
                    <v-icon left>mdi-close</v-icon>
                    Cancel
                </v-btn>
                <v-spacer></v-spacer>
                <v-btn
                    color="#2962ff"
                    variant="flat"
                    @click="sendInquiry"
                    class="submit-btn"
                    size="large"
                    :loading="loading"
                    :disabled="loading"
                >
                    <v-icon left>mdi-send</v-icon>
                    Send Inquiry
                </v-btn>
            </v-card-actions>
        </v-card>
    </v-dialog>

    <!-- Success Dialog -->
    <v-dialog v-model="successDialog" max-width="500" class="success-dialog">
        <v-card class="success-card">
            <v-card-text class="success-content">
                <div class="success-icon">
                    <v-icon color="success" size="64">mdi-check-circle</v-icon>
                </div>
                <h3 class="success-title">Inquiry Sent Successfully!</h3>
                <p class="success-message">
                    Thank you for contacting us. We'll get back to you within 24 hours.
                </p>
            </v-card-text>
            <v-card-actions class="success-actions">
                <v-spacer></v-spacer>
                <v-btn
                    color="#2962ff"
                    variant="flat"
                    @click="successDialog = false"
                    class="success-btn"
                    size="large"
                >
                    Got It
                </v-btn>
            </v-card-actions>
        </v-card>
    </v-dialog>
</template>

<script>
import emailjs from "emailjs-com";

export default {
    name: 'ElegantNavBar',
    data() {
        return {
            logoPath: require("@/assets/CCIT - logo.png"),
            mobileMenuOpen: false,
            activeItem: 0,
            dialogInq: false,
            successDialog: false,
            loading: false,
            
            // Form data
            formData: {
                name: "",
                contact: "",
                branch: "",
                source: "",
                message: "",
            },

            // Form options
            branchOptions: [
                'Ambalangoda',
                'Galle', 
                'Horana',
                'Matara',
                'Piliyandala',
                'Kalutara'
            ],
            sourceOptions: [
                'Social Media',
                'Website',
                'Friend/Referral',
                'Advertisement',
                'Other'
            ],

            menuItems: [
                {
                    text: "Home",
                    link: "/",
                    icon: "mdi-home-outline"
                },
                {
                    text: "About",
                    link: "/about",
                    icon: "mdi-information-outline"
                },
                {
                    text: "Core Values",
                    link: "/corevalues",
                    icon: "mdi-shield-check-outline"
                },
                {
                    text: "Programmes",
                    link: "/courses",
                    icon: "mdi-book-education-outline"
                },
                {
                    text: "News & Events",
                    link: "/news",
                    icon: "mdi-calendar-text-outline"
                },
                {
                    text: "Careers",
                    link: "/careers",
                    icon: "mdi-briefcase-outline"
                }
            ]
        };
    },
    methods: {
        toggleMobileMenu() {
            this.mobileMenuOpen = !this.mobileMenuOpen;
        },
        closeMobileMenu() {
            this.mobileMenuOpen = false;
        },
        setActiveItem(index) {
            this.activeItem = index;
        },
        openContact() {
            window.location.href = '/contact';
        },

        async sendInquiry() {
            // Validate form
            if (!this.formData.name || !this.formData.branch || !this.formData.message) {
                alert("Please fill out all required fields.");
                return;
            }

            this.loading = true;

            const branchConfig = {
                Ambalangoda: {
                    serviceId: "service_lfaw7ig",
                    templateId: "template_2qr8exc",
                    publicKey: "RrKZfdB7O-c_xrVE3",
                },
                Galle: {
                    serviceId: "service_a0rf5c8",
                    templateId: "template_6bv0ico",
                    publicKey: "5DFKJ881pqi_jmuPZ",
                },
                Horana: {
                    serviceId: "service_a0rf5c8",
                    templateId: "template_6bv0ico",
                    publicKey: "5DFKJ881pqi_jmuPZ",
                },
                Matara: {
                    serviceId: "service_a0rf5c8",
                    templateId: "template_6bv0ico",
                    publicKey: "5DFKJ881pqi_jmuPZ",
                },
                Piliyandala: {
                    serviceId: "service_a0rf5c8",
                    templateId: "template_6bv0ico",
                    publicKey: "5DFKJ881pqi_jmuPZ",
                },
                Kalutara: {
                    serviceId: "service_mg2271v",
                    templateId: "template_loig6cz",
                    publicKey: "MJPUAdls_w9W5hPaK",
                },
            };

            const selectedBranchConfig = branchConfig[this.formData.branch];
            if (!selectedBranchConfig) {
                alert("Invalid branch selected.");
                this.loading = false;
                return;
            }

            const templateParams = {
                name: this.formData.name,
                contact: this.formData.contact || "Not provided",
                branch: this.formData.branch,
                source: this.formData.source || "Not provided",
                message: this.formData.message,
            };

            try {
                await emailjs.send(
                    selectedBranchConfig.serviceId,
                    selectedBranchConfig.templateId,
                    templateParams,
                    selectedBranchConfig.publicKey
                );
                
                this.dialogInq = false;
                this.successDialog = true;
                this.clearForm();
            } catch (error) {
                console.error("Failed to send inquiry. Error details:", error);
                alert(`Failed to send inquiry. Please try again or contact us directly.`);
            } finally {
                this.loading = false;
            }
        },

        clearForm() {
            this.formData = {
                name: "",
                contact: "",
                branch: "",
                source: "",
                message: "",
            };
        }
    }
};
</script>

<style scoped>
/* Elegant Navigation Styles */
.elegant-navbar {
    font-family: 'Inter', 'Poppins', sans-serif;
    position: relative;
    z-index: 1000;
}

/* Top Navigation Bar */
.top-nav {
    background: rgba(255, 255, 255, 0.98);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid rgba(0, 0, 0, 0.08);
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.04);
    padding: 0.5px 0; 
}

/* Bottom Navigation Menu */
.bottom-nav {
    background: linear-gradient(135deg, white 0%, white 100%);
    box-shadow: 0 4px 20px rgba(41, 98, 255, 0.15);
}

.nav-container {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0.75rem 2rem;
    max-width: 1400px;
    margin: 0 auto;
}

/* Brand Section */
.brand-section {
    display: flex;
    align-items: center;
    gap: 1rem;
}

.logo-container {
    display: flex;
    align-items: center;
}

.brand-logo {
    height: 100px;
    width: auto;
    transition: transform 0.3s ease;
    filter: drop-shadow(0 2px 4px rgba(0, 0, 0, 0.1));
}

.brand-logo:hover {
    transform: scale(1.05);
}

.brand-text {
    display: flex;
    flex-direction: column;
}

.brand-name {
    font-size: 1.8rem;
    font-weight: 700;
    background: linear-gradient(135deg, black 0%, black 50%, black 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin: 0;
    line-height: 1.1;
    letter-spacing: -0.5px;
}

.brand-tagline {
    font-size: 0.7rem;
    color: #666;
    margin: 0;
    font-weight: 500;
    letter-spacing: 0.3px;
}

/* Top Action Buttons */
.top-actions {
    display: flex;
    align-items: center;
    gap: 0.5rem;
}

.top-action-btn {
    display: flex;
    align-items: center;
    gap: 0.4rem;
    padding: 0.6rem 1rem;
    border-radius: 8px;
    text-decoration: none;
    font-weight: 500;
    font-size: 0.85rem;
    transition: all 0.3s ease;
    border: none;
    cursor: pointer;
    white-space: nowrap;
}

.lms-btn {
    background: rgba(41, 98, 255, 0.1);
    color: #2962ff;
    border: 1px solid rgba(41, 98, 255, 0.2);
}

.lms-btn:hover {
    background: rgba(41, 98, 255, 0.15);
    transform: translateY(-1px);
    box-shadow: 0 4px 12px rgba(41, 98, 255, 0.2);
}

.payment-btn {
    background: rgba(76, 175, 80, 0.1);
    color: #4caf50;
    border: 1px solid rgba(76, 175, 80, 0.2);
}

.payment-btn:hover {
    background: rgba(76, 175, 80, 0.15);
    transform: translateY(-1px);
    box-shadow: 0 4px 12px rgba(76, 175, 80, 0.2);
}

.contact-btn {
    background: rgba(156, 39, 176, 0.1);
    color: #9c27b0;
    border: 1px solid rgba(156, 39, 176, 0.2);
}

.contact-btn:hover {
    background: rgba(156, 39, 176, 0.15);
    transform: translateY(-1px);
    box-shadow: 0 4px 12px rgba(156, 39, 176, 0.2);
}

.inquiry-btn {
    background: linear-gradient(135deg, #ff6d00 0%, #ff9100 100%);
    color: white;
    box-shadow: 0 2px 8px rgba(255, 109, 0, 0.3);
}

.inquiry-btn:hover {
    transform: translateY(-1px);
    box-shadow: 0 4px 15px rgba(255, 109, 0, 0.4);
}

.btn-icon {
    font-size: 1rem;
}

/* Main Menu in Bottom Nav */
.main-menu {
    display: flex;
    list-style: none;
    margin: 0;
    padding: 0;
    gap: 0.5rem;
    align-items: center;
    justify-content: center;
    width: 100%;
}

.menu-item {
    position: relative;
}

.menu-link {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    padding: 0.8rem 1.5rem;
    color: black;
    text-decoration: none;
    border-radius: 8px;
    transition: all 0.3s ease;
    font-weight: 500;
    font-size: 0.95rem;
    position: relative;
    overflow: hidden;
}

.menu-link:hover {
    background: #FFD700;
    transform: translateY(-1px);
}

.menu-link::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
    transition: left 0.6s ease;
}

.menu-link:hover::before {
    left: 100%;
}

.menu-icon {
    display: flex;
    align-items: center;
    transition: transform 0.3s ease;
}

.menu-link:hover .menu-icon {
    transform: scale(1.1);
}

.menu-indicator {
    position: absolute;
    bottom: -2px;
    left: 50%;
    width: 0;
    height: 2px;
    background: rgba(255, 255, 255, 0.8);
    border-radius: 2px;
    transition: all 0.3s ease;
    transform: translateX(-50%);
}

.menu-indicator.active {
    width: 70%;
}

.menu-text {
    font-size: 0.9rem;
    position: relative;
    z-index: 2;
}

/* Mobile Toggle */
.mobile-toggle {
    display: none;
    flex-direction: column;
    background: transparent;
    border: 1px solid rgba(0, 0, 0, 0.1);
    padding: 0.6rem;
    cursor: pointer;
    gap: 0.25rem;
    border-radius: 6px;
    transition: all 0.3s ease;
}

.mobile-toggle:hover {
    background: rgba(0, 0, 0, 0.05);
}

.toggle-line {
    width: 18px;
    height: 2px;
    background: #37474f;
    border-radius: 2px;
    transition: all 0.3s ease;
}

.mobile-toggle.active .toggle-line:nth-child(1) {
    transform: rotate(45deg) translate(5px, 5px);
}

.mobile-toggle.active .toggle-line:nth-child(2) {
    opacity: 0;
}

.mobile-toggle.active .toggle-line:nth-child(3) {
    transform: rotate(-45deg) translate(5px, -5px);
}

/* Mobile Menu */
.mobile-menu {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(255, 255, 255, 0.98);
    backdrop-filter: blur(20px);
    z-index: 999;
    transform: translateX(-100%);
    transition: transform 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.mobile-menu.active {
    transform: translateX(0);
}

.mobile-menu-container {
    height: 100%;
    display: flex;
    flex-direction: column;
}

.mobile-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.5rem 2rem;
    border-bottom: 1px solid rgba(0, 0, 0, 0.08);
    background: linear-gradient(135deg, white 0%, white 100%);
}

.mobile-brand {
    display: flex;
    align-items: center;
    gap: 1rem;
}

.mobile-logo {
    height: 45px;
    width: auto;
}

.mobile-brand-text h2 {
    font-size: 1.4rem;
    font-weight: 700;
    color: black;
    margin: 0;
}

.mobile-brand-text p {
    font-size: 0.75rem;
    color: black;
    margin: 0;
}

.mobile-close {
    background: rgba(255, 255, 255, 0.2);
    border: none;
    border-radius: 8px;
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: all 0.3s ease;
    color: black;
}

.mobile-close:hover {
    background: rgba(255, 255, 255, 0.3);
}

.mobile-content {
    flex: 1;
    padding: 1.5rem;
    display: flex;
    flex-direction: column;
    overflow-y: auto;
}

/* Mobile Top Actions */
.mobile-top-actions {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0.75rem;
    margin-bottom: 2rem;
}

.mobile-top-action-btn {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    padding: 1rem;
    border-radius: 10px;
    text-decoration: none;
    font-weight: 500;
    transition: all 0.3s ease;
    border: none;
    cursor: pointer;
    text-align: center;
    justify-content: center;
    font-size: 0.85rem;
}

/* Mobile Menu Section */
.mobile-menu-section {
    margin-bottom: 2rem;
}

.mobile-section-title {
    color: #2962ff;
    font-size: 1rem;
    font-weight: 600;
    margin-bottom: 1rem;
    padding-bottom: 0.5rem;
    border-bottom: 1px solid rgba(0, 0, 0, 0.1);
}

.mobile-nav-items {
    list-style: none;
    margin: 0;
    padding: 0;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
}

.mobile-nav-item {
    opacity: 0;
    transform: translateX(-20px);
    animation: slideInRight 0.5s ease forwards;
}

.mobile-nav-item:nth-child(1) { animation-delay: 0.1s; }
.mobile-nav-item:nth-child(2) { animation-delay: 0.2s; }
.mobile-nav-item:nth-child(3) { animation-delay: 0.3s; }
.mobile-nav-item:nth-child(4) { animation-delay: 0.4s; }
.mobile-nav-item:nth-child(5) { animation-delay: 0.5s; }
.mobile-nav-item:nth-child(6) { animation-delay: 0.6s; }

@keyframes slideInRight {
    to {
        opacity: 1;
        transform: translateX(0);
    }
}

.mobile-nav-link {
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 1rem 1.25rem;
    color: #37474f;
    text-decoration: none;
    border-radius: 10px;
    transition: all 0.3s ease;
    font-weight: 500;
    background: rgba(0, 0, 0, 0.02);
    border: 1px solid rgba(0, 0, 0, 0.05);
}

.mobile-nav-link:hover {
    background: rgba(41, 98, 255, 0.08);
    color: #2962ff;
    transform: translateX(8px);
}

.mobile-nav-icon {
    font-size: 1.1rem;
}

/* Mobile Contact Info */
.mobile-contact {
    margin-top: auto;
    padding-top: 1.5rem;
    border-top: 1px solid rgba(0, 0, 0, 0.08);
}

.contact-item {
    display: flex;
    align-items: center;
    gap: 0.75rem;
    padding: 0.5rem 0;
    color: #666;
    font-size: 0.85rem;
}

.contact-item .v-icon {
    color: #2962ff;
}

/* Inquiry Dialog Styles */
.inquiry-dialog {
    font-family: 'Inter', 'Poppins', sans-serif;
}

.dialog-card {
    border-radius: 20px;
    overflow: hidden;
    box-shadow: 0 25px 50px rgba(0, 0, 0, 0.15);
    background: white;
}

.dialog-header {
    background: linear-gradient(135deg, #2962ff 0%, #448aff 100%);
    padding: 2rem;
    color: white;
}

.header-content {
    display: flex;
    align-items: center;
    gap: 1rem;
}

.icon-container {
    background: rgba(255, 255, 255, 0.2);
    border-radius: 50%;
    width: 60px;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: center;
    backdrop-filter: blur(10px);
}

.header-icon {
    font-size: 2rem;
    color: white;
}

.header-text {
    flex: 1;
}

.dialog-title {
    font-size: 1.5rem;
    font-weight: 700;
    margin-bottom: 0.5rem;
    color: white;
}

.dialog-subtitle {
    color: rgba(255, 255, 255, 0.9);
    font-size: 1rem;
}

.dialog-body {
    padding: 2rem;
}

.inquiry-form {
    margin-bottom: 1rem;
}

.required-note {
    color: #666;
    font-size: 0.8rem;
}

.dialog-actions {
    padding: 1.5rem 2rem;
    display: flex;
    align-items: center;
}

.cancel-btn {
    border: 1px solid #ddd;
    color: #666;
    font-weight: 500;
}

.submit-btn {
    background: linear-gradient(135deg, #2962ff 0%, #448aff 100%);
    color: white;
    font-weight: 500;
    box-shadow: 0 4px 15px rgba(41, 98, 255, 0.3);
}

.submit-btn:hover {
    box-shadow: 0 6px 20px rgba(41, 98, 255, 0.4);
}

/* Success Dialog */
.success-dialog {
    font-family: 'Inter', 'Poppins', sans-serif;
}

.success-card {
    border-radius: 20px;
    overflow: hidden;
    text-align: center;
    box-shadow: 0 25px 50px rgba(0, 0, 0, 0.15);
}

.success-content {
    padding: 3rem 2rem;
}

.success-icon {
    margin-bottom: 1.5rem;
    animation: scaleIn 0.5s ease;
}

@keyframes scaleIn {
    from {
        transform: scale(0);
        opacity: 0;
    }
    to {
        transform: scale(1);
        opacity: 1;
    }
}

.success-title {
    font-size: 1.5rem;
    font-weight: 700;
    color: #1a1a1a;
    margin-bottom: 1rem;
}

.success-message {
    color: #666;
    line-height: 1.6;
    font-size: 1rem;
}

.success-actions {
    padding: 1.5rem 2rem;
}

.success-btn {
    background: linear-gradient(135deg, #2962ff 0%, #448aff 100%);
    color: white;
    font-weight: 500;
}

/* Responsive Design */
@media (max-width: 1024px) {
    .nav-container {
        padding: 0.75rem 1.5rem;
    }
    
    .top-action-btn {
        padding: 0.5rem 0.8rem;
        font-size: 0.8rem;
    }
    
    .menu-link {
        padding: 0.7rem 1.2rem;
        font-size: 0.9rem;
    }
    
    .brand-name {
        font-size: 1.6rem;
    }
    
    .brand-logo {
        height: 45px;
    }
}

@media (max-width: 768px) {
    .top-actions,
    .bottom-nav {
        display: none;
    }
    
    .mobile-toggle {
        display: flex;
    }
    
    .brand-tagline {
        display: none;
    }
    
    .brand-name {
        font-size: 1.5rem;
    }
    
    .brand-logo {
        height: 40px;
    }

    .mobile-top-actions {
        grid-template-columns: 1fr;
    }

    .dialog-header {
        padding: 1.5rem;
    }

    .header-content {
        flex-direction: column;
        text-align: center;
        gap: 0.75rem;
    }

    .dialog-body {
        padding: 1.5rem;
    }

    .dialog-actions {
        padding: 1rem 1.5rem;
        flex-direction: column;
        gap: 0.75rem;
    }

    .cancel-btn, .submit-btn {
        width: 100%;
    }
}

@media (max-width: 480px) {
    .nav-container {
        padding: 0.5rem 1rem;
    }
    
    .brand-name {
        font-size: 1.3rem;
    }
    
    .brand-logo {
        height: 35px;
    }
    
    .mobile-content {
        padding: 1rem;
    }
    
    .mobile-header {
        padding: 1rem 1.5rem;
    }
}

/* Animation */
.elegant-navbar {
    animation: slideDown 0.8s ease-out;
}

@keyframes slideDown {
    from {
        transform: translateY(-100%);
        opacity: 0;
    }
    to {
        transform: translateY(0);
        opacity: 1;
    }
}
</style>