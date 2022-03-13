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
          <table
            class="table table-bordered"
            id="dataTable"
            
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
              <tr v-for="(item, idx) in items" :key="item.id">
                <td>Иван Иванов</td>
                <td>{{ item.name }}</td>
                <td>01.01.2020</td>
                <td>1000 $</td>
                <td>
                  <div
                    @click="editItem(idx)"
                    class="btn btn-sm btn-primary btn-icon-split"
                  >
                    <span class="icon text-white">
                      <i class="fas fa-pen"></i>
                    </span>
                  </div>
                  <div
                    @click="deleteItem(idx)"
                    class="btn btn-sm btn-danger btn-icon-split"
                  >
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
              <label for="exampleInputEmail1">Имя</label>
              <input
                v-model="create.name"
                type="text"
                class="form-control"
                placeholder="Имя"
              />
            </div>
          </b-modal>
          <b-modal v-model="editModal" title="BootstrapVue" @ok="updateItem">
            <div class="form-group">
              <label for="exampleInputEmail1">Имя</label>
              <input
                v-model="update.name"
                type="text"
                class="form-control"
                placeholder="Имя"
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
      },
      update: {
        name: '',
        id: '',
      },
      createModel: false,
      editModal: false,
    }
  },
  mounted() {
    this.$axios.$get('/roles').then((response) => {
      this.items = response.items
    })
  },
  methods: {
    createItem() {
      console.log('createItem')
      this.$axios.$post('/roles', this.create).then((response) => {
        this.items.push(response.item)
      })
    },
    editItem(index) {
      let item = this.items[index]
      this.update.name = item.name
      this.update.id = item.id
      this.editModal = true
    },
    updateItem() {
      this.$axios
        .$put('/roles/' + this.update.id, this.update)
        .then((response) => {
          this.items.splice(
            this.items.findIndex((item) => item.id === this.update.id),
            1,
            response.item
          )
        })
    },
    deleteItem(index) {
      let item = this.items[index]
      this.$axios.$delete('/roles/' + item.id).then(() => {
        this.items.splice(index, 1)
      })
    },
  },
}
</script>

<style></style>
