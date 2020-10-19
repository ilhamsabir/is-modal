<template>
	<div id="app">
		<button @click="openModal">Show Modal</button>

		<div>
			<div>
				<IsModal
					class="modal-demo-sample"
					:size="'large'"
					v-if="show"
					@close="show = false"
					:hide-header="false"
					:hide-footer="false">
					<template slot="header">
						<h3>Header</h3>
					</template>
					<template slot="body">
						Body
					</template>
					<template slot="footer">
						Footer
					</template>
				</IsModal>
			</div>

		</div>
	</div>
</template>

<script>
import IsModal from './components/IsModal.vue'

export default {
	name: 'App',
	components: {
		IsModal
	},
	data() {
		return {
			show: false,
		}
	},
	methods: {
		openModal() {
			this.show = true;
		},
	}
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.modal-mask {
	position: fixed;
	z-index: 999999;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	background-color: rgba(0, 0, 0, .3);
	display: table;
	transition: opacity 0.3s ease;
	/* min-height: 980px; */
}

.modal-wrapper {
	display: table-cell;
	padding-left: 1em;
	padding-right: 1em;
	vertical-align: middle;
}

.modal-wrapper.has-scroll {
	position: absolute;
	top: 0;
	left: 0;
	right: 0;
	bottom: 0;
	padding-top: 10vh;
	padding-bottom: 10vh;
	overflow-y: auto;
}

.modal-container {
	margin: 0 auto;
	width: 100%;
	background-color: #fff;
	border-radius: 3px;
	box-shadow: 0 0 0 1px rgba(0, 0, 0, 0.05), 0 2px 4px 0 rgba(0, 0, 0, 0.2);
	transition: all 0.3s ease;
}

.modal-container-small {
	max-width: 320px;
}

.modal-container-medium {
	max-width: 600px;
}

.modal-container-large {
	max-width: 930px;
}

.modal-header {
	padding: 1em;
	color: #555;
	background-color: #f6f7f9;
	border-bottom: 1px solid #dee1e4;
	align-items: center;
	display: flex;
	justify-content: space-between;

	.close {
		padding: .3rem;
		line-height: 16px;
		border: 0;
		font-size: 19px;
		background: transparent;
		cursor: pointer;
	}

	h3 {
		margin: 0;
		font-size: 1.3em;
		font-weight: bold;
		padding: 0 0.3rem;

		.material-icons,
		.fa-icon {
			margin-right: 0.5em;
			font-size: 1.3em;
			vertical-align: middle;
		}

		.fa-icon {
			position: relative;
			top: -3px;
		}

		.text {
			vertical-align: middle;
		}
	}
}



.modal-body {
	padding: 1.5em;
}

.modal-body .tab-content .box {
	padding: 25px;
	border-top-left-radius: 0 !important;
	border-top-right-radius: 0 !important;
}

.modal-body .tab-content .btn {
	font-size: 0.9em;
}

.modal-body .tab-content textarea {
	font-size: 0.9em;
}

.modal-footer {
	text-align: right;
	border-top: 1px solid #dee1e4;
	background-color: #f6f7f9;
	padding: 14px 24px;
	border-bottom-left-radius: 4px;
	border-bottom-right-radius: 4px;
}

.modal-footer .btn {
	margin-right: 0.5em;
	font-size: 0.875rem;
}

.modal-footer .btn:last-child {
	margin-right: 0;
}

.modal-default-button {
	float: right;
}

/*
   * The following styles are auto-applied to elements with
   * transition="modal" when their visibility is toggled
   * by Vue.js.
   *
   * You can easily play with the modal transition by editing
   * these styles.
   */
.modal-enter {
	opacity: 0;
}

.modal-leave-active {
	opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
	-webkit-transform: scale(1.1);
	transform: scale(1.1);
}

.modal-close {
	cursor: pointer;
}

.modal-close:hover {
	color: #000;
}

.modal-close .material-icons {
	display: block;
}

.modal-empty-data {
	padding: 1.5em;
	border-radius: 3px;
	border: 1px dashed #d1d1d1;
}

.modal-fade {
	transition: opacity 0.15s linear;
}

</style>
