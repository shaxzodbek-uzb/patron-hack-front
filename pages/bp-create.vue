<template>
  <div class="container-fluid">
    <div class="row">
      <div class="card w-100 shadow mb-4">
        <div class="card-header py-3">
          <div
            class="m-0 font-weight-bold text-primary d-flex justify-content-between align-items-center"
          >
            Бизнес процесс
            <span>
              <a
                @click="itemCreate"
                type="button"
                data-toggle="modal"
                data-target="#exampleModal"
                class="btn btn-sm btn-success bg-success btn-icon-split dropdown-item"
              >
                <span class="icon text-white">
                  <i class="text-white fas fa-save"></i>
                </span>
                <span class="text-white px-2 py-1">Сохранить</span>
              </a>
            </span>
          </div>
        </div>
        <div class="card-body">
          <form class="row" action="">
            <div class="input-group col-6 input-group-sm mb-3">
              <input
              v-model="create.name"
                type="text"
                class="form-control"
                aria-label="Sizing example input"
                aria-describedby="inputGroup-sizing-sm"
                placeholder="Название бизнес процесса"
              />
            </div>

            <div class="input-group col-6 input-group-sm mb-3">
              <input
              v-model="create.code"
                type="text"
                class="form-control"
                aria-label="Sizing example input"
                aria-describedby="inputGroup-sizing-sm"
                placeholder="Детали платежа"
              />
            </div>

            <div class="input-group col-6 input-group-sm mb-3">
              <input
                type="text"
                class="form-control"
                aria-label="Sizing example input"
                aria-describedby="inputGroup-sizing-sm"
                placeholder="Сумма платежа"
              />
            </div>

            <div class="input-group col-6 input-group-sm mb-3">
              <select v-model="items" class="bp-select small text-muted">
                <option>Выберите бизнес процесс</option>
                <option v-for="(item, code) in items" :key="code">
                  {{ item.code }}
                </option>
              </select>
            </div>
          </form>
        </div>
      </div>
    </div>

    <div class="row">
      <div class="card w-100 shadow mb-4">
        <div class="card-header py-3">
          <div
            class="m-0 font-weight-bold text-primary d-flex justify-content-between align-items-center"
          >
            Бизнес процесс
          </div>
        </div>
        <div class="card-body">
          <div class="table-responsive border rounded">
            <table class="table" id="dataTable" cellspacing="0">
              <thead>
                <tr class="border-0 small">
                  <th class="border-bottom"></th>
                  <th class="border-bottom">Имя</th>
                  <th class="border-bottom">Код</th>
                  <th class="border-bottom">Группы классификации</th>
                  <th class="border-bottom">Статус</th>
                  <th class="border-bottom"></th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="count in trCount" :key="count" class="border-bottom">
                  <td>
                    <div class="form-check d-flex justify-content-center">
                      <input
                        class="form-check-input mt-2 ml-1"
                        type="checkbox"
                        value=""
                        id="defaultCheck1"
                      />
                    </div>
                  </td>
                  <td>
                    <input
                      type="text"
                      class="form-control form-control-sm"
                      placeholder="Имя"
                    />
                  </td>
                  <td>
                    <select
                      class="form-control form-control-sm"
                      v-model="items"
                    >
                      <option selected>Выберите код</option>
                      <option v-for="(item, code) in items" :key="code">
                        {{ item.code }}
                      </option>
                    </select>
                  </td>
                  <td>
                    <select
                      class="form-control form-control-sm"
                      v-model="items"
                    >
                      <option selected>Выберите группу</option>
                      <option v-for="(item, code) in items" :key="code">
                        {{ item.name }}
                      </option>
                    </select>
                  </td>
                  <td>
                    <span class="d-flex justify-content-space-between">
                      <div class="input-group input-group-sm">
                        <input
                          placeholder="Оценка"
                          type="text"
                          class="form-control form-control-sm"
                          aria-label="Sizing example input"
                          aria-describedby="inputGroup-sizing-sm"
                        />
                        <input
                          placeholder="Балл"
                          type="text"
                          class="form-control form-control-sm"
                          aria-label="Sizing example input"
                          aria-describedby="inputGroup-sizing-sm"
                        />
                      </div>
                    </span>
                  </td>
                  <td>
                    <button @click="trCount++" class="btn btn-sm btn-primary">
                      <i class="fas fa-plus"></i>
                    </button>
                  </td>
                </tr>
              </tbody>
              <tfoot>
                <td class="text-center small text-success" colspan="5">
                  Заполните все поля для добавления нового процесса
                </td>
              </tfoot>
            </table>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      trCount: 1,
      create: {
        name: '',
        code: '',
      },
    }
  },
  mounted() {
    this.$axios.$get('/classification-groups').then((response) => {
      this.items = response.items
      console.log(response)
    })
  },
  methods: {
    itemCreate() {
      this.$axios
        .$post('/classification-groups', this.create)
        .then((response) => {
          console.log(response)
        })
        .catch((error) => {
          console.log(error)
        })
    },
  },
}
</script>

<style scoped>
.bp-select {
  width: 100%;
  background: none;
  border-radius: 5px;
  border: 1px solid rgb(186, 199, 199);
}

table tbody td {
  border: none;
}

input:focus {
  outline: none;
}

input[type='checkbox'] {
  appearance: none;
  width: 1.5em;
  height: 1.5em;
  position: relative;
  margin: 0 0.5em 0 0;
  cursor: pointer;
  transform: scale(0.8);
}

input[type='checkbox']:before {
  content: '';
  width: 100%;
  height: 100%;
  background: #ddd;
  color: #fff;
  text-align: center;
  line-height: 1.5;
  border-radius: 0.4em;
  position: absolute;
  top: -4px;
  left: 0;
  z-index: 10;
}

input[type='checkbox']:checked:before {
  font-family: -apple-system !important;
  content: '\2714';
  background: #3e64d3;
}

input[type='checkbox']:after {
  content: '';
  width: 300%;
  height: 300%;
  background-color: #3e64d3;
  border-radius: 100%;
  position: absolute;
  top: 30%;
  left: 50%;
  z-index: 5;
  opacity: 0;
  transform: translate(-50%, -50%);
  animation: none;
}

input[type='checkbox']:checked:after {
  animation: check 0.3s;
}

@keyframes check {
  0% {
    transform: translate(-50%, -50%) scale(0.1);
    opacity: 1;
  }
  40% {
    opacity: 1;
  }
  100% {
    transform: translate(-50%, -50%) scale(1);
    opacity: 0;
  }
}
</style>
