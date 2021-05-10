<template>
	<v-row class="keyboard-page" justify="center" align="center">
		<v-col cols="12" sm="12" md="12">
			<div class="literal-container">
				<span
					v-for="(char, index) in currentWord"
					:key="index"
					class="literal"
					:class="{select: keyIndex === index}"
				>
					{{ char }}
				</span>
			</div>
			<input v-model="input" type="text" class="input-area" />

			<v-row class="info-container">
				<v-col align="center">
					<div class="number">38</div>
					<div class="label">count</div>
				</v-col>

				<v-col align="center">
					<div class="number">132</div>
					<div class="label">speed</div>
				</v-col>
			</v-row>
		</v-col>
	</v-row>
</template>

<script>
export default {
	data() {
		return {
			words: [
				'const',
				'let',
				'function',
				'return',
				'false',
				'true',
				'if',
				'else',
				'else if',
				'this',
				'log',
				'export',
				'default',
				'new',
				'result',
				'push',
				'shift',
				'unshift',
				'item',
				'key',
				'pull',
				'git',
				'status',
				'checkout',
				'merge',
				'container',
				'display',
				'width',
				'height',
				'Object',
				'Array',
				'break',
				'case',
				'catch',
				'continue',
				'delete',
				'finally',
				'for',
				'instanceof',
				'typeof',
				'null',
				'switch',
				'throw',
				'try',
				'props',
				'info',
				'description',
				'type',
				'required',
				'class',
				'data',
				'computed',
				'methods',
				'components',
				'disabled',
				'@click',
				'submit',
				'handler',
				'form',
				'order',
				'card',
				'side',
				'title',
				'page',
				'div',
				'done',
				'error',
				'style',
				'span',
				'wait',
				'text',
				'center',
				'current',
				'input',
				'price',
				'sale',
				'limit',
				'scoped',
				'valid',
				'v-if',
				'v-model',
				'id',
				'label',
				'options',
				'reduce',
				'placeholder',
				'watch',
				'mounted',
			],
			input: '',
			currentWord: '',
			keyIndex: 0,
		};
	},
	watch: {
		input(v) {
			if (v && this.currentWord.startsWith(v)) {
				this.keyIndex++;

				if (v === this.currentWord) {
					this.keyIndex = 0;
					this.input = '';
					this.updateText();
				}
			} else {
				this.keyIndex = 0;
				this.input = '';
			}
		},
	},
	mounted() {
		this.updateText();
	},
	methods: {
		shuffleWords() {
			for (let i = 0; i < this.words.length; i++) {
				const newPos = Math.floor(Math.random() * this.words.length);

				[this.words[i], this.words[newPos]] = [
					this.words[newPos],
					this.words[i],
				];
			}
		},
		generateText() {
			this.shuffleWords();
			const index = Math.random() * this.words.length;

			return this.words[Math.floor(index)];
		},
		updateText() {
			this.currentWord = this.generateText();
		},
	},
};
</script>
