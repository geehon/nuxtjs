<template>
  <div class="p-4">
    <div class="max-w-sm rounded overflow-hidden shadow-lg mb-4 w-80">
      <img
        class="w-full"
        src="https://cdn.jsdelivr.net/gh/geehon/blogImgBed/img/card-top.jpg"
        alt="Sunset in the mountains"
      />
      <div class="px-6 py-4 pb-2">
        <div class="font-bold text-xl mb-1 text-gray-700">服务资费详情</div>
        <div class="flex flex-col py-1 text-gray-500 text-sm font-sans font-semibold">
          <div class="flex flex-row ">
            <p>可用: {{ -balance }}</p>
          </div>
          <div class="flex flex-row py-1">
            <p>未结: {{ -pending_charges }}</p>
          </div>
          <div class="flex flex-row">
            <p>余额: {{ computedBalance }}</p>
          </div>
        </div>
      </div>
      <div class="px-6 pb-4 text-gray-500 text-xs">
        <span>更新于：{{ updated_at }}</span>
      </div>
    </div>
  </div>
</template>

<style lang="postcss" scoped>
</style>
<script>
export default {
  async asyncData({ $axios }) {
    const { balance, pending_charges, updated_at } = await $axios.$get(
      "https://www.brownapp.tk/api/v1/vpsInfo"
    );
    return { balance, pending_charges, updated_at };
  },
  methods: {},
  data() {
    return {};
  },
  computed:{
    computedBalance:function(){
      return Math.floor((-this.balance-this.pending_charges) * 100) / 100;
    }
  },
  head() {
    return {
      title: "服务资费",
    };
  },
};
</script>