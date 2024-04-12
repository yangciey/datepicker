<template>
  <div class="input">
    <el-input
      id="ipt"
      ref="iptRef"
      :suffix-icon="ri"
      v-model="state.sfsj"
      :style="{ width: 196 * mul + 'px', height: 32 * mul + 'px' }"
      @focus="focus"
      @blur="blur"
      ><!--placeholder="请输入事发单位"-->
    </el-input>
    <div
      class="datepop"
      v-if="state.tc"
      @mouseenter="mouseenter"
      @mouseleave="mouseleave"
      @click="click"
    >
      <Datepop @datetime="datetime" :date="state.sfsj"></Datepop>
    </div>
  </div>
</template>
<script setup>
import { dayjs } from "element-plus";
import ri from "@/views/main/assets/iconComponents/dateIcon.vue";
const iptRef = ref();
const otherStroe = useOtherStore();
const mul = otherStroe.mul;
const emit = defineEmits(["datetime"]);
const formData = inject("formData");
const props = defineProps({
  // 过来的值需要用深拷贝 JSON.parse(JSON.stringify(...))
  sfsj: {
    type: String,
    default: () => "",
  },
});
const state = reactive({
  tc: false,
  sfsj: "",
  click: {},
  flag: false,
  enter: false,
  in: 1,
});
const datetime = (v, i) => {
  state.sfsj = dayjs(v).format("YYYY-MM-DD HH:mm:ss");
  emit("datetime", state.sfsj);
  state.tc = i;
};
const focus = () => {
  state.tc = true;
  state.in = 1;
  console.log("<><><>", state.in, state.enter);
};
const mouseenter = () => {
  state.enter = true;
  state.in = 1;
};
const click = () => {
  iptRef.value.focus();
};
const mouseleave = () => {
  state.enter = false;
  state.in = 0;
};
const blur = () => {
  if (state.enter) {
    if (state.in == 1) {
      state.tc = true;
    } else {
      state.enter = false;
      state.tc = false;
    }
  } else {
    state.tc = false;
  }
};
onMounted(() => {});
watch(
  () => props.sfsj,
  () => {
    state.sfsj = props.sfsj;
  }
);
</script>
<style lang="scss" scoped>
.input {
  width: 178.25px;
  height: 32px;
  display: flex;
}
.datepop {
  width: 288px;
  max-height: 336px;
  padding: 20px 5px 9px 5px;
  top: 34px;
  left: 0px;
  position: absolute;
  z-index: 4;
  background: #ffffff;
  border: 1px solid #d6d6d6;
  box-shadow: 0px 3px 6px 0px rgba(0, 0, 0, 0.35);
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
