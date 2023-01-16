<template>
  <form action="">
    <div class="input-item">
      <label for="protein">Protein</label>
      <input
        type="number"
        name="protein"
        id="protein"
        v-model="qualifNutrients.protein"
      />
    </div>
    <div class="input-item">
      <label for="fiber">Fiber</label>
      <input
        type="number"
        name="fiber"
        id="fiber"
        v-model="qualifNutrients.fiber"
      />
    </div>
    <div class="input-item">
      <label for="vitamC">Vitamin C</label>
      <input
        type="number"
        name="vitamC"
        id="vitamC"
        v-model="qualifNutrients.vitamC"
      />
    </div>
    <div class="input-item">
      <label for="calcium">Calcium</label>
      <input
        type="number"
        name="calcium"
        id="calcium"
        v-model="qualifNutrients.calcium"
      />
    </div>
    <div class="input-item">
      <label for="iron">Iron</label>
      <input
        type="number"
        name="iron"
        id="iron"
        v-model="qualifNutrients.iron"
      />
    </div>
    <div class="input-item">
      <label for="energyDensity">energyDensity</label>
      <input
        type="number"
        name="energyDensity"
        id="energyDensity"
        v-model="energyDensity"
      />
    </div>
    <p>------------------</p>
    <div class="input-item">
      <label for="saturedFattyAcids">saturedFattyAcids</label>
      <input
        type="number"
        name="saturedFattyAcids"
        id="saturedFattyAcids"
        v-model="desqualifNutrients.saturedFattyAcids"
      />
    </div>
    <div class="input-item">
      <label for="sugar">sugar</label>
      <input
        type="number"
        name="sugar"
        id="sugar"
        v-model="desqualifNutrients.sugar"
      />
    </div>
    <div class="input-item">
      <label for="sodium">sodium</label>
      <input
        type="number"
        name="sodium"
        id="sodium"
        v-model="desqualifNutrients.sodium"
      />
    </div>
    <input type="button" value="Calculate Product" />
  </form>
  <div>
    <p>Sain value: {{ sain }}</p>
    <p>Lim value: {{ lim }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      energyDensity: 0,
      qualifNutrients: {
        protein: 0,
        fiber: 0,
        vitamC: 0,
        calcium: 0,
        iron: 0,
      },
      desqualifNutrients: {
        saturedFattyAcids: 0,
        sugar: 0,
        sodium: 0,
      },
    };
  },
  computed: {
    sain() {
      const maxGoodValues = {
        protein: 65,
        fiber: 25,
        vitamC: 110,
        calcium: 900,
        iron: 12.5,
      };

      const kcal = this.energyDensity;
      return (
        ((((this.qualifNutrients.protein / maxGoodValues.protein +
          this.qualifNutrients.fiber / maxGoodValues.fiber +
          this.qualifNutrients.vitamC / maxGoodValues.vitamC +
          this.qualifNutrients.calcium / maxGoodValues.calcium +
          this.qualifNutrients.iron / maxGoodValues.iron) /
          2) *
          100) /
          kcal) *
        100
      );
    },
    lim() {
      const maxValues = {
        saturedFattyAcids: 22,
        sugar: 50,
        sodium: 3153,
      };
      return (
        ((this.desqualifNutrients.saturedFattyAcids /
          maxValues.saturedFattyAcids +
          this.desqualifNutrients.sugar / maxValues.sugar +
          this.desqualifNutrients.sodium / maxValues.sodium) /
          3) *
        100
      );
    },
  },
  methods: {
    calculate() {
      const maxGoodValues = {
        protein: 65,
        fiber: 25,
        vitamC: 110,
        calcium: 900,
        iron: 12.5,
      };

      const kcal = this.energyDensity;
      this.sain =
        ((((this.qualifNutrients.protein / maxGoodValues.protein +
          this.qualifNutrients.fiber / maxGoodValues.fiber +
          this.qualifNutrients.vitamC / maxGoodValues.vitamC +
          this.qualifNutrients.calcium / maxGoodValues.calcium +
          this.qualifNutrients.iron / maxGoodValues.iron) /
          2) *
          100) /
          kcal) *
        100;

      const maxValues = {
        saturedFattyAcids: 22,
        sugar: 50,
        sodium: 3153,
      };
      this.lim(
        ((this.desqualifNutrients.saturedFattyAcids /
          maxValues.saturedFattyAcids +
          this.desqualifNutrients.sugar / maxValues.sugar +
          this.desqualifNutrients.sodium / maxValues.sodium) /
          3) *
          100
      );
    },
  },
};
</script>

<style>
.input-item {
  display: flex;
  flex-direction: column;
  margin: 1rem;
}
</style>
