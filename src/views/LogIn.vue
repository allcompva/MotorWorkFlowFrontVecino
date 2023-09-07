<template>
  <div class="container" style="overflow-y: hidden; background-color: white">
    <div class="row">
      <!-- BEGIN: Login Info -->
      <div class="col-md-12" style="text-align: center; padding: 35px">
        <div
          @click="verTramite()"
          style="
            margin-top: 50px;
            --bs-bg-opacity: 1;
            --bs-border-opacity: 1;
            background-color: rgba(var(--bs-white-rgb), var(--bs-bg-opacity));
            border-color: transparent;
            border-radius: 0.375rem;
            box-shadow: -2px -2px 14px 0px #00000075;
            position: relative;
            padding-bottom: 35px;
          "
        >
          <img
            style="height: 150px; width: auto; display: inline; margin-top: 5%"
            src="../assets/Logo2.png"
          />
          <h2
            style="
              margin-top: 35px;
              font-size: 24px;
              font-weight: 700;
              color: darkcyan;
            "
          >
            Portal e-tramite
          </h2>
          <button
            @click="btnIngresar"
            class="btn btn-primary"
            style="margin-top: 25px; margin-bottom: 35px"
          >
            Ingresar
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
//import { useRoute } from 'vue-router'

export default {
  inject: ['mq'],
  data: () => ({
    user: '',
    password: '',
    usuario: null,
    labelError: false,
  }),
  setup() {},
  components: {},
  mounted() {},
  methods: {
    btnIngresar() {
      window.location.href =
        'https://vecino.villaallende.gov.ar/LogInCidi.aspx?url=https%3A%2F%2Fvecino.villaallende.gov.ar%2Fetramites%2F%23%2FListaTramites'
    },
  },
}
</script>
