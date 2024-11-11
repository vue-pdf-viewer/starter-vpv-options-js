<script>
	import { defineComponent } from "vue";
	import { VPdfViewer, VPVBaseProps, useLicense } from "@vue-pdf-viewer/viewer";
	export default defineComponent({
		components: { VPdfViewer },
		props: {
			...VPVBaseProps,
			title: {
				type: String,
			},
		},
		data() {
			return {
				// Initially, we assume the license is not validated
				isValidated: false,
				// License information will be stored here once the `useLicense` hook is called
				license: null,
			};
		},
		watch: {
			license(v) {
				// Watch the `license` data property
				// When `license` is updated, check if it contains a valid `licenseKey`
				if (v?.licenseKey) {
					// If the `licenseKey` is present, mark the license as validated, or you can add your logic
					this.isValidated = true;
				}
			},
		},
		beforeMount() {
			// Call the `useLicense` hook with the license key inside the `beforeMount` lifecycle hook
			const licenseKey = "your-license-key";

			// This calls `useLicense` which typically returns an object with license data
			const res = useLicense({ licenseKey });
			// // Assign the license data to the component's `license` property
			// // which will trigger the watcher when the data is updated which you can log to see how it looks like
			this.license = res.license;
		},
	});
</script>

<template>
	<div>
		<h2>
			{{ title }}
		</h2>
		<!-- If the license is validated, show the VPdfViewer component, so the watermark will be gone -->
		<div :style="{ width: '1028px', height: '700px', margin: '0 auto' }">
			<VPdfViewer v-bind="$props" />
		</div>
	</div>
</template>
