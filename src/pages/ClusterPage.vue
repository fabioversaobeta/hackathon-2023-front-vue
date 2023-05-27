<template>
  <!-- Example split danger button -->
  <div class="content">
    <HeaderComponent />
    <hr />
    <div>
      <b-dropdown id="dropdown-1" text="Clusters" class="m-md-2">
        <b-dropdown-item v-for="cluster in clusters" :key="cluster.title" @click="handleSelectCluster(cluster)">
          {{ cluster.title }}
        </b-dropdown-item>
      </b-dropdown>
    </div>

    <div class="card w900">
      <div class="card-body w900">
        <b-badge v-show="kibanaLink" variant="dark" class="kibana-link">
          <a :href="kibanaLink" target="_blank">Kibana Link</a>
        </b-badge>
        <hr />
        <pre>{{ requestBody }}</pre>
      </div>
    </div>
  </div>
</template>

<script>
  import HeaderComponent from '@/components/HeaderComponent.vue';

  export default {
    name: "ClusterPage",
    components: {
      HeaderComponent
    },
    data() {
      return {
          responseData: null,
          clusters: [],
          variants: [],
          selectedCluster: {},
          kibanaLink: '',
          isOutline: false,
          requestBody: {}
      };
    },
    mounted() {
      const amazon = 'https://r0zeh4svk7.execute-api.us-west-1.amazonaws.com/prod';
        this.axios.get(amazon)
          .then(response => {
            const responseData = response.data;
            this.requestBody = responseData;
            const clusters = Object.values(responseData.clusters);

            if (clusters.length > 0) {
                this.autoSelectClusters(clusters);
                this.autoSelectCluster(clusters[0]);
            }
          })
            .catch(error => {
            console.error(error);
          });
    },
    methods: {
        autoSelectClusters(clusters) {
          this.clusters = clusters;
        },
        autoSelectCluster(cluster) {
          this.selectCluster(cluster);
        },
        handleSelectCluster(cluster) {
          this.selectCluster(cluster);
        },
        selectCluster(cluster) {
          this.kibanaLink = cluster.kibana_url;
          this.isOutline = cluster.title === 'Cluster -1';
          this.selectedCluster = cluster;
          this.requestBody = cluster;
          delete(this.requestBody.kibana_url);
        }
    }
}
</script>

<style>
  .content {
    width: 100%;
    overflow-wrap: break-word;
  }
  .card {
    background-color: white;
    margin-top: 20px;
    margin-right: 40px;
    overflow-wrap: break-word;
  }
  .card-body {
    overflow-wrap: break-word;
  }
  .w900 {
    width: 100%;
  }
  .kibana-link a, .kibana-link a:hover {
    color: white;
  }
</style>
