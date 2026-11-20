# Petition statistics

`index.html` reads `data.json` (counts only: no names, street addresses or full
postal codes) and draws the map and charts with no external requests.

Live at `https://map.restoreislandrail.com/petition/`.

## Embed

```html
<iframe id="rir-petition" src="https://map.restoreislandrail.com/petition/?embed"
  style="width:100%;height:2400px;border:0" title="Restore Island Rail petition statistics" loading="lazy"></iframe>
<script>
window.addEventListener('message', e => {
  if (e.origin === 'https://map.restoreislandrail.com' && e.data && e.data.type === 'rir-petition-height')
    document.getElementById('rir-petition').style.height = e.data.height + 'px';
});
</script>
```

`?embed` drops the page background and outer padding; add `&theme=light` or
`&theme=dark` to fix the colours instead of following the visitor's setting.

## Updating

`data.json` is rebuilt from a fresh petition export (the tab-separated
UTF-16 CSV). Never commit the export itself: it contains signers' names.
