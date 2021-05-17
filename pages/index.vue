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
					<div class="number">{{ info.count }}</div>
					<div class="label">count</div>
				</v-col>

				<v-col align="center">
					<div class="number">{{ speed }}</div>
					<div class="label">speed</div>
				</v-col>
			</v-row>
		</v-col>
	</v-row>
</template>

<script>
import {mapGetters} from 'vuex';

export default {
	data() {
		return {
			input: '',
			currentWord: '',
			keyIndex: 0,
			info: {
				startTime: Date.now(),
				count: 0,
			},
		};
	},
	computed: {
		...mapGetters({words: 'trainer/words'}),
		speed() {
			const seconds = (Date.now() - this.info.startTime) / 1000;
			const charsInOneSecond = this.info.count / seconds;

			return Math.floor(charsInOneSecond * 60) || 0;
		},
	},
	watch: {
		input(v) {
			const isValidChar = v && this.currentWord.startsWith(v);

			if (!isValidChar) {
				this.clear();
				return false;
			}

			this.keyIndex++;
			this.info.count++;

			// finish current word
			if (v === this.currentWord) this.init();
		},
	},
	mounted() {
		this.init();
	},
	methods: {
		clear() {
			this.keyIndex = 0;
			this.input = '';
		},
		init() {
			this.clear();
			this.updateText();
		},
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
