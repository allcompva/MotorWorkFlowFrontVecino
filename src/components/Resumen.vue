<template>
  <template v-if="inicio">
    <CForm class="row g-3 needs-validation">
      <CRow>
        <CCol xs="12">
          <CCardTitle
            style="
              margin-bottom: 10px;
              margin-top: 0px;
              font-size: 18px;
              font-weight: 500;
              color: var(--roofsie-gray);
            "
            >¿Confirma el ingreso de datos?</CCardTitle
          >
          <p style="margin-top: 15px; margin-bottom: 3px">
            Iniciador: <strong>{{ iniciador }}</strong>
          </p>
          <p>
            Representado: <strong>{{ representado }}</strong>
          </p>
        </CCol>
      </CRow>
      <template v-if="filasUnicas != null">
        <CRow v-for="(itemRow, i) in filasUnicas" :key="i">
          <CCol
            style="margin-bottom: 35px"
            xs="12"
            :lg="itemCol.col"
            :xl="itemCol.col"
            v-for="(itemCol, ic) in formulario.filter(
              (persona) => persona.row === itemRow.row,
            )"
            :key="ic"
          >
            <template v-if="itemCol.id_ddjj != 0">
              <CCardTitle
                style="
                  margin-bottom: 10px;
                  margin-top: 0px;
                  font-size: 18px;
                  font-weight: 500;
                  color: var(--roofsie-gray);
                "
                >Solicitud</CCardTitle
              >
              <hr />
              <div v-html="itemCol.objDDJJ.texto"></div>
            </template>
            <template v-if="itemCol.id_formulario != 0">
              <CCardTitle
                style="
                  margin-bottom: 10px;
                  margin-top: 0px;
                  font-size: 18px;
                  font-weight: 500;
                  color: var(--roofsie-gray);
                "
              >
                {{
                  itemCol.objFormulario.nombre[0].toUpperCase() +
                  itemCol.objFormulario.nombre.substring(1).toLowerCase()
                }}
              </CCardTitle>
              <hr />
              <CCardText
                v-if="
                  itemCol.objFormulario != null &&
                  itemCol.objFormulario != 'undefined'
                "
              >
                <CRow
                  v-for="(campo, c) in itemCol.objFormulario.lstCampos.filter(
                    (filas, index, self) =>
                      index === self.findIndex((f) => f.row === filas.row),
                  )"
                  :key="c"
                  style="padding: 0; padding-bottom: 5px"
                >
                  <CCol
                    xs="12"
                    :lg="item.col"
                    :xl="item.col"
                    v-for="(
                      item, ico
                    ) in itemCol.objFormulario.lstCampos.filter(
                      (persona) => persona.row === campo.row,
                    )"
                    :key="ico"
                  >
                    <div v-if="item.id_tipo_campo == 1">
                      <p>
                        {{
                          item.etiqueta[0].toUpperCase() +
                          item.etiqueta.substring(1).toLowerCase()
                        }}: <br /><strong>{{ item.ingreso_usuario }}</strong>
                      </p>
                    </div>
                    <div v-if="item.id_tipo_campo == 2">
                      <p>
                        {{
                          item.etiqueta[0].toUpperCase() +
                          item.etiqueta.substring(1).toLowerCase()
                        }}: <br /><strong>{{ item.ingreso_usuario }}</strong>
                      </p>
                    </div>
                    <div v-if="item.id_tipo_campo == 3">
                      <p>
                        {{
                          item.etiqueta[0].toUpperCase() +
                          item.etiqueta.substring(1).toLowerCase()
                        }}: <br /><strong>{{ item.ingreso_usuario }}</strong>
                      </p>
                    </div>
                    <div v-if="item.id_tipo_campo == 4">
                      <p>
                        {{
                          item.etiqueta[0].toUpperCase() +
                          item.etiqueta.substring(1).toLowerCase()
                        }}: <br /><strong>{{ item.ingreso_usuario }}</strong>
                      </p>
                    </div>
                    <div v-if="item.id_tipo_campo == 5">
                      <p>
                        {{
                          item.etiqueta[0].toUpperCase() +
                          item.etiqueta.substring(1).toLowerCase()
                        }}: <br /><strong>{{ item.ingreso_usuario }}</strong>
                      </p>
                    </div>
                    <div v-if="item.id_tipo_campo == 6">
                      <p>
                        {{
                          item.etiqueta[0].toUpperCase() +
                          item.etiqueta.substring(1).toLowerCase()
                        }}: <br /><strong>{{ item.ingreso_usuario }}</strong>
                      </p>
                    </div>
                    <div v-if="item.id_tipo_campo == 7">
                      <p>
                        {{
                          item.etiqueta[0].toUpperCase() +
                          item.etiqueta.substring(1).toLowerCase()
                        }}: <br /><strong>{{ item.ingreso_usuario }}</strong>
                      </p>
                    </div>
                    <div v-if="item.id_tipo_campo == 8">
                      <p>
                        {{
                          item.etiqueta[0].toUpperCase() +
                          item.etiqueta.substring(1).toLowerCase()
                        }}: <br />

                        <strong v-if="item.formato_resultado == 'texto'">
                          {{ item.ingreso_usuario }}</strong
                        >
                        <strong v-else-if="item.formato_resultado == 'comas'">
                          {{ item.ingreso_usuario.split(',')[1] }}</strong
                        >
                      </p>
                    </div>
                    <div v-if="item.id_tipo_campo == 9">
                      <p style="margin-top: 10px; margin-bottom: 10px">
                        {{
                          item.etiqueta[0].toUpperCase() +
                          item.etiqueta.substring(1).toLowerCase()
                        }}
                      </p>
                      <p
                        v-for="seleccionado in item.ingreso_usuario"
                        :key="seleccionado.value"
                        style="display: flex"
                      >
                        <CIcon icon="cil-task" style="height: 25px" />&nbsp;
                        <strong>{{ seleccionado.text }}</strong>
                      </p>
                    </div>
                    <div v-if="item.id_tipo_campo == 14">
                      <p>
                        {{
                          item.etiqueta[0].toUpperCase() +
                          item.etiqueta.substring(1).toLowerCase()
                        }}: <br />

                        <strong v-if="item.formato_resultado == 'texto'">
                          {{ item.ingreso_usuario }}</strong
                        >
                        <strong v-else-if="item.formato_resultado == 'comas'">
                          {{ item.ingreso_usuario.split(',')[1] }}</strong
                        >
                      </p>
                    </div>
                  </CCol>
                </CRow>
              </CCardText>
            </template>
            <template
              v-if="
                itemCol.id_adjunto != 0 &&
                itemCol.objAdjunto.ingreso_usuario != ''
              "
            >
              <template v-if="itemCol.objAdjunto.multiple == false">
                <template
                  v-if="
                    itemCol.objAdjunto.extenciones_aceptadas ==
                    'application/pdf'
                  "
                >
                  <CCardTitle
                    style="
                      margin-bottom: 10px;
                      margin-top: 0px;
                      font-size: 18px;
                      font-weight: 500;
                      color: var(--roofsie-gray);
                    "
                    >Documentación</CCardTitle
                  >
                  <hr />
                  <CWidgetStatsF
                    color="danger"
                    :value="itemCol.objAdjunto.etiqueta"
                    :title="itemCol.objAdjunto.descripcion"
                  >
                    <template #icon>
                      <CIcon :icon="icon.cibAdobeAcrobatReader" size="xl" />
                    </template>
                  </CWidgetStatsF>
                </template>
                <template v-else>
                  <CCardTitle
                    style="
                      margin-bottom: 10px;
                      margin-top: 0px;
                      font-size: 18px;
                      font-weight: 500;
                      color: var(--roofsie-gray);
                    "
                  >
                    {{ itemCol.objAdjunto.etiqueta }}
                  </CCardTitle>
                  <hr />
                  <CAlert
                    style="display: inline-flex; margin: 0px; padding: 5px"
                  >
                    <img
                      :src="itemCol.objAdjunto.ingreso_usuario"
                      style="
                        height: 100px;
                        width: auto;
                        margin-top: 20px;
                        border: solid gray;
                        border-radius: 15px;
                      "
                    />
                  </CAlert>
                </template>
              </template>
              <template v-else>
                <CCardTitle
                  style="
                    margin-bottom: 10px;
                    margin-top: 0px;
                    font-size: 18px;
                    font-weight: 500;
                    color: var(--roofsie-gray);
                  "
                >
                  {{ itemCol.objAdjunto.descripcion }}
                </CCardTitle>
                <hr />
                <CAlert
                  v-for="(image, index) in image"
                  :key="index"
                  style="display: inline-flex; margin: 0px; padding: 5px"
                >
                  <img
                    :src="image"
                    style="
                      height: 100px;
                      width: auto;
                      margin-top: 20px;
                      border: solid gray;
                      border-radius: 15px;
                    "
                  />
                </CAlert>
              </template>
            </template>
          </CCol>
        </CRow>
      </template>
      <CRow>
        <CCol xs="12">
          <button
            type="submit"
            @click="btnSiguiente_clickHijo(paso, 0)"
            class="btn btn-primary shadow-md me-2"
            style="float: left"
          >
            <span>Anterior</span><i class="pi pi-arrow-left"></i>
          </button>
          <button
            type="button"
            @click="subirArchivosMarcoLegal()"
            class="btn btn-primary shadow-md me-2"
            style="float: right"
          >
            <span>Enviar</span><i class="pi pi-arrow-right"></i>
          </button>
        </CCol>
      </CRow>
    </CForm>
  </template>
  <template v-else>
    <CCard>
      <CCardBody
        style="
          text-align: center;
          border: solid #2c9587;
          box-shadow: 0px 0px 12px 6px rgba(44, 149, 135, 0.9);
          -webkit-box-shadow: 0px 0px 10px 5px rgba(44, 149, 135, 0.9);
          -moz-box-shadow: 0px 0px 12px 6px rgba(44, 149, 135, 0.9);
        "
      >
        <i class="fa fa-check btn-delete" style="color: #2c9587"></i>
        <h3 style="font-size: 24px">Su tramite se genero exitosamente!</h3>
        <CButton
          @click="btnFinalizar()"
          color="primary"
          style="
            color: #fff !important;
            background-color: #2c9587 !important;
            border-color: #2c9587 !important;
            margin-top: 25px;
          "
          >Continuar</CButton
        >
      </CCardBody>
    </CCard>
  </template>
</template>
<style>
.v-select.v-select--chips:not(
    .v-text-field--single-line
  ).v-text-field--box.v-input--dense
  .v-select__selections,
.v-select.v-select--chips:not(
    .v-text-field--single-line
  ).v-text-field--enclosed.v-input--dense
  .v-select__selections {
  min-height: 40px;
}
hr:not([size]) {
  height: 2px;
}
hr {
  margin: 1rem 0;
  color: inherit;
  background-color: #ffc107;
  border: 0;
  opacity: 0.75;
}
.v-alert__content {
  padding-left: 10px;
}
</style>

<script>
import { CIcon } from '@coreui/icons-vue'
import * as icon from '@coreui/icons'
import axios from 'axios'
import Cookies from 'js-cookie'
export default {
  components: {
    CIcon,
  },
  data: () => ({
    inicio: true,
    icon,
    maxValue: 0,
    text: '',
    value: '',
    chkDJJ: false,
    chipErrorDDJJ: false,
    nroPaso: 2,
    error: false,
    contador: 0,
    textoError: '',
    habilita: false,
    errors: [],
    multisel: null,
    formulario: null,
    visibleLiveDemo: false,
    image: [],
    filasUnicas: [],
  }),
  mounted() {
    this.formulario = this.$store.getters.getPaso
    this.image = this.$store.getters.getPreviaImagenes
    this.filasUnicas = this.formulario.filter(
      (filas, index, self) =>
        index === self.findIndex((f) => f.row === filas.row),
    )
    console.log(JSON.stringify(this.filasUnicas))
  },
  props: {
    iniciador: {
      type: String,
      default: '',
    },
    representado: {
      type: String,
      default: 'A si mismo',
    },
    paso: {
      type: Number,
      default: 0,
    },
  },
  methods: {
    btnFinalizar() {
      this.$router.push('/ListaTramites/' + Cookies.get('hash'))
    },
    btnSiguiente_clickHijo(pasoDestino, direccion) {
      this.$emit('tengo_resultados', pasoDestino, direccion)
    },
    async subirArchivosMarcoLegal() {
      let InstFormData = new FormData()
      InstFormData.append(
        'resultados',
        JSON.stringify(this.$store.getters.getPaso),
      )
      InstFormData.append('idTramite', this.$store.getters.idTramite)
      InstFormData.append('idPaso', this.$store.getters.idPaso)
      InstFormData.append('cuit', Cookies.get('vecino_cuit'))
      InstFormData.append(
        'cuitrepresentado',
        this.$store.getters.cuitrepresentado,
      )
      this.formulario = (
        await axios.post('/Paso/savePaso', InstFormData, {
          headers: {
            'Content-Type': 'multipart/form-data',
          },
        })((this.inicio = false))
      ).data
    },
  },
}
</script>
<style src="vue-multiselect/dist/vue-multiselect.css"></style>
