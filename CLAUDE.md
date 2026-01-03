# Claude Code Project Instructions

## Security Requirements

**IMPORTANT:** Before every commit or push, you MUST validate the following security checks:

1. **No hardcoded secrets** - Scan all files for passwords, API keys, tokens, or credentials
2. **No dangerous JavaScript** - Check for `eval()`, `document.write()`, or `innerHTML` with user input
3. **No insecure sources** - Ensure all external scripts use HTTPS, not HTTP
4. **No server-side code** - Verify no PHP or other server-side code in HTML files
5. **No sensitive URLs** - Check that no internal/private URLs are exposed

### Pre-commit checklist:
```bash
# Run these checks before committing:
grep -rE "(password|secret|api_key|apikey|token|credential)[\s]*[=:]" --include="*.html" .
grep -rE "(eval\(|document\.write\()" --include="*.html" .
grep -rE "script.*src=.*http://" --include="*.html" .
```

If any of these checks find issues, DO NOT commit until they are resolved.

## Project Overview

This is a TRMNL e-ink display plugin for Daily AI by AI news. It displays AI news headlines, summaries, and action items.

## File Structure

- `trmnl-plugin-full.html` - Full screen layout (800x480)
- `trmnl-layout-half-horizontal.html` - Half horizontal layout
- `trmnl-layout-half-vertical.html` - Half vertical (not supported message)
- `trmnl-layout-quadrant.html` - Quadrant layout (image + title)
- `trmnl-layout-shared.html` - Shared section (CSS/JS only, prepended to all layouts)
- `preview.html` - Local preview file

## TRMNL Framework

Use native TRMNL classes wherever possible:
- Layout: `layout`, `layout--col`, `layout--row`, `gap--small`, `gap--medium`
- Grid: `grid`, `grid--cols-2`, `grid--cols-3`, `col--span-1`, `col--span-2`
- Typography: `title`, `title--small`, `description`, `label`, `label--small`, `label--underline`
- Spacing: `mt--small`, `mb--small`, `pb--small`, `p--small`
- Footer: `title_bar` with `.image`, `.title`, `.instance`

Minimize inline styles - only use for properties without native classes (border, filter, etc.)
