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
          <b>Cambridge College of British English (CCBE)</b> Careers is your
          gateway to a world of possibilities and a launchpad for your
          professional aspirations. Be part of a prestigious institution that
          not only prioritizes academic excellence but also nurtures a thriving
          community of dedicated professionals. Together, we inspire confidence,
          build futures, and redefine what it means to succeed. Your career
          journey begins here at Cambridge College of British English!
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
              <!-- Image Container with Zoom -->
              <div class="image-container" @click="openImageZoom(career.image)">
                <v-img
                  :src="career.image"
                  height="300"
                  width="auto"
                  cover
                  class="career-image"
                  @error="handleImageError(index)"
                >
                  <template v-slot:placeholder>
                    <div class="image-placeholder">
                      <v-progress-circular
                        indeterminate
                        color="#FFD700"
                      ></v-progress-circular>
                      <p>Loading image...</p>
                    </div>
                  </template>
                </v-img>
                <div class="card-overlay">
                  <v-icon class="overlay-icon">mdi-account-tie</v-icon>
                  <span class="overlay-text">Career</span>
                </div>
                <!-- Zoom Indicator -->
                <div class="zoom-indicator">
                  <v-icon color="white" size="20"
                    >mdi-magnify-plus-outline</v-icon
                  >
                  <span class="zoom-text">Click to View</span>
                </div>
              </div>

              <!-- Card Content -->
              <v-card-text class="card-content">
                <div class="career-badge">Opportunity</div>
                <h3 class="career-title">Join Our Team</h3>
                <p class="career-description">
                  Explore exciting career opportunities and grow with us in a
                  dynamic educational environment.
                </p>
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
            Join our prestigious institution and be part of a team that's
            transforming English education. We offer competitive packages,
            professional development, and a supportive work environment.
          </p>
          <v-btn class="cta-button" size="large" @click="openApplicationDialog">
            Start Your Application
            <v-icon right>mdi-rocket-launch</v-icon>
          </v-btn>
        </div>
      </section>
    </v-container>

     <ArrowButton></ArrowButton>
    <ChatBot></ChatBot>
    <FooterPage></FooterPage>

    <!-- Image Zoom Dialog -->
    <v-dialog
      v-model="imageZoomDialog"
      max-width="95vw"
      max-height="95vh"
      persistent
      class="image-zoom-dialog-wrapper"
    >
      <v-card class="image-zoom-dialog">
        <div class="zoom-dialog-header">
          <v-btn icon @click="closeImageZoom" class="close-zoom-btn">
            <v-icon>mdi-close</v-icon>
          </v-btn>
          <div class="zoom-controls">
            <v-btn
              icon
              @click="zoomOut"
              :disabled="zoomLevel <= 0.5"
              class="control-btn"
            >
              <v-icon>mdi-magnify-minus</v-icon>
            </v-btn>
            <span class="zoom-percentage"
              >{{ Math.round(zoomLevel * 100) }}%</span
            >
            <v-btn
              icon
              @click="zoomIn"
              :disabled="zoomLevel >= 3"
              class="control-btn"
            >
              <v-icon>mdi-magnify-plus</v-icon>
            </v-btn>
            <v-btn icon @click="resetZoom" class="control-btn">
              <v-icon>mdi-autorenew</v-icon>
            </v-btn>
          </div>
        </div>

        <div
          class="image-zoom-container"
          @mousemove="handleMouseMove"
          @wheel="handleWheel"
        >
          <div
            class="zoomed-image-wrapper"
            :style="{
              transform: `scale(${zoomLevel}) translate(${panX}px, ${panY}px)`,
              cursor: isDragging
                ? 'grabbing'
                : zoomLevel > 1
                ? 'grab'
                : 'default',
            }"
            @mousedown="startDrag"
            @mouseup="stopDrag"
            @mouseleave="stopDrag"
          >
            <img
              :src="currentZoomImage"
              class="zoomed-image"
              @load="handleImageLoad"
              @error="handleZoomImageError"
              alt="Career Opportunity"
            />
            <div v-if="imageLoading" class="zoom-placeholder">
              <v-progress-circular
                indeterminate
                color="#FFD700"
                size="64"
              ></v-progress-circular>
              <p>Loading high-quality image...</p>
            </div>
          </div>

          <!-- Scroll Bars -->
          <div v-if="zoomLevel > 1" class="scroll-bars-container">
            <div class="vertical-scrollbar" @mousedown="startVerticalScroll">
              <div
                class="vertical-scroll-thumb"
                :style="{
                  height: verticalThumbHeight + '%',
                  top: verticalThumbPosition + '%',
                }"
              ></div>
            </div>
            <div
              class="horizontal-scrollbar"
              @mousedown="startHorizontalScroll"
            >
              <div
                class="horizontal-scroll-thumb"
                :style="{
                  width: horizontalThumbWidth + '%',
                  left: horizontalThumbPosition + '%',
                }"
              ></div>
            </div>
          </div>
        </div>

        <!-- <div class="zoom-footer">
          <p class="image-instructions">
            • Use mouse wheel to zoom in/out • Drag to pan when zoomed • Scroll
            bars available when zoomed • Click outside or press ESC to close
          </p>
        </div> -->
      </v-card>
    </v-dialog>

    <!-- Application Dialog -->
    <div class="text-center">
      <v-dialog v-model="dialog" max-width="800" persistent>
        <v-card class="application-dialog">
          <div class="dialog-header">
            <v-icon class="dialog-icon">mdi-briefcase-outline</v-icon>
            <h2 class="dialog-title">Career Application</h2>
            <p class="dialog-subtitle">
              Join the Cambridge College of British English Family
            </p>
          </div>

          <v-card-text class="dialog-content">
            <v-row dense>
              <v-col cols="12" md="6">
                <v-text-field
                  label="Your Full Name"
                  v-model="formData.name"
                  required
                  variant="outlined"
                  color="#FFD700"
                  prepend-inner-icon="mdi-account"
                ></v-text-field>
              </v-col>
              <v-col cols="12" md="6">
                <v-select
                  :items="[
                    'Teaching',
                    'Administration',
                    'Management',
                    'Marketing',
                    'Development',
                    'Business Development',
                  ]"
                  v-model="formData.position"
                  label="Position Applying For"
                  required
                  variant="outlined"
                  color="#FFD700"
                  prepend-inner-icon="mdi-briefcase-outline"
                ></v-select>
              </v-col>
              <v-col cols="12" md="6">
                <v-select
                  :items="[
                    'Ambalangoda',
                    'Galle',
                    'Horana',
                    'Matara',
                    'Piliyandala',
                  ]"
                  v-model="formData.branch"
                  label="Preferred Branch Location"
                  required
                  variant="outlined"
                  color="#FFD700"
                  prepend-inner-icon="mdi-map-marker"
                ></v-select>
              </v-col>
              <v-col cols="12" md="6">
                <v-select
                  :items="[
                    'Masters',
                    'Bachelors',
                    'HND',
                    'Diploma',
                    'Certificate',
                  ]"
                  v-model="formData.qualifications"
                  label="Highest Educational Qualifications"
                  required
                  variant="outlined"
                  color="#FFD700"
                  prepend-inner-icon="mdi-school"
                ></v-select>
              </v-col>
              <v-col cols="12" md="6">
                <v-select
                  :items="[
                    'No Experience',
                    '<2 Years',
                    '<3 Years',
                    '<4 Years',
                    '4+ Years',
                  ]"
                  v-model="formData.experience"
                  label="Relevant Experience"
                  required
                  variant="outlined"
                  color="#FFD700"
                  prepend-inner-icon="mdi-chart-timeline"
                ></v-select>
              </v-col>
              <v-col cols="12" md="6">
                <v-select
                  :items="[
                    'Social Media',
                    'Website',
                    'Friend/Referral',
                    'Newspaper',
                    'Other',
                  ]"
                  v-model="formData.source"
                  label="How did you hear about us?"
                  required
                  variant="outlined"
                  color="#FFD700"
                  prepend-inner-icon="mdi-information"
                ></v-select>
              </v-col>
              <v-col cols="12" md="6">
                <v-text-field
                  label="Contact Number"
                  v-model="formData.contact"
                  variant="outlined"
                  color="#FFD700"
                  prepend-inner-icon="mdi-phone"
                ></v-text-field>
              </v-col>
              <v-col cols="12" md="6">
                <v-text-field
                  label="Email Address"
                  v-model="formData.email"
                  type="email"
                  variant="outlined"
                  color="#FFD700"
                  prepend-inner-icon="mdi-email"
                ></v-text-field>
              </v-col>
            </v-row>
            <small class="text-caption required-note"
              >*indicates required field</small
            >
          </v-card-text>

          <v-divider></v-divider>

          <v-card-actions class="dialog-actions">
            <v-btn
              class="cancel-btn"
              variant="outlined"
              @click="dialog = false"
              size="large"
            >
              <v-icon left>mdi-close-circle</v-icon>
              Cancel
            </v-btn>
            <v-btn
              class="submit-btn"
              variant="flat"
              @click="sendInquiry"
              :loading="loading"
              size="large"
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
            <v-icon color="#FFD700" size="48" class="mr-3"
              >mdi-check-circle</v-icon
            >
            Application Sent Successfully!
          </v-card-title>
          <v-card-text class="success-content text-center">
            <p>
              Thank you for your interest in joining Cambridge College of
              British English!
            </p>
            <p>
              Your application has been successfully submitted and will be
              reviewed by our HR team.
            </p>
            <p class="success-note">
              <v-icon color="#FFD700" small class="mr-1">mdi-clock</v-icon>
              We will contact you within 3-5 working days
            </p>
          </v-card-text>
          <v-divider></v-divider>
          <v-card-actions class="success-actions">
            <v-spacer></v-spacer>
            <v-btn
              class="close-success-btn"
              variant="flat"
              @click="successDialog = false"
              size="large"
            >
              <v-icon left>mdi-thumb-up</v-icon>
              Great, Thank You!
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
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

export default {
  name: "CareersPage",
  data() {
    return {
      dialog: false,
      successDialog: false,
      loading: false,
      imageZoomDialog: false,
      currentZoomImage: "",
      zoomLevel: 1,
      panX: 0,
      panY: 0,
      isDragging: false,
      lastMouseX: 0,
      lastMouseY: 0,
      imageLoading: false,
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
      verticalThumbHeight: 100,
      verticalThumbPosition: 0,
      horizontalThumbWidth: 100,
      horizontalThumbPosition: 0,
      isVerticalScrolling: false,
      isHorizontalScrolling: false,
      lastScrollY: 0,
      lastScrollX: 0,
      careers: [
        {
          image:
            "https://ik.imagekit.io/u3wbiya66/Careers/C1.jpg?updatedAt=1760439871391",
          loaded: true,
        },
        {
          image:
            "https://ik.imagekit.io/u3wbiya66/Careers/C2.jpg?updatedAt=1760439871237",
          loaded: true,
        },
        {
          image:
            "https://ik.imagekit.io/u3wbiya66/Careers/WhatsApp%20Image%202025-08-22%20at%2008.47.25_0277efb2.jpg?updatedAt=1755832794043",
          loaded: true,
        },
        {
          image:
            "https://ik.imagekit.io/u3wbiya66/Careers/WhatsApp%20Image%202025-08-22%20at%2008.46.00_3a637631.jpg?updatedAt=1755832782647",
          loaded: true,
        },
        {
          image:
            "https://ik.imagekit.io/u3wbiya66/Careers/2.png?updatedAt=1755833509742",
          loaded: true,
        },
        {
          image:
            "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0006.jpg?updatedAt=1737434201584",
          loaded: true,
        },
        {
          image:
            "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0011.jpg?updatedAt=1737435218639",
          loaded: true,
        },
        {
          image:
            "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0009.jpg?updatedAt=1737435218715",
          loaded: true,
        },
        {
          image:
            "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0007.jpg?updatedAt=1737435218724",
          loaded: true,
        },
        {
          image:
            "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0010.jpg?updatedAt=1737435218885",
          loaded: true,
        },
        {
          image:
            "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0012.jpg?updatedAt=1737435219022",
          loaded: true,
        },
        {
          image:
            "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0008.jpg?updatedAt=1737435219045",
          loaded: true,
        },
        {
          image:
            "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0015.jpg?updatedAt=1737435219046",
          loaded: true,
        },
        {
          image:
            "https://ik.imagekit.io/u3wbiya66/IMG-20250121-WA0014.jpg?updatedAt=1737435219125",
          loaded: true,
        },
      ],
    };
  },
  components: {
    NavBar,
    FooterPage,
    ChatBot,
    ArrowButton
  },
  mounted() {
    AOS.init({
      duration: 1000,
      once: true,
      offset: 100,
    });
    // Add keyboard event listener for ESC key
    document.addEventListener("keydown", this.handleKeyPress);

    // Preload images for better performance
    this.preloadImages();
  },
  beforeUnmount() {
    // Remove keyboard event listener
    document.removeEventListener("keydown", this.handleKeyPress);
  },
  methods: {
    openApplicationDialog() {
      this.dialog = true;
    },

    updateScrollbarMetrics() {
      // Calculate scroll thumb sizes based on zoom level
      const baseSize = 80;
      this.verticalThumbHeight = Math.max(0, baseSize / this.zoomLevel);
      this.horizontalThumbWidth = Math.max(0, baseSize / this.zoomLevel);

      // Calculate scroll thumb positions based on pan position
      const maxPan = 80 * (this.zoomLevel - 1);
      if (maxPan > 0) {
        this.verticalThumbPosition =
          (-this.panY / maxPan) * (80 - this.verticalThumbHeight);
        this.horizontalThumbPosition =
          (-this.panX / maxPan) * (80 - this.horizontalThumbWidth);
      } else {
        this.verticalThumbPosition = 0;
        this.horizontalThumbPosition = 0;
      }
    },

    startVerticalScroll(event) {
      this.isVerticalScrolling = true;
      this.lastScrollY = event.clientY;
      document.addEventListener("mousemove", this.handleVerticalScroll);
      document.addEventListener("mouseup", this.stopVerticalScroll);
      event.preventDefault();
    },

    handleVerticalScroll(event) {
      if (!this.isVerticalScrolling) return;

      const scrollbar = document.querySelector(".vertical-scrollbar");
      if (!scrollbar) return;

      const scrollbarRect = scrollbar.getBoundingClientRect();
      const scrollbarHeight = scrollbarRect.height;
      const deltaY = event.clientY - this.lastScrollY;

      const scrollRatio = deltaY / scrollbarHeight;
      const maxPan = 80 * (this.zoomLevel - 1);

      this.panY = Math.max(
        -maxPan,
        Math.min(0, this.panY - scrollRatio * maxPan * 2)
      );
      this.lastScrollY = event.clientY;
      this.updateScrollbarMetrics();
    },

    stopVerticalScroll() {
      this.isVerticalScrolling = false;
      document.removeEventListener("mousemove", this.handleVerticalScroll);
      document.removeEventListener("mouseup", this.stopVerticalScroll);
    },

    startHorizontalScroll(event) {
      this.isHorizontalScrolling = true;
      this.lastScrollX = event.clientX;
      document.addEventListener("mousemove", this.handleHorizontalScroll);
      document.addEventListener("mouseup", this.stopHorizontalScroll);
      event.preventDefault();
    },

    handleHorizontalScroll(event) {
      if (!this.isHorizontalScrolling) return;

      const scrollbar = document.querySelector(".horizontal-scrollbar");
      if (!scrollbar) return;

      const scrollbarRect = scrollbar.getBoundingClientRect();
      const scrollbarWidth = scrollbarRect.width;
      const deltaX = event.clientX - this.lastScrollX;

      const scrollRatio = deltaX / scrollbarWidth;
      const maxPan = 80 * (this.zoomLevel - 1);

      this.panX = Math.max(
        -maxPan,
        Math.min(0, this.panX - scrollRatio * maxPan * 2)
      );
      this.lastScrollX = event.clientX;
      this.updateScrollbarMetrics();
    },

    stopHorizontalScroll() {
      this.isHorizontalScrolling = false;
      document.removeEventListener("mousemove", this.handleHorizontalScroll);
      document.removeEventListener("mouseup", this.stopHorizontalScroll);
    },

    // Image Loading Methods
    preloadImages() {
      this.careers.forEach((career) => {
        const img = new Image();
        img.src = career.image;
        img.onload = () => {
          career.loaded = true;
        };
        img.onerror = () => {
          career.loaded = false;
          console.warn("Failed to load image:", career.image);
        };
      });
    },

    handleImageError(index) {
      console.error(
        `Failed to load image at index ${index}:`,
        this.careers[index].image
      );
      this.careers[index].loaded = false;
    },

    handleZoomImageError() {
      console.error("Failed to load zoom image:", this.currentZoomImage);
      this.imageLoading = false;
    },

    handleImageLoad() {
      this.imageLoading = false;
    },

    // Image Zoom Methods
    openImageZoom(imageUrl) {
      this.currentZoomImage = imageUrl;
      this.imageZoomDialog = true;
      this.imageLoading = true;
      this.resetZoom();

      // Force image reload
      const img = new Image();
      img.src = imageUrl;
      img.onload = () => {
        this.imageLoading = false;
        this.updateScrollbarMetrics();
      };
      img.onerror = () => {
        this.imageLoading = false;
        console.error("Failed to load image for zoom:", imageUrl);
      };
    },

    closeImageZoom() {
      this.imageZoomDialog = false;
      this.resetZoom();
      this.imageLoading = false;
    },

    zoomIn() {
      if (this.zoomLevel < 3) {
        this.zoomLevel = Math.min(this.zoomLevel + 0.25, 3);
        this.updateScrollbarMetrics();
      }
    },

    zoomOut() {
      if (this.zoomLevel > 0.3) {
        this.zoomLevel = Math.max(this.zoomLevel - 0.25, 0.3);
        if (this.zoomLevel === 1) {
          this.resetPan();
        }
        this.updateScrollbarMetrics();
      }
    },

    resetZoom() {
      this.zoomLevel = 1;
      this.resetPan();
      this.updateScrollbarMetrics();
    },

    resetPan() {
      this.panX = 0;
      this.panY = 0;
    },

    handleWheel(event) {
      event.preventDefault();
      if (event.deltaY < 0) {
        this.zoomIn();
      } else {
        this.zoomOut();
      }
    },

    startDrag(event) {
      if (this.zoomLevel > 1) {
        this.isDragging = true;
        this.lastMouseX = event.clientX;
        this.lastMouseY = event.clientY;
      }
    },

    stopDrag() {
      this.isDragging = false;
    },

    handleMouseMove(event) {
      if (this.isDragging && this.zoomLevel > 1) {
        const deltaX = event.clientX - this.lastMouseX;
        const deltaY = event.clientY - this.lastMouseY;

        const maxPan = 80 * (this.zoomLevel - 1);
        this.panX = Math.max(-maxPan, Math.min(0, this.panX + deltaX));
        this.panY = Math.max(-maxPan, Math.min(0, this.panY + deltaY));

        this.lastMouseX = event.clientX;
        this.lastMouseY = event.clientY;
        this.updateScrollbarMetrics();
      }
    },

    handleKeyPress(event) {
      if (event.key === "Escape" && this.imageZoomDialog) {
        this.closeImageZoom();
      }
    },

    async sendInquiry() {
      this.loading = true;
      const formData = this.formData;

      try {
        // Send first email to info@ccbe.lk
        await emailjs.send(
          "service_s33obqe",
          "template_mz5d1yg",
          formData,
          "WIB0bG1OPslsktqa2"
        );
        console.log("First email sent successfully");

        // Send second email to Jobs@ccbe.lk
        await emailjs.send(
          "service_eypw2ip",
          "template_ygw1cnq",
          formData,
          "sW9PkDNeVewlET9FF"
        );
        console.log("Second email sent successfully");

        // Show success dialog
        this.successDialog = true;
        this.dialog = false;

        // Open Google Form in new tab
        window.open(
          "https://docs.google.com/forms/d/e/1FAIpQLSco34ONLHBhIu6kfET6PNMynrJ-R5x9qRLIfGrYSquXd9tmwQ/viewform?fbzx=5328050623112666009",
          "_blank"
        );

        // Reset the form
        this.clearForm();
      } catch (error) {
        console.error("Error sending emails:", error);
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
  background: linear-gradient(135deg, white 0%, white 50%, white 100%);
  min-height: 100vh;
  color: #ffffff;
  font-family: "Inter", "Poppins", sans-serif;
}

.main-container {
  background: transparent;
  padding: 2rem 1rem;
  max-width: 1400px;
  margin: 0 auto;
}

/* Header Section */
.header-section {
  text-align: center;
  padding: 4rem 0 3rem;
  margin-bottom: 3rem;
  border-radius: 20px;
  margin: 2rem 1rem 4rem;
  position: relative;
  overflow: hidden;
}

.page-title {
  font-family: "Inter", "Poppins", sans-serif;
  font-size: 2rem;
  font-weight: 900;
  color: black;
  margin-bottom: 2rem;
  text-transform: uppercase;
  letter-spacing: 2px;
  text-shadow: 0 4px 20px rgba(255, 215, 0, 0.3);
  line-height: 1.1;
}

.highlight {
  background: linear-gradient(135deg, #ffd700 0%, #ffa500 50%, #ff8c00 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  position: relative;
  display: inline-block;
}

.highlight::after {
  content: "";
  position: absolute;
  bottom: -8px;
  left: 0;
  width: 100%;
  height: 3px;
  background: linear-gradient(
    90deg,
    transparent,
    #ffd700,
    #ffa500,
    #ffd700,
    transparent
  );
  opacity: 0.8;
  border-radius: 2px;
}

.intro-text {
  font-family: "Inter", sans-serif;
  font-size: 1.1rem;
  line-height: 1.8;
  color: black;
  max-width: 1100px;
  margin: 0 auto;
  text-align: center;
  padding: 0 2rem;
  font-weight: 400;
}

.intro-text b {
  color: black;
  font-weight: 600;
}

/* Careers Section */
.careers-section {
  padding: 3rem 0;
  position: relative;
}

.careers-section::before {
  content: "";
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 100px;
  height: 3px;
  background: linear-gradient(90deg, transparent, #ffd700, transparent);
}

.careers-grid {
  margin: 0 -12px;
}

/* Career Card */
.career-card {
  background: linear-gradient(145deg, #2d2d2d 0%, #1a1a1a 100%);
  border: 2px solid #333;
  border-radius: 25px;
  overflow: hidden;
  transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
  height: 100%;
  position: relative;
  margin-bottom: 2.5rem;
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.3);
}

.career-card::before {
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
  transition: left 0.8s ease;
  z-index: 1;
}

.career-card:hover::before {
  left: 100%;
}

.career-card:hover {
  transform: translateY(-20px) scale(1.02);
  border-color: #ffd700;
  box-shadow: 0 35px 60px rgba(255, 215, 0, 0.25);
}

/* Image Container with Zoom */
.image-container {
  position: relative;
  overflow: hidden;
  cursor: pointer;
  border-radius: 23px 23px 0 0;
}

.career-image {
  transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
  position: relative;
}

.career-card:hover .career-image {
  transform: scale(1.08);
}

.zoom-indicator {
  position: absolute;
  bottom: 1.5rem;
  left: 50%;
  transform: translateX(-50%);
  background: linear-gradient(
    135deg,
    rgba(0, 0, 0, 0.9) 0%,
    rgba(26, 26, 26, 0.9) 100%
  );
  padding: 0.7rem 1.5rem;
  border-radius: 25px;
  display: flex;
  align-items: center;
  gap: 0.7rem;
  opacity: 0;
  transition: all 0.4s ease;
  backdrop-filter: blur(15px);
  border: 1px solid rgba(255, 215, 0, 0.4);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.5);
}

.image-container:hover .zoom-indicator {
  opacity: 1;
  transform: translateX(-50%) translateY(-8px);
}

.zoom-text {
  font-family: "Inter", sans-serif;
  font-size: 0.85rem;
  font-weight: 700;
  color: #ffd700;
  text-transform: uppercase;
  letter-spacing: 0.8px;
}

.image-placeholder {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 300px;
  background: linear-gradient(135deg, #333 0%, #222 100%);
  gap: 1rem;
  border-radius: 23px 23px 0 0;
}

.image-placeholder p {
  font-family: "Inter", sans-serif;
  font-size: 0.9rem;
  color: #e0e0e0;
  margin: 0;
}

.card-overlay {
  position: absolute;
  top: 1.2rem;
  right: 1.2rem;
  background: linear-gradient(
    135deg,
    rgba(255, 215, 0, 0.95) 0%,
    rgba(255, 165, 0, 0.95) 100%
  );
  padding: 0.6rem 1.2rem;
  border-radius: 20px;
  display: flex;
  align-items: center;
  gap: 0.6rem;
  backdrop-filter: blur(10px);
  box-shadow: 0 4px 15px rgba(255, 215, 0, 0.3);
  z-index: 2;
}

.overlay-icon {
  color: #000000 !important;
  font-size: 1.3rem !important;
}

.overlay-text {
  font-family: "Inter", sans-serif;
  font-size: 0.85rem;
  font-weight: 700;
  color: #000000;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

/* Card Content */
.card-content {
  padding: 2.5rem 2rem;
  position: relative;
  z-index: 2;
}

.career-badge {
  font-family: "Inter", sans-serif;
  font-size: 0.75rem;
  font-weight: 800;
  color: #ffd700;
  background: linear-gradient(
    135deg,
    rgba(255, 215, 0, 0.15) 0%,
    rgba(255, 165, 0, 0.1) 100%
  );
  padding: 0.5rem 1.2rem;
  border-radius: 20px;
  display: inline-block;
  margin-bottom: 1.2rem;
  text-transform: uppercase;
  letter-spacing: 1px;
  border: 1px solid rgba(255, 215, 0, 0.3);
}

.career-title {
  font-family: "Inter", sans-serif;
  font-size: 1.5rem;
  font-weight: 800;
  color: #ffffff;
  line-height: 1.3;
  margin-bottom: 1rem;
  min-height: 3.8rem;
  background: linear-gradient(135deg, #ffffff 0%, #e0e0e0 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.career-description {
  font-family: "Inter", sans-serif;
  font-size: 1rem;
  line-height: 1.6;
  color: #b0b0b0;
  margin-bottom: 0;
  font-weight: 400;
}

/* Card Actions */
.card-actions {
  padding: 0 2rem 2.5rem;
  display: flex;
  justify-content: center;
}

.apply-now-btn {
  background: linear-gradient(
    135deg,
    #ffd700 0%,
    #ffa500 50%,
    #ff8c00 100%
  ) !important;
  color: #000000 !important;
  font-weight: 700 !important;
  font-family: "Inter", sans-serif !important;
  border: 2px solid transparent !important;
  border-radius: 30px !important;
  padding: 1rem 2.5rem !important;
  text-transform: none !important;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1) !important;
  font-size: 1rem !important;
  letter-spacing: 0.5px;
  box-shadow: 0 6px 20px rgba(255, 215, 0, 0.3) !important;
  position: relative;
  overflow: hidden;
}

.apply-now-btn::before {
  content: "";
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    90deg,
    transparent,
    rgba(255, 255, 255, 0.2),
    transparent
  );
  transition: left 0.6s ease;
}

.apply-now-btn:hover::before {
  left: 100%;
}

.apply-now-btn:hover {
  transform: translateY(-3px) scale(1.05);
  box-shadow: 0 12px 30px rgba(255, 215, 0, 0.5) !important;
  border-color: #ffd700 !important;
}

/* CTA Section */
.cta-section {
  text-align: center;
  padding: 4rem 0;
  margin-top: 2rem;
}

.cta-section::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: url("data:image/svg+xml,%3Csvg width='100' height='100' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M11 18c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm48 25c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm-43-7c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm63 31c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM34 90c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm56-76c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM12 86c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm28-65c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm23-11c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-6 60c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm29 22c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zM32 63c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm57-13c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-9-21c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM60 91c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM35 41c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM12 60c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2z' fill='%23ffd700' fill-opacity='0.03' fill-rule='evenodd'/%3E%3C/svg%3E");
  opacity: 0.6;
}

.cta-content {
  max-width: 600px;
  margin: 0 auto;
}

.cta-title {
  font-family: "Inter", sans-serif;
  font-size: 2.5rem;
  font-weight: 700;
  color: #ffffff;
  margin-bottom: 1rem;
}

.cta-description {
  font-family: "Inter", sans-serif;
  font-size: 1.1rem;
  line-height: 1.6;
  color: black;
  margin-bottom: 2rem;
}

.cta-button {
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
  box-shadow: 0 8px 25px rgba(255, 215, 0, 0.3) !important;
}

.cta-button::before {
  content: "";
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    90deg,
    transparent,
    rgba(255, 255, 255, 0.3),
    transparent
  );
  transition: left 0.7s ease;
}

.cta-button:hover::before {
  left: 100%;
}

/* Image Zoom Dialog */
.image-zoom-dialog-wrapper {
  z-index: 1000;
}

.image-zoom-dialog {
  background: rgba(10, 10, 10, 0.98) !important;
  border: 3px solid #ffd700;
  border-radius: 20px;
  overflow: hidden;
  height: 95vh;
  display: flex;
  flex-direction: column;
  box-shadow: 0 25px 50px rgba(0, 0, 0, 0.8);
}

.zoom-dialog-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 1rem;
  background: linear-gradient(
    135deg,
    rgba(26, 26, 26, 0.98) 0%,
    rgba(45, 45, 45, 0.95) 100%
  );
  border-bottom: 1px solid #333;
  
  z-index: 1001;
}

.close-zoom-btn {
  color: #ffd700 !important;
  background: linear-gradient(
    135deg,
    rgba(255, 215, 0, 0.15) 0%,
    rgba(255, 165, 0, 0.1) 100%
  ) !important;
  border: 0.5px solid rgba(255, 215, 0, 0.3) !important;
  transition: all 0.3s ease !important;
}

.close-zoom-btn:hover {
  background: linear-gradient(
    135deg,
    rgba(255, 215, 0, 0.25) 0%,
    rgba(255, 165, 0, 0.2) 100%
  ) !important;
  transform: scale(1.1);
}

.zoom-controls {
  display: flex;
  align-items: center;
  gap: 1.2rem;
  background: linear-gradient(
    135deg,
    rgba(0, 0, 0, 0.9) 0%,
    rgba(26, 26, 26, 0.8) 100%
  );
  padding: 0.8rem 1rem;
  border-radius: 20px;
  border: 2px solid #ffd700;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.5);
}

.control-btn {
  color: #ffd700 !important;
  background: rgba(255, 215, 0, 0.1) !important;
  transition: all 0.3s ease !important;
  border-radius: 12px !important;
}

.control-btn:hover {
  background: rgba(255, 215, 0, 0.25) !important;
  transform: scale(1.15);
  box-shadow: 0 4px 15px rgba(255, 215, 0, 0.3);
}

.control-btn:disabled {
  color: #666 !important;
  background: rgba(102, 102, 102, 0.1) !important;
  opacity: 0.5;
  transform: none !important;
  box-shadow: none !important;
}

.zoom-percentage {
  font-family: "Inter", sans-serif;
  font-weight: 800;
  color: #ffd700;
  min-width: 60px;
  text-align: center;
  font-size: 1.1rem;
  text-shadow: 0 2px 10px rgba(255, 215, 0, 0.5);
}

.image-zoom-container {
  flex: 1;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #000;
  position: relative;
  cursor: grab;
}

.zoomed-image-wrapper {
  transition: transform 0.1s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
}

.zoomed-image {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
  display: block;
  border-radius: 8px;
}

.zoom-placeholder {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
  color: #ffd700;
  gap: 1.5rem;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(
    135deg,
    rgba(10, 10, 10, 0.95) 0%,
    rgba(26, 26, 26, 0.9) 100%
  );
  backdrop-filter: blur(10px);
}

.zoom-placeholder p {
  font-family: "Inter", sans-serif;
  font-size: 1.2rem;
  color: #e0e0e0;
  font-weight: 500;
}

/* .zoom-footer {
  padding: 1.5rem;
  background: linear-gradient(
    135deg,
    rgba(26, 26, 26, 0.98) 0%,
    rgba(45, 45, 45, 0.95) 100%
  );
  border-top: 2px solid #333;
  text-align: center;
  z-index: 1001;
} */

/* .image-instructions {
  font-family: "Inter", sans-serif;
  font-size: 0.9rem;
  color: #ffd700;
  margin: 0;
  font-weight: 500;
  letter-spacing: 0.5px;
} */

/* Enhanced Image Quality on Zoom */
.zoomed-image {
  image-rendering: -webkit-optimize-contrast;
  image-rendering: crisp-edges;
  image-rendering: high-quality;
}

/* Smooth transitions for zoom */
.zoomed-image-wrapper {
  will-change: transform;
}

/* Application Dialog Styles */
.application-dialog {
  background: linear-gradient(145deg, white 0%, white 100%) !important;
  border: 3px solid #333;
  border-radius: 25px;
  overflow: hidden;
  box-shadow: 0 25px 50px rgba(0, 0, 0, 0.5);
}

.dialog-header {
  background: linear-gradient(135deg, white 0%, white 100%);
  padding: 2rem;
  text-align: center;
  color: #000000;
}

.dialog-header::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23000000' fill-opacity='0.1'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
  opacity: 0.3;
}

.dialog-icon {
  font-size: 3rem !important;
  margin-bottom: 1rem;
}

.dialog-title {
  font-family: "Inter", sans-serif;
  font-size: 1.8rem;
  font-weight: 700;
  margin: 0;
}

.dialog-subtitle {
  font-family: "Inter", sans-serif;
  font-size: 1.1rem;
  margin: 0.5rem 0 0;
  opacity: 0.9;
  position: relative;
  z-index: 2;
  font-weight: 500;
}

.dialog-content {
  color: black !important;
  padding: 3rem !important;
  
}

.required-note {
  color: red !important;
  font-weight: 700;
  font-size: 0.8rem;
  margin-top: 1rem;
  display: block;
}

.dialog-actions {
  padding: 2rem 3rem !important;
  display: flex;
  justify-content: space-between;
  gap: 1.5rem;
  
}

.cancel-btn {
  color: #ff6b6b !important;
  border-color: #ff6b6b !important;
  font-weight: 700;
  border-width: 2px !important;
  border-radius: 25px !important;
  padding: 0.8rem 2rem !important;
  transition: all 0.3s ease !important;
}

.cancel-btn:hover {
  background: rgba(255, 107, 107, 0.1) !important;
  transform: translateY(-2px);
}

.submit-btn {
  background: linear-gradient(135deg, #ffd700 0%, #ffa500 100%) !important;
  color: #000000 !important;
  font-weight: 700;
  border-radius: 25px !important;
  padding: 0.8rem 2.5rem !important;
  transition: all 0.3s ease !important;
  box-shadow: 0 6px 20px rgba(255, 215, 0, 0.3) !important;
}

.submit-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 25px rgba(255, 215, 0, 0.5) !important;
}

/* Success Dialog */
.success-dialog {
  background: linear-gradient(145deg, #1a1a1a 0%, #2d2d2d 100%) !important;
  border: 3px solid #333;
  border-radius: 25px;
  overflow: hidden;
  box-shadow: 0 25px 50px rgba(0, 0, 0, 0.5);
}

.success-title {
  background: linear-gradient(135deg, #ffd700 0%, #ffa500 50%, #ff8c00 100%);
  color: #000000 !important;
  font-family: "Inter", sans-serif;
  font-weight: 800;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2.5rem;
  font-size: 1.5rem;
  letter-spacing: 0.5px;
}

.success-content {
  padding: 3rem !important;
  color: #e0e0e0;
  font-family: "Inter", sans-serif;
  background: linear-gradient(
    135deg,
    rgba(45, 45, 45, 0.5) 0%,
    rgba(26, 26, 26, 0.3) 100%
  );
  text-align: center;
}

.success-content p {
  font-size: 1.1rem;
  line-height: 1.6;
  margin-bottom: 1.5rem;
}

.success-note {
  color: #ffd700;
  font-weight: 600;
  margin-top: 1.5rem;
  font-size: 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
}

.success-actions {
  padding: 2rem 3rem !important;
  background: linear-gradient(
    135deg,
    rgba(26, 26, 26, 0.8) 0%,
    rgba(45, 45, 45, 0.6) 100%
  );
}

.close-success-btn {
  background: linear-gradient(135deg, #ffd700 0%, #ffa500 100%) !important;
  color: #000000 !important;
  font-weight: 700;
  border-radius: 25px !important;
  padding: 0.8rem 2.5rem !important;
  transition: all 0.3s ease !important;
  box-shadow: 0 6px 20px rgba(255, 215, 0, 0.3) !important;
}

.close-success-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 25px rgba(255, 215, 0, 0.5) !important;
}

/* Floating Animation */
.career-card {
  animation: float 8s ease-in-out infinite;
}

.career-card:nth-child(4n + 1) {
  animation-delay: 0s;
}

.career-card:nth-child(4n + 2) {
  animation-delay: 2s;
}

.career-card:nth-child(4n + 3) {
  animation-delay: 4s;
}

.career-card:nth-child(4n + 4) {
  animation-delay: 6s;
}

@keyframes float {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-15px);
  }
}

.career-card:hover {
  animation: none;
}

/* Additional Effects */
.career-card::after {
  content: "";
  position: absolute;
  top: -2px;
  left: -2px;
  right: -2px;
  bottom: -2px;
  background: linear-gradient(45deg, #ffd700, #ffa500, #ff8c00, #ffd700);
  border-radius: 27px;
  z-index: -1;
  opacity: 0;
  transition: opacity 0.4s ease;
  background-size: 400% 400%;
  animation: shimmer 3s ease-in-out infinite;
}

.career-card:hover::after {
  opacity: 0.4;
}

/* Scroll Bars Styles */
.scroll-bars-container {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  pointer-events: none;
  z-index: 10;
}

.vertical-scrollbar {
  position: absolute;
  top: 10px;
  right: 8px;
  bottom: 10px;
  width: 12px;
  background: rgba(0, 0, 0, 0.3);
  border-radius: 6px;
  pointer-events: auto;
  transition: background-color 0.3s ease;
}

.vertical-scrollbar:hover {
  background: rgba(0, 0, 0, 0.5);
}

.vertical-scroll-thumb {
  position: absolute;
  left: 2px;
  width: 8px;
  background: linear-gradient(135deg, #ffd700 0%, #ffa500 100%);
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  box-shadow: 0 2px 8px rgba(255, 215, 0, 0.4);
}

.vertical-scroll-thumb:hover {
  background: linear-gradient(135deg, #ffa500 0%, #ff8c00 100%);
}

.horizontal-scrollbar {
  position: absolute;
  left: 10px;
  right: 10px;
  bottom: 8px;
  height: 12px;
  background: rgba(0, 0, 0, 0.3);
  border-radius: 6px;
  pointer-events: auto;
  transition: background-color 0.3s ease;
}

.horizontal-scrollbar:hover {
  background: rgba(0, 0, 0, 0.5);
}

.horizontal-scroll-thumb {
  position: absolute;
  top: 2px;
  height: 8px;
  background: linear-gradient(135deg, #ffd700 0%, #ffa500 100%);
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  box-shadow: 0 2px 8px rgba(255, 215, 0, 0.4);
}

.horizontal-scroll-thumb:hover {
  background: linear-gradient(135deg, #ffa500 0%, #ff8c00 100%);
}

@keyframes shimmer {
  0%,
  100% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
}

/* Responsive scrollbars */
@media (max-width: 768px) {
  .vertical-scrollbar {
    width: 10px;
    right: 6px;
  }

  .vertical-scroll-thumb {
    width: 6px;
    left: 2px;
  }

  .horizontal-scrollbar {
    height: 10px;
    bottom: 6px;
  }

  .horizontal-scroll-thumb {
    height: 6px;
    top: 2px;
  }

  .image-instructions {
    font-size: 0.8rem;
  }
}

@media (max-width: 600px) {
  .vertical-scrollbar {
    width: 8px;
    right: 4px;
  }

  .vertical-scroll-thumb {
    width: 4px;
    left: 2px;
  }

  .horizontal-scrollbar {
    height: 8px;
    bottom: 4px;
  }

  .horizontal-scroll-thumb {
    height: 4px;
    top: 2px;
  }

  .image-instructions {
    font-size: 0.7rem;
  }
}

/* Responsive Design */
@media (max-width: 1260px) {
  .main-container {
    max-width: 1200px;
  }
}

@media (max-width: 960px) {
  .page-title {
    font-size: 3.2rem;
  }

  .intro-text {
    font-size: 1.2rem;
    padding: 0 1.5rem;
  }

  .career-title {
    font-size: 1.3rem;
    min-height: auto;
  }

  .cta-title {
    font-size: 2.8rem;
  }

  .cta-description {
    font-size: 1.1rem;
  }
}

@media (max-width: 768px) {
  .header-section {
    margin: 1rem 0.5rem 3rem;
    padding: 3rem 1rem;
  }

  .page-title {
    font-size: 2.8rem;
  }

  .intro-text {
    font-size: 1.1rem;
    padding: 0 1rem;
  }

  .careers-section {
    padding: 2rem 0;
  }

  .career-card {
    margin-bottom: 2rem;
  }

  .card-content {
    padding: 2rem 1.5rem;
  }

  .career-title {
    font-size: 1.2rem;
  }

  .cta-section {
    margin: 3rem 0.5rem 1rem;
    padding: 4rem 1rem;
  }

  .cta-title {
    font-size: 2.4rem;
  }

  .cta-description {
    font-size: 1rem;
  }

  .cta-button {
    padding: 1rem 3rem !important;
    font-size: 1.1rem !important;
  }

  .zoom-controls {
    gap: 0.8rem;
    padding: 0.6rem 1.2rem;
  }

  .zoom-percentage {
    min-width: 45px;
    font-size: 1rem;
  }

  .dialog-content {
    padding: 2rem !important;
  }

  .dialog-actions {
    padding: 1.5rem 2rem !important;
    flex-direction: column;
  }
}

@media (max-width: 600px) {
  .main-container {
    padding: 1rem 0.5rem;
  }

  .header-section {
    padding: 2.5rem 1rem;
    margin: 0.5rem 0.25rem 2rem;
  }

  .page-title {
    font-size: 2.2rem;
    margin-bottom: 1.5rem;
  }

  .intro-text {
    font-size: 1rem;
    text-align: left;
    line-height: 1.6;
  }

  .card-content {
    padding: 1.5rem;
  }

  .career-title {
    font-size: 1.1rem;
    min-height: auto;
  }

  .career-description {
    font-size: 0.9rem;
  }

  .card-actions {
    padding: 0 1.5rem 1.5rem;
  }

  .apply-now-btn {
    padding: 0.8rem 2rem !important;
    font-size: 0.9rem !important;
  }

  .cta-section {
    padding: 3rem 1rem;
    margin: 2rem 0.25rem 1rem;
  }

  .cta-title {
    font-size: 1.8rem;
  }

  .cta-description {
    font-size: 0.95rem;
    margin-bottom: 2rem;
  }

  .cta-button {
    padding: 0.9rem 2.5rem !important;
    font-size: 1rem !important;
  }

  .zoom-dialog-header {
    padding: 1rem 1.5rem;
    flex-direction: column;
    gap: 1rem;
  }

  .zoom-controls {
    order: -1;
    gap: 0.5rem;
    padding: 0.5rem 1rem;
  }

  .control-btn {
    width: 36px !important;
    height: 36px !important;
  }

  .zoom-percentage {
    min-width: 40px;
    font-size: 0.9rem;
  }

  .image-instructions {
    font-size: 0.75rem;
  }

  .dialog-header {
    padding: 2rem 1.5rem;
  }

  .dialog-title {
    font-size: 1.8rem;
  }

  .dialog-subtitle {
    font-size: 1rem;
  }

  .dialog-content {
    padding: 1.5rem !important;
  }

  .success-content {
    padding: 2rem !important;
  }

  .success-content p {
    font-size: 1rem;
  }
}

/* High-resolution displays */
@media (min-width: 1920px) {
  .main-container {
    max-width: 1600px;
  }

  .page-title {
    font-size: 5rem;
  }

  .intro-text {
    font-size: 1.4rem;
  }

  .career-title {
    font-size: 1.6rem;
  }

  .cta-title {
    font-size: 3.5rem;
  }
}

/* Print styles */
@media print {
  .careers-page {
    background: white !important;
    color: black !important;
  }

  .career-card {
    break-inside: avoid;
    border: 1px solid #ccc !important;
    box-shadow: none !important;
  }

  .apply-now-btn,
  .cta-button {
    display: none !important;
  }
}
</style>
