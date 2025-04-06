<template>
  <div class="container">
    <header class="header">
      <div class="logo-container">
        <div class="logo">K</div>
        <h1 class="title">Kolibri</h1>
      </div>
      <div class="header-actions">
        <button
          id="help-button"
          class="help-btn"
          @click="startOnboarding"
          aria-label="Start onboarding tour"
        >
          <svg
            class="icon"
            xmlns="http://www.w3.org/2000/svg"
            width="20"
            height="20"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <circle cx="12" cy="12" r="10"></circle>
            <path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"></path>
            <line x1="12" y1="17" x2="12.01" y2="17"></line>
          </svg>
        </button>
      </div>
    </header>

    <div class="grid">
      <!-- Sidebar -->
      <div class="sidebar">
        <div class="sidebar-item" id="dashboard">
          <svg
            class="icon"
            xmlns="http://www.w3.org/2000/svg"
            width="20"
            height="20"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <path d="m3 9 9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"></path>
            <polyline points="9 22 9 12 15 12 15 22"></polyline>
          </svg>
          <span>Dashboard</span>
        </div>
        <div class="sidebar-item" id="learn">
          <svg
            class="icon"
            xmlns="http://www.w3.org/2000/svg"
            width="20"
            height="20"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <path d="M2 3h6a4 4 0 0 1 4 4v14a3 3 0 0 0-3-3H2z"></path>
            <path d="M22 3h-6a4 4 0 0 0-4 4v14a3 3 0 0 1 3-3h7z"></path>
          </svg>
          <span>Learn</span>
        </div>
        <div class="sidebar-item" id="library">
          <svg
            class="icon"
            xmlns="http://www.w3.org/2000/svg"
            width="20"
            height="20"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <polygon points="23 7 16 12 23 17 23 7"></polygon>
            <rect x="1" y="5" width="15" height="14" rx="2" ry="2"></rect>
          </svg>
          <span>Content Library</span>
        </div>
      </div>

      <!-- Main Content -->
      <div class="main-content">
        <div class="content-card">
          <div class="search-container" id="search">
            <input
              type="text"
              placeholder="Search for courses and resources..."
              class="search-input"
            />
            <svg
              class="search-icon"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            >
              <circle cx="11" cy="11" r="8"></circle>
              <line x1="21" y1="21" x2="16.65" y2="16.65"></line>
            </svg>
          </div>

          <div class="journey-section">
            <h2 class="section-title">Your Learning Journey</h2>
            <div class="progress-container">
              <div class="progress-header">
                <span class="progress-title">Mathematics Basics</span>
                <span class="progress-percentage">60% complete</span>
              </div>
              <div class="progress-bar">
                <div class="progress-fill" style="width: 60%"></div>
              </div>
            </div>
          </div>

          <div class="progress-section" id="progress">
            <h2 class="section-title">Recent Progress</h2>
            <div class="progress-item">
              <div class="progress-icon completed">
                <svg
                  class="icon"
                  xmlns="http://www.w3.org/2000/svg"
                  width="20"
                  height="20"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <polyline points="20 6 9 17 4 12"></polyline>
                </svg>
              </div>
              <div>
                <h3 class="progress-item-title">
                  Completed: Introduction to Fractions
                </h3>
                <p class="progress-item-date">Yesterday at 3:45 PM</p>
              </div>
            </div>
            <div class="progress-item">
              <div class="progress-icon started">
                <svg
                  class="icon"
                  xmlns="http://www.w3.org/2000/svg"
                  width="20"
                  height="20"
                  viewBox="0 0 24 24"
                  fill="none"
                  stroke="currentColor"
                  stroke-width="2"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                >
                  <path d="M2 3h6a4 4 0 0 1 4 4v14a3 3 0 0 0-3-3H2z"></path>
                  <path d="M22 3h-6a4 4 0 0 0-4 4v14a3 3 0 0 1 3-3h7z"></path>
                </svg>
              </div>
              <div>
                <h3 class="progress-item-title">
                  Started: Multiplication and Division
                </h3>
                <p class="progress-item-date">Today at 10:20 AM</p>
              </div>
            </div>
          </div>
        </div>

        <div v-if="!hasCompletedOnboarding" class="welcome-card">
          <h2 class="welcome-title">New to Kolibri?</h2>
          <p class="welcome-text">
            Take a quick tour to learn how to get the most out of your learning
            experience.
          </p>
          <button @click="startOnboarding" class="start-tour-btn">
            Start Tour
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import tippy from "tippy.js";
  import "tippy.js/dist/tippy.css";
  import "tippy.js/themes/light.css";

  export default {
    data() {
      return {
        currentStep: 0,
        isTourActive: false,
        hasCompletedOnboarding: false,
        tippyInstances: [],
        steps: [
          {
            target: "#help-button",
            content:
              "<h3>Welcome to Kolibri!</h3><p>This tour will guide you through key features.</p>",
            position: "bottom",
          },
          {
            target: "#dashboard",
            content:
              "<h3>Dashboard</h3><p>Track your progress and access courses here.</p>",
            position: "right",
          },
          {
            target: "#learn",
            content:
              "<h3>Learn Section</h3><p>Access all your courses and materials here.</p>",
            position: "right",
          },
          {
            target: "#library",
            content:
              "<h3>Content Library</h3><p>Browse educational content by subject.</p>",
            position: "right",
          },
          {
            target: "#search",
            content:
              "<h3>Search Feature</h3><p>Find specific topics and resources here.</p>",
            position: "bottom",
          },
          {
            target: "#progress",
            content:
              "<h3>Progress Tracking</h3><p>Monitor your learning achievements here.</p>",
            position: "top",
          },
        ],
      };
    },
    mounted() {
      this.checkTourStatus();
      this.initTour();
      // Start tour automatically if not completed
      if (!this.hasCompletedOnboarding) {
        const savedStep = localStorage.getItem("tour_current_step");
        if (savedStep) {
          this.currentStep = parseInt(savedStep);
          this.startOnboarding();
        }
      }
    },
    methods: {
      initTour() {
        this.tippyInstances = this.steps.map((step, index) => {
          const element = document.querySelector(step.target);
          return tippy(element, {
            content: this.createStepContent(index),
            allowHTML: true,
            interactive: true,
            trigger: "manual",
            placement: step.position,
            theme: "light",
            zIndex: 9999,
            onShow: (instance) => {
              // Add highlight class to target element
              instance.reference.classList.add("tour-highlight");
              this.handleStepChange(index);

              // Scroll adjustment
              instance.reference.scrollIntoView({
                behavior: "smooth",
                block: "center",
                inline: "center",
              });

              instance.popper.querySelectorAll("button").forEach((button) => {
                button.addEventListener("click", (e) => {
                  const action = e.target.dataset.action;
                  if (action === "next") this.nextStep();
                  if (action === "prev") this.previousStep();
                  if (action === "finish" || action === "skip") this.endTour();
                });
              });
            },
            onHide: (instance) => {
              // Remove highlight class
              instance.reference.classList.remove("tour-highlight");
            },
          });
        });
      },

      showStep(index) {
        this.tippyInstances.forEach((instance, i) => {
          if (i === index) {
            instance.show();
          } else {
            instance.hide();
          }
        });
        // Save current step
        localStorage.setItem("tour_current_step", index);
      },

      createOverlay() {
        const overlay = document.createElement("div");
        overlay.className = "tour-overlay";
        overlay.style.backdropFilter = "blur(3px)";
        document.body.appendChild(overlay);
      },
      createStepContent(index) {
        return `
        <div class="tour-content">
          <div class="tour-body">${this.steps[index].content}</div>
          <div class="tour-footer">
            ${
              index > 0
                ? `<button class="tour-btn secondary" data-action="prev">Back</button>`
                : ""
            }
            ${
              index < this.steps.length - 1
                ? `<button class="tour-btn primary" data-action="next">Next</button>`
                : `<button class="tour-btn primary" data-action="finish">Finish</button>`
            }
            <button class="tour-btn secondary" data-action="skip">Skip</button>
          </div>
        </div>
      `;
      },

      startOnboarding() {
        this.isTourActive = true;
        this.currentStep = 0;
        this.showStep(0);
        this.createOverlay();
      },
      nextStep() {
        if (this.currentStep < this.steps.length - 1) {
          this.currentStep++;
          this.showStep(this.currentStep);
        }
      },

      previousStep() {
        if (this.currentStep > 0) {
          this.currentStep--;
          this.showStep(this.currentStep);
        }
      },

      endTour() {
        this.isTourActive = false;
        this.hasCompletedOnboarding = false; // Demo mode: always keep false
        this.tippyInstances.forEach((instance) => instance.hide());
        this.removeOverlay();
        // Clear saved step for demo purposes
        localStorage.removeItem("tour_current_step");
      },
      removeOverlay() {
        const overlay = document.querySelector(".tour-overlay");
        if (overlay) overlay.remove();
      },

      checkTourStatus() {
        this.hasCompletedOnboarding =
          localStorage.getItem("kolibri_tour_completed") === "true";
      },

      handleStepChange(index) {
        this.currentStep = index;
      },
    },
  };
</script>

<style>
  /* Tour styling */
  .tour-overlay {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 9990;
    pointer-events: none;
    backdrop-filter: blur(4px);
    background: rgba(255, 255, 255, 0.7) !important;
  }

  .tour-content {
    padding: 20px;
    min-width: 300px;
  }

  .tour-body h3 {
    margin: 0 0 10px 0;
    font-size: 1.2em;
  }

  .tour-body p {
    margin: 0;
    font-size: 0.9em;
  }

  .tour-footer {
    margin-top: 15px;
    display: flex;
    gap: 10px;
    justify-content: flex-end;
  }

  .tour-btn {
    padding: 6px 12px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }

  .tour-btn.primary {
    background: #2563eb;
    color: white;
  }

  .tour-btn.secondary {
    background: #f3f4f6;
    color: #4b5563;
  }
  .tour-highlight {
    box-shadow: 0 0 0 3px #2563eb !important;
    border-radius: 8px;
    position: relative;
    z-index: 9992;
    background: white;
    animation: pulse-glow 1.5s infinite;
  }

  /* Pulse animation */
  [data-tippy-root] .tippy-box {
    position: relative;
  }

  [data-tippy-root] .tippy-box::after {
    content: "";
    position: absolute;
    top: -5px;
    left: -5px;
    right: -5px;
    bottom: -5px;
    border-radius: 8px;
    animation: pulse 2s infinite;
    z-index: -1;
  }
  [data-tippy-root] {
    z-index: 9993; /* Ensure tooltip is above overlay */
  }

  @keyframes pulse {
    0% {
      box-shadow: 0 0 0 0 rgba(37, 99, 235, 0.5);
    }
    70% {
      box-shadow: 0 0 0 10px rgba(37, 99, 235, 0);
    }
    100% {
      box-shadow: 0 0 0 0 rgba(37, 99, 235, 0);
    }
  }

  @keyframes pulse-glow {
    0% {
      box-shadow: 0 0 0 0 rgba(37, 99, 235, 0.4);
    }
    70% {
      box-shadow: 0 0 0 10px rgba(37, 99, 235, 0);
    }
    100% {
      box-shadow: 0 0 0 0 rgba(37, 99, 235, 0);
    }
  }

  /* Existing application styles */
  .container {
    max-width: 100vw;
    margin: 0 auto;
    padding: 20px;
    background-color: #f5f5f5;
    min-height: 100vh;
  }

  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 40px;
  }

  .logo-container {
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .logo {
    width: 40px;
    height: 40px;
    background-color: #2563eb;
    color: white;
    font-weight: bold;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 6px;
  }

  .title {
    font-size: 24px;
    font-weight: bold;
    color: #1e293b;
  }

  .header-actions {
    display: flex;
    gap: 8px;
  }

  .help-btn {
    padding: 8px;
    border-radius: 50%;
    background: none;
    border: none;
    cursor: pointer;
    color: #4b5563;
  }

  .help-btn:hover {
    background-color: #f3f4f6;
  }

  .grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 24px;
  }

  @media (min-width: 768px) {
    .grid {
      grid-template-columns: 1fr 3fr;
    }
  }

  .sidebar {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .sidebar-item {
    background-color: white;
    padding: 16px;
    border-radius: 8px;
    box-shadow: 0 1px 2px rgba(0, 0, 0, 0.05);
    display: flex;
    align-items: center;
    gap: 12px;
    color: #4b5563;
    cursor: pointer;
  }

  .sidebar-item:hover {
    background-color: #f9fafb;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .main-content {
    display: flex;
    flex-direction: column;
    gap: 24px;
  }

  .content-card {
    background-color: white;
    padding: 24px;
    border-radius: 8px;
    box-shadow: 0 1px 2px rgba(0, 0, 0, 0.05);
  }

  .search-container {
    position: relative;
    margin-bottom: 24px;
    max-width: 100%;
  }

  .search-input {
    width: 100%;
    padding: 8px 12px 8px 36px;
    border: 1px solid #d1d5db;
    border-radius: 6px;
    font-size: 14px;
  }

  .search-input:focus {
    outline: none;
    border-color: #2563eb;
    box-shadow: 0 0 0 2px rgba(37, 99, 235, 0.2);
  }

  .search-icon {
    position: absolute;
    left: 12px;
    top: 50%;
    transform: translateY(-50%);
    width: 20px;
    height: 20px;
    color: #9ca3af;
  }

  .section-title {
    font-size: 20px;
    font-weight: 600;
    color: #1e293b;
    margin-bottom: 16px;
  }

  .progress-container {
    background-color: #f3f4f6;
    padding: 16px;
    border-radius: 8px;
  }

  .progress-header {
    display: flex;
    justify-content: space-between;
    margin-bottom: 8px;
  }

  .progress-title {
    font-weight: 500;
    color: #4b5563;
  }

  .progress-percentage {
    font-size: 14px;
    color: #6b7280;
  }

  .progress-bar {
    width: 100%;
    height: 10px;
    background-color: #e5e7eb;
    border-radius: 9999px;
    overflow: hidden;
  }

  .progress-fill {
    height: 100%;
    background-color: #2563eb;
    border-radius: 9999px;
  }

  .progress-item {
    display: flex;
    align-items: center;
  }
  .progress-item:hover {
    background-color: #f9fafb;
  }

  .progress-icon {
    width: 40px;
    height: 40px;
    border-radius: 6px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .progress-icon.completed {
    background-color: #dcfce7;
    color: #16a34a;
  }

  .progress-icon.started {
    background-color: #dbeafe;
    color: #2563eb;
  }

  .progress-item-title {
    font-weight: 500;
    color: #4b5563;
  }

  .progress-item-date {
    font-size: 14px;
    color: #6b7280;
  }

  .welcome-card {
    background: linear-gradient(to right, #eff6ff, #eef2ff);
    padding: 24px;
    border-radius: 8px;
    border: 1px solid #dbeafe;
  }

  .welcome-title {
    font-size: 18px;
    font-weight: 500;
    color: #1e40af;
    margin-bottom: 8px;
  }

  .welcome-text {
    color: #1e40af;
    margin-bottom: 12px;
  }

  .start-tour-btn {
    background-color: #2563eb;
    color: white;
    padding: 8px 16px;
    border-radius: 6px;
    border: none;
    cursor: pointer;
  }

  .start-tour-btn:hover {
    background-color: #1e40af;
  }

  /* Icon styles */
  .icon {
    width: 20px;
    height: 20px;
  }
</style>
