<template>
  <div class="hello">
    <label>
      チーム数：
      <input
        type="number"
        value="2"
        min="2"
        v-model="team_num">
    </label>
    <label
      v-for="index in Number(team_num)"
      :key="index">
      {{ index }} :
      <input
        v-model="teams[index - 1]"
        type="text">
    </label>
    <button
      @click="plus()">
      +
    </button>
    <button
      @click="shuffle()">
      shuffle
    </button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      teams: [],
      team_num: 2
    }
  },
  methods: {
    shuffle () {

      console.log('チーム数：' + this.teams.length);
      for (let i = 0; i < this.teams.length; i++) {
        const r = Math.floor(Math.random() % (i + 1));
        const tmp = this.teams[i];
        this.$set(this.teams, i, this.teams[r]);
        this.$set(this.teams, r, tmp);
      }
      console.log(this.teams);
    },
    plus () {
      this.team_num++;
    }
  }
}
</script>

<style scoped>
  label {
    display: block;
    margin: 20px auto;
  }
</style>
