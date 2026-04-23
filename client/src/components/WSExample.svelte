<script>
    let message = $state("");
    let messageFromServer = $state("");
    let connection;

    const openConnection = () => {
        connection = new WebSocket("ws://localhost:8000/api/pings/ws");

        connection.onmessage = (event) => {
            messageFromServer = event.data;
        }
    }

    const sendMessage = async () => {
        connection.send(message);
        message = "";
    }



    if (!import.meta.env.SSR){
        openConnection()
    }


</script>

<p>WS EXAMPLE!</p>

<input type="text" bind:value={message}/>
<button onclick={() => sendMessage()}>Send</button>

<p>TEST: {messageFromServer}</p>