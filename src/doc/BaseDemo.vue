<template>
  <a-button @click="selectedNode">获取选中节点</a-button>
  <VirTree
    ref="virTree"
    :source="list"
    :default-selected-key="defaultSelectedKey"
  />
</template>

<script setup lang="tsx">
import { TreeNodeOptions, VirTree, TreeContext } from '@ysx-libs/vue-virtual-tree';
const defaultNodeKey =[]
function recursion(path = '0', level = 3, h = 15): TreeNodeOptions[] {
    const list = [];
    for (let i = 0; i < h; i += 1) {
      const nodeKey = `${path}-${i}`;
      defaultNodeKey.push(nodeKey)
      const treeNode: TreeNodeOptions  = {
        nodeKey,
        name: nodeKey,
        children: [],
        extra: { a: 'a' }
      };

      if (level > 0) {
        treeNode.children = recursion(nodeKey, level - 1);
      }
      list.push(treeNode);
    }
    return list;
  }
  const list = $ref(recursion());
  const defaultSelectedKey = $ref('0-2');

  const virTree = $ref<TreeContext>();

  const selectedNode = () => {
    const node = virTree!.getSelectedNode();
    console.log('selected node', node);
  }
</script>
