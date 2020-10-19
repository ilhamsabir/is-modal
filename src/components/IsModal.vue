<template>
	<transition name="modal">
		<div
			class="modal-mask"
			:class="`modal-type-${type}`">
			<div class="modal-wrapper has-scroll">
				<div class="modal-container" :class="`modal-container-${size}`">
					<div class="modal-header" v-if="$slots.header">
						<slot name="header">Modal Header</slot>
						<!-- <div class="modal-close" @click="$emit('close')" v-if="showClose">
							x
						</div> -->
						<button type="button" class="close hidden" @click="$emit('close')">
							<span aria-hidden="true">&times;</span>
						</button>
					</div>

					<div class="modal-body" :class="{ 'p-0': full }">
						<slot name="body">Modal Body</slot>
					</div>

					<div class="modal-footer" v-if="!hideFooter">
						<slot name="footer">
							<button class="btn btn-primary" @click="$emit('close')">OK</button>
						</slot>
					</div>
				</div>
			</div>
		</div>
	</transition>
</template>

<script>
export default {
	name: 'IsModal',
	props: {
		size: {
			type: String,
			default: 'small',
		},
		showClose: {
			type: Boolean,
			default: true,
		},
		hideFooter: {
			type: Boolean,
			default: false,
		},
		full: {
			type: Boolean,
			default: false,
		},
		type: {
			type: String,
			default: 'popup', // popup, lightbox
		},
	},
	methods: {
		onKeyup(event) {
			if (event.key === 'Escape') {
				this.$emit('close');
			}
		},
	},
	created() {
		document.body.classList.add('modal-open');
		window.addEventListener('keyup', this.onKeyup);
	},
	destroyed() {
		document.body.classList.remove('modal-open');
		window.removeEventListener('keyup', this.onKeyup);
	},
};
</script>
