<template>
    <div></div>
</template>
  
<script>
import mitt from 'mitt'
import * as THREE from 'three';
  
  export default {
    data() {
      return {
        scene: null
      };
    },
    created() {
      // Listen for the scene-created event from GlobeVue
      const emitter = mitt()
        emitter.on('scene-created', (data) => {
            console.log("scene-created")
            this.scene = data.scene;
            this.addMarkers();
        });
    },
    methods: {
      addMarkers() {
        // Add markers to the scene
        const geometry = new THREE.SphereGeometry(0.1, 32, 32);
        const material = new THREE.MeshBasicMaterial({ color: 0xff0000 });
        const marker = new THREE.Mesh(geometry, material);
        this.scene.add(marker);
      }
    }
  };
  </script>