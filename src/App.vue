<template>
  <div class="container">
    <div class="col-md-6 col-md-offset-3">
      <h3>Directive Sınavı</h3>
      <!-- Soru -->
      <!-- Event'leri dinleyecek v-on gibi çalışan bir Directive geliştiriniz. -->
      <div class="box mr-5 col-md-2" v-custom-on-event:click="getMessage">Click</div>
      <div class="box mr-5 col-md-2" v-custom-on-event:mousemove="getMessage">Mousemove</div>
      <div class="box mr-5 col-md-2" v-custom-on-event:mousedown="getMessage">Mousedown</div>
      <div class="box mr-5 col-md-2" v-custom-on-event:mouseout="getMessage">Mouseout</div>
      <div class="box mr-5 col-md-2" v-custom-on-event:mouseover="getMessage">Mouseover</div>
      <input
        class="box mr-5 col-md-2"
        type="text"
        v-custom-on-event:keypress="getMessage"
        placeholder="Keypress"
      />
      <input
        class="box mr-5 col-md-2"
        type="text"
        v-custom-on-event:keydown="getMessage"
        placeholder="Keydown"
      />
      <input
        class="box mr-5 col-md-2"
        type="text"
        v-custom-on-event:keyup="getMessage"
        placeholder="Keyup"
      />
    </div>
  </div>
</template>

<script>
export default {
  directives: {
    customOnEvent: {
      bind(el, binding) {
        const eventType = binding.arg;
        const functionName = binding.value;

        el.addEventListener(eventType, functionName);
      }
    }
  },
  methods: {
    getMessage() {
      alert("Hello Custom Directive!");
    }
  }
};
</script>

<style>
.box {
  height: 100px;
  width: 100px;
  background: pink;
  margin-right: 10px;
  margin-bottom: 10px;
  line-height: 100px;
  text-align: center;
}
</style>
