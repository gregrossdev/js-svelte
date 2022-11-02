<script>
    import { marked } from 'marked';
    let value = `Some words are *italic*, some are **bold**`;
</script>

<h3>Textarea Inputs</h3>
<textarea bind:value></textarea>
{@html marked(value)}

<style>
    textarea { width: 100%; height: 200px; }
</style>