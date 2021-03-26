<template>
	<markdown-renderer :markdown="markdown" />
	<pre ref="mdSource" style="display: none">
# Hello World

```mermaid
erDiagram
    Parent ||--o{ Child : has
```
</pre
	>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import MarkdownRenderer from "./components/markdown-renderer.vue";

export default defineComponent({
	name: "App",
	data: () => ({
		markdown: "",
	}),
	components: {
		MarkdownRenderer,
	},
	mounted() {
		this.markdown = this.$refs.mdSource.innerText;
	},
});
</script>
