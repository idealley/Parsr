<template functional>
	<g class="WordGroup">
		<rect
			class="Word"
			:x="props.element.box.l"
			:y="props.element.box.t"
			:width="props.element.box.w"
			:height="props.element.box.h"
			@click="listeners['custom-event'](props.element)"
		/>
		<text
			:id="'Word_' + props.element.id"
			:x="props.element.box.l"
			:y="props.element.box.t + props.element.box.h"
			fill="black"
			:textLength="props.element.box.w"
			:lengthAdjust="
				props.fonts.filter(font => font.id === props.element.font).shift().size
					? 'spacing'
					: 'spacingAndGlyphs'
			"
			:style="{
				fontSize: props.fonts.filter(font => font.id === props.element.font).shift().size * 0.6,
				fill: props.fonts.filter(font => font.id === props.element.font).shift().color,
			}"
			:font-weight="fontWeight"
			@click="listeners['custom-event'](props.element)"
			>{{ !Array.isArray(props.element.content) ? props.element.content.trim() : 'Array empty'
			}}{{ props.element.fakeSpace ? '&nbsp;' : '' }}</text
		>
	</g>
</template>

<script>
import pageElementMixin from '@/mixins/pageElementMixin';

export default {
	mixins: [pageElementMixin],
	methods: {
		displayProps() {
			console.log(this.props);
		},
	},
	/*computed: {
		wordStyle() {
			console.log(this.props.element.font);
			const font = this.$store.getters.wordFont(this.props.element.font);
			if (font) {
				return 'font-size:' + font.size * 0.8 + 'px';
			}

			return 'font-size: 1em';
		},
		fontWeight() {
			console.log(this.props.element.font);
			const font = this.$store.getters.wordFont(this.props.element.font);
			if (font) {
				return font.weight;
			}

			return 'normal';
		},
	},*/
};
</script>
