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
              <nuxt-link
                to="/business-process/create"
                class="btn btn-sm btn-primary bg-primary btn-icon-split dropdown-item"
              >
                <span class="icon text-white">
                  <i class="text-white fas fa-plus"></i>
                </span>
                <span class="text-white px-2">Добавить</span>
              </nuxt-link>
            </span>
          </div>
        </div>
        <div class="card-body">
          <div class="table-responsive">
            <table v-if="!showLoader" class="table table-bordered" id="dataTable" cellspacing="0">
              <thead>
                <tr>
                  <th>Имя</th>
                  <th>Детали платежа</th>
                  <th>Сумма платежа</th>
                  <th>группы классификации</th>
                  <th>Действия</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="(item, idx) in items" :key="item.id">
                  <td>{{ item.name }}</td>
                  <td>Быстро</td>
                  <td>{{ item.payment_amount }}</td>
                  <td>{{ getGroupName(item.classification_group) }}</td>
                  <td>
                    <a @click="editItem(idx)" class="btn btn-sm btn-primary btn-icon-split">
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
      items: [],
      idx: '',
      showLoader: true,
    }
  },
  mounted() {
    this.$axios.$get('/business-processes').then((response) => {
      this.items = response.items
      this.showLoader = false
      console.log(response)
    })
    this.$axios.$get('/classification-groups').then((response) => {
      this.groups = response.items
    })
  },
  methods: {
    getGroupName(item) {
      return item ? item.name : '-'
    },
    deleteItem(index) {
      let item = this.items[index]
      this.$axios.$delete('/business-processes/' + item.id).then(() => {
        this.items.splice(this.items.findIndex((i) => i.id === item.id))
      })
    },
  },
}
</script>
