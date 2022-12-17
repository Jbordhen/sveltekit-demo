<script lang="ts">
	$: todoList = [] as {
		name: string;
		isCompleted: boolean;
		id: number;
	}[];

	const addTodo = () => {
		const input = document.querySelector('input');
		if (!input || input.value === '') {
			alert('Please enter a todo');
			return;
		}
		todoList = [
			...todoList,
			{
				name: input.value,
				isCompleted: false,
				id: todoList.length + 1 + new Date().getTime()
			}
		];
		input.value = '';
	};

	const toggleTodo = (e: Event) => {
		const target = e.target as HTMLInputElement;
		const id = target.parentElement?.id;
		if (!id) return;
		const todo = todoList.find((todo) => todo.id === Number(id));
		if (todo) {
			todo.isCompleted = !todo.isCompleted;
		}
	};
</script>

<section id="todo-list">
	<h1>Simple Todo List</h1>
	<div>
		<input type="text" placeholder="Add a todo" />
		<button on:click={addTodo}>Add</button>
	</div>
	<ul>
		{#each todoList as todo}
			<li id={`${todo.id}`}>
				<input type="checkbox" checked={todo.isCompleted} on:change={toggleTodo} />
				{todo.name}
			</li>
		{/each}
	</ul>
	<a href="/">Home Page</a>
</section>

<style>
	.completed {
		text-decoration: line-through;
	}

	.pointer {
		cursor: pointer;
	}
</style>
