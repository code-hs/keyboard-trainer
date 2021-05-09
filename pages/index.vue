<template>
	<v-row class="keyboard-page" justify="center" align="center">
		<v-col cols="12" sm="12" md="12">
			<label class="literal-container"
				><span class="literal success"> R</span><span class="literal"> W</span
				><span class="literal fail"> [</span><span class="literal"> /</span
				><span class="literal"> E</span><span class="literal"> W</span></label
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
		return {};
	},
	created() {},
};
</script>
