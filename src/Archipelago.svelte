<script lang="ts">
    import { createEventDispatcher } from "svelte";
    import {
        Client,
        ITEMS_HANDLING_FLAGS,
        SERVER_PACKET_TYPE,
    } from "archipelago.js";
    // this is the type of status update messages:
    import type { PrintJSONPacket } from "archipelago.js";
    const dispatch = createEventDispatcher();

    interface Message {
        text: string;
    }

    interface APConnectionInfo {
        hostname: string;
        port: number;
        game: string;
        name: string;
        items_handling: number;
    }

    let apConnectionInfo: APConnectionInfo = {
        hostname: "archipelago.gg",
        port: 38281,
        game: "Game name",
        name: "Player name",
        items_handling: ITEMS_HANDLING_FLAGS.REMOTE_ALL,
    };

    function message(message: Message) {
        dispatch("message", message);
    }
</script>
