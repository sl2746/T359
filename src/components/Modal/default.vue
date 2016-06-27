<template>
  <layout :modaldata.sync="modaldata" :close.sync="close">
    <div class="default-tab" v-if="$route.path.replace('/','') != 'contracts' && $route.path.replace('/','') != 'literatures'">
      <ul class="btns f-cb">
        <li v-for="item in ['问题解答','参考案例','相关法规']"
            v-text="item"
            :class="[index === $index ? 'active' : '']"
            @click="change($index)"></li>
      </ul>
      <ul class="contents">
        <li v-show="index === 0">
            <div style="max-height:300px;overflow:auto;">
              <div v-html="(modaldata.content || modaldata.template || ' ') | marked">
              </div>
            </div>
        </li>
        <li v-show="index === 1">
            <div style="max-height:300px;overflow:auto;">
              <ul v-for="case1 in modaldata.relations.cases">
                <li>
                  <div v-text="case1.name" @click="showCase">
                  </div>
                  <fieldset v-html="(case1.content || ' ') | marked" v-show="false">
                  </fieldset>
                  </br>
                </li>
              </ul>
            </div>
        </li>
        <li v-show="index === 2">
            <div style="max-height:300px;overflow:auto;">
              <ul v-for="clause in modaldata.relations.clauses">
                <li>
                  <div v-text="clause.name" @click="showNode">
                  </div>
                  <fieldset v-html="(clause.content || ' ') | marked" v-show="false">
                  </fieldset>
                  </br>
                </li>
              </ul>
            </div>
        </li>
      </ul>
    </div>
    <div class="default-tab" v-else>
      <ul class="contents">
        <div style="max-height:300px;overflow:auto;">
          <div v-html="(modaldata.content || ' ') | marked">
          </div>
        </div>
      </ul>
    </div>
  </div>
  </layout>
</template>

<script>
  import marked from 'marked';
  import Layout from './layout.vue';

  export default {
    props: {
      close: Boolean,
      modaldata:Object
    },
    data() {
      return {
        index: 0
      }
    },
    filters: {
      marked: marked
    },
    methods: {
      change(index) {
        this.index = index
      },
      showNode(){
        let el = event.srcElement?event.srcElement:event.target,
            fieldset = el.parentNode.childNodes[3];
        fieldset.style.display = 'block';
      },
      showCase(){
        let el = event.srcElement?event.srcElement:event.target,
            fieldset = el.parentNode.childNodes[3];
        fieldset.style.display = 'block';
      }
    },
    components: {
      Layout
    }
  }
</script>

<style>
  @import '../../css/modal/index.css';
</style>
