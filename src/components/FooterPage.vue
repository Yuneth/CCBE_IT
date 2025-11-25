<template>
  <v-footer
    class="footer-container text-center d-flex flex-column"
    color="#1a1a1a"
  >
    <div class="footer-content">
      <!-- Main Footer Content -->
      <div class="footer-main">
        <div class="footer-title-container">
          <strong class="footer-title">Shaping the Future of Education</strong>
        </div>
        <div class="contact-info">
          <strong class="contact-text"
            >Hot Line : 071 3 999 666 | Email : info@ccbe.lk</strong
          >
        </div>

        <!-- Social Media Icons -->
        <div class="social-icons">
          <v-btn
            v-for="icon in icons"
            :key="icon.name"
            class="social-btn"
            variant="text"
            @click="navigate(icon.link)"
            :aria-label="`Follow us on ${icon.name.replace('mdi-', '')}`"
          >
            <v-icon size="24">{{ icon.name }}</v-icon>
          </v-btn>
        </div>
      </div>

      <!-- Logo Section -->
      <div class="logo-section">
        <v-row justify="center" align="center" class="logo-row">
          <v-col cols="12" sm="6" md="3" lg="2" class="logo-col">
            <img
              class="main-logo"
              :src="logo"
              alt="Cambridge College of British English Logo"
            />
          </v-col>
          <v-col cols="12" sm="6" md="3" lg="2" class="logo-col">
            <img class="partner-logo1" :src="lable1" alt="WEP Partner Logo" />
          </v-col>
          <v-col cols="12" sm="6" md="3" lg="2" class="logo-col">
            <img class="partner-logo2" :src="lable2" alt="IELTS Partner Logo" />
          </v-col>
          <v-col cols="12" sm="6" md="3" lg="2" class="logo-col">
            <img class="partner-logo3" :src="lable3" alt="CES Partner Logo" />
          </v-col>
        </v-row>
      </div>

      <!-- Legal Links -->
      <div class="legal-links">
        <a href="#" @click.prevent="showPrivacyPolicy = true" class="legal-link"
          >Privacy Policy</a
        >
        <span class="link-separator">|</span>
        <a
          href="#"
          @click.prevent="showTermsOfService = true"
          class="legal-link"
          >Terms of Service</a
        >
      </div>

      <!-- Copyright Section -->
      <div class="copyright-section">
        <p class="mission-text">
          At Cambridge College of British English, we are committed to providing
          students with the tools they need to succeed academically and beyond.
        </p>
        <p class="copyright-text">
          Copyright © 2025 Cambridge College of British English. All rights
          reserved.
        </p>
      </div>
    </div>

    <!-- Privacy Policy Dialog -->
    <v-dialog
      v-model="showPrivacyPolicy"
      max-width="800px"
      scrollable
      class="modern-dialog"
    >
      <v-card class="dialog-card">
        <div class="dialog-header">
          <v-icon class="dialog-icon">mdi-shield-account</v-icon>
          <h3 class="dialog-title">Privacy Policy</h3>
        </div>
        <v-card-text class="dialog-body">
          <p>
            At Cambridge College of British English (CCBE), we are committed to
            protecting your privacy and ensuring the security of your personal
            information. This Privacy Policy explains how we collect, use,
            disclose, and safeguard the information you provide when using our
            platform, website, and services. By accessing or using our services,
            you consent to the practices described in this policy.
          </p>

          <h4 class="policy-heading">1. Information We Collect</h4>
          <strong>a. Personal Information</strong>
          <ul>
            <li>Full Name</li>
            <li>Email Address</li>
            <li>Phone Number</li>
            <li>Address</li>
          </ul>
          <strong>b. Payment Information</strong>
          <ul>
            <li>Payment Card Details</li>
            <li>Billing Address</li>
            <li>Transaction History</li>
          </ul>
          <p>
            We do not store payment details directly on our servers. Payments
            are securely processed through trusted third-party payment gateways.
          </p>

          <h4 class="policy-heading">2. How We Use Your Information</h4>
          <ul>
            <li>Service Delivery</li>
            <li>Personalization</li>
            <li>Communication</li>
            <li>Marketing</li>
            <li>Security</li>
            <li>Research and Improvement</li>
          </ul>

          <h4 class="policy-heading">3. Information Sharing and Disclosure</h4>
          <strong>a. Service Providers</strong>
          <ul>
            <li>Payment Processing</li>
            <li>Data Analysis</li>
            <li>Platform Maintenance</li>
            <li>Email and Communication</li>
          </ul>
          <strong>b. Legal Requirements</strong>
          <p>
            We may disclose your information if required by law, legal process,
            or regulatory authorities.
          </p>

          <h4 class="policy-heading">4. Data Security</h4>
          <p>
            We use SSL encryption and other technical measures to protect your
            data. However, no platform can guarantee 100% security.
          </p>

          <h4 class="policy-heading">5. Retention of Information</h4>
          <p>
            We retain your information only as long as necessary for operational
            and legal purposes.
          </p>

          <h4 class="policy-heading">6. Your Rights</h4>
          <ul>
            <li>Access</li>
            <li>Correction</li>
            <li>Deletion</li>
            <li>Opt-Out</li>
          </ul>

          <h4 class="policy-heading">7. Cookies and Tracking Technologies</h4>
          <p>
            We use cookies to improve your browsing experience. You can manage
            cookie settings in your browser.
          </p>

          <h4 class="policy-heading">8. Third-Party Links</h4>
          <p>
            We are not responsible for third-party privacy practices. Please
            review their policies.
          </p>

          <h4 class="policy-heading">9. Children's Privacy</h4>
          <p>
            Our services are not intended for individuals under 13 without
            parental consent.
          </p>

          <h4 class="policy-heading">10. Changes to the Privacy Policy</h4>
          <p>
            We may update this policy periodically. Please review it regularly
            for changes.
          </p>

          <h4 class="policy-heading">11. Contact Us</h4>
          <p>Email: info@ccbe.lk<br />Tel No: 071 3 999 666</p>
        </v-card-text>
        <v-divider class="dialog-divider"></v-divider>
        <v-card-actions class="dialog-actions">
          <v-btn
            color="primary"
            variant="outlined"
            @click="showPrivacyPolicy = false"
            class="action-btn"
          >
            Close
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>

    <!-- Terms of Service Dialog -->
    <v-dialog
      v-model="showTermsOfService"
      max-width="800px"
      scrollable
      class="modern-dialog"
    >
      <v-card class="dialog-card">
        <div class="dialog-header">
          <v-icon class="dialog-icon">mdi-file-document</v-icon>
          <h3 class="dialog-title">Terms & Conditions</h3>
        </div>
        <v-card-text class="dialog-body">
          <h4>Welcome to ccbe.lk!</h4>
          <p>
            These terms and conditions outline the rules and regulations for the
            use of our website. By accessing this website, we assume you accept
            these terms and conditions. Do not continue to use ccbe.lk if you do
            not agree to all the terms and conditions stated on this page.
          </p>

          <h4 class="policy-heading">1. Use of Site</h4>
          <ul>
            <li>
              Use the site for any illegal activities or violate any local,
              state, or international laws.
            </li>
            <li>
              Attempt to interfere with the site's security features or its
              operation.
            </li>
            <li>
              Use the site to distribute harmful content, such as malware or
              spam.
            </li>
          </ul>

          <h4 class="policy-heading">2. Intellectual Property Rights</h4>
          <p>
            All content on ccbe.lk, including text, graphics, logos, images, and
            any other material, is the property of Cambridge College of British
            English and is protected by copyright and other intellectual
            property rights. Unauthorized use or reproduction is prohibited.
          </p>
          <ul>
            <li>
              You may not modify, distribute, or reproduce any content from this
              site without our express written consent.
            </li>
            <li>
              Any trademarks or logos displayed on this site are the property of
              Cambridge College of British English and may not be used without
              permission.
            </li>
          </ul>

          <h4 class="policy-heading">3. Privacy Policy</h4>
          <p>
            Your privacy is very important to us. Please review our Privacy
            Policy to understand our practices regarding personal information.
          </p>
          <ul>
            <li>
              We use SSL encryption and industry-standard security measures to
              protect your data.
            </li>
            <li>
              We will not share your personal information with third parties
              without your consent, except as required by law.
            </li>
          </ul>

          <h4 class="policy-heading">4. Links to Third-Party Websites</h4>
          <p>
            ccbe.lk may include links to third-party websites that are not
            controlled by us. We do not:
          </p>
          <ul>
            <li>Endorse the content of these third-party websites.</li>
            <li>
              Assume any responsibility for the content or practices of
              third-party websites.
            </li>
          </ul>
          <p>You access these links at your own risk.</p>

          <h4 class="policy-heading">5. Payment Terms</h4>
          <ul>
            <li>
              Payments are securely processed through trusted third-party
              gateways.
            </li>
            <li>We do not store payment details directly on our servers.</li>
            <li>Any refunds or exchanges are governed by our Refund Policy.</li>
          </ul>

          <h4 class="policy-heading">6. Limitation of Liability</h4>
          <p>
            Cambridge College of British English is not liable for any damages
            or losses related to the use or inability to use the website. This
            includes, but is not limited to:
          </p>
          <ul>
            <li>Errors, interruptions, or technical issues on the site.</li>
            <li>Unauthorized access to user data.</li>
            <li>Loss of data or profits arising from the use of the site.</li>
          </ul>

          <h4 class="policy-heading">7. Changes to Terms</h4>
          <p>
            We reserve the right to update or change these terms and conditions
            at any time without prior notice.
          </p>
          <ul>
            <li>Any changes will be posted on this page.</li>
            <li>
              Your continued use of the site after changes are posted
              constitutes your acceptance of the updated terms.
            </li>
          </ul>

          <h4 class="policy-heading">8. Governing Law</h4>
          <p>
            These terms and conditions are governed by and construed in
            accordance with the laws of Sri Lanka.
          </p>
          <ul>
            <li>Any disputes will be resolved under these laws.</li>
            <li>
              Any legal action arising out of the use of this site shall be
              brought exclusively in the courts of Sri Lanka.
            </li>
          </ul>

          <h4 class="policy-heading">9. Contact Information</h4>
          <p>
            If you have any questions about these Terms and Conditions, please
            contact us at:
          </p>
          <ul>
            <li><strong>Email:</strong> info@ccbe.lk</li>
            <li><strong>Phone:</strong> 071 3 999 666</li>
          </ul>
        </v-card-text>
        <v-divider class="dialog-divider"></v-divider>
        <v-card-actions class="dialog-actions">
          <v-btn
            color="primary"
            variant="outlined"
            @click="showTermsOfService = false"
            class="action-btn"
          >
            Close
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-footer>
</template>

<script>
export default {
  data() {
    return {
      logo: require("@/assets/CCIT - logo.png"),
      lable1: require("@/assets/CamE.png"),
      lable2: require("@/assets/IELTS.png"),
      lable3: require("@/assets/CES.png"),
      icons: [
        { name: "mdi-instagram", link: "https://www.instagram.com/ccbeamb" },
        {
          name: "mdi-facebook",
          link: "https://www.facebook.com/ccbe.ambalangoda",
        },
        {
          name: "mdi-youtube",
          link: "https://www.youtube.com/@cambridgecollegeofbritishe9360",
        },
        {
          name: "mdi-music-note",
          link: "https://www.tiktok.com/@cambridgecollege9",
        },
      ],
      showPrivacyPolicy: false,
      showTermsOfService: false,
    };
  },
  methods: {
    navigate(link) {
      window.open(link, "_blank");
    },
  },
};
</script>

<style scoped>
.footer-container {
  background: linear-gradient(135deg, #1a1a1a 0%, #2d2d2d 100%) !important;
  border-top: 3px solid #ffd700;
  padding: 3rem 1rem 2rem !important;
  color: #ffffff;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  width: 100%;
}

/* Main Footer Content */
.footer-main {
  text-align: center;
  margin-bottom: 2rem;
}

.footer-title-container {
  margin-bottom: 1rem;
}

.footer-title {
  font-family: "Inter", "Poppins", sans-serif;
  font-size: 2rem;
  font-weight: 700;
  background: linear-gradient(135deg, #ffd700 0%, #ffa500 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  display: inline-block;
}

.contact-info {
  margin-bottom: 1.5rem;
}

.contact-text {
  font-family: "Inter", sans-serif;
  font-size: 1.1rem;
  color: #e0e0e0;
  font-weight: 500;
}

/* Social Icons */
.social-icons {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 2rem;
}

.social-btn {
  color: #ffd700 !important;
  transition: all 0.3s ease !important;
  border-radius: 50% !important;
  width: 48px !important;
  height: 48px !important;
}

.social-btn:hover {
  color: #ffffff !important;
  background: linear-gradient(135deg, #ffd700 0%, #ffa500 100%) !important;
  transform: translateY(-2px);
  box-shadow: 0 4px 15px rgba(255, 215, 0, 0.3) !important;
}

/* Logo Section */
.logo-section {
  background: linear-gradient(135deg, #0f0f0f 0%, #ebe8e8 50%);
  padding: 2rem 1rem;
  border-radius: 16px;
  margin-bottom: 2rem;
  border: 2px solid #333;
}

.logo-row {
  margin: 0 -8px;
}

.logo-col {
  padding: 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
}

.main-logo {
  max-width: 200px;
  height: auto;
  transition: transform 0.3s ease;
}

.main-logo:hover {
  transform: scale(1.05);
}

.partner-logo {
  max-width: 150px;
  height: auto;
  margin-right: 100px;
}

.partner-logo1 {
  max-width: 175px;
  height: auto;
  margin-right: 50px;
}

.partner-logo2 {
  max-width: 150px;
  height: auto;
  margin-right: 50px;
}

.partner-logo3 {
  max-width: 250px;
  height: auto;
}

.partner-logo:hover {
  transform: scale(1.05);
}

/* Legal Links */
.legal-links {
  margin-bottom: 1.5rem;
  text-align: center;
}

.legal-link {
  color: #ffd700;
  font-family: "Inter", sans-serif;
  font-size: 0.95rem;
  text-decoration: none;
  font-weight: 500;
  padding: 0.5rem 1rem;
  border-radius: 6px;
  transition: all 0.3s ease;
  display: inline-block;
}

.legal-link:hover {
  color: #ffffff;
  background: rgba(255, 215, 0, 0.2);
  text-decoration: underline;
}

.link-separator {
  color: #666;
  margin: 0 0.5rem;
}

/* Copyright Section */
.copyright-section {
  text-align: center;
  border-top: 1px solid #333;
  padding-top: 1.5rem;
}

.mission-text {
  font-family: "Inter", sans-serif;
  font-size: 1rem;
  line-height: 1.6;
  color: #e0e0e0;
  margin-bottom: 1rem;
  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
}

.copyright-text {
  font-family: "Inter", sans-serif;
  font-size: 0.9rem;
  color: #999;
  margin: 0;
}

/* Dialog Styles */
.modern-dialog {
  font-family: "Inter", "Poppins", sans-serif;
}

.dialog-card {
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 25px 50px rgba(0, 0, 0, 0.4);
  border: 2px solid #ffd700;
  background: #1a1a1a;
}

.dialog-header {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 2rem 2rem 1.5rem;
  background: linear-gradient(135deg, #000000 0%, #1a1a1a 100%);
  color: #ffd700;
  border-bottom: 1px solid #333;
}

.dialog-icon {
  font-size: 2rem !important;
  color: #ffd700 !important;
}

.dialog-title {
  font-weight: 700;
  font-size: 1.5rem;
  margin: 0;
  letter-spacing: -0.25px;
  text-shadow: 0 2px 8px rgba(255, 215, 0, 0.3);
}

.dialog-body {
  padding: 2rem;
  background: #1a1a1a;
  color: #e0e0e0;
  font-family: "Inter", sans-serif;
  line-height: 1.6;
}

.dialog-divider {
  margin: 0 2rem;
  border-color: #333;
}

.dialog-actions {
  padding: 1.5rem 2rem;
  display: flex;
  justify-content: flex-end;
  background: #1a1a1a;
  border-top: 1px solid #333;
}

.action-btn {
  border-radius: 8px;
  font-weight: 600;
  text-transform: none;
  padding: 0.75rem 2rem;
  font-family: "Inter", "Poppins", sans-serif;
}

.policy-heading {
  font-family: "Inter", sans-serif;
  font-weight: 600;
  color: #ffd700;
  margin: 1.5rem 0 0.5rem 0;
  font-size: 1.1rem;
}

.dialog-body ul {
  margin: 0.5rem 0;
  padding-left: 1.5rem;
}

.dialog-body li {
  margin-bottom: 0.25rem;
  color: #e0e0e0;
}

.dialog-body strong {
  color: #ffd700;
}

/* Responsive Design */
@media (max-width: 960px) {
  .footer-title {
    font-size: 1.8rem;
  }

  .contact-text {
    font-size: 1rem;
  }

  .logo-section {
    padding: 1.5rem 0.5rem;
  }

  .main-logo {
    max-width: 160px;
  }

  .partner-logo {
    max-width: 120px;
  }
}

@media (max-width: 600px) {
  .footer-container {
    padding: 2rem 1rem 1rem !important;
  }

  .footer-title {
    font-size: 1.5rem;
  }

  .contact-text {
    font-size: 0.9rem;
  }

  .social-icons {
    gap: 0.5rem;
  }

  .social-btn {
    width: 40px !important;
    height: 40px !important;
  }

  .logo-row {
    margin: 0 -4px;
  }

  .logo-col {
    padding: 0.5rem;
  }

  .main-logo {
    max-width: 140px;
  }

  .partner-logo {
    max-width: 100px;
  }

  .mission-text {
    font-size: 0.9rem;
  }

  .copyright-text {
    font-size: 0.8rem;
  }

  .legal-link {
    font-size: 0.85rem;
    padding: 0.25rem 0.5rem;
  }
}
</style>
