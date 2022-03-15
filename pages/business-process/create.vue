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
              </div>
            </span>
          </div>
        </div>
        <div class="card-body">
          <form class="row" action>
            <div class="input-group col-6 input-group-sm mb-3">
              <input
                v-model="create.name"
                type="text"
                class="form-control"
                placeholder="Название бизнес процесса"
              />
            </div>

            <div class="input-group col-6 input-group-sm mb-3">
              <input
                v-model="create.payment_detail"
                type="text"
                class="form-control"
                placeholder="Детали платежа"
              />
            </div>

            <div class="input-group col-6 input-group-sm mb-3">
              <input
                v-model="create.payment_amount"
                type="text"
                class="form-control"
                placeholder="Сумма платежа"
              />
            </div>

            <div class="input-group col-6 input-group-sm mb-3">
              <select
                v-model="create.classification_group_id"
                class="small w-100"
                aria-placeholder="Выберите бизнес процесс"
              >
                <option
                  v-for="(item, code) in groups"
                  :key="code"
                  :value="item.id"
                >{{ item.code }}: {{ item.name }}</option>
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
          >Бизнес процесс</div>
        </div>
        <div class="card-body">
          <div class="table-responsive border rounded">
            <table class="table" id="dataTable" cellspacing="0">
              <thead>
                <tr class="border-0 small">
                  <th class="border-bottom"></th>
                  <th class="border-bottom">Код</th>
                  <th class="border-bottom">Классификации</th>
                  <th class="border-bottom">Дата</th>
                  <th class="border-bottom"></th>
                </tr>
              </thead>
              <tbody>
                <tr
                  v-for="classification in create.classifications"
                  :key="classification.id"
                  class="border-bottom"
                >
                  <td>
                    <div class="form-check d-flex justify-content-center">
                      <input
                        v-model="classification.checked"
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
                      <input
                        v-model="classification.date_start"
                        type="date"
                        class="form-control form-control-sm"
                      />
                      <input
                        v-model="classification.date_finish"
                        type="date"
                        class="form-control form-control-sm"
                      />
                    </div>
                  </td>
                </tr>
              </tbody>
              <tfoot>
                <td
                  class="text-center small text-success"
                  colspan="5"
                >Заполните все поля для добавления нового процесса</td>
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
      groups: [],
      create: {
        name: '',
        payment_detail: '',
        payment_amount: '',
        classification_group_id: '',
        classifications: [],
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
          this.create.classifications = items
        })
    },
  },
  methods: {
    itemCreate() {
      console.log('createItem')
      this.$axios.$post('/business-processes', this.create).then((response) => {
        this.$router.push('/business-process')
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
