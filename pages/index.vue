<template>
  <div class="p-4">
    <div class="max-w-sm rounded overflow-hidden shadow-lg mb-4 w-screen">
      <img
        class="w-full"
        src="https://cdn.jsdelivr.net/gh/geehon/blogImgBed/img/card-top.jpg"
        alt="Sunset in the mountains"
      />
      <div class="px-6 py-4 pb-2">
        <div class="font-bold text-xl mb-1 text-gray-700">服务资费详情</div>
        <div class="flex flex-col py-1 text-gray-500 text-sm font-sans font-semibold">
          <div class="flex flex-row ">
            <p>余额: {{ -account.balance }} $</p>
          </div>
          <div class="flex flex-row py-1">
            <p>未结: {{ account.pending_charges }} $</p>
          </div>
          <div class="flex flex-row">
            <p>最后充值: {{ -account.last_payment_amount }} $</p>
          </div>
        </div>
      </div>

      <div class="px-6 pb-4 text-gray-500 text-xs">
        <span>更新于：{{ (new Date()).toLocaleString('en-GB') }}</span>
      </div>
    </div>
  </div>
</template>

<style lang="postcss" scoped>
</style>
<script>
export default {
  async asyncData({ $axios }) {
    const { account } = await $axios.$get("https://blog.geehon.top/api/v0/monitor");
    // console.log()
    return { account };
  },
  methods: {},
  data() {
    return { };
  },

  head(){
    return{
      title:'服务资费'
    }
  }
};
</script>