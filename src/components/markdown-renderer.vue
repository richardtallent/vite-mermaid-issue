<template>
	<div ref="mdel" v-html="renderedHtml" class="relative markdown richtext" />
</template>
<script lang="ts">
import { defineComponent } from "vue";
import MarkdownIt from "markdown-it";
//import MarkdownItAttrs from "markdown-it-attrs";
//import MarkdownItBracketedSpans from "markdown-it-bracketed-spans";
//import MarkdownItContainer from "markdown-it-container";
//import MarkdownItDefList from "markdown-it-deflist";
//import MarkdownItLinkAttributes from "markdown-it-link-attributes";
//import MarkdownItSub from "markdown-it-sub";
//import MarkdownItSup from "markdown-it-sup";
import markdownItMermaid from "@liradb2000/markdown-it-mermaid";

const md = MarkdownIt({ html: true, linkify: true }); // ...options
md //.use(MarkdownItAttrs)
	//.use(MarkdownItBracketedSpans)
	//.use(MarkdownItContainer)
	//.use(MarkdownItDefList)
	//.use(MarkdownItLinkAttributes)
	//.use(MarkdownItSub)
	//.use(MarkdownItSup)
	.use(markdownItMermaid); // Note: compiled run-time issue trying to pass config options to markdownItMermaid

export default defineComponent({
	name: "MarkdownRenderer",
	props: {
		markdown: {
			type: String,
			required: true,
		},
	},
	data: () => ({
		currentMarkdown: "",
	}),
	computed: {
		renderedHtml(): string {
			return md.render(this.currentMarkdown);
		},
	},
	watch: {
		markdown: {
			immediate: true,
			handler(newValue: string) {
				this.currentMarkdown = newValue;
			},
		},
	},
});
</script>
