<script>
    let num1 = $state(0n);
    let num2 = $state(0n);

    let addition = $derived(num1 + num2);
    let subtraction = $derived(num1 - num2);
    let multiplication = $derived(num1 * num2);

    // 0で割る場合は計算しない
    let division = $derived(num2 !== 0n ? num1 / num2 : null);
    let remainder = $derived(num2 !== 0n ? num1 % num2 : null);
</script>

<h1>BigInt四則演算計算機</h1>

<div>
    <input
        type="number"
        step="1"
        value={num1.toString()}
        oninput={(e) => num1 = BigInt(e.currentTarget.value)}
        placeholder="数値1"
    />

    <input
        type="number"
        step="1"
        value={num2.toString()}
        oninput={(e) => num2 = BigInt(e.currentTarget.value)}
        placeholder="数値2"
    />
</div>

<div>
    <p>{num1} + {num2} = {addition}</p>
    <p>{num1} - {num2} = {subtraction}</p>
    <p>{num1} × {num2} = {multiplication}</p>

    {#if num2 !== 0n}
        <p>{num1} ÷ {num2} = {division}</p>
        <p>{num1} % {num2} = {remainder}</p>
    {:else}
        <p>割り算：0では割れません</p>
        <p>余り：0では計算できません</p>
    {/if}
</div>