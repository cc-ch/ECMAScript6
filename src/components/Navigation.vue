<template>
    <div :class="$style.navigation">
        <ul>
           <li v-for="(item, i) in allNavList" v-bind:key="i" :class="{ [$style.active]: i === active}" @click="selectActive(i)">
               {{item.title}}
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: "navigation",
        methods: {
            selectActive(i) {
                console.log(i);
                this.$store.commit("updateActive", i);
                this.$store.commit("updateNavCode", i);
            }
        },
        created () {
        },
        data() {
            return {};
        },
        computed: {
            allNavList() {
                return this.$store.getters.availableNav;
            },
            active() {
                return this.$store.state.active;
            }
        }
    }
</script>

<style module>
.navigation {
  width: 240px;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  border: solid 1px var(--gray);
  overflow: scroll;
} 
.navigation ul {
  margin: 0;
  padding: 0;
}

.navigation ul li {
  width: 100%;
  font-size: 14px;
  font-weight: normal;
  padding: 12px 6px 12px 15px;
  cursor: pointer;
  position: relative;
  /* border-bottom: solid 1px var(--gray); */
}
.navigation ul li.active {
    background-color: rgb(230, 247, 255);
    box-sizing: border-box;
    color: rgb(24, 144, 255);
}
.navigation ul li.active::after {
    position: absolute;
    height: 44px;
    width: 2px;
    background: #409eff;
    content: '';
    top: 0;
    right: 0;
}

</style>