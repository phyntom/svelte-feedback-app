<script>
    import FeedbackItem from './FeedbackItem.svelte';
    import {fade,scale} from "svelte/transition"

    export let feedbacks = [];
</script>
<main>
    <h1>Feedback List</h1>
    {#each feedbacks as fb (fb.id)}
    <div in:scale out:fade="{{duration: 500}}">
        <FeedbackItem  item={fb} on:delete-feedback/>
    </div>
    {/each}
</main>