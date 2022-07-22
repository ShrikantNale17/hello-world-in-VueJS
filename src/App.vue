<template>
  <div id="app">
    <div>{{ greet }} {{ user }}</div>
    <div v-text="channel"></div>
    <div v-html="hack"></div>
    <h3 :id="headingId">Vue JS</h3>
    <button :disabled="isDisabled">Click me!</button>
    <h2 class="underline">Underline text</h2>
    <h2 class="underline" :class="status">Status</h2>
    <h2 :class="isPromoted && 'promoted'">Promoted Movie</h2>
    <h2 :class="!isSoldout ? 'sold-out' : 'new'">Soldout? movie</h2>
    <h2 :class="['new', 'promoted']">Newly promoted movie</h2>
    <h2 :class="[isPromoted && 'promoted', isSoldout ? 'sold-out' : 'new']">
      Array conditional movie
    </h2>
    <h2
      :class="{
        promoted: isPromoted,
        new: !isSoldout,
        'sold-out': isSoldout,
      }"
    >
      Object conditional movie
    </h2>
    <h2
      :style="{
        color: highlightcolor,
        fontSize: headersize + 'px',
        padding: '20px',
      }"
    >
      Inline style
    </h2>
    <h2 :style="headerStyleObject">Style Object</h2>
    <div :style="[baseStyleObject, successStyleObject]">Success Style</div>
    <div :style="[baseStyleObject, dangerStyleObject]">Danger Style</div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      greet: "Hello",
      user: "Shrikant",
      channel: "Codevolution",
      hack: '<a href="#" onclick="alert(`You have been hacked!`)">Win a prize!</a>',
      headingId: "Id",
      isDisabled: true,
      status: "danger",
      isPromoted: true,
      isSoldout: true,
      highlightcolor: "orange",
      headersize: 50,
      headerStyleObject: {
        color: "orange",
        fontSize: "50px",
        padding: "20px",
      },
      baseStyleObject: {
        fontSize: "50px",
        padding: "10px",
      },
      successStyleObject: {
        color: "green",
        backgroundColor: "lightgreen",
        border: "1px solid green",
        padding: "20px",
      },
      dangerStyleObject: {
        color: "darkred",
        backgroundColor: "red",
        border: "1px solid darkred",
      },
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.underline {
  text-decoration: underline;
}

.promoted {
  font-style: italic;
}

.sold-out {
  color: red;
}

.new {
  color: olivedrab;
}
</style>
