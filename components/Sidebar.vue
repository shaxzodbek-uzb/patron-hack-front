<template>
  <div>
    <ul
      class="navbar-nav bg-gradient-primary sidebar sidebar-dark accordion"
      id="accordionSidebar"
    >
      <nuxt-link
        to="/"
        class="sidebar-brand d-flex align-items-center justify-content-center"
      >
        <img style="width: 70%" src="~/assets/images/logo.png" alt="" />
      </nuxt-link>

      <hr class="sidebar-divider my-0" />

      <li class="nav-item active">
        <nuxt-link to="/" class="nav-link">
          <i class="fas fa-fw fa-tachometer-alt"></i>
          <span>Главная</span></nuxt-link
        >
      </li>

      <hr class="sidebar-divider" />

      <div class="sidebar-heading">Интерфейс</div>

      <li class="nav-item">
        <nuxt-link to="/user" class="nav-link collapsed">
          <i class="fas fa-user"></i>
          <span>Ползователь</span>
        </nuxt-link>
      </li>

      <li class="nav-item">
        <nuxt-link to="/role" class="nav-link collapsed">
          <i class="fas fa-fw fa-award"></i>
          <span>Позиции</span>
        </nuxt-link>
      </li>

      <li class="nav-item">
        <nuxt-link to="/" class="nav-link">
          <i class="fas fa-fw fas fa-project-diagram"></i>
          <span>Орг. структура</span></nuxt-link
        >
      </li>

      <li class="nav-item">
        <nuxt-link to="/" class="nav-link">
          <i class="fas fa-fw fa-chart-area"></i>
          <span>Бизнес правила</span>
        </nuxt-link>
      </li>

      <li class="nav-item">
        <nuxt-link to="" class="nav-link">
          <i class="fas fa-fw far fa-credit-card"></i>
          <span>Тип платежа</span>
        </nuxt-link>
      </li>

      <hr class="sidebar-divider d-none d-md-block" />

      <div class="text-center d-none d-md-inline">
        <button class="rounded-circle border-0" id="sidebarToggle"></button>
      </div>
    </ul>
  </div>
</template>

<script>
export default {}
</script>

<style></style>
