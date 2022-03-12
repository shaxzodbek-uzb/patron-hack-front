<template>
  <div>
    <div class="container-fluid">
      <!-- Page Heading -->

      <div class="row">
        <div class="card w-100 shadow mb-4">
          <div class="card-header py-3">
            <div
              class="m-0 font-weight-bold text-primary d-flex justify-content-between align-items-center"
            >
              Ползователи
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
                class="table table-bordered"
                id="dataTable"
                width="100%"
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
                  <tr>
                    <td>Андрей Тимофеев</td>
                    <td>Менеджер</td>
                    <td>Офис 1</td>
                    <td>$12,000</td>
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
                    <td>Николай Коперник</td>
                    <td>Бизнес тренер</td>
                    <td>Москва</td>
                    <td>$12,000</td>
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
                    <td>Александр Коновалов</td>
                    <td>Бизнес тренер</td>
                    <td>Офис 2</td>
                    <td>$12,000</td>
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
                    <td>Ирина Сергеевна</td>
                    <td>Секретар</td>
                    <td>ташкент</td>
                    <td>$12,000</td>
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
                    <td>Александр Коновалов</td>
                    <td>Бизнес тренер</td>
                    <td>Офис 2</td>
                    <td>$12,000</td>
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
                    <td>Андрей Тимофеев</td>
                    <td>Менеджер</td>
                    <td>Офис 1</td>
                    <td>$12,000</td>
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
                    <td>Николай Коперник</td>
                    <td>Бизнес тренер</td>
                    <td>Москва</td>
                    <td>$12,000</td>
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
                    <td>Александр Коновалов</td>
                    <td>Бизнес тренер</td>
                    <td>Офис 2</td>
                    <td>$12,000</td>
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
                    <td>Ирина Сергеевна</td>
                    <td>Секретар</td>
                    <td>ташкент</td>
                    <td>$12,000</td>
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
                    <td>Александр Коновалов</td>
                    <td>Бизнес тренер</td>
                    <td>Офис 2</td>
                    <td>$12,000</td>
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
                    <td>Андрей Тимофеев</td>
                    <td>Менеджер</td>
                    <td>Офис 1</td>
                    <td>$12,000</td>
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
                    <td>Николай Коперник</td>
                    <td>Бизнес тренер</td>
                    <td>Москва</td>
                    <td>$12,000</td>
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
                    <td>Александр Коновалов</td>
                    <td>Бизнес тренер</td>
                    <td>Офис 2</td>
                    <td>$12,000</td>
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
                    <td>Ирина Сергеевна</td>
                    <td>Секретар</td>
                    <td>ташкент</td>
                    <td>$12,000</td>
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
                    <td>Александр Коновалов</td>
                    <td>Бизнес тренер</td>
                    <td>Офис 2</td>
                    <td>$12,000</td>
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
  </div>
</template>

<script>
export default {}
</script>

<style></style>
