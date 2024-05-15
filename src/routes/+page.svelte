<script>
    /** @type {number} */
    let sum = $state(0)

    /** @type {string|null} */
    let operator = $state(null)

    /**
     * 
     * @param {number} n
     */
    function handle_number(n) {
        if (operator === null) {
            sum = n
            return
        }
        switch (operator) {
            case '+':
                sum += n
                break
            case '-':
                sum -= n
                break
            case '*':
                sum *= n
                break
            case '/':
                sum /= n
                break
        }
    }

    const keyboard = [
        [7, 8, 9, '+'],
        [4, 5, 6, '-'],
        [1, 2, 3, '*'],
        [null, 0, null, '/']
    ]

    /**
     * 
     * @param {string|null} op
     */
    function handle_operator(op) {
        operator = op
    }
</script>

<table>
    <thead>
        <tr>
            <td id="sum" colspan="4">{sum}</td>
        </tr>
    </thead>
    <tbody>
        {#each keyboard as row}
            <tr>
            {#each row as key}
                {#if key === null}
                    <td></td>
                {:else if typeof key === 'string'}
                    <td><button type="button" onclick={() => handle_operator(key)}>{key}</button></td>
                {:else}
                    <td><button type="button" onclick={() => handle_number(key)}>{key}</button></td>
                {/if}
            {/each}
            </tr>
        {/each}
    </tbody>
</table>

<style lang="scss">
    td {
        text-align: center;
        font-size: 30px;

    }
    button {
        height: 125px;
        width: 125px;
        font-size: 30px;
    }
    #sum {text-align: right; padding-right: 30px;}
</style>
