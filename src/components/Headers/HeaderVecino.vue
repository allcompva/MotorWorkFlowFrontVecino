<template v-if="NombreFormateado != null && NombreFormateado != 'undefined'">
  <CHeader position="sticky" class="mb-4 headermuni">
    <CContainer style="padding-left: 25px">
      <CRow style="width: 100%">
        <template v-if="pantalla > 768">
          <CCol xs="4">
            <CHeaderBrand class="mx-auto" to="/">
              <a type="button" @click="redireccionar">
                <img src="../../assets/logo.png" alt="" style="height: 60px" />
              </a>
            </CHeaderBrand>
          </CCol>
          <CCol xs="4" style="text-align: center">
            <h2 style="font-size: 28px; font-weight: bold; color: dimgray">
              E-Tramites
            </h2>
          </CCol>
          <CCol
            xs="4"
            style="
              text-align: right;
              background-color: #2d353a;
              padding: 5px;
              border-top-left-radius: 10px;
              border-bottom-left-radius: 10px;
              right: 0;
              position: fixed;
            "
          >
            <CHeaderNav style="display: inline-flex">
              <span
                class="fa fa-envelope"
                style="
                  color: white;
                  align-items: center;
                  display: flex;
                  font-size: 24px;
                  margin-right: 25px;
                "
              ></span>
              <CDropdown>
                <CDropdownToggle
                  style="background-color: transparent; color: white"
                >
                  <img
                    :src="foto"
                    alt="foto"
                    style="
                      height: 40px;
                      border-radius: 50%;
                      width: 50px;
                      display: inline;
                    "
                  /><P
                    style="
                      color: white;
                      align-items: center;
                      display: inline;
                      padding-right: 25px;
                      padding-left: 10px;
                      font-weight: bold;
                      text-align: left;
                    "
                    >{{ NombreFormateado }}</P
                  ></CDropdownToggle
                >
                <CDropdownMenu>
                  <CDropdownItem @click="cerrarsesion"
                    >Cerrar Sesion</CDropdownItem
                  >
                </CDropdownMenu>
              </CDropdown>
            </CHeaderNav>
          </CCol>
        </template>
        <template v-else>
          <CCol xs="6" style="padding: 15px">
            <CHeaderBrand class="mx-auto" to="/">
              <a type="button" @click="redireccionar">
                <img src="../../assets/Logo2.png" alt="" style="height: 60px" />
              </a>
            </CHeaderBrand>
          </CCol>
          <CCol
            xs="6"
            style="
              text-align: right;
              background-color: transparent;
              padding: 15px;
              right: 0;
            "
          >
            <CHeaderNav style="display: inline-flex">
              <span
                class="fa fa-envelope"
                style="
                  color: white;
                  align-items: center;
                  display: flex;
                  font-size: 24px;
                  margin-right: 25px;
                "
              ></span>
              <CDropdown>
                <CDropdownToggle
                  style="
                    background-color: transparent;
                    color: white;
                    box-shadow: none;
                  "
                >
                  <img
                    :src="foto"
                    alt="foto"
                    style="height: 40px; border-radius: 50%; width: 50px"
                /></CDropdownToggle>
                <CDropdownMenu style="z-index: 200">
                  <CDropdownItem
                    @click="cerrarsesion"
                    style="background-color: white"
                    >Cerrar Sesion</CDropdownItem
                  >
                </CDropdownMenu>
              </CDropdown>
            </CHeaderNav>
          </CCol>
        </template>
      </CRow>
    </CContainer>
  </CHeader>
</template>
<style>
.headermuni {
  background: rgb(248, 249, 250);
  padding-right: 0;
  height: 100px;
  background: linear-gradient(
    0deg,
    rgba(248, 249, 250, 1) 0%,
    rgba(218, 219, 219, 1) 100%
  );
}
</style>
<script>
import Cookies from 'js-cookie'
import axios from 'axios'
export default {
  inject: ['mq'],
  name: 'AppHeader',
  components: {},
  data: () => ({
    NombreFormateado: '',
    foto: '',
    pantalla: 0,
  }),
  mounted() {
    this.NombreFormateado = Cookies.get('vecino_nombreFormateado')
    axios
      .get(
        '/Usuarios/TraerFotoPerfil?Hash=' +
          Cookies.get('hash') +
          '&cuit=' +
          Cookies.get('vecino_cuit'),
      )
      .then((response) => (this.foto = response.data))
      .catch((this.labelError = true))
    this.pantalla = window.innerWidth
  },
  methods: {
    redireccionar() {
      if (
        document.cookie
          .split(';')
          .some((item) => item.trim().startsWith('hash'))
      ) {
        this.$router.push('/ListaTramites/' + Cookies.get('hash'))
      }
    },
    cerrarsesion() {
      Cookies.remove('vecino_cuit')
      Cookies.remove('vecino_cuitRepresentado')
      Cookies.remove('vecino_cuitFormateado')
      Cookies.remove('vecino_nombreFormateado')
      Cookies.remove('hash')
      this.$router.push('/LogIn')
    },
  },
}
</script>
