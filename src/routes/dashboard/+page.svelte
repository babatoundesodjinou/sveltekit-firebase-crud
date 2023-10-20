<script>
    let todoList = ["Do the groceries"];
    let currTodo = '';
    let error = false;

    function addTodo(){
        error = false;
        if (!currTodo) {
            error = true;
        }

        todoList = [...todoList, currTodo];
        currTodo = "";
    }
</script>

<div class="mainContainer">
    <div class="headerContainer">
        <h1>Todo list</h1>
        <button><p><i class="fa-regular fa-floppy-disk"></i></p>Save</button>
    </div>
    <main>
        {#each todoList as todo, index}
            <div class="todo">
                <p>
                    { index + 1 }. { todo }
                </p>
                <div class="actions">
                    <i class="fa-regular fa-pen-to-square"></i>
                    <i class="fa-regular fa-trash-can"></i>
                </div>
            </div>
        {/each}
    </main>
    <div class={"enterTodo " + (error ? "errorBorder" : "")} >
        <input bind:value={currTodo} type="text" placeholder="Enter Todo">
        <button on:click={addTodo}>ADD</button>
    </div>
</div>

<style>
    .mainContainer{
        display: flex;
        flex-direction: column;
        min-height: 100vh;  
        width: 100%;
        max-width: 1000px;
        gap: 24px;
        padding: 24px;
        margin: 0 auto;
    }

    .headerContainer{
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    .headerContainer button{
        background: #003c5b;
        border: none;
        cursor: pointer;
        padding: 10px 18px;
        border-radius: 4px;
        font-weight: 700;
        display: flex;
        align-items: center;
        gap: 10px;
        color: white;
    }

    .headerContainer button i{
        font-size: 1.1rem;
    }

    .headerContainer button:hover{
        opacity: 0.7;
    }

    main{
        display: flex;
        flex-direction: column;
        gap: 8px;
        flex: 1;
    }

    .todo{
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 4px 8px;
        border-left: 1px solid cyan;
    }

    .actions{
        display: flex;
        align-items: center;
        gap: 8px;
        font-size: 1.3rem;
    }

    .enterTodo{
        display: flex;
        align-items: stretch;
        border: 1px solid #0891b2;
        border-radius: 5px;
        overflow: hidden;
    }

    .errorBorder{
        border-color: coral !important;
    }

    .enterTodo input{
        background: transparent;
        border: none;
        padding: 14px;
        color: white;
        flex: 1;
    }

    .enterTodo input:focus{
        outline: none;
    }

    .enterTodo button{
        padding: 0 14px;
        background: #003c5b;
        border: none;
        color: cyan;
        font-weight: 600;
        cursor: pointer;

    }

    .enterTodo button:hover{
        background: transparent;
    }
</style>