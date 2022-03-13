<template>
  <div id="content-wrapper" class="d-flex flex-column">
    <div id="content">
      <div class="container-fluid">
        <div class="row">
          <div class="card w-100 shadow mb-4">
            <div class="card-header py-3">
              <div
                class="m-0 font-weight-bold text-primary d-flex justify-content-between align-items-center"
              >
                Группа классификация
                <span>
                  <a
                    @click="createModal = true"
                    class="btn btn-sm btn-primary btn-icon-split"
                    type="button"
                    data-toggle="modal"
                    data-target="#exampleModal"
                  >
                    <span class="icon text-white">
                      <i class="text-white fas fa-plus"></i>
                    </span>
                    <span class="text px-2">Добавить</span>
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
                      <th>Код</th>
                      <th>Имя</th>
                      <th>Действия</th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr v-for="item in items" :key="item.id">
                      <td>{{ item.name }}</td>
                      <td>System Architect</td>
                      <td>
                        <div
                          @click="editItem(idx)"
                          class="btn btn-sm btn-primary btn-icon-split"
                        >
                          <span class="icon text-white">
                            <i class="fas fa-pencil-alt"></i>
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
                <b-modal
                  v-model="createModal"
                  title="Группа классификация"
                  @ok="createItem"
                >
                  <div class="form-group">
                    <label for="exampleInputEmail1">Бизнес правила</label>
                    <input
                      v-model="create.name"
                      type="text"
                      class="form-control"
                      placeholder="Введите правила"
                    />
                  </div>
                </b-modal>
                <b-modal
                  v-model="editModal"
                  title="Тип платежа"
                  @ok="updateItem"
                >
                  <div class="form-group">
                    <label for="exampleInputEmail1">Тип платежа</label>
                    <input
                      v-model="update.name"
                      type="text"
                      class="form-control"
                      placeholder="Введите тип"
                    />
                  </div>
                </b-modal>
              </div>
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
      this.items = response.items
      console.log(response)
    })
  },
  methods: {
    createItem() {
      console.log('createItem')
      this.$axios
        .$post('/organizational-structures', this.create)
        .then((response) => {
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
        .$put('/organizational-structures/' + this.update.id, this.update)
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
      this.$axios.$delete('/organizational-structures/' + item.id).then(() => {
        this.items.splice(this.items.findIndex((item) => item.id === item.id))
      })
    },
  },
}
</script>

<style></style>
