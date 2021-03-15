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
        v-model="teams[index]"
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
      let order = [];
      let target = this.teams;

      console.log(this.teams.length);

      for (let index = 0; index < this.teams.length; index++) {
        const num = Math.floor( Math.random() * (this.teams.length - index - 1) );
        console.log(num);
        order.push(target[num]);
        target = target.filter(n => n !== num);
      }

      this.teams = order;
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
