<template>
  <div class="container-fluid">
    <!-- Page Heading -->
    <div class="row">
      <div class="card w-100 shadow mb-4">
        <div class="card-header py-3">
          <div
            class="m-0 font-weight-bold text-primary d-flex justify-content-between align-items-center"
          >
            Бизнес процесс
            <span>
              <a
                type="button"
                data-toggle="modal"
                data-target="#exampleModal"
                class="btn btn-sm btn-primary bg-primary btn-icon-split dropdown-item"
              >
                <span class="icon text-white">
                  <i class="text-white fas fa-plus"></i>
                </span>
                <span class="text-white">Добавить</span>
              </a>
            </span>
          </div>
        </div>
        <div class="card-body">
          <div class="table-responsive">
            <table
              v-if="!showLoader"
              class="table table-bordered"
              id="dataTable"
              cellspacing="0"
            >
              <thead>
                <tr>
                  <th>Имя</th>
                  <th>Позиция</th>
                  <th>Дата начала</th>
                  <th>Зарплата</th>
                  <th>Действия</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="item in items" :key="item.id">
                  <td>{{ item.name }}</td>
                  <td>Бизнес тренер</td>
                  <td>Офис 2</td>
                  <td>$12,000</td>
                  <td>
                    <a
                      @click="editItem(idx)"
                      class="btn btn-sm btn-primary btn-icon-split"
                    >
                      <span class="icon text-white">
                        <i class="fas fa-pencil-alt"></i>
                      </span>
                    </a>
                    <a class="btn btn-sm btn-danger btn-icon-split">
                      <span class="icon text-white">
                        <i class="fas fa-trash"></i>
                      </span>
                    </a>
                  </td>
                </tr>
              </tbody>
            </table>
            <Loader v-else-if="showLoader" />
            <b-modal
              title="BootstrapVue"
            >
              <div class="form-group">
                <label for="exampleInputEmail1">Имя</label>
                <input
                  type="text"
                  class="form-control"
                  placeholder="Имя"
                />
              </div>
            </b-modal>
            <b-modal  title="BootstrapVue" >
              <div class="form-group">
                <label for="exampleInputEmail1">Имя</label>
                <input
                  type="text"
                  class="form-control"
                  placeholder="Имя"
                />
              </div>
            </b-modal>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style></style>
