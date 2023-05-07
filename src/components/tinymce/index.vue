<template>
  <section id="textarea">Tinymce Editor</section>
</template>

<script>
import tinymce from "../tinymce/tinymce.min.js";
import "./themes/silver/theme.min.js";
import "./models/dom/model.min.js";
import "./icons/default/icons.min.js";
import "./langs/zh-Hans.js";
import './skins/content/default/content.min.css'
import './skins/ui/oxide/skin.min.css'

import './plugins/preview/plugin.min.js'
export default {
  props: {
    value: {
      type: String,
      default: '',
    }
  },
  mounted() {
    tinymce.init({
      selector: '#textarea',  // change this value according to your HTML
      language: 'zh-Hans',
      plugin: 'a_tinymce_plugin',
      a_plugin_option: true,
      a_configuration_option: 400,
      // 菜单栏
      menubar: 'bar1 bar2',
      menu: {
        bar1: { title: '菜单栏1', items: 'copy paste' },
        bar2: { title: '菜单栏2', items: 'cut preview' }
      },
      // 工具栏
      toolbar: 'undo redo preview',
      // 插件
      plugins: 'preview',
      // 监听 初始化完成事件
      setup: (editor) => {
        editor.on('init', (e) => {
          editor.setContent(this.value);
        });
      },
      init_instance_callback: (editor) => {
        editor.on('input', (e) => {
          this.$emit('input', e.target.innerHTML);
        });
        editor.on('change', (e) => {
          this.$emit('input', e.level.content);
        });
      }
    });
  }
}
</script>

<style>
@import url('./skins/ui/oxide/skin.min.css');
</style>