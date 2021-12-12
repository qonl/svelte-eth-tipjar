<script lang="ts">
    const web3 = new Web3(Web3.givenProvider);

    let amount: string = '0.01';

    const send = async function (amount: string): Promise<void> {
        const accounts = await window.ethereum.request({ method: 'eth_requestAccounts'});
        
        const wei = web3.utils.toWei(amount, 'ether'); 

        if (accounts.length > 0) {
            window.ethereum.request({ 
                method: 'eth_sendTransaction',
                params: [{
                    from: accounts[0],
                    // update your account number here
                    to: '0xB5d0b32baF74254FC6bfCeba1ab5393dBe2059C5',
                    value: web3.utils.toHex(wei)
                }],
            });
        }
    }

    const handleSubmit = () => {
        if (window.ethereum) {
            send(amount);
        }
    }
</script>

<form on:submit|preventDefault={handleSubmit} class={window.ethereum ? 'has-eth' : 'no-eth'}>
    <label for="tip">If you like my work, please consider sending me a tip!</label>
    <input id="tip" bind:value={amount}> <span>ETH</span>
    <button>Tip</button>
    <div class="message">
        <p>Please install MetaMask in order to use this feature.</p>
    </div>
</form>

<style>
    /* for fading in the form */
	@keyframes fadein {
		0% {
			visibility: hidden;
			opacity: 0;
			transform: translate(0, 24px);
		}
		100% {
			opacity: 1;
			transform: translate(0, 0);
		}
	}

	form {
		position: fixed;
		bottom: 24px;
		right: 24px;
		max-width: var(--form-width);

		background: var(--form-back);
		color: var(--form-fore);
		padding: 24px;

		display: grid;
		grid-gap: 16px 8px;
		grid-template-areas: "label label" "input eth" "button button";
		grid-template-columns: 1fr auto;
		align-items: center;

		/* display: none; */
		animation: fadein 0.4s 0.8s ease-in-out both;
	}

	form.has-eth { 
		display: grid;
		animation: fadein 0.4s 0.8s ease-in-out both;
	}

	form label {
		grid-area: label;

		display: block;
		font-size: 16px;
	}

	form input {
		grid-area: input;

		appearance: none;
		width: 100%;
		border: none;
		padding: 8px;

		font-variation-settings: "wght" 600;
		text-align: right;

		background: var(--form-back);
		color: var(--form-fore);
		border: 1px solid var(--form-border);
		transition: border-color 0.2s ease-in-out;
	}

	form input:focus {
		border: 1px solid var(--form-fore);
		outline: none;
	}

	form span {
		grid-area: eth;
	}

	form button {
		grid-area: button;
		appearance: none;
		border: none;
		background: var(--form-fore);
		color: var(--form-back);
		font: inherit;
		padding: 8px;
		font-size: 16px;
	}

    .message {
        display: none;
        padding: 1rem 1rem;
    }

    form.no-eth .message { 
        position: absolute;
        width: 100%;
        height: 100%;
		display: flex;
		place-content: center;
        color: white;
        background: #0000009c;
	}
</style>