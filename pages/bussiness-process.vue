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
                @click="createModal = true"
                type="button"
                data-toggle="modal"
                data-target="#exampleModal"
                class="btn btn-sm btn-primary bg-primary btn-icon-split dropdown-item"
              >
                <span class="icon text-white">
                  <i class="text-white fas fa-plus"></i>
                </span>
                <span class="text-white px-2">Добавить</span>
              </a>
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
            <b-modal v-model="createModal" title="BootstrapVue" @ok="createItem">
              <div class="form-group">
                <label for="exampleInputEmail1">Имя</label>
                <input v-model="create.name" type="text" class="form-control" placeholder="Имя" />
                <label for="exampleInputEmail1">Детали платежа</label>
                <input
                  v-model="create.payment_detail"
                  type="text"
                  class="form-control"
                  placeholder="Детали платежа"
                />
                <label for="exampleInputEmail1">Сумма платежа</label>
                <input
                  v-model="create.payment_amount"
                  type="text"
                  class="form-control"
                  placeholder="Сумма платежа"
                />
                <label for="exampleInputEmail1">ID группы классификации</label>
                <select v-model="create.classification_group_id">
                  <option v-for="item in groups" :key="item.id" :value="item.id">{{ item.name }}</option>
                </select>
              </div>
            </b-modal>
            <b-modal v-model="editModal" title="BootstrapVue" @ok="updateItem">
              <div class="form-group">
                <label>Имя</label>
                <input type="text" class="form-control" v-model="update.name" placeholder="Имя" />
                <label>Детали платежа</label>
                <input
                  type="text"
                  class="form-control"
                  v-model="update.payment_detail"
                  placeholder="Детали платежа"
                />
                <label>Сумма платежа</label>
                <input
                  type="text"
                  class="form-control"
                  v-model="update.payment_amount"
                  placeholder="Сумма платежа"
                />
                <label>группы классификации</label>
                <select v-model="update.classification_group_id">
                  <option v-for="item in groups" :key="item.id" :value="item.id">{{ item.name }}</option>
                </select>
              </div>
            </b-modal>
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
      showLoader: false,
      idx: '',
      createModal: false,
      editModal: false,
      showLoader: true,
      create: {
        name: '',
        payment_detail: '',
        payment_amount: '',
        classification_group_id: '',
      },
      update: {
        name: '',
        payment_detail: '',
        payment_amount: '',
        classification_group_id: '',
      },
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
    createItem() {
      console.log('createItem')
      this.$axios.$post('/business-processes', this.create).then((response) => {
        this.items.push(response.item)
      })
    },
    editItem(index) {
      let item = this.items[index]
      this.update.id = item.id
      this.update.name = item.name
      this.update.payment_detail = item.payment_detail
      this.update.payment_amount = item.payment_amount
      this.update.classification_group_id = item.classification_group_id
      this.editModal = true
    },
    updateItem() {
      this.$axios
        .$put('/business-processes/' + this.update.id, this.update)
        .then((response) => {
          this.items.splice(
            this.items.findIndex((i) => i.id === this.update.id),
            1,
            response.item
          )
        })
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
