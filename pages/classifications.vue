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
                Классификации
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
                <table class="table table-bordered" id="dataTable" cellspacing="0">
                  <thead>
                    <tr>
                      <th>Код</th>
                      <th>Имя</th>
                      <th>Группа</th>
                      <th>Действия</th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr v-for="(item,idx) in items" :key="item.id">
                      <td>{{ item.code }}</td>
                      <td>{{ item.name }}</td>
                      <td>{{ getClassificationName(item.classification_group) }}:{{ getClassificationCode(item.classification_group) }}</td>
                      <td>
                        <div @click="editItem(idx)" class="btn btn-sm btn-primary btn-icon-split">
                          <span class="icon text-white">
                            <i class="fas fa-pencil-alt"></i>
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
                <b-modal v-model="createModal" title="Классификации" @ok="createItem">
                  <div class="form-group">
                    <label>Название</label>
                    <input
                      v-model="create.name"
                      type="text"
                      class="form-control"
                      placeholder="Введите правила"
                    />
                  </div>
                  <div class="form-group">
                    <label>Код</label>
                    <input
                      v-model="create.code"
                      type="text"
                      class="form-control"
                      placeholder="Введите правила"
                    />
                  </div>
                  <div class="form-group">
                    <label>Группа</label>
                    <select v-model="create.classification_group_id" class="form-control">
                      <option v-for="item in groups" :key="item.id" :value="item.id">{{ item.name }}</option>
                    </select>
                  </div>
                </b-modal>
                <b-modal v-model="editModal" title="Классификации" @ok="updateItem">
                  <div class="form-group">
                    <label>Название</label>
                    <input
                      v-model="update.name"
                      type="text"
                      class="form-control"
                      placeholder="Введите правила"
                    />
                  </div>
                  <div class="form-group">
                    <label>Код</label>
                    <input
                      v-model="update.code"
                      type="text"
                      class="form-control"
                      placeholder="Введите правила"
                    />
                  </div>
                  <div class="form-group">
                    <label>Группа</label>
                    <select v-model="update.classification_group_id" class="form-control">
                      <option v-for="item in groups" :key="item.id" :value="item.id">{{ item.name }}</option>
                    </select>
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
      groups: [],
      create: {
        name: '',
        code: '',
        classification_group_id: null,
      },
      update: {
        id: '',
        name: '',
        code: '',
        classification_group_id: null,
      },
      createModal: false,
      editModal: false,
    }
  },
  mounted() {
    this.$axios.$get('/classifications').then((response) => {
      this.items = response.items
    })
    this.$axios.$get('/classification-groups').then((response) => {
      this.groups = response.items
    })
  },
  methods: {
    getClassificationName(group) {
      // return group name or '-'
      if (group && group.name) {
        return group.name
      } else {
        return '-'
      }
    },
    getClassificationCode(group) {
      // return group code or '-'
      if (group && group.code) {
        return group.code
      } else {
        return '-'
      }
    },
    createItem() {
      console.log('createItem')
      this.$axios.$post('/classifications', this.create).then((response) => {
        this.items.push(response.item)
      })
    },
    editItem(index) {
      let item = this.items[index]
      this.update.name = item.name
      this.update.code = item.code
      this.update.classification_group_id = item.classification_group_id
      this.update.id = item.id
      this.editModal = true
    },
    updateItem() {
      this.$axios
        .$put('/classifications/' + this.update.id, this.update)
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
      this.$axios.$delete('/organizational-structures/' + item.id).then(() => {
        this.items.splice(this.items.findIndex((i) => i.id === item.id))
      })
    },
  },
}
</script>

<style></style>
