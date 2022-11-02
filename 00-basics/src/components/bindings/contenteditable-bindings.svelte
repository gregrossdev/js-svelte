<script>
    let html = '<p>Write some text!</p>';
</script>

<h3>Content Editable Bindings</h3>
<div
        contenteditable="true"
        bind:innerHTML={html}
/>
<pre>{html}</pre>

<style>
    [contenteditable] {
        padding: 0.5em;
        border: 1px solid #eee;
        border-radius: 4px;
    }
</style>