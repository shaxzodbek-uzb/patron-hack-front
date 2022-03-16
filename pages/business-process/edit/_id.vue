<template>
  <div class="container-fluid">
    <div class="row">
      <div class="card w-100 shadow mb-4">
        <div class="card-header py-3">
          <div
            class="m-0 font-weight-bold text-primary d-flex justify-content-between align-items-center"
          >
            Бизнес процесс: {{ update.id }}
            <span>
              <div
                @click="updateItem"
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
          <form class="row small">
            <label class="input-group col-6 input-group-sm mb-3">
              Название
              <input
                v-model="update.name"
                type="text"
                class="form-control w-100"
                placeholder="Название бизнес процесса"
              />
            </label>

            <label class="input-group col-6 input-group-sm mb-3">
              Детали платежа
              <input
                v-model="update.payment_detail"
                type="text"
                class="form-control w-100"
                placeholder="Детали платежа"
              />
            </label>

            <label class="input-group col-6 input-group-sm mb-3">
              Сумма платежа
              <input
                v-model="update.payment_amount"
                type="text"
                class="form-control w-100"
                placeholder="Сумма платежа"
              />
            </label>

            <label class="input-group col-6 input-group-sm mb-3">
              Выберите бизнес процесс
              <select
                v-model="update.classification_group_id"
                class="small form-control w-100"
                aria-placeholder="Выберите бизнес процесс"
              >
                <option
                  disabled
                  v-for="(item, code) in groups"
                  :key="code"
                  :value="item.id"
                >
                  {{ item.code }}: {{ item.name }}
                </option>
              </select>
            </label>
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
                  <th class="border-bottom">Код</th>
                  <th class="border-bottom">Группы классификации</th>
                  <th class="border-bottom">
                    <span class="row text-center">
                      <div class="col-6">Начало</div>
                      <div class="col-6">Конец</div>
                    </span>
                  </th>
                  <th class="border-bottom">Оценка</th>
                  <th class="border-bottom"></th>
                </tr>
              </thead>
              <tbody>
                <tr
                  v-for="(classification, index) in update.classifications"
                  :key="classification.id"
                  class="border-bottom"
                >
                  <td>{{ classification.code }}</td>
                  <td>{{ classification.name }}</td>
                  <td>
                    <div class="row text-center">
                      <span class="col-6">
                        {{ classification.pivot.date_start }}
                      </span>
                      <span class="col-6">
                        {{ classification.pivot.date_finish }}
                      </span>
                    </div>
                  </td>
                  <td>
                    <div
                      class="input-group input-group-sm"
                      v-if="!classification.pivot.done"
                    >
                      <input
                        placeholder="Время"
                        type="text"
                        class="form-control form-control-sm"
                        aria-label="Sizing example input"
                        aria-describedby="inputGroup-sizing-sm"
                        v-model="classification.pivot.time_rate"
                      />
                      <input
                        placeholder="Качество"
                        type="text"
                        class="form-control form-control-sm"
                        aria-label="Sizing example input"
                        aria-describedby="inputGroup-sizing-sm"
                        v-model="classification.pivot.quality_rate"
                      />
                    </div>
                    <div v-else>
                      <span class="badge badge-warning">
                        {{ classification.pivot.time_rate }}
                      </span>
                      <span class="badge badge-info">
                        {{ classification.pivot.quality_rate }}
                      </span>
                    </div>
                  </td>
                  <td>
                    <div
                      class="btn btn-sm btn-success btn-icon-split"
                      @click="completeClassification(index)"
                      v-if="!classification.pivot.done"
                    >
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

      <b-modal
        v-model="createModal"
        title="Группа классификация"
        @ok="createItem"
      >
        <div class="form-group">
          <div class="row">
            <div class="col-md-6">
              <label class="input-group input-group-sm">
                Общая сумма:
                  <input
                    type="text"
                    class="form-control w-100"
                    readonly
                    :value="update.payment_amount"
                  />
              </label>
            </div>
            <div class="col-md-6">
              <label class="input-group input-group-sm">
                Тип платежа
                <select class="form-control small w-100">
                  <option
                    v-for="(item, code) in payment"
                    :key="code"
                    :value="item.id"
                  >
                    {{ item.name }}
                  </option>
                </select>
              </label>
            </div>
          </div>
        </div>
      </b-modal>

      <!-- Pie Chart -->
      <div class="w-100" v-if="update.status == 'done'">
        <div class="card shadow mb-4">
          <!-- Card Header - Dropdown -->
          <div
            class="card-header py-3 d-flex flex-row align-items-center justify-content-between"
          >
            <h6 class="m-0 font-weight-bold text-primary">
              Количество платежей
            </h6>
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
            <ChartLine :height="100" :chartdata="dataset" />
          </div>
        </div>
        <div class="d-flex justify-content-end pb-5">
          <button
            class="btn btn-sm btn-primary btn-icon-split"
            @click="createModal = true"
          >
            <span class="icon text-white">
              <i class="fas fa-check"></i>
            </span>
            <span class="text">Завершить</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      createModal: true,
      loading: false,
      groups: [],
      create: {
        payment_amount: '',
        payment_type: '',
      },
      update: {
        id: this.$route.params.id,
        name: '',
        payment_detail: '',
        payment_amount: '',
        classification_group_id: '1',
        classifications: [],
        status: 'new',
      },
    }
  },
  computed: {
    dataset() {
      const low_rates = this.update.classifications.map((item) =>
        parseInt((item.low_rate / item.max_rate) * 100)
      )

      const high_rates = this.update.classifications.map((item) =>
        parseInt((item.high_rate / item.max_rate) * 100)
      )
      const middle_rates = this.update.classifications.map((item) =>
        parseInt((item.middle_rate / item.max_rate) * 100)
      )
      const classification_rates = this.update.classifications.map(
        (item) =>
          ((Number(item.pivot.time_rate) + Number(item.pivot.quality_rate)) /
            2 /
            item.max_rate) *
          100
      )
      const labels = this.update.classifications.map((item) => item.code)
      // if one of the rates has no items return false
      if (
        low_rates.length === 0 ||
        high_rates.length === 0 ||
        middle_rates.length === 0 ||
        classification_rates === 0 ||
        labels === 0
      ) {
        return false
      }

      return {
        labels,
        datasets: [
          {
            fill: false,
            label: 'Максимум',
            data: high_rates,
            borderWidth: 2,
            backgroundColor: false,
            borderColor: 'lime',
          },

          {
            fill: false,
            label: 'Средний',
            data: middle_rates,
            borderWidth: 2,
            backgroundColor: false,
            borderColor: 'green',
          },
          {
            fill: false,

            label: 'Минимум',
            data: low_rates,
            borderWidth: 2,
            backgroundColor: false,
            borderColor: 'red',
          },

          {
            fill: false,

            label: 'Рейтинг в классификации',
            data: classification_rates,
            borderWidth: 2,
            backgroundColor: false,
            borderColor: 'blue',
          },
        ],
      }
    },
  },
  mounted() {
    this.$axios
      .$get(`/business-processes/${this.update.id}`)
      .then(({ item }) => {
        this.update.name = item.name
        this.update.payment_detail = item.payment_detail
        this.update.payment_amount = item.payment_amount
        this.update.classification_group_id = item.classification_group_id
        this.update.classifications = item.classifications
        this.update.status = item.status
        this.groups = [item.classification_group]
        this.$nextTick(() => {
          this.loading = false
        })
      })
    this.$axios.$get(`/payment-types`).then(({ items }) => {
      this.payment = items
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
    updateItem() {
      this.$axios
        .put('/business-processes/' + this.update.id, this.update)
        .then(({ data: { items } }) => {
          this.$router.push('/business-process')
        })
    },
    completeClassification(index) {
      this.$axios
        .post('/business-processes/complete-classification', {
          business_process_id: this.update.id,
          classification_id: this.update.classifications[index].id,
          time_rate: this.update.classifications[index].pivot.time_rate,
          quality_rate: this.update.classifications[index].pivot.quality_rate,
        })
        .then(({ data: { done, success } }) => {
          if (success) {
            this.update.classifications[index].pivot.done = true
          }
          if (done) {
            this.update.status = 'done'
          }
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
