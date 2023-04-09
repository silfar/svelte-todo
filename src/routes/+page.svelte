<script lang="ts">

    
	import Task from "../lib/Task.svelte";
    interface ITask{
        id: number;
        texto: string;
        completed: boolean;
    }
    let tasks: ITask[] = [];

    function addTask() {
        tasks = [
            ...tasks,
            {   id: tasks.length + 1,
                texto: "nova tarefa",
                completed: false,
            },
        ];
    }

    // create a function to del a task
    function delTask(index: number) {
        tasks = tasks.filter((_, i) => i !== index);
    }

</script>

<div class="p-4  h-screen flex items-center flex-col space-y-2 max-w-lg mx-auto">
    
    <button class="w-full flex justify-center space-x-2 p-3 border-2 text-neutral-500 border-neutral-300 border-dashed font-semibold"
            on:click={addTask}>
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6">
            <path fill-rule="evenodd" d="M12 2.25c-5.385 0-9.75 4.365-9.75 9.75s4.365 9.75 9.75 9.75 9.75-4.365 9.75-9.75S17.385 2.25 12 2.25zM12.75 9a.75.75 0 00-1.5 0v2.25H9a.75.75 0 000 1.5h2.25V15a.75.75 0 001.5 0v-2.25H15a.75.75 0 000-1.5h-2.25V9z" clip-rule="evenodd" />
        </svg>
        <spam>Nova Tarefa</spam>
    </button>

    {#each tasks as task}
        <!-- <div class="w-max flex justify-between"> -->
            <Task 
                bind:texto={task.texto} 
                bind:completed={task.completed}
            />

            <button class="ml-4">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M14.74 9l-.346 9m-4.788 0L9.26 9m9.968-3.21c.342.052.682.107 1.022.166m-1.022-.165L18.16 19.673a2.25 2.25 0 01-2.244 2.077H8.084a2.25 2.25 0 01-2.244-2.077L4.772 5.79m14.456 0a48.108 48.108 0 00-3.478-.397m-12 .562c.34-.059.68-.114 1.022-.165m0 0a48.11 48.11 0 013.478-.397m7.5 0v-.916c0-1.18-.91-2.164-2.09-2.201a51.964 51.964 0 00-3.32 0c-1.18.037-2.09 1.022-2.09 2.201v.916m7.5 0a48.667 48.667 0 00-7.5 0" />
                  </svg>
            </button>

        <!-- </div> -->
   {/each}
    
    

</div>