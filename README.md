# Daily AI News - TRMNL Plugin

A plugin for [TRMNL](https://usetrmnl.com) e-ink displays that shows the latest AI news headlines, summaries, and action items from [Daily AI by AI](https://dailyaibyai.news).

## Features

- **AI-generated hero image** prominently displayed
- Daily AI news headlines and summaries
- Actionable takeaways for staying current with AI developments
- Clean e-ink optimized layout with grayscale image processing
- Branded title bar with dailyaibyai.news link
- Links to full episodes and podcast

## Plugin Variants

### Full Screen Layout (`trmnl-plugin-full.html`)
- 800x480 pixels (full TRMNL OG display)
- Uses TRMNL native elements (`view`, `layout`, `grid`, `title`, `description`, `label`, `title_bar`)
- Vertical column layout: stories at top, hero image + actions in lower section
- Shows 4 stories with summaries and 3 action items
- Native `title_bar` footer with "DAILY AI" branding
- Best for dedicated news display

### Half Vertical Layout (`trmnl-plugin-half.html`)
- 390x460 pixels (half of display)
- Uses TRMNL native elements for consistent styling
- Compact header with thumbnail image and headline
- Shows 3 stories and 2 action items
- Good for combining with other plugins in a mashup

## Setup Instructions

### 1. Create a Private Plugin in TRMNL

1. Log into your TRMNL account at [usetrmnl.com](https://usetrmnl.com)
2. Go to **Plugins** > **Private Plugins**
3. Click **Create New Plugin**

### 2. Configure the Data Source

In the plugin settings, set up the polling URL:

- **Polling URL**: `https://static.dailyaibyai.news/summary/latest.json`
- **Polling Interval**: Recommended 3600 seconds (1 hour) or more

### 3. Add the Markup

1. Copy the contents of your preferred layout file (`trmnl-plugin-full.html` or `trmnl-plugin-half.html`)
2. Paste into the TRMNL plugin markup editor
3. Use the live preview to verify the layout

### 4. Configure Display Settings

- **Layout Size**: Select "Full" for the full layout, or "Half Vertical" for the compact version
- **Playlist Position**: Choose where in your rotation this plugin appears

## JSON Data Structure

The plugin expects data in this format from the API:

```json
{
  "date": "2026-01-03",
  "title": "OpenAI Launches Voice-First Hardware with Jony Ive Partnership",
  "stories": [
    {
      "headline": "ByteDance orders $54 billion in Nvidia AI chips",
      "summary": "Chinese companies are placing massive orders for Nvidia chips..."
    }
  ],
  "action_items": [
    "Monitor AI chip supply dynamics for investment opportunities",
    "Evaluate voice-first AI interfaces for product development"
  ],
  "episode_url": "https://dailyaibyai.news",
  "generated_at": "2026-01-03T07:15:00.000000"
}
```

## Customization

### Modify Story Count

To show more or fewer stories, edit the `limit` parameter in the Liquid loops:

```liquid
{% for story in stories limit:3 %}
```

### Adjust Truncation

Control text length with the `truncate` filter:

```liquid
{{ story.summary | truncate: 120 }}
```

### Styling

The plugin uses TRMNL's native elements and CSS framework:
- `view view--full` / `view view--half_vertical` - main containers
- `layout layout--col` - vertical layouts
- `grid grid--cols-2` - two-column grids
- `title` / `title--small` - headlines
- `description` - body text with automatic sizing
- `label` / `label--small` / `label--underline` - labels and headers
- `title_bar` - native footer component

See [TRMNL Framework Documentation](https://usetrmnl.com/framework) for all available classes.

## Links

- **Daily AI by AI Website**: [dailyaibyai.news](https://dailyaibyai.news)
- **TRMNL Documentation**: [docs.usetrmnl.com](https://docs.usetrmnl.com)
- **TRMNL Framework**: [usetrmnl.com/framework](https://usetrmnl.com/framework)

## License

MIT License - Feel free to modify and adapt for your needs.
