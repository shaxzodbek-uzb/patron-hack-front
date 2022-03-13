<template>
  <div>
    <!-- Page Heading -->
    <div class="d-sm-flex align-items-center justify-content-between mb-4">
      <h1 class="h3 mb-0 text-gray-800">Главная</h1>
      <a href="#" class="d-none d-sm-inline-block btn btn-sm btn-primary shadow-sm">
        <i class="fas fa-download fa-sm text-white"></i> Generate Report
      </a>
    </div>

    <!-- Content Row -->

    <div class="row">
      <!-- Area Chart -->
      <LineChart :height="180" />

      <!-- Pie Chart -->
      <div class="col-xl-4 col-lg-5">
        <div class="card shadow mb-4">
          <!-- Card Header - Dropdown -->
          <div class="card-header py-3 d-flex flex-row align-items-center justify-content-between">
            <h6 class="m-0 font-weight-bold text-primary">Revenue Sources</h6>
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
            <h6 class="m-0 font-weight-bold text-primary">Projects</h6>
          </div>
          <div class="card-body">
            <h4 class="small font-weight-bold">
              Server Migration
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
              Sales Tracking
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
              Customer Database
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
              Payout Details
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
              Account Setup
              <span class="float-right">Complete!</span>
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

        <!-- Color System -->
        <div class="row">
          <div class="col-lg-6 mb-4">
            <div class="card bg-primary text-white shadow">
              <div class="card-body">
                Primary
                <div class="text-white small">#4e73df</div>
              </div>
            </div>
          </div>
          <div class="col-lg-6 mb-4">
            <div class="card bg-success text-white shadow">
              <div class="card-body">
                Success
                <div class="text-white small">#1cc88a</div>
              </div>
            </div>
          </div>
          <div class="col-lg-6 mb-4">
            <div class="card bg-info text-white shadow">
              <div class="card-body">
                Info
                <div class="text-white small">#36b9cc</div>
              </div>
            </div>
          </div>
          <div class="col-lg-6 mb-4">
            <div class="card bg-warning text-white shadow">
              <div class="card-body">
                Warning
                <div class="text-white small">#f6c23e</div>
              </div>
            </div>
          </div>
          <div class="col-lg-6 mb-4">
            <div class="card bg-danger text-white shadow">
              <div class="card-body">
                Danger
                <div class="text-white small">#e74a3b</div>
              </div>
            </div>
          </div>
          <div class="col-lg-6 mb-4">
            <div class="card bg-secondary text-white shadow">
              <div class="card-body">
                Secondary
                <div class="text-white small">#858796</div>
              </div>
            </div>
          </div>
          <div class="col-lg-6 mb-4">
            <div class="card bg-light text-black shadow">
              <div class="card-body">
                Light
                <div class="text-black-50 small">#f8f9fc</div>
              </div>
            </div>
          </div>
          <div class="col-lg-6 mb-4">
            <div class="card bg-dark text-white shadow">
              <div class="card-body">
                Dark
                <div class="text-white small">#5a5c69</div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="col-lg-6 mb-4">
        <!-- Illustrations -->
        <div class="card shadow mb-4">
          <div class="card-header py-3">
            <h6 class="m-0 font-weight-bold text-primary">Illustrations</h6>
          </div>
          <div class="card-body">
            <div class="chart"></div>
          </div>
        </div>

        <!-- Approach -->
        <div class="card shadow mb-4">
          <div class="card-header py-3">
            <h6 class="m-0 font-weight-bold text-primary">Development Approach</h6>
          </div>
          <div class="card-body">
            <p>
              Patron ERP 2 makes extensive use of Bootstrap 4 utility classes in order to reduce
              CSS bloat and poor page performance. Custom CSS classes are used to create
              custom components and custom utility classes.
            </p>
            <p class="mb-0">
              Before working with this theme, you should become familiar with the
              Bootstrap framework, especially the utility classes.
            </p>
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
