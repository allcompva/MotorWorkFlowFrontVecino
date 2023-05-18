<template>
  <div
    data-v-92b86960=""
    data-v-34dd9120=""
    class="box"
    style="text-align: left"
    @click="verTramite()"
  >
    <div style="padding: 5px !important; text-align: center; min-height: 145px">
      <img
        :src="
          'https://vecino.villaallende.gov.ar/img/' +
          tramite.logo_unidad_administrativa
        "
        style="
          height: 50px;
          width: auto;
          margin: 00;
          margin-top: 10px;
          margin-left: 10px;
        "
      />
      <div
        style="
          text-align: center;
          padding-left: 10px;
          margin-top: 5px !important;
          margin-bottom: 10px;
        "
      >
        <a data-v-92b86960="" class="fw-medium">{{ tramite.nombre }}</a>
      </div>
    </div>
  </div>
</template>
<style scoped>
@import '../assets/css/app.css';
.text-gray-600 {
  --bs-text-opacity: 1;
  color: rgba(var(--bs-gray-600-rgb), var(--bs-text-opacity)) !important;
  padding-top: 5px;
}
.btn-primary {
  background-color: rgb(15 153 202) !important;
}
.main-header-two__shape-3 {
  bottom: 0.5px !important;
}
img {
  display: inline !important;
}
.box,
.pagination .page-item.active .page-link,
.search-result .search-result__content {
  --bs-bg-opacity: 1;
  --bs-border-opacity: 1;
  background-color: rgba(var(--bs-white-rgb), var(--bs-bg-opacity));
  border-color: transparent;
  border-top: solid 1px lightgray;
  border-radius: 0.375rem;
  box-shadow: 0 3px 20px #0000000b;
  position: relative;
  box-shadow: 1px 3px 2px 1px
      var(--v-shadow-key-umbra-opacity, rgba(0, 0, 0, 0.2)),
    0 1px 1px 0 var(--v-shadow-key-penumbra-opacity, rgba(0, 0, 0, 0.14)),
    0 1px 3px 0 var(--v-shadow-key-penumbra-opacity, rgba(0, 0, 0, 0.12));
}
</style>
<script>
import Cookies from 'js-cookie'
export default {
  inject: ['mq'],
  data: () => ({
    tabPaneActiveKey: 1,
  }),
  components: {},
  async mounted() {},
  props: {
    tramite: {
      type: Object,
      default: () => ({
        id: 1,
        nombre: undefined,
        descripcion: undefined,
        fecha_crea: undefined,
        usu_crea: undefined,
        fecha_modifica: undefined,
        usu_modifica: undefined,
        activo: undefined,
        fecha_baja: undefined,
        usu_baja: undefined,
        id_unidad_organizativa: undefined,
        nombre_unidad_organizativa: undefined,
        logo_unidad_administrativa: undefined,
      }),
    },
  },
  methods: {
    validadeFormOne() {
      return false
    },
    verTramite() {
      this.$router.push(
        '/Tramite/' + Cookies.get('hash') + '/' + this.tramite.primer_paso,
      )
    },
  },
}
</script>
