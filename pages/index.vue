<template>
  <div>
    <!-- Page Heading -->
    <div class="d-sm-flex align-items-center justify-content-between mb-4">
      <h1 class="h3 mb-0 text-gray-800">Главная</h1>
      <a href="#" class="d-none d-sm-inline-block btn btn-sm btn-primary shadow-sm">
        <i class="fas fa-download fa-sm text-white"></i>  Создать отчет
      </a>
    </div>

    <!-- Content Row -->

    <div class="row">
      <!-- Area Chart -->
      <LineChart :height="200" style="padding-bottom: 20px" />

      <!-- Pie Chart -->
      <div class="col-xl-4 col-lg-5">
        <div class="card shadow mb-4">
          <!-- Card Header - Dropdown -->
          <div class="card-header py-3 d-flex flex-row align-items-center justify-content-between">
            <h6 class="m-0 font-weight-bold text-primary">Количество платежей</h6>
            <div class="dropdown no-arrow">
              <a
                class="dropdown-toggle"
                href="#"
                role="button"
                id="dropdownMenuLink"
                data-toggle="dropdown"
                aria-haspopup="true"
                aria-expanded="false"
              >
                <i class="fas fa-ellipsis-v fa-sm fa-fw text-gray-400"></i>
              </a>
            </div>
          </div>
          <!-- Card Body -->
          <div class="card-body">
            <ChartLine />
          </div>
        </div>
      </div>
    </div>

    <!-- Content Row -->
    <div class="row">
      <!-- Content Column -->
      <div class="col-lg-6 mb-4">
        <!-- Project Card Example -->
        <div class="card shadow mb-4">
          <div class="card-header py-3">
            <h6 class="m-0 font-weight-bold text-primary">Оценкы БПМ</h6>
          </div>
          <div class="card-body">
            <h4 class="small font-weight-bold">
              Плохо
              <span class="float-right">20%</span>
            </h4>
            <div class="progress mb-4">
              <div
                class="progress-bar bg-danger"
                role="progressbar"
                style="width: 20%"
                aria-valuenow="20"
                aria-valuemin="0"
                aria-valuemax="100"
              ></div>
            </div>
            <h4 class="small font-weight-bold">
              Hеудовлетворительный
              <span class="float-right">40%</span>
            </h4>
            <div class="progress mb-4">
              <div
                class="progress-bar bg-warning"
                role="progressbar"
                style="width: 40%"
                aria-valuenow="40"
                aria-valuemin="0"
                aria-valuemax="100"
              ></div>
            </div>
            <h4 class="small font-weight-bold">
              Удовлетворительный
              <span class="float-right">60%</span>
            </h4>
            <div class="progress mb-4">
              <div
                class="progress-bar"
                role="progressbar"
                style="width: 60%"
                aria-valuenow="60"
                aria-valuemin="0"
                aria-valuemax="100"
              ></div>
            </div>
            <h4 class="small font-weight-bold">
              Хорошо
              <span class="float-right">80%</span>
            </h4>
            <div class="progress mb-4">
              <div
                class="progress-bar bg-info"
                role="progressbar"
                style="width: 80%"
                aria-valuenow="80"
                aria-valuemin="0"
                aria-valuemax="100"
              ></div>
            </div>
            <h4 class="small font-weight-bold">
              Отлично
              <span class="float-right">Завершенo!</span>
            </h4>
            <div class="progress">
              <div
                class="progress-bar bg-success"
                role="progressbar"
                style="width: 100%"
                aria-valuenow="100"
                aria-valuemin="0"
                aria-valuemax="100"
              ></div>
            </div>
          </div>
        </div>
      </div>

      <div class="col-lg-6 mb-4">
        <div class="card shadow mb-4">
          <div class="card-header py-3">
            <h6 class="m-0 font-weight-bold text-primary">Определение оценки</h6>
          </div>
          <div class="card-body">
            <div class="small">
              <b-badge class="circle text-danger" variant="danger">.</b-badge>
              <span>Плохо - </span>
              <span>
                если бизнес-процесс оценивается плохо, значит, в процессе очень много недостатков, и трудно надеяться на будущее этого бизнеса.
                <br><br>
              </span>
            </div>
            <div class="small">
              <b-badge class="circle text-warning" variant="warning">.</b-badge>
            <span>Hеудовлетворительный - </span>
            <span>
              если бизнес-процесс оценивается неудовлетворительно, значит, в процессе много недостатков, но надеяться на будущее этого бизнеса невозможно.
              <br><br>
            </span>
            </div>
            <div class="small">
              <b-badge class="circle text-primary" variant="primary">.</b-badge>
            <span>
              Удовлетворительный - 
            </span>
            <span>
              если бизнес-процесс оценивается удовлетворительно, значит, в процессе мало недостатков, но надеяться на будущее этого бизнеса возможно.
              <br><br>
            </span>
            </div>
            <div class="small">
              <b-badge class="circle text-info" variant="info">.</b-badge>
              <span>
                Хорошо - 
              </span>
              <span>
                если бизнес-процесс оценивается хорошо, значит, в процессе все нормальнo...
                <br><br>
              </span>
            </div>
            <div class="small">
              <b-badge class="circle text-success" variant="success">.</b-badge>
              <span>
                Отлично - 
              </span>
              <span>
                если бизнес-процесс оценивается отлично, значит, в процессе почти нет недостатков, а это говорит о том, что вероятность достижения больших фекалий с этим проектом очень высока в процентах
                <br>
              </span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Sidebar from '../components/Sidebar.vue'

export default {
  components: {
    Sidebar,
  },
  name: 'IndexPage',
}
</script>

<style scoped>
.circle {
  width: 16px;
  border-radius: 50%;
}
</style>