<template>
  <demo-block :title="t('basicUsage')">
    <van-rate v-model="value1" />
  </demo-block>

  <demo-block :title="t('customIcon')">
    <van-rate v-model="value2" icon="like" void-icon="like-o" />
  </demo-block>

  <demo-block :title="t('customStyle')">
    <van-rate
      v-model="value3"
      :size="25"
      color="#ffd21e"
      void-icon="star"
      void-color="#eee"
    />
  </demo-block>

  <demo-block :title="t('halfStar')">
    <van-rate v-model="value4" allow-half />
  </demo-block>

  <demo-block :title="t('customCount')">
    <van-rate v-model="value5" :count="6" />
  </demo-block>

  <demo-block :title="t('disabled')">
    <van-rate v-model="value6" disabled />
  </demo-block>

  <demo-block :title="t('readonly')">
    <van-rate v-model="value6" readonly />
  </demo-block>

  <demo-block :title="t('readonlyHalfStar')">
    <van-rate v-model="value7" readonly allow-half />
  </demo-block>

  <demo-block v-if="!isWeapp" :title="t('changeEvent')">
    <van-rate v-model="value8" @change="onChange" />
  </demo-block>
</template>

<script lang="ts">
import { toRefs, reactive } from 'vue';
import { useTranslate } from '@demo/use-translate';
import { Toast } from '../../toast';

const i18n = {
  'zh-CN': {
    halfStar: '半星',
    disabled: '禁用状态',
    customIcon: '自定义图标',
    customStyle: '自定义样式',
    customCount: '自定义数量',
    readonly: '只读状态',
    readonlyHalfStar: '只读状态小数显示',
    changeEvent: '监听 change 事件',
    toastContent: (value: number) => `当前值：${value}`,
  },
  'en-US': {
    halfStar: 'Half Star',
    disabled: 'Disabled',
    customIcon: 'Custom Icon',
    customStyle: 'Custom Style',
    customCount: 'Custom Count',
    readonly: 'Readonly',
    readonlyHalfStar: 'Readonly Half Star',
    changeEvent: 'Change Event',
    toastContent: (value: number) => `current value：${value}`,
  },
};

export default {
  setup() {
    const t = useTranslate(i18n);
    const state = reactive({
      value1: 3,
      value2: 3,
      value3: 3,
      value4: 2.5,
      value5: 4,
      value6: 3,
      value7: 3.3,
      value8: 2,
    });

    const onChange = (value: number) => Toast(t('toastContent', value));

    return {
      ...toRefs(state),
      t,
      onChange,
    };
  },
};
</script>

<style lang="less">
@import '../../style/var';

.demo-rate {
  padding-bottom: 20px;
  background-color: #fff;

  .van-rate {
    margin-left: @padding-md;
  }
}
</style>
