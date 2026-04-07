<script lang="ts">
    // Can be given with default value
    let {answer = 50} = $props()
</script>

<p>
    This is a Nested paragraph {answer}
</p>