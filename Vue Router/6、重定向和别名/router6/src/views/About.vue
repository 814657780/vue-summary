<template>
  <div class="about">
    <h1>This is an about page</h1>
    <router-link :to="{name:'child1'}">go to child1</router-link></br>
    <router-link :to="{name:'child2'}">go to child2</router-link></br>
    <router-link :to="{name:'child3'}">go to child3</router-link></br>
    <router-link :to="{name:'child4'}">go to child4</router-link></br>
    <router-link :to="{name:'child5'}">go to child5</router-link></br>
    <router-link :to="{name:'child6'}">go to child6</router-link>
    <router-view></router-view>
  </div>
</template>
