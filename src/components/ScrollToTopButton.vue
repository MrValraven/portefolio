<template>
    <button id="btnScrollToTop" aria-label="Scroll to top">
		<i class="fa fa-arrow-up" aria-hidden="true" ></i>
	</button>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'ScrollToTopButton',
});
</script>

<style lang="scss">
$darkBlue: #274C77;

#btnScrollToTop {
    position: fixed;
	right: 10px;
	bottom: 10px;
	width: 50px;
	height: 50px;
	border-radius: 50%;
	color: white;
	background-color: $darkBlue;
	outline: none;
	border: 1px solid darken($color: $darkBlue, $amount: 10%);
	box-shadow: rgba(50, 50, 93, 0.25) 0px 13px 27px -5px, rgba(0, 0, 0, 0.3) 0px 8px 16px -8px;
	opacity: 1;
	cursor: pointer;
	
	z-index: 10;

    &:hover {

		i {
			transform: scale(1.2);
		}
    }

	i {
		transition: all 0.5s cubic-bezier(0.075, 0.82, 0.165, 1);
	}
}
    
</style>

