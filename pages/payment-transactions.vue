<template>
  <div class="container-fluid h-auto w-100">
    <!-- Page Heading -->

    <div class="row">
      <div class="card w-100 shadow mb-4">
        <div class="card-header py-3">
          <div
            class="m-0 font-weight-bold text-primary d-flex justify-content-between align-items-center"
          >
            История платежей
            <span>
              <a
                class="btn btn-sm btn-primary btn-icon-split"
                type="button"
                data-toggle="modal"
                data-target="#exampleModal"
              >
                <span class="icon text-white">
                  <i class="text-white fas fa-plus"></i>
                </span>
                <span class="text" @click="createModel = true">Добавить</span>
              </a>
            </span>
          </div>
        </div>
        <div class="card-body">
          <div class="table-responsive">
            <table v-if="!showLoader" class="table table-bordered" id="dataTable" cellspacing="0">
              <thead>
                <tr>
                </tr>
              </thead>
              <tbody>
                {{ items }}
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
      showLoader: true,
      items: [],
    }
  },
  mounted() {
    this.$axios.$get('/payment-transactions').then((response) => {
      this.items = response.items
      this.showLoader = false
    })
  },
}
</script>

<style></style>
