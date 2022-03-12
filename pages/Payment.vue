<template>
  <div class="container-fluid h-auto w-100">
    <!-- Page Heading -->

    <div class="row">
      <div class="card w-100 shadow mb-4">
        <div class="card-header py-3">
          <div
            class="m-0 font-weight-bold text-primary d-flex justify-content-between align-items-center"
          >
            Тип платежа
            <span>
              <a
                href="#"
                class="btn btn-sm btn-primary btn-icon-split"
                type="button"
                data-toggle="modal"
                data-target="#exampleModal"
              >
                <span class="icon text-white-50">
                  <i class="text-white fas fa-plus"></i>
                </span>
                <span class="text">Добавить</span>
              </a>
            </span>
          </div>
        </div>
        <div class="card-body">
          <div class="table-responsive">
            <table
              class="table table-bordered"
              id="dataTable"
              width="100%"
              cellspacing="0"
            >
              <thead>
                <tr>
                  <td>Тип платежа</td>
                  <td>Действия</td>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td>Денежные средства</td>
                  <td>
                    <a href="#" class="btn btn-sm btn-primary btn-icon-split">
                      <span class="icon text-white-50">
                        <i class="fas fa-pencil-alt"></i>
                      </span>
                    </a>
                    <a href="#" class="btn btn-sm btn-danger btn-icon-split">
                      <span class="icon text-white-50">
                        <i class="fas fa-trash"></i>
                      </span>
                    </a>
                  </td>
                </tr>
                <tr>
                  <td>Денежные средства</td>
                  <td>
                    <a href="#" class="btn btn-sm btn-primary btn-icon-split">
                      <span class="icon text-white-50">
                        <i class="fas fa-pencil-alt"></i>
                      </span>
                    </a>
                    <a href="#" class="btn btn-sm btn-danger btn-icon-split">
                      <span class="icon text-white-50">
                        <i class="fas fa-trash"></i>
                      </span>
                    </a>
                  </td>
                </tr>
                <tr>
                  <td>Денежные средства</td>
                  <td>
                    <a href="#" class="btn btn-sm btn-primary btn-icon-split">
                      <span class="icon text-white-50">
                        <i class="fas fa-pencil-alt"></i>
                      </span>
                    </a>
                    <a href="#" class="btn btn-sm btn-danger btn-icon-split">
                      <span class="icon text-white-50">
                        <i class="fas fa-trash"></i>
                      </span>
                    </a>
                  </td>
                </tr>

                <tr>
                  <td>Платежная карта</td>
                  <td>
                    <a href="#" class="btn btn-sm btn-primary btn-icon-split">
                      <span class="icon text-white-50">
                        <i class="fas fa-pencil-alt"></i>
                      </span>
                    </a>
                    <a href="#" class="btn btn-sm btn-danger btn-icon-split">
                      <span class="icon text-white-50">
                        <i class="fas fa-trash"></i>
                      </span>
                    </a>
                  </td>
                </tr>
                <tr>
                  <td>Номер счета</td>
                  <td>
                    <a href="#" class="btn btn-sm btn-primary btn-icon-split">
                      <span class="icon text-white-50">
                        <i class="fas fa-pencil-alt"></i>
                      </span>
                    </a>
                    <a href="#" class="btn btn-sm btn-danger btn-icon-split">
                      <span class="icon text-white-50">
                        <i class="fas fa-trash"></i>
                      </span>
                    </a>
                  </td>
                </tr>
                <tr>
                  <td>Карта банка</td>
                  <td>
                    <a href="#" class="btn btn-sm btn-primary btn-icon-split">
                      <span class="icon text-white-50">
                        <i class="fas fa-pencil-alt"></i>
                      </span>
                    </a>
                    <a href="#" class="btn btn-sm btn-danger btn-icon-split">
                      <span class="icon text-white-50">
                        <i class="fas fa-trash"></i>
                      </span>
                    </a>
                  </td>
                </tr>
              </tbody>
            </table>
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
