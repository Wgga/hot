<template>
	<footer>
		<div class="copyright">
			<n-text class="description">{{ packageJson.description }}</n-text>
			<n-text class="author" :depth="3" @click="jumpLink(packageJson.github)">
				Made by {{ packageJson.author }}
			</n-text>
		</div>
		<n-text v-if="icp" :depth="3" class="icp" @click="jumpLink('https://beian.miit.gov.cn/')">{{ icp }}</n-text>
	</footer>
</template>

<script setup>
import packageJson from "@/../package.json";

const icp = ref(import.meta.env.VITE_ICP ? import.meta.env.VITE_ICP : null);

// 链接跳转
const jumpLink = (url) => {
	window.open(url);
};
</script>

<style lang="scss" scoped>
footer {
	height: 100px;
	padding: 0 5vw;
	max-width: 1800px;
	margin: 20px auto 0;
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;

	.copyright {
		margin-bottom: 4px;

		.description {
			&::after {
				content: "";
				margin: 0 6px;
			}
		}
	}

	.author {
		cursor: pointer;
		transition: all 0.3s;

		&:hover {
			color: var(--n-code-text-color);
		}
	}

	.icp {
		font-size: 13px;
		cursor: pointer;
		transition: all 0.3s;

		&:hover {
			color: var(--n-code-text-color);
		}
	}
}
</style>
