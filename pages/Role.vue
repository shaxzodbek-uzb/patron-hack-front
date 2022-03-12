<template>
  <div>
    <div class="card w-100 shadow mb-4">
      <div class="card-header py-3">
        <div
          class="m-0 font-weight-bold text-primary d-flex justify-content-between align-items-center"
        >
          Позиции
          <span>
            <a
              type="button"
              data-toggle="modal"
              data-target="#exampleModal"
              class="btn btn-sm btn-primary btn-icon-split"
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
                <th scope="col">Имя</th>
                <th scope="col">Позиция</th>
                <th scope="col">Дата начала</th>
                <th scope="col">Зарплата</th>
                <th scope="col">Действия</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>Иван Иванов</td>
                <td>Менеджер</td>
                <td>01.01.2020</td>
                <td>1000 $</td>
                <td>
                  <a href="#" class="btn btn-sm btn-primary btn-icon-split">
                    <span class="icon text-white-50">
                      <i class="fas fa-pen"></i>
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
                <td>Иван Иванов</td>
                <td>Менеджер</td>
                <td>01.01.2020</td>
                <td>1000 $</td>
                <td>
                  <a href="#" class="btn btn-sm btn-primary btn-icon-split">
                    <span class="icon text-white-50">
                      <i class="fas fa-pen"></i>
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
                <td>Иван Иванов</td>
                <td>Менеджер</td>
                <td>01.01.2020</td>
                <td>1000 $</td>
                <td>
                  <a href="#" class="btn btn-sm btn-primary btn-icon-split">
                    <span class="icon text-white-50">
                      <i class="fas fa-pen"></i>
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
                <td>Иван Иванов</td>
                <td>Менеджер</td>
                <td>01.01.2020</td>
                <td>1000 $</td>
                <td>
                  <a href="#" class="btn btn-sm btn-primary btn-icon-split">
                    <span class="icon text-white-50">
                      <i class="fas fa-pen"></i>
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
                <td>Иван Иванов</td>
                <td>Менеджер</td>
                <td>01.01.2020</td>
                <td>1000 $</td>
                <td>
                  <a href="#" class="btn btn-sm btn-primary btn-icon-split">
                    <span class="icon text-white-50">
                      <i class="fas fa-pen"></i>
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
                <td>Иван Иванов</td>
                <td>Менеджер</td>
                <td>01.01.2020</td>
                <td>1000 $</td>
                <td>
                  <a href="#" class="btn btn-sm btn-primary btn-icon-split">
                    <span class="icon text-white-50">
                      <i class="fas fa-pen"></i>
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
                <td>Иван Иванов</td>
                <td>Менеджер</td>
                <td>01.01.2020</td>
                <td>1000 $</td>
                <td>
                  <a href="#" class="btn btn-sm btn-primary btn-icon-split">
                    <span class="icon text-white-50">
                      <i class="fas fa-pen"></i>
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
                <td>Петр Петров</td>
                <td>Менеджер</td>
                <td>01.01.2020</td>
                <td>1000 $</td>
                <td>
                  <a href="#" class="btn btn-sm btn-primary btn-icon-split">
                    <span class="icon text-white-50">
                      <i class="fas fa-pen"></i>
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
</template>

<script>
export default {}
</script>

<style></style>
