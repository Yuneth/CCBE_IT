<template>
  <v-footer
    class="footer-container text-center d-flex flex-column"
    color="#1a1a1a"
  >
    <div class="footer-content">
      <!-- Main Footer Content -->
      <div class="footer-main">
        <div class="footer-title-container">
          <strong class="footer-title">Shaping the </strong>
          <span class="highlight"
            > Future of Education</span
          >
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
            <v-icon size="20">{{ icon.name }}</v-icon>
          </v-btn>
        </div>
      </div>

      <!-- Logo Section -->
      <div class="logo-section">
        <v-row justify="center" align="center" class="logo-row">
          <v-col cols="6" sm="3" md="3" lg="2" class="logo-col">
            <img
              class="main-logo"
              :src="logo"
              alt="Cambridge College of British English Logo"
            />
          </v-col>
          <v-col cols="6" sm="3" md="3" lg="2" class="logo-col">
            <img class="partner-logo1" :src="lable1" alt="WEP Partner Logo" />
          </v-col>
          <v-col cols="6" sm="3" md="3" lg="2" class="logo-col">
            <img class="partner-logo2" :src="lable2" alt="IELTS Partner Logo" />
          </v-col>
          <v-col cols="6" sm="3" md="3" lg="2" class="logo-col">
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
      logo: require("@/assets/logo-New.png"),
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
  background: linear-gradient(135deg, white 0%, white 50%) !important;
  border-top: '';
  padding: 2rem 1rem 1.5rem !important;
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
  margin-bottom: 1.5rem;
}

.footer-title-container {
  margin-bottom: 0.75rem;
}

.footer-title {
  font-family: "Inter", "Poppins", sans-serif;
  font-size: 1.8rem;
  font-weight: 700;
  background: linear-gradient(135deg, black 0%, black 50%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  display: inline-block;
}

.highlight {
  background: linear-gradient(135deg, #ffd700 0%, #ffa500 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  font-size: 1.8rem;
  font-weight: 700;
}

.contact-info {
  margin-bottom: 1.25rem;
}

.contact-text {
  font-family: "Inter", sans-serif;
  font-size: 1rem;
  color: black;
  font-weight: 500;
}

/* Social Icons */
.social-icons {
  display: flex;
  justify-content: center;
  gap: 0.75rem;
  margin-bottom: 1.5rem;
}

.social-btn {
  color: black !important;
  transition: all 0.3s ease !important;
  border-radius: 50% !important;
  width: 42px !important;
  height: 42px !important;
}

.social-btn:hover {
  color: black !important;
  background: linear-gradient(135deg, #ffd700 0%, #ffa500 100%) !important;
  transform: translateY(-2px);
  box-shadow: 0 3px 12px rgba(255, 215, 0, 0.3) !important;
}

/* Logo Section */
.logo-section {
  background: linear-gradient(135deg, white 0%, white 50%);
  padding: 1.5rem 0.75rem;
  border-radius: 12px;
  margin-bottom: 1.5rem;
  border: 1px solid white;
}

.logo-row {
  margin: 0 -6px;
}

.logo-col {
  padding: 0.75rem;
  display: flex;
  justify-content: center;
  align-items: center;
}

.main-logo {
  max-width: 160px;
  height: auto;
  transition: transform 0.3s ease;
}

.main-logo:hover {
  transform: scale(1.05);
}

.partner-logo1 {
  max-width: 140px;
  height: auto;
}

.partner-logo2 {
  max-width: 120px;
  height: auto;
}

.partner-logo3 {
  max-width: 200px;
  height: auto;
}

.partner-logo:hover {
  transform: scale(1.05);
}

/* Legal Links */
.legal-links {
  margin-bottom: 1.25rem;
  text-align: center;
}

.legal-link {
  color: black;
  font-family: "Inter", sans-serif;
  font-size: 0.9rem;
  text-decoration: none;
  font-weight: 500;
  padding: 0.4rem 0.75rem;
  border-radius: 6px;
  transition: all 0.3s ease;
  display: inline-block;
}

.legal-link:hover {
  color: #ffffff;
  background: black;
  text-decoration: underline;
}

.link-separator {
  color: #666;
  margin: 0 0.4rem;
}

/* Copyright Section */
.copyright-section {
  text-align: center;
  border-top: 1px solid #333;
  padding-top: 1.25rem;
}

.mission-text {
  font-family: "Inter", sans-serif;
  font-size: 0.95rem;
  line-height: 1.5;
  color: black;
  margin-bottom: 0.75rem;
  max-width: 700px;
  margin-left: auto;
  margin-right: auto;
}

.copyright-text {
  font-family: "Inter", sans-serif;
  font-size: 0.85rem;
  color: #999;
  margin: 0;
}

/* Dialog Styles */
.modern-dialog {
  font-family: "Inter", "Poppins", sans-serif;
}

.dialog-card {
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.4);
  border: 2px solid #ffd700;
  background: #1a1a1a;
}

.dialog-header {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 1.5rem 1.5rem 1rem;
  background: linear-gradient(135deg, white 0%, white 100%);
  color: black;
  border-bottom: 1px solid #333;
}

.dialog-icon {
  font-size: 1.8rem !important;
  color: #ffd700 !important;
}

.dialog-title {
  font-weight: 700;
  font-size: 1.3rem;
  margin: 0;
  letter-spacing: -0.25px;
  text-shadow: 0 2px 8px rgba(255, 215, 0, 0.3);
}

.dialog-body {
  padding: 1.5rem;
  background: white;
  color: black;
  font-family: "Inter", sans-serif;
  line-height: 1.5;
  font-size: 0.9rem;
}

.dialog-divider {
  margin: 0 1.5rem;
  border-color: #333;
}

.dialog-actions {
  padding: 1.25rem 1.5rem;
  display: flex;
  justify-content: flex-end;
  background: white;
  border-top: 1px solid #333;
}

.action-btn {
  border-radius: 8px;
  font-weight: 600;
  text-transform: none;
  padding: 0.6rem 1.5rem;
  font-family: "Inter", "Poppins", sans-serif;
}

.policy-heading {
  font-family: "Inter", sans-serif;
  font-weight: 600;
  color: black;
  margin: 1.25rem 0 0.5rem 0;
  font-size: 1rem;
}

.dialog-body ul {
  margin: 0.5rem 0;
  padding-left: 1.25rem;
}

.dialog-body li {
  margin-bottom: 0.25rem;
  color: black;
}

.dialog-body strong {
  color: black;
}

/* Responsive Design */
@media (max-width: 960px) {
  .footer-title {
    font-size: 1.6rem;
  }

  .contact-text {
    font-size: 0.95rem;
  }

  .logo-section {
    padding: 1.25rem 0.5rem;
  }

  .main-logo {
    max-width: 140px;
  }

  .partner-logo1 {
    max-width: 120px;
  }

  .partner-logo2 {
    max-width: 100px;
  }

  .partner-logo3 {
    max-width: 160px;
  }
}

@media (max-width: 768px) {
  .footer-container {
    padding: 1.5rem 0.75rem 1rem !important;
  }

  .footer-title {
    font-size: 1.4rem;
  }

  .contact-text {
    font-size: 0.9rem;
  }

  .social-icons {
    gap: 0.5rem;
  }

  .social-btn {
    width: 38px !important;
    height: 38px !important;
  }

  .logo-row {
    margin: 0 -4px;
  }

  .logo-col {
    padding: 0.5rem;
  }

  .main-logo {
    max-width: 120px;
  }

  .partner-logo1 {
    max-width: 100px;
  }

  .partner-logo2 {
    max-width: 80px;
  }

  .partner-logo3 {
    max-width: 140px;
  }

  .mission-text {
    font-size: 0.9rem;
  }

  .copyright-text {
    font-size: 0.8rem;
  }

  .legal-link {
    font-size: 0.85rem;
    padding: 0.3rem 0.5rem;
  }

  .dialog-header {
    padding: 1.25rem 1rem 0.75rem;
  }

  .dialog-body {
    padding: 1.25rem;
  }

  .dialog-actions {
    padding: 1rem 1.25rem;
  }
}

@media (max-width: 480px) {
  .footer-container {
    padding: 1rem 0.5rem 0.75rem !important;
  }

  .footer-title {
    font-size: 1.2rem;
  }

  .contact-text {
    font-size: 0.85rem;
  }

  .social-btn {
    width: 36px !important;
    height: 36px !important;
  }

  .logo-section {
    padding: 1rem 0.25rem;
  }

  .logo-col {
    padding: 0.25rem;
  }

  .main-logo {
    max-width: 100px;
  }

  .partner-logo1 {
    max-width: 80px;
  }

  .partner-logo2 {
    max-width: 70px;
  }

  .partner-logo3 {
    max-width: 120px;
  }

  .mission-text {
    font-size: 0.85rem;
  }

  .copyright-text {
    font-size: 0.75rem;
  }

  .legal-links {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  .link-separator {
    display: none;
  }

  .dialog-header {
    padding: 1rem 0.75rem 0.5rem;
  }

  .dialog-body {
    padding: 1rem;
    font-size: 0.85rem;
  }

  .dialog-actions {
    padding: 0.75rem 1rem;
  }

  .action-btn {
    padding: 0.5rem 1.25rem;
  }
}

/* Touch-friendly improvements */
@media (hover: none) {
  .social-btn:hover {
    transform: none;
  }
  
  .legal-link:hover {
    background: transparent;
  }
  
  .main-logo:hover {
    transform: none;
  }
}

/* Reduced motion support */
@media (prefers-reduced-motion: reduce) {
  .social-btn {
    transition: none;
  }
  
  .main-logo {
    transition: none;
  }
  
  .legal-link {
    transition: none;
  }
}
</style>