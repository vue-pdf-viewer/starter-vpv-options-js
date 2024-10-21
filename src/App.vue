<script>
  import AppPdfViewer from "./components/AppPdfViewer.vue";
  export default {
    components: { AppPdfViewer },
    data() {
      const toolbarOptions = false
      return {
        pdfSrc: 'https://raw.githubusercontent.com/mozilla/pdf.js/ba2edeae/web/compressed.tracemonkey-pldi-09.pdf',
        toolbarOptions
      }
    }
  }
</script>

<template>
  <div>
    <h1>VPV Starter Toolkit: Vue + Options API</h1>
    <br />
    <h2>Default Toolbar</h2>
    <div class="pdf-viewer-wrapper">
      <AppPdfViewer :src="pdfSrc" />
    </div>
    <h2>Without Toolbar</h2>
    <div class="pdf-viewer-wrapper">
      <AppPdfViewer :src="pdfSrc" :toolbar-options="toolbarOptions" />
    </div>
    <h2>Mobile</h2>
    <div class="pdf-viewer-wrapper-mobile">
      <AppPdfViewer :src="pdfSrc" />
    </div>
    <AppPdfViewer :src="pdfSrc" title="Shared Component" />
  </div>
</template>

<style scoped>
  .pdf-viewer-wrapper {
    width: 1028px;
    height: 700px;
    margin: 0 auto;
  }

  .pdf-viewer-wrapper-mobile {
    width: 600px;
    height: 700px;
    margin: 0 auto;
  }
</style>
