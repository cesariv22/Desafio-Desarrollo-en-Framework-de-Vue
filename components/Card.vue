<template>
  <div>
      <b-card class="text-center display-4">Elenco Rick and Morty</b-card>
    <b-container>
      <b-row>
        <b-col
          v-for="personaje in cardPersonajes"
          :key="personaje.id"
          cols="12"
          md="4"
        >
          <b-card
            bg-variant="dark"
            text-variant="white"
            :title="personaje.name" 
            :img-src="personaje.image"
            :img-alt="personaje.name"
            img-top
            tag="article"
            style="max-width: 20rem"
            class="mb-2 card-element"
          >
          </b-card>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  name: 'CardNuxt',
  data() {
    return {
      cardPersonajes: [],
    }
  },
  created() {
    this.getData()
  },
  methods: {
    async getData() {
      try {
        const req = await fetch('https://rickandmortyapi.com/api/character')
        const data = await req.json()
        this.cardPersonajes = data.results
      } catch (error) {
        error(error)
      }
    },
  },
}
</script>

<style>
.card-element {
    min-height: 21.5rem;

}
</style>
