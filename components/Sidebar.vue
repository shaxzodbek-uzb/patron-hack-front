<template>
  <div>
    <ul
      class="navbar-nav font-weight-bold bg-gradient-primary sidebar sidebar-dark accordion"
      id="accordionSidebar"
    >
      <nuxt-link to="/" class="sidebar-brand d-flex align-items-center justify-content-center">
        <img style="width: 70%" src="~/assets/images/logo.png" alt />
      </nuxt-link>

      <hr class="sidebar-divider my-0" />

      <li class="nav-item active">
        <nuxt-link to="/" class="nav-link">
          <i class="fas fa-fw fa-tachometer-alt"></i>
          <span>Главная</span>
        </nuxt-link>
      </li>

      <hr class="sidebar-divider" />

      <div class="sidebar-heading">Интерфейс</div>

      <li class="nav-item">
        <nuxt-link to="/employees" class="nav-link collapsed">
          <i class="fas fa-user"></i>
          <span>Сотрудники</span>
        </nuxt-link>
      </li>

      <li class="nav-item">
        <nuxt-link to="/employee-positions" class="nav-link collapsed">
          <i class="fas fa-fw fa-award"></i>
          <span>Позиции</span>
        </nuxt-link>
      </li>

      <li class="nav-item">
        <nuxt-link to="/organizational-structures" class="nav-link">
          <i class="fas fa-fw fas fa-project-diagram"></i>
          <span>Орг. структура</span>
        </nuxt-link>
      </li>

      <li class="nav-item">
        <nuxt-link to="/business-process" class="nav-link collapsed" data-toggle="collapse">
          <i v-if="!isCollapsed" class="fas fa-folder"></i>
          <i v-else class="fas fa-folder-open"></i>
          <span @click="isCollapsed = !isCollapsed" v-b-toggle.my-collapse>Бизнес процесс</span>
        </nuxt-link>
        <div
          id="collapseTwo"
          class="collapse"
          aria-labelledby="headingTwo"
          data-parent="#accordionSidebar"
        ></div>
        <b-collapse id="my-collapse" class="bg-white p-2 rounded" style="font-size: 12px">
          <nuxt-link to="/classifications" class="collapse-item d-block">Классификация</nuxt-link>
          <nuxt-link to="/classification-groups" class="collapse-item d-block">Группы</nuxt-link>
        </b-collapse>
      </li>
      <!-- <b-collapse id="my-collapse">
        <b-card title="Collapsible card"> Hello world! </b-card>
      </b-collapse>-->

      <li class="nav-item">
        <nuxt-link to="/rules" class="nav-link">
          <i class="fas fa-fw fa-chart-area"></i>
          <span>Бизнес правила</span>
        </nuxt-link>
      </li>

      <li class="nav-item">
        <nuxt-link to="/payment-types" class="nav-link">
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
export default {
  name: 'Sidebar',
  data() {
    return {
      isCollapsed: false,
    }
  },
}
</script>