<script>
    import {useCountState} from "../states/countState.svelte"
    const countState = useCountState();
</script>

<button onclick={()=>countState.increment()}>Count {countState.count ?? "Loading..."}!</button>