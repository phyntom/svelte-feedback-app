<script>
    import {createEventDispatcher} from 'svelte' ;
    import Card from './Card.svelte';
    export let item;

    const dispatch = createEventDispatcher();

    const handleDelete = (itemId)=>{
      dispatch('delete-feedback',itemId)
    }
</script>
<Card>
   <div class="num-display">
    {item.rating}
   </div>
   <button class="close" on:click={(e)=> handleDelete(item.id)}>X</button>
   <p class="text-display">
    {item.text}
   </p>
</Card>
<style>
    .num-display{
        position: absolute;
        background-color: #ff6a95;
        width: 50px;
        height: 50px;
        border-radius: 50%;
        top: -10px;
        left: -10px;
        padding: 10px;
        text-align: center;
        border: 1px #eee solid;
        font-size: 19px;
    }
    .close{
        position: absolute;
        text-align: center;
        width: 30px;
        height: 30px;
        top: 5px;
        right: 15px;
        cursor: pointer;
        border: 1px rgba(0, 0, 0, 0.3) dotted;
        border-radius: 50%;
        border:none;
        background: none;
    }
</style>