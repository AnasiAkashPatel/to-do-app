# to-do-app
Hi Iam Anasi Akash , Today I Have Created A To-Do List In HTML CSS JAVASCRIPT
<!DOCTYPE html>

<html lang="en">

<head>

	<meta charset="UTF-8">

	<meta http-equiv="X-UA-Compatible" content="IE=edge">

	<meta name="viewport" content="width=device-width, initial-scale=1.0">

	<title>Task List 2021</title>

	<style>

:root {

	--dark: #374151;

	--darker: #1F2937;

	--darkest: #111827;

	--grey: #6B7280;

	--pink: #EC4899;

	--purple: #8B5CF6;

	--light: #EEE;

}

* {

	margin: 0;

	box-sizing: border-box;

	font-family: "Fira sans", sans-serif;

}

body {

	display: flex;

	flex-direction: column;

	min-height: 100vh;

	color: #FFF;

	background-color: var(--dark);

}

header {

	padding: 2rem 1rem;

	max-width: 800px;

	width: 100%;

	margin: 0 auto;

}

header h1{ 

	font-size: 2.5rem;

	font-weight: 300;

	color: var(--grey);

	margin-bottom: 1rem;

}

#new-task-form {

	display: flex;;

}

input, button {

	appearance: none;

	border: none;

	outline: none;

	background: none;

}

#new-task-input {

	flex: 1 1 0%;

	background-color: var(--darker);

	padding: 1rem;

	border-radius: 1rem;

	margin-right: 1rem;

	color: var(--light);

	font-size: 1.25rem;

}

#new-task-input::placeholder {

	color: var(--grey);

}

#new-task-submit {

	color: var(--pink);

	font-size: 1.25rem;

	font-weight: 700;

	background-image: linear-gradient(to right, var(--pink), var(--purple));

	-webkit-background-clip: text;

	-webkit-text-fill-color: transparent;

	cursor: pointer;

	transition: 0.4s;

}

#new-task-submit:hover {

	opacity: 0.8;

}

#new-task-submit:active {

	opacity: 0.6;

}

main {

	flex: 1 1 0%;

	max-width: 800px;

	width: 100%;

	margin: 0 auto;

}

.task-list {

	padding: 1rem;

}

.task-list h2 {

	font-size: 1.5rem;

	font-weight: 300;

	color: var(--grey);

	margin-bottom: 1rem;

}

#tasks .task {

	display: flex;

	justify-content: space-between;

	background-color: var(--darkest);

	padding: 1rem;

	border-radius: 1rem;

	margin-bottom: 1rem;

}

.task .content {

	flex: 1 1 0%;

}

.task .content .text {

	color: var(--light);

	font-size: 1.125rem;

	width: 100%;

	display: block;

	transition: 0.4s;

}

.task .content .text:not(:read-only) {

	color: var(--pink);

}

.task .actions {

	display: flex;

	margin: 0 -0.5rem;

}

.task .actions button {

	cursor: pointer;

	margin: 0 0.5rem;

	font-size: 1.125rem;

	font-weight: 700;

	text-transform: uppercase;

	transition: 0.4s;

}

.task .actions button:hover {

	opacity: 0.8;

}

.task .actions button:active {

	opacity: 0.6;

}

.task .actions .edit {

	background-image: linear-gradient(to right, var(--pink), var(--purple));

	-webkit-background-clip: text;

	-webkit-text-fill-color: transparent;

}

.task .actions .delete {

	color: crimson;

}

</style>

</head>

<body>

		<header>

		<h1>Task List 2022</h1>

		<form id="new-task-form">

			<input 

				type="text" 

				name="new-task-input" 

				id="new-task-input" 

				placeholder="What do you have planned?" />

			<input 

				type="submit"

				id="new-task-submit" 

				value="Add task" />

		</form>

	</header>

	<main>

		<section class="task-list">

			<h2>Tasks</h2>

			<div id="tasks">

				<!-- <div class="task">

					<div class="content">

						<input 

							type="text" 

							class="text" 

							value="A new task"

							readonly>

					</div>

					<div class="actions">

						<button class="edit">Edit</button>

						<button class="delete">Delete</button>

					</div>

				</div> -->

			</div>

		</section>

	</main>

	<script>

window.addEventListener('load', () => {

	const form = document.querySelector("#new-task-form");

	const input = document.querySelector("#new-task-input");

	const list_el = document.querySelector("#tasks");

	form.addEventListener('submit', (e) => {

		e.preventDefault();

		const task = input.value;

		const task_el = document.createElement('div');

		task_el.classList.add('task');

		const task_content_el = document.createElement('div');

		task_content_el.classList.add('content');

		task_el.appendChild(task_content_el);

		const task_input_el = document.createElement('input');

		task_input_el.classList.add('text');

		task_input_el.type = 'text';

		task_input_el.value = task;

		task_input_el.setAttribute('readonly', 'readonly');

		task_content_el.appendChild(task_input_el);

		const task_actions_el = document.createElement('div');

		task_actions_el.classList.add('actions');

		

		const task_edit_el = document.createElement('button');

		task_edit_el.classList.add('edit');

		task_edit_el.innerText = 'Edit';

		const task_delete_el = document.createElement('button');

		task_delete_el.classList.add('delete');

		task_delete_el.innerText = 'Delete';

		task_actions_el.appendChild(task_edit_el);

		task_actions_el.appendChild(task_delete_el);

		task_el.appendChild(task_actions_el);

		list_el.appendChild(task_el);

		input.value = '';

		task_edit_el.addEventListener('click', (e) => {

			if (task_edit_el.innerText.toLowerCase() == "edit") {

				task_edit_el.innerText = "Save";

				task_input_el.removeAttribute("readonly");

				task_input_el.focus();

			} else {

				task_edit_el.innerText = "Edit";

				task_input_el.setAttribute("readonly", "readonly");

			}

		});

		task_delete_el.addEventListener('click', (e) => {

			list_el.removeChild(task_el);

		});

	});

});</script>

</body>

</html>
