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
              <div
                @click="UpdateItem"
                type="button"
                class="btn btn-sm btn-success bg-success btn-icon-split dropdown-item"
              >
                <span class="icon text-white">
                  <i class="text-white fas fa-save"></i>
                </span>
                <span class="text-white px-2 py-1">Сохранить</span>
              </div>
            </span>
          </div>
        </div>
        <div class="card-body">
          <form class="row" action>
            <div class="input-group col-6 input-group-sm mb-3">
              <input
                :value="group"
                type="text"
                class="form-control"
                placeholder="Название бизнес процесса"
              />
            </div>

            <div class="input-group col-6 input-group-sm mb-3">
              <input
                v-model="update.payment_detail"
                type="text"
                class="form-control"
                placeholder="Детали платежа"
              />
            </div>

            <div class="input-group col-6 input-group-sm mb-3">
              <input
                v-model="update.payment_amount"
                type="text"
                class="form-control"
                placeholder="Сумма платежа"
              />
            </div>

            <div class="input-group col-6 input-group-sm mb-3">
              <select
                v-model="update.classification_group_id"
                class="small w-100"
                aria-placeholder="Выберите бизнес процесс"
              >
                <option
                  v-for="(item, code) in groups"
                  :key="code"
                  :value="item.id"
                >
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
                  <th class="border-bottom">Код</th>
                  <th class="border-bottom">Группы классификации</th>
                  <th class="border-bottom">Дата</th>
                  <th class="border-bottom">Оценка</th>
                  <th class="border-bottom"></th>
                </tr>
              </thead>
              <tbody>
                <tr
                  v-for="classification in classifications"
                  :key="classification.id"
                  class="border-bottom"
                >
                  <td>
                    <div class="form-check d-flex justify-content-center">
                      <input
                        class="form-check-input mt-2 ml-1"
                        type="checkbox"
                        value
                        id="defaultCheck1"
                      />
                    </div>
                  </td>
                  <td>{{ classification.code }}</td>
                  <td>{{ classification.name }}</td>
                  <td>
                    <div class="input-group input-group-sm">
                      <input type="date" class="form-control form-control-sm" />
                      <input type="date" class="form-control form-control-sm" />
                    </div>
                  </td>
                  <td>
                    <div class="input-group input-group-sm">
                      <input
                        placeholder="Время"
                        type="text"
                        class="form-control form-control-sm"
                        aria-label="Sizing example input"
                        aria-describedby="inputGroup-sizing-sm"
                      />
                      <input
                        placeholder="Качество"
                        type="text"
                        class="form-control form-control-sm"
                        aria-label="Sizing example input"
                        aria-describedby="inputGroup-sizing-sm"
                      />
                    </div>
                  </td>
                  <td>
                    <div class="btn btn-sm btn-success btn-icon-split">
                      <span class="icon text-white">
                        <i class="fas fa-check"></i>
                      </span>
                    </div>
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
      classifications: [],
      groups: [],
      update: {
        name: '1',
        payment_detail: 'Бистро',
        payment_amount: '12000',
        classification_group_id: '1',
        classifications: [{ id: 1, date_start: null, date_finish: null }],
      },
    }
  },
  mounted() {
    this.$axios.$get('/classification-groups').then((response) => {
      this.groups = response.items
      console.log(response)
    })
  },
  watch: {
    'create.classification_group_id'() {
      this.$axios
        .get('/classifications', {
          params: {
            classification_group_id: this.create.classification_group_id,
          },
        })
        .then(({ data: { items } }) => {
          this.classifications = items
        })
    },
  },
  methods: {
    itemUpdate() {
      this.$axios
        .put('/classifications/' + this.update.id, this.update)
        .then(({ data: { items } }) => {
          this.classifications = items
        })
    },
  },
}
</script>

<style scoped>
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
