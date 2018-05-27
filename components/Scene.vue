<template>
    <div ref="scene" id="container">
      
    </div>
    
</template>
<script lang="ts">
import {
  Component, 
  Prop,
  Vue
} from "nuxt-property-decorator"


import axios, { AxiosResponse } from 'axios'
import * as THREE from 'three'


@Component({})
export default class Scene extends Vue {

  private _name: string; 

  private camera: THREE.PerspectiveCamera; 
	private scene: THREE.Scene;
	private renderer: THREE.WebGLRenderer;
  private mesh: THREE.Mesh; 
  private geometry: THREE.BoxGeometry; 
  private material: THREE.MeshNormalMaterial;
  private container: HTMLCanvasElement;
  private te: HTMLCanvasElement;

  $refs: Vue["$refs"] & {
    scene: HTMLCanvasElement,
    num: string
  }

  constructor () {
    super();
    this._name = "World"; 
    
    this.$refs.num = 'Test';     
  }
  private init() {
      this.container = this.$refs.scene;

      this.camera = new THREE.PerspectiveCamera(70, this.container.clientWidth/this.container.clientHeight, 0.01, 10);
      this.camera.position.z = 1;

      this.scene = new THREE.Scene();

      this.geometry = new THREE.BoxGeometry(0.2, 0.2, 0.2);
      this.material = new THREE.MeshNormalMaterial();

      this.mesh = new THREE.Mesh(this.geometry, this.material);
      this.scene.add(this.mesh); 

      this.renderer = new THREE.WebGLRenderer({antialias: true});
      this.renderer.setSize(this.container.clientWidth, this.container.clientHeight);
      this.container.appendChild(this.renderer.domElement);
    }
  private animate() {
      requestAnimationFrame(this.animate);
      this.mesh.rotation.x += 0.01;
      this.mesh.rotation.y += 0.02;
      this.renderer.render(this.scene, this.camera);
  }
  mounted () {
    console.log(this.$refs.scene ); 
    this.test();
    this.init();
		this.animate();
  }

  private test() {
      //console.log(this._name);
  };
  
  
}
</script>
<style scoped>

</style>
