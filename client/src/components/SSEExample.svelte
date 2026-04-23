<script>

    let ping = $state("");

    const listenPings = () => {
        const eventSource = new EventSource("http://localhost:8000/api/pings/stream");

        eventSource.onmessage = (event) => {
            ping = event.data;
        }

    }

    if(!import.meta.env.SSR){
        listenPings();
    }


</script>

<p>TEST {ping}</p>