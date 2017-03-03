<style>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  background: rgba(197, 201, 208, 0.8);
  overflow: auto;
  z-index: 9000;
  -moz-transition: all .5s;
  -o-transition: all .5s;
  -webkit-transition: all .5s;
  transition: all .5s;
}
.modal .modal-wrapper {
  position: relative;
  max-width: 376px;
  padding: 45px 82px;
  margin: 90px 0;
  border-radius: 5px;
  background: #fff;
  -moz-transition: all .5s;
  -o-transition: all .5s;
  -webkit-transition: all .5s;
  transition: all .5s;
  z-index: 9020;
}
@media only screen and (min-width: 320px) and (max-width: 425px) {
  .modal .modal-wrapper {
    margin: 50px auto;
    padding: 20px;
    min-width: 270px;
    max-width: 320px;
  }
}
.modal .modal-wrapper .close {
  position: absolute;
  top: 15px;
  right: 30px;
  font-size: 0.813em;
  cursor: pointer;
  -moz-transition: all .25s;
  -o-transition: all .25s;
  -webkit-transition: all .25s;
  transition: all .25s;
}
.modal .modal-wrapper .close:hover {
  color: #cccccc;
}
.modal .modal-wrapper .button {
  font-size: 0.95em;
}
.modal .modal-wrapper .modal-container, .modal .modal-wrapper .modal-header, .modal .modal-wrapper .modal-body {
  display: block;
  width: 100%;
}
.modal .modal-wrapper .modal-container small, .modal .modal-wrapper .modal-header small, .modal .modal-wrapper .modal-body small {
  font-weight: normal;
  font-weight: 1em;
}
.modal .modal-wrapper .modal-container h2, .modal .modal-wrapper .modal-header h2, .modal .modal-wrapper .modal-body h2 {
  font-size: 1.625em;
  border-bottom: 1px solid #e1e6ed;
  padding-bottom: 28px;
  margin-bottom: 10px;
  line-height: 0.9;
}
.modal .modal-wrapper .modal-footer {
  width: 100%;
  font-size: 0.813em;
}
.modal .modal-wrapper .modal-footer p {
  padding-top: 0;
}
.modal.no-padding .modal-wrapper {
  padding: 0 !important;
}
.modal.modal-sm .modal-wrapper {
  margin: 0 0 0 -200px;
  padding: 30px 60px;
}
.modal.modal-lg .modal-wrapper {
  width: 900px;
  max-width: 900px;
  padding: 45px 60px;
}
.modal.modal-lg .modal-wrapper .modal-header h2 small {
  padding-top: 18px;
  font-size: 0.6em;
}

body.modal-open {
  overflow-y: hidden;
}
</style>

<template>
	<transition name="modal">
		<div class="modal" @keyup.esc="close()">
			<div class="modal-wrapper">
				<span class="close" @click="close()">&times;</span>
				<div class="modal-container">
					<div class="modal-header">
						<slot name="header">
						</slot>
					</div>

					<div class="modal-body">
						<slot name="body">
						</slot>
					</div>

					<div class="modal-footer">
						<slot name="footer">
						</slot>
					</div>
				</div>
			</div>
		</div>
	</transition>
</template>

<script>

export default {
	name: "Modal",

	methods: {
		close(){
			this.show = false;
			document.body.classList.remove("modal-open")
			this.$emit('close')
		}
	}
}
</script>
