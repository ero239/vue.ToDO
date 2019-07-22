<template>
	<div>
		<form @submit="addTodo">
			<input type="text" v-model="title" placeholder="Add new todo...">
			<input type="submit" value="Submit new ToDo" class="btn">
		</form>
	</div>
</template>

<script>



export default {
	name: "AddTodo",
	data() {
		return {
			title: ''
		}
	},
	methods: {
		addTodo(e) {
			e.preventDefault();
			const newTodo = {
				title: this.title,
				completed: false
			};
			this.$emit('addTodo', newTodo);
			this.title = '';
		}
	}
}
</script>

<style scoped>
	form {
		margin: 30px 0;
		display: flex;
	}
	input[type="text"] {
		flex: 10;
		padding: 5px;
		border: none;
	}
	input[type="submit"] {
		flex: 2;
		background-color: rgb(255, 255, 255);
		box-shadow: 0 0 15px 0 rgb(226, 226, 226);
		border-radius: 15px;
		color: black;
		font-weight: 500;
		font-size: 15px;
		margin: 0 5px 0 0;
	}
</style>