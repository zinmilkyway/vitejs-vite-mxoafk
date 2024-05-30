<template>
  <div class="doc-container">
    <section class="sec mid">
      <a-typography-title :level="3">代码演示</a-typography-title>
      <a-row :gutter="16" class="demo-boxes">
        <a-col :span="12">
          <demo-box
            id="base-demo"
            title="基本用法"
            desc="展开、选中、禁用的基本功能"
            code-type="base"
            href="//github.com/lycHub/ysx-library/blob/master/projects/demo/src/doc/BaseDemo.vue"
          >
            <base-demo />
          </demo-box>
          <demo-box
            id="async-dada-demo"
            title="异步加载数据"
            desc="点击展开节点，动态加载数据。"
            code-type="asyncData"
            href="//github.com/lycHub/ysx-library/blob/master/projects/demo/src/doc/AsyncDataDemo.vue"
          >
            <async-data-demo />
          </demo-box>
          <demo-box
            id="custom-icon-demo"
            title="自定义图标"
            desc="自定义展开、收起图标"
            code-type="customIcon"
            href="//github.com/lycHub/ysx-library/blob/master/projects/demo/src/doc/CustomIconDemo.vue"
          >
            <custom-icon-demo />
          </demo-box>
          <demo-box
            id="search-demo"
            title="搜索树"
            desc="自行实现搜索功能"
            code-type="search"
            href="//github.com/lycHub/ysx-library/blob/master/projects/demo/src/doc/SearchDemo.vue"
            online="//stackblitz.com/edit/vitejs-vite-1j17xa?file=src/doc/SearchDemo.vue"
          >
            <search-demo />
          </demo-box>
        </a-col>
        <a-col :span="12">
          <demo-box
            id="checkbox-demo"
            title="可勾选"
            desc="showCheckbox属性开启勾选，默认父子节点联动，设置checkStrictly属性，可让父子节点不做联动"
            code-type="checkbox"
            href="//github.com/lycHub/ysx-library/blob/master/projects/demo/src/doc/CheckboxDemo.vue"
          >
            <checkbox-demo />
          </demo-box>
          <demo-box
            id="custom-node-demo"
            title="自定义渲染节点"
            desc="绑定render函数或使用slot自定义节点，参数data为当前node数据。注意：如果改变了默认的高度(size), 需要传入size属性"
            code-type="customNode"
            href="//github.com/lycHub/ysx-library/blob/master/projects/demo/src/doc/CustomNodeDemo.vue"
          >
            <custom-node-demo />
          </demo-box>
          <demo-box
            id="virtual-demo"
            title="虚拟树"
            desc="传入 props.virtual 使用虚拟tree，高度为 size * remain"
            code-type="customNode"
            href="//github.com/lycHub/ysx-library/blob/master/projects/demo/src/doc/VirtualDemo.vue"
          >
            <virtual-demo />
          </demo-box>
        </a-col>
      </a-row>
    </section>
  </div>
</template>

<script lang="tsx">
import {defineComponent} from 'vue';
import DemoBox from './DemoBox.vue';
import BaseDemo from './BaseDemo.vue';
import CheckboxDemo from './CheckboxDemo.vue';
import AsyncDataDemo from './AsyncDataDemo.vue';
import CustomNodeDemo from './CustomNodeDemo.vue';
import CustomIconDemo from './CustomIconDemo.vue';
import VirtualDemo from './VirtualDemo.vue';
import SearchDemo from './SearchDemo.vue';

export default defineComponent({
  name: 'DocContainer',
  components: { DemoBox, BaseDemo, CheckboxDemo, AsyncDataDemo, CustomNodeDemo, CustomIconDemo, VirtualDemo, SearchDemo },
  setup() {
    const rowClsName = (_: any, index: number) => ([5, 6, 7, 8].includes(index) ? 'table-row-abandoned' : null);

    return {
      rowClsName
    }
  }
});
</script>

<style scoped>
.doc-container {
  width: 1300px;
  margin: 0 auto;
  padding: 30px 20px;
  border: 1px solid var(--border-color);
}

.doc-container .sec {
  margin-bottom: 10px;
}

.doc-container .sec.mid {
  margin: 10px 0;
}

.doc-container .sec h3 {
  font-size: var(--font-size-huge);
}
</style>
