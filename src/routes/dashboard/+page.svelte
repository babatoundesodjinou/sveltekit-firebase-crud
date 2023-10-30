<script>
    let todoList = [];
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

    function editTodo(index){
        let newTodoList = todoList.filter((val, i) =>{
            return i !== index;
        });

        currTodo = todoList[index];
        todoList = newTodoList;
    }

    function removeTodo(index){
        let newTodoList = todoList.filter((val, i) =>{
            return i !== index;
        });

        todoList = newTodoList;
    }

</script>

<div class="mainContainer">
    <div class="headerContainer">
        <h1>Todo list</h1>
        <div class="headerBtns">
            <button>
                <i class="fa-regular fa-floppy-disk"></i>
                <p>Save</p>
            </button>
            
            <button>
                <i class="fa-solid fa-right-from-bracket"></i>
                <p>Logout</p>
            </button>

        </div>
    </div>
    <main>
        {#if todoList.length === 0}
            You have nothing to do
        {/if}

        {#each todoList as todo, index}
            <div class="todo">
                <p>
                    { index + 1 }. { todo }
                </p>
                <div class="actions">
                    <i on:click={() =>{
                        editTodo(index)
                    }} 
                    on:keydown={ () =>{} } class="fa-regular fa-pen-to-square"></i>
                    <i   on:click={() =>{
                        removeTodo(index)
                    }} 
                    on:keydown={ () =>{} } class="fa-regular fa-trash-can"></i>
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

    .headerBtns{
        display: flex;
        align-items: center;
        gap: 14px;

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

    .actions i {
        cursor: pointer;
    }

    .actions i:hover{
        color: coral;
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