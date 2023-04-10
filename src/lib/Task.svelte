<script lang="ts">
	import { bind } from "svelte/internal";
    export let texto: string;
    export let completed: boolean;
     
</script>


<div class="w-full flex justify-between p-3 text-neutral-500 rounded-md space-x-2 ">
    <input 
        type="checkbox" 
        bind:checked={completed} 
        class="cursor-pointer accent-purple-600 "
    />
    <input 
        type="text" 
        bind:value={texto} 
        disabled={completed}
        class="disabled:opacity-50 disabled:line-through flex-1"
    />
    
        
</div>

