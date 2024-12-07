<template>
    <v-container>
  <v-card
    :disabled="loading"
    :loading="loading"
    class="mx-auto my-12"
    max-width="374"
  >
    <template v-slot:loader="{ isActive }">
      <v-progress-linear
        :active="isActive"
        color="deep-purple"
        height="4"
        indeterminate
      ></v-progress-linear>
    </template>

    <v-img
      height="250"
      src="/burger.jpg"
      cover
    ></v-img>

    <v-card-item>
      <v-card-title>La Cocina de Alan</v-card-title>

      <v-card-subtitle>
        <span class="me-1">Local Favorite</span>

        <v-icon
          color="error"
          icon="mdi-fire-circle"
          size="small"
        ></v-icon>
      </v-card-subtitle>
    </v-card-item>

    <v-card-text>
      <v-row
        align="center"
        class="mx-0"
      >
        <v-rating
          :model-value="4.5"
          color="amber"
          density="compact"
          size="small"
          half-increments
          readonly
        ></v-rating>

        <div class="text-grey ms-4">
          4.3 (413) <span style="color: green; inline">+11.5%</span>
        </div>
      </v-row>

      <div class="my-4 text-subtitle-1">
        $$ • Argentino, Burgers
      </div>

      <v-card-text class="justify-center">
        <div style="background-color: #d4edda; padding: 6px; border-radius: 8px; text-align: center;">
            <span class="text-h6 font-weight-bold text-success">54 malas reviews evitadas</span>
        </div>
    </v-card-text>

      <div>Platos pequeños, ensaladas y sándwiches: un ambiente íntimo con 12 asientos en el interior y una terraza al aire libre.</div>
    </v-card-text>






    <v-card-actions>
      <v-btn
        color="blue"
        text="📍 Ver en Maps"
        block
        border
        @click="checkMaps"
      ></v-btn>
    </v-card-actions>

    <v-divider class="mx-4 mb-1"></v-divider>

    <v-card-title>Tus Camareros:</v-card-title>

    <v-chip-group
      class="pa-4 custom-active-class"
      multiple
      column
      
      v-model="selectedChips"

    >
        <v-chip value="1" color="blue">Azul • 54 reviews • 4.6★</v-chip>
        <v-chip value="2" color="red">Rojo • 34 reviews • 4.7★</v-chip>
        <v-chip value="3" color="green">Verde • 64 reviews • 3.8★</v-chip>
        <v-chip value="4" color="purple">Morao • 12 reviews • 4.5★</v-chip>
    </v-chip-group>

    <v-card-actions class="d-flex flex-row half">
      <v-btn
        color="purple"
        text="📈 Ver datos"
        block
        border
        @click="checkStatistics"
      ></v-btn>
      <v-btn
        color="blue"
        text="💬 Quejas"
        block
        border
        @click="checkQuejas"
      ></v-btn>
    </v-card-actions>

    <v-expand-transition>
        <div v-if="showData" class="pa-3">

            <v-divider></v-divider>
        <v-card-title class="text-h5 text-center">datos</v-card-title>
        <v-img
        src="/pie.png"
        alt="Encabezado"
        class="mb-3"
        cover
      ></v-img>
      <v-img
        src="/histogram.png"
        alt="Encabezado"
        class="mb-3"
        cover
      ></v-img>
        </div>

    </v-expand-transition>

      <v-expand-transition>
        <div v-if="showOpinions" class="pa-3">

        <v-divider></v-divider>
        <v-card-title class="text-h5 text-center">Opiniones</v-card-title>
        <v-card-text>
        <v-list>
            <v-list-item v-for="(opinion, index) in opiniones" :key="index">
                <v-list-item-content>
                <v-rating
                    v-model="opinion.estrellas"
                    color="amber"
                    background-color="grey lighten-2"
                    readonly
                ></v-rating>
                <p class="mt-2 text-wrap">
                    {{ opinion.texto }}
                </p>
                </v-list-item-content>
            </v-list-item>
            </v-list>
        </v-card-text>


        </div>
      </v-expand-transition>
  </v-card>
    </v-container>
  </template>
  
  <script>
export default {
    data: () => ({
      loading: false,
      selection: 1,
      selectedChips: ['1', '2', '3', '4'],
      showData: false,
      showOpinions: false,
      opiniones: [
        {
          estrellas: 3,
          texto: "El servicio fue aceptable, pero hubo varios inconvenientes que me impidieron disfrutarlo completamente.",
        },
        {
          estrellas: 2,
          texto: "La experiencia dejó mucho que desear. Hubo muchos problemas y no se resolvieron adecuadamente.",
        },
        {
          estrellas: 1,
          texto: "No estoy satisfecho. La calidad del servicio fue muy baja y no recomendaría este lugar a otros.",
        },
        {
            estrellas: 3,
            texto: "El servicio fue mediocre, esperaba más por el precio pagado. Hay áreas que necesitan mejorar urgentemente.",
        },
        {
            estrellas: 2,
            texto: "La comunicación fue muy lenta y confusa, y al final no cumplieron con lo prometido. No volveré a usar este servicio.",
        },
        {
            estrellas: 1,
            texto: "Totalmente decepcionante. Nada salió como se planeó y el personal no fue de ayuda en absoluto.",
        },
        {
            estrellas: 3,
            texto: "Podría haber sido mejor. Algunos aspectos fueron buenos, pero otros dejaron una mala impresión general.",
        },
        {
            estrellas: 2,
            texto: "Los tiempos de espera fueron demasiado largos y el producto final no cumplió con mis expectativas.",
        }
      ],

    }),

    methods: {
      checkMaps () {
        this.loading = true

        setTimeout(() => (this.loading = false), 2000)
      },
      checkQuejas() {
        this.showOpinions = true
        this.showData = false
      },
      checkStatistics() {
        this.showData = true
        this.showOpinions = false
      }
    },
  }
  </script>
  
<style scoped>

.no-checkmark .v-chip__filter {
  display: none !important;
}
.half {
  max-width: 50%!important;
}

</style>