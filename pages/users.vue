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
                  @click="createModal = true"
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
                  <tr v-for="item in items" :key="item.id">
                    <td>{{ item.name }}</td>
                    <td>Бизнес тренер</td>
                    <td>Офис 2</td>
                    <td>$12,000</td>
                    <td>
                      <a
                        @click="editItem(idx)"
                        class="btn btn-sm btn-primary btn-icon-split"
                      >
                        <span class="icon text-white">
                          <i class="fas fa-pencil-alt"></i>
                        </span>
                      </a>
                      <a
                        
                        class="btn btn-sm btn-danger btn-icon-split"
                      >
                        <span class="icon text-white">
                          <i class="fas fa-trash"></i>
                        </span>
                      </a>
                    </td>
                  </tr>
                </tbody>
              </table>
              <b-modal
                v-model="createModal"
                title="BootstrapVue"
                @ok="createItem"
              >
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
              <b-modal
                v-model="editModal"
                title="BootstrapVue"
                @ok="updateItem"
              >
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
      createModal: false,
      editModal: false,
    }
  },
  mounted() {
    this.$axios.$get('/organizational-structures').then((response) => {
      console.log(response)
      this.items = response.items
    })
  },
  methods: {
    createItem() {
      console.log('createItem')
      this.$axios.$post('/users/', this.create).then((response) => {
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
        .$put('/users/' + this.update.id, this.update)
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
      this.$axios.$delete('/users/' + item.id).then(() => {
        this.items.splice(index, 1)
      })
    },
  },
}
</script>

<style></style>
