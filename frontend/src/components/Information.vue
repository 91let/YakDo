<template>
  <v-card style="padding:20px">
    <div id="list">
      <div>
        <h3>영업시간</h3>
        <div v-if="checkChips()" style="margin:2px;">
            <v-chip
                small
                label
                class="ma-1"
                color="secondary"
                text-color="white"
                v-for="category in (this.$store.state.data.pharmacy.p_status.split(','))"
                :key="category">
                {{category}}
            </v-chip>
            </div>
        🕛 {{ p_oper }}
      </div>
      <div v-if="p_tel.length">
        <h3>전화번호</h3>
        📞 {{ p_tel }}
        <a :href="`tel: + ${p_tel}`"
          ><v-btn small color="primary">전화걸기</v-btn></a
        >
      </div>
      <div v-if="p_special.length">
        <h3>특이사항</h3>
        {{ p_special }}
      </div>
    </div>
  </v-card>
</template>

<script>
export default {
    props: {
        p_tel : {
            type: String,
            default: () => "",
        },
        p_oper: {
            type: String,
            default: () => "",
        },
        p_special: {
            type: String,
            default: () => "",
        }
    },
    methods: {
        checkChips() {
            if(this.$store.state.data.pharmacy.p_status.length > 0) return true
            else false
        }
    },
}
</script>

<style>
#list div {
  margin: 30px;
}

@media screen and (min-width: 601px) {
  #list {
    font-size: 30px;
  }
}

@media screen and (max-width: 600px) {
  #list {
    font-size: 20px;
  }
}
</style>
