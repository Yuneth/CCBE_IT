<template>
  <nav class="navbar navbar-expand-lg navbar-custom sticky-top">
    <div class="container">
      <router-link class="navbar-brand" to="/">
        <h2 class="logo-text">CCIT</h2>
        <small class="logo-subtext">Cambridge College of Information Technology</small>
      </router-link>
      
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
        <span class="navbar-toggler-icon"></span>
      </button>
      
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item">
            <router-link class="nav-link" to="/">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/about">About</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/courses">Courses</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/facilities">Facilities</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/contact">Contact</router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'NavigationBar'
}
</script>

<style scoped>
.navbar-custom {
  background-color: var(--header-bg);
  box-shadow: var(--shadow);
  padding: 1rem 0;
}

.logo-text {
  color: var(--primary-color);
  font-weight: 700;
  margin: 0;
  font-size: 2rem;
}

.logo-subtext {
  color: var(--text-secondary);
  font-size: 0.8rem;
  display: block;
}

.navbar-brand {
  text-decoration: none;
}

.nav-link {
  color: var(--text-primary) !important;
  font-weight: 500;
  margin: 0 10px;
  transition: color 0.3s ease;
}

.nav-link:hover,
.nav-link.router-link-active {
  color: var(--accent-color) !important;
}

.navbar-toggler {
  border-color: var(--border-color);
}

.navbar-toggler-icon {
  background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 30 30'%3e%3cpath stroke='rgba%280, 188, 212, 1%29' stroke-linecap='round' stroke-miterlimit='10' stroke-width='2' d='M4 7h22M4 15h22M4 23h22'/%3e%3c/svg%3e");
}
</style>