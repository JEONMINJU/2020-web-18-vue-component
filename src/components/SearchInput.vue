<template>
	<div class="input-wrapper">
		<b-form-input v-model="query" placeholder="검색할 상품명을 입력하세요." />
		<i v-show="query.length" @click="onClick" class="fa fa-times-circle"></i>
	</div>
</template>
<script>
/*
? 부모가 자식에게 데이터를 전달하려면 props(v-bind)로 전달한다.
? 자식이 부모에게 데이터를 전달하려면 event(v-on, $emit)로 전달한다.
*/
export default {
	name: 'SearchInput',
	data() {
		return {
			query: ''
		}
	},
	watch: {
		query: function(n) {
			this.$emit('@onChange', n)
		}
	},
	methods: {
		onClick(e) {
			this.query = ''
		},
	}
}
</script>
<style scoped>
.input-wrapper {position: relative;}
input {padding: 1em; font-size: 1.25em;}
i {position: absolute; right: 0.75em; top: 50%; transform: translateY(-50%); font-size: 1.125em; cursor: pointer;}
i:hover {color: #911515}
</style>