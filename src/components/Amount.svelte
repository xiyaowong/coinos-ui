<script>
  import { s, f, toFiat } from "$lib/utils";
  import { fiat } from "$lib/store";
  const { amount, tip, rate, currency } = $props();
</script>

<div>
  <h2 class="text-2xl md:text-3xl font-semibold flex justify-center items-end">
    <div class="flex items-center">
      <iconify-icon icon="ph:lightning-fill" class="text-yellow-300"
      ></iconify-icon>{s(amount)}
    </div>

    {#if tip}
      <div class="flex items-center text-lg ml-2">
        <div>+</div>
        <iconify-icon icon="ph:lightning-fill" class="text-yellow-300"
        ></iconify-icon>
        <div>{s(tip)}</div>
      </div>
    {/if}
  </h2>
  <h3 class="text-secondary md:text-lg">
    {f(toFiat(amount, rate), currency)}
    {#if tip}
      <span class="text-base">
        + {f(toFiat(tip, rate), currency)}
      </span>
    {/if}
  </h3>
</div>
