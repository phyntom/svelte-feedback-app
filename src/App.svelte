<script>
    import FeedbackForm from './components/FeedbackForm.svelte';
import FeedbackList from './components/FeedbackList.svelte';
import FeedbackStat from './components/FeedbackStat.svelte';


let feedbacks= [
    {
    id: '1',
    rating: 10,
    text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
  },
  {
    id: '2',
    rating: 9,
    text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
  }, 
  {
    id: '3',
    rating: 8,
    text: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. consequuntur vel vitae commodi alias voluptatem est voluptatum ipsa quae.',
  }
  ]

  $:count =  feedbacks.length;
  $:average = feedbacks.reduce((a,item) => a + item.rating, 0) / count

  const deleteFeedback=(e)=>{
    const itemId= e.detail;
    feedbacks = feedbacks.filter((item) => item.id != itemId);
  }

  const addFeedBack=(e)=>{
    const newFeedBack = e.detail;
    feedbacks = [newFeedBack,...feedbacks]
  }

 
</script>

<main class='container'>
    <FeedbackForm on:submit-feedback={addFeedBack} />
    <FeedbackStat count={count} average={average} />
	<FeedbackList feedbacks={feedbacks} on:delete-feedback={deleteFeedback} />
</main>
