<script>
    import { onDestroy } from 'svelte';
    import FeedbackForm from './components/FeedbackForm.svelte';
    import FeedbackList from './components/FeedbackList.svelte';
    import FeedbackStat from './components/FeedbackStat.svelte';
    import { FeedbackStore } from './store';

    $: count = $FeedbackStore.length;
    $: average = $FeedbackStore.reduce((a, item) => a + item.rating, 0) / count;

    const deleteFeedback = (e) => {
        const itemId = e.detail;
        FeedbackStore.update((currentData) => {
            return currentData.filter((item) => item.id != itemId);
        });
    };

    let feedbacks = [];

    const unsubscribe = FeedbackStore.subscribe((data) => (feedbacks = data));

    onDestroy(() => {
        unsubscribe();
    });
</script>

<main class="container">
    <FeedbackForm />
    <FeedbackStat />
    <FeedbackList {feedbacks} on:delete-feedback={deleteFeedback} />
</main>
