<template>
  <div>
    <ul
      class="navbar-nav bg-gradient-primary sidebar sidebar-dark accordion"
      id="accordionSidebar"
    >
      <a
        class="sidebar-brand d-flex align-items-center justify-content-center"
        href="index.html"
      >
        <img style="width: 70%" src="~/assets/images/logo.png" alt="" />
      </a>

      <hr class="sidebar-divider my-0" />

      <li class="nav-item active">
        <a class="nav-link" href="index.html">
          <i class="fas fa-fw fa-tachometer-alt"></i>
          <span>Главная</span></a
        >
      </li>

      <hr class="sidebar-divider" />

      <div class="sidebar-heading">Интерфейс</div>

      <li class="nav-item">
        <a class="nav-link collapsed" href="user.html">
          <i class="fas fa-user"></i>
          <span>Ползователь</span>
        </a>
      </li>

      <li class="nav-item">
        <a class="nav-link collapsed" href="role.html">
          <i class="fas fa-fw fa-award"></i>
          <span>Позиции</span>
        </a>
      </li>


      <li class="nav-item">
        <a class="nav-link" href="orgStructure.html">
          <i class="fas fa-fw fas fa-project-diagram"></i>
          <span>Орг. структура</span></a
        >
      </li>

      <li class="nav-item">
        <a class="nav-link" href="orgStructure.html">
          <i class="fas fa-fw fa-chart-area"></i>
          <span>Бизнес правила</span>
        </a>
      </li>

      <li class="nav-item">
        <a class="nav-link" href="payment.html">
          <i class="fas fa-fw far fa-credit-card"></i>
          <span>Тип платежа</span>
        </a>
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
