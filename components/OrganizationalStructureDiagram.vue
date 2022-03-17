<template>
  <div class="row">
    <div class="card w-100 shadow mb-4">
      <div class="card-header py-3">
        <div
          class="m-0 font-weight-bold text-primary d-flex justify-content-between align-items-center"
        >Бизнес процесс</div>
      </div>
      <div class="card-body">
        <vue-tree
          style="width: 100%; height: 600px;"
          :dataset="treeData"
          :config="treeConfig"
          linkStyle="straight"
        >
          <template v-slot:node="{ node, collapsed }">
            <div class="rich-media-node" :style="{ border: collapsed ? '2px solid grey' : '' }">
              <!-- <img :src="node.avatar" style="width: 48px; height: 48px; border-raduis: 4px;" /> -->
              <span style="padding: 4px 0; font-weight: bold;">{{ node.name }}</span>
            </div>
          </template>
        </vue-tree>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  ssr: false,
  components: {
    VueTree: () => import('@ssthouse/vue-tree-chart'),
  },
  props: {
    treeData: {
      default: () => {},
    },
  },
  name: 'treemap',
  data() {
    return {
      richMediaData: {
        name: 'James',
        value: 800,
        avatar:
          'https://gravatar.com/avatar/db51fdaf64d942180b5200ca37d155a4?s=400&d=robohash&r=x',
        children: [
          {
            name: 'Bob',
            value: 400,
            avatar:
              'https://gravatar.com/avatar/16b3b886b837257757c5961513396a06?s=400&d=robohash&r=x',
            children: [
              {
                name: 'C1',
                value: 100,
                avatar:
                  'https://gravatar.com/avatar/4ee8775f23f12755db978cccdc1356d9?s=400&d=robohash&r=x',
              },
              {
                name: 'C2',
                value: 300,
                avatar:
                  'https://gravatar.com/avatar/d3efa8fa639bdada96a7d0b4372e0a96?s=400&d=robohash&r=x',
              },
              {
                name: 'C3',
                value: 200,
                avatar:
                  'https://gravatar.com/avatar/4905bc3e5dc51a61e3b490ccf1891107?s=400&d=robohash&r=x',
              },
            ],
          },
          {
            name: 'Smith',
            value: 200,
            avatar:
              'https://gravatar.com/avatar/d05d081dbbb513180025300b715d5656?s=400&d=robohash&r=x',
            children: [
              {
                name: 'S1',
                value: 230,
                avatar:
                  'https://gravatar.com/avatar/60c1e69e690d943c5dc06568148debc4?s=400&d=robohash&r=x',
              },
            ],
          },
          {
            name: 'Jackson',
            value: 300,
            avatar:
              'https://gravatar.com/avatar/581f7a711c815d9671c35ebd815ec1e4?s=400&d=robohash&r=x',
          },
        ],
      },
      treeConfig: {
        nodeWidth: 150,
        nodeHeight: 80,
        levelHeight: 200,
      },
    }
  },
}
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.rich-media-node {
  width: 120px;
  padding: 8px;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
  color: white;
  background-color: #f7c616;
  border-radius: 4px;
}
</style>