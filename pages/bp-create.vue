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
                type="button"
                data-toggle="modal"
                data-target="#exampleModal"
                class="btn btn-sm btn-success bg-success btn-icon-split dropdown-item"
              >
                <span class="icon text-white">
                  <i class="text-white fas fa-save"></i>
                </span>
                <span class="text-white px-2 py-1">Сохранить</span>
              </a>
            </span>
          </div>
        </div>
        <div class="card-body">
          <div class="table-responsive border rounded">
            <table class="table" id="dataTable" cellspacing="0">
              <thead>
                <tr class="border-0">
                  <th class="border-bottom">Имя</th>
                  <th class="border-bottom">Детали платежа</th>
                  <th class="border-bottom">Сумма платежа</th>
                  <th class="border-bottom">Группы классификации</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td class="border-0">
                    <input
                      type="text"
                      class="form-control form-control-sm"
                      placeholder="Имя"
                    />
                  </td>
                  <td class="border-0">
                    <input
                      type="text"
                      class="form-control form-control-sm"
                      placeholder="Детали платежа"
                    />
                  </td>
                  <td class="border-0">
                    <input
                      type="text"
                      class="form-control form-control-sm"
                      placeholder="Сумма платежа"
                    />
                  </td>
                  <td class="border-0">
                    <select v-model="items" class="border rounded py-1">
                      <option v-for="item in items" :key="item.id">
                        {{ item }}
                      </option>
                    </select>
                  </td>
                </tr>
              </tbody>
              <tfoot>
                <td class="text-center small text-success" colspan="4">
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
      items: [],
    }
  },
  mounted() {
    this.$axios.$get('/classification-groups').then((response) => {
      this.items = response.items
      console.log(response)
    })
  },
}
</script>
