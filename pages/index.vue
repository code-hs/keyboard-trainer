<template>
	<v-row class="keyboard-page" justify="center" align="center">
		<v-col cols="12" sm="12" md="12">
			<label class="literal-container"
				>

				<span class="literal success"> R</span><span class="literal"> W</span
				><span class="literal fail"> [</span><span class="literal"> /</span
				><span class="literal"> E</span><span class="literal"> W</span>

			</label
			>
			<input type="text" class="input-area" />

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
			input: '',
			currentWord: '',
			keyIndex: 0,
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
			],
		};
	},
	created() {
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
			return this.words[0];
		},
		updateText() {
			this.currentWord = this.generateText();
		},
	},
};
</script>
