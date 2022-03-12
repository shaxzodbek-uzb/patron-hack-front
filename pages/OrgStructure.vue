<template>
  <div id="content-wrapper" class="d-flex flex-column">
    <div id="content">
      <div class="container-fluid">
        <div class="row">
          <div class="card w-100 shadow mb-4">
            <div class="card-header py-3">
              <div
                class="m-0 font-weight-bold text-primary d-flex justify-content-between align-items-center"
              >
                Организационная структура
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
                      <th>Имя</th>
                      <th>Parent Id</th>
                      <th>Действия</th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr>
                      <td>Tiger Nixon</td>
                      <td>System Architect</td>
                      <td>
                        <a
                          href="#"
                          class="btn btn-sm btn-primary btn-icon-split"
                        >
                          <span class="icon text-white-50">
                            <i class="fas fa-pencil-alt"></i>
                          </span>
                        </a>
                        <a
                          href="#"
                          class="btn btn-sm btn-danger btn-icon-split"
                        >
                          <span class="icon text-white-50">
                            <i class="fas fa-trash"></i>
                          </span>
                        </a>
                      </td>
                    </tr>
                    <tr>
                      <td>Garrett Winters</td>
                      <td>Accountant</td>
                      <td>
                        <a
                          href="#"
                          class="btn btn-sm btn-primary btn-icon-split"
                        >
                          <span class="icon text-white-50">
                            <i class="fas fa-pencil-alt"></i>
                          </span>
                        </a>
                        <a
                          href="#"
                          class="btn btn-sm btn-danger btn-icon-split"
                        >
                          <span class="icon text-white-50">
                            <i class="fas fa-trash"></i>
                          </span>
                        </a>
                      </td>
                    </tr>
                    <tr>
                      <td>Ashton Cox</td>
                      <td>Junior Technical Author</td>
                      <td>
                        <a
                          href="#"
                          class="btn btn-sm btn-primary btn-icon-split"
                        >
                          <span class="icon text-white-50">
                            <i class="fas fa-pencil-alt"></i>
                          </span>
                        </a>
                        <a
                          href="#"
                          class="btn btn-sm btn-danger btn-icon-split"
                        >
                          <span class="icon text-white-50">
                            <i class="fas fa-trash"></i>
                          </span>
                        </a>
                      </td>
                    </tr>
                    <tr>
                      <td>Cedric Kelly</td>
                      <td>Senior Javascript Developer</td>
                      <td>
                        <a
                          href="#"
                          class="btn btn-sm btn-primary btn-icon-split"
                        >
                          <span class="icon text-white-50">
                            <i class="fas fa-pencil-alt"></i>
                          </span>
                        </a>
                        <a
                          href="#"
                          class="btn btn-sm btn-danger btn-icon-split"
                        >
                          <span class="icon text-white-50">
                            <i class="fas fa-trash"></i>
                          </span>
                        </a>
                      </td>
                    </tr>
                    <tr>
                      <td>Airi Satou</td>
                      <td>Accountant</td>
                      <td>
                        <a
                          href="#"
                          class="btn btn-sm btn-primary btn-icon-split"
                        >
                          <span class="icon text-white-50">
                            <i class="fas fa-pencil-alt"></i>
                          </span>
                        </a>
                        <a
                          href="#"
                          class="btn btn-sm btn-danger btn-icon-split"
                        >
                          <span class="icon text-white-50">
                            <i class="fas fa-trash"></i>
                          </span>
                        </a>
                      </td>
                    </tr>
                    <tr>
                      <td>Brielle Williamson</td>
                      <td>Integration Specialist</td>
                      <td>
                        <a
                          href="#"
                          class="btn btn-sm btn-primary btn-icon-split"
                        >
                          <span class="icon text-white-50">
                            <i class="fas fa-pencil-alt"></i>
                          </span>
                        </a>
                        <a
                          href="#"
                          class="btn btn-sm btn-danger btn-icon-split"
                        >
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
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style></style>
