# CLAUDE.md — Project instructions for Claude Code

## Architecture

`index.html` is a single-file app. Module HTML (e.g. the Cable Tray Fill calculator)
is stored as gzip+base64 in the `DATA` JS object and decompressed at runtime.
The source for the tray module lives in `C:/Users/Michaelkirsanov/tray_module.html`.

**Workflow for editing modules:**
1. Edit `tray_module.html` (the decompressed source)
2. Compress with PowerShell GZipStream → base64
3. Replace `DATA.tray` value in `index.html` with the new base64 string

## IMPORTANT — Do not remove

### Google Analytics
The following block must always be present at the top of `<head>` in `index.html`.
Do NOT remove or overwrite it when updating the file:

```html
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-5S8H7G6VZ9"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-5S8H7G6VZ9');
</script>
```

After any full rewrite of `index.html`, verify this block is still present with:
```
grep -c "G-5S8H7G6VZ9" index.html
```
Expected output: `2` (once in each script tag).
