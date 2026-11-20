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

`?embed` drops the page background and outer padding.

## Colour themes

The page opens in **Moderate** (mid-tone, low glare). Visitors can switch with
the Colours menu, and their choice is remembered in their browser. Themes:
`moderate`, `light`, `dark`, `heritage`, `night`, `contrast` (high contrast).

- `&theme=heritage` (any theme name) in the link opens in that theme without
  changing the visitor's saved choice.
- `&picker=off` hides the Colours menu, e.g. to lock an embed to your site's look:
  `?embed&theme=heritage&picker=off`.

## Updating

`data.json` is rebuilt from a fresh petition export (the tab-separated
UTF-16 CSV). Never commit the export itself: it contains signers' names.
