<script>
	import { defineComponent } from "vue";
	import { VPdfViewer, VPVBaseProps } from "@vue-pdf-viewer/viewer";
	export default defineComponent({
		components: { VPdfViewer },
		props: {
			...VPVBaseProps,
			title: {
				type: String,
			},
		},
		data() {
			return {};
		},
		watch: {
			"$refs.pdfViewer": {
				handler(v) {
					console.log("These are VPV instance properties", Object.keys(v));
				},
				deep: true,
			},
		},
	});
</script>

<template>
	<div>
		<h2>
			{{ title }}
		</h2>
		<!-- If the license is validated, show the VPdfViewer component, so the watermark will be gone -->
		<div :style="{ height: '700px', margin: '0 auto' }">
			<VPdfViewer
				v-bind="$props"
				ref="pdfViewer" />
		</div>
	</div>
</template>
