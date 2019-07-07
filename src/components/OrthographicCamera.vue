<script>
import { OrthographicCamera } from 'three';
import Object3D from './Object3D'

export default {
  name: 'OrthographicCamera',
  mixins: [Object3D], // this throws an error
  inject: ['global'],
  props: {
    obj: Object,
  },
  data() {
    let curObj = this.obj;
    const { w, h } = this.global.rendererSize; // fixme
    if (!curObj) {
      curObj = new OrthographicCamera(-500, 500, 500, -500, 0.1, 1000);
    }
    curObj.name = curObj.name || curObj.type;
    return { curObj };
  },
  mounted() {
    this.global.camera = this.curObj;
  },
};
</script>