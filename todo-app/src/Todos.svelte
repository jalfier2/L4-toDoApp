<script>

    import { fly } from 'svelte/transition'; 
    let todoItem = ''; 
    let todoList = [];

    function addToList() {
        if (!todoItem) return; 
        todoList = [...todoList, {
            text: todoItem,
            status: false 
        }]; 
        todoItem = '';
    }
    // remove items from array
    function removeFromList(index) {
        todoList.splice(index, 1); 
        // index is the item we're deleting, 1 is the number of items we are deleting.
        todoList = todoList; 
    }

</script>

<form on:submit|preventDefault={addToList}>
  <span class="inputBox">  <input class="input is-rounded" placeholder="ex. feed dogs" bind:value={todoItem}> </span>
</form>

<ul class="todo-list">
    {#each todoList as item, index}
    <li class="box" transition:fly="{{ y: 20, duration: 200 }}">
    <input bind:checked={item.status} class="checkbox" type="checkbox"> 
    <span class:checked={item.status}> {item.text}</span>
    <button class="delete is-small" type="button" on:click={() => removeFromList(index)}></button>
    </li>
    {/each}
</ul>

<style>
.todo-list {
    list-style: none; 
}
.checked {
    text-decoration: line-through;
    text-decoration-color: rgb(119, 32, 32); 
}
.inputBox,.input {
    width: 30%; 
}
.delete {
    vertical-align: middle;
    float: right;  
}
.checkbox {
    vertical-align: bottom;
    float: left; 
    margin-bottom: 0; 
}
.todo-list {
 text-align: center;
 width: 30%; 
}

.box {
    align-items: center; 
    margin: auto; 
    margin-bottom: 1em; 
    margin-top: 1em; 
    box-shadow: 0 0.5em 1em -0.125em rgb(10 10 10 / 10%), 0 0 0 2px rgb(10 10 10 / 2%);
}
ul, .todo-list {
    padding-left: auto; 
    padding-right: auto; 
    margin: auto; 
}
.span {
    text-align: left; 
}
</style>