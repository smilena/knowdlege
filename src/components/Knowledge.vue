<template>
  <div>
    <h1>Representación de información y conocimiento</h1>
    <h2>{{y}} = 4({{x}}) + 5</h2>
    <h3>Ingrese el valor de x </h3>
    <input v-model="x">
    <button v-on:click="click">Calcular</button>
    <h5>{{message}}</h5>
  </div>
</template>

<script>

import * as tf from '@tensorflow/tfjs';

export default {
  name: 'Knowdlege',
  data: function (){
    return {
      y: 'y',
      x: 'x',
      message: ''
    }
  },
  methods:{
    click:function(){
      this.message = 'Estoy aprendiendo...';
      this.y = 'y';
       this.getY();
    },

    getY:function() {
      const model = tf.sequential();
      model.add(tf.layers.dense({units: 1, inputShape: [1]}));
      model.compile({loss: 'meanSquaredError', optimizer: 'sgd'});

      const xs = tf.tensor(Array.from([-2.0, 0.0, 4.0, 1.0, 6.0, 5.0, 3.0, -3.0]));
      const ys = tf.tensor(Array.from([-3.0,5.0,21.0,9.0,29.0,25.0,17.0,-7.0]));

      model.fit(xs, ys, {epochs: 300}).then(() => {
        return (model.predict(tf.tensor([parseInt(this.x)])).data());
      }).then(tensor => {
        this.message = '';
        this.y = tensor[0];
        });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h2{
  font-size: 30px;
}
</style>
