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
              @click="createModel = true"
              type="button"
              data-toggle="modal"
              data-target="#exampleModal"
              class="btn btn-sm btn-primary btn-icon-split"
            >
              <span class="icon text-white">
                <i class="text-white fas fa-plus"></i>
              </span>
              <span class="text">Добавить</span>
            </a>
          </span>
        </div>
      </div>
      <div class="card-body">
        <div class="table-responsive">
          <table class="table table-bordered" id="dataTable" cellspacing="0">
            <thead>
              <tr>
                <th scope="col">Позиция</th>
                <th scope="col">Зарплата</th>
                <th scope="col">Действия</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="(item, idx) in items" :key="item.id">
                <td>{{ item.name }}</td>
                <td>${{ item.salary }}</td>
                <td>
                  <div @click="editItem(idx)" class="btn btn-sm btn-primary btn-icon-split">
                    <span class="icon text-white">
                      <i class="fas fa-pen"></i>
                    </span>
                  </div>
                  <div @click="deleteItem(idx)" class="btn btn-sm btn-danger btn-icon-split">
                    <span class="icon text-white">
                      <i class="fas fa-trash"></i>
                    </span>
                  </div>
                </td>
              </tr>
            </tbody>
          </table>
          <b-modal v-model="createModel" title="BootstrapVue" @ok="createItem">
            <div class="form-group">
              <label for="exampleInputEmail1">Название</label>
              <input v-model="create.name" type="text" class="form-control" placeholder="Название" />
            </div>
            <div class="form-group">
              <label for="exampleInputEmail1">Зарплата</label>
              <input
                v-model="create.salary"
                type="text"
                class="form-control"
                placeholder="Зарплата"
              />
            </div>
          </b-modal>
          <b-modal v-model="editModal" title="BootstrapVue" @ok="updateItem">
            <div class="form-group">
              <label for="exampleInputEmail1">Название</label>
              <input v-model="update.name" type="text" class="form-control" placeholder="Название" />
            </div>
            <div class="form-group">
              <label for="exampleInputEmail1">Зарплата</label>
              <input
                v-model="update.salary"
                type="text"
                class="form-control"
                placeholder="Зарплата"
              />
            </div>
          </b-modal>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [],
      create: {
        name: '',
        salary: 0,
      },
      update: {
        id: '',
        name: '',
        salary: 0,
      },
      createModel: false,
      editModal: false,
    }
  },
  mounted() {
    this.$axios.$get('/employee-positions').then((response) => {
      this.items = response.items
    })
  },
  methods: {
    createItem() {
      console.log('createItem')
      this.$axios.$post('/employee-positions', this.create).then((response) => {
        this.items.push(response.item)
      })
    },
    editItem(index) {
      let item = this.items[index]
      this.update.name = item.name
      this.update.salary = item.salary
      this.update.id = item.id
      this.editModal = true
    },
    updateItem() {
      this.$axios
        .$put('/employee-positions/' + this.update.id, this.update)
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
      this.$axios.$delete('/employee-positions/' + item.id).then(() => {
        this.items.splice(this.items.findIndex((i) => i.id === item.id))
      })
    },
  },
}
</script>

<style></style>
