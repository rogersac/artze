# Met Art Fullscreen Display

This project is a single-page browser app that searches the Metropolitan Museum of Art collection and displays public domain paintings fullscreen as a rotating slideshow.

## Image source

Images and artwork metadata come from The Metropolitan Museum of Art Collection API:

- Search endpoint: `https://collectionapi.metmuseum.org/public/collection/v1/search`
- Object detail endpoint: `https://collectionapi.metmuseum.org/public/collection/v1/objects/{id}`

The app searches for matching object IDs first, then fetches object details as each slideshow item is about to be shown. It only displays objects that:

- are public domain
- have a primary image
- are identified as paintings

The caption shown over for each image includes the artwork title, artist, date, and a note that the image and metadata come from the Met Open Access collection.

## Display settings

### Search term

Required. This text is sent to the Met search API as the query string and determines which candidate artworks are considered for display.

Examples:

- `Monet`
- `landscape`
- `flowers`
- `Van Gogh`

### Seconds per painting

Controls how long each artwork stays on screen before the slideshow advances automatically.

- Minimum: `5`
- Maximum: `3600`
- Default: `60`

### Maximum paintings to load

Controls how many candidate results the app tries to work with for the slideshow.

- Minimum: `1`
- Maximum: `100`
- Default: `30`

The app may inspect more than this number of raw search candidates behind the scenes so it can find enough usable paintings.

### Department

Narrows the search to a specific Met department, or searches across all departments when left at `Any department`.

Available options:

- `Any department`
- `European Paintings`
- `Modern and Contemporary Art`
- `American Paintings and Sculpture`
- `Asian Art`

### Image orientation

Filters images by aspect ratio after the object detail is loaded.

Available options:

- `Any orientation`
- `Horizontal / landscape`
- `Vertical / portrait`
- `Square`

### Always show caption

Controls whether the artwork caption stays visible at all times during the slideshow.

- Enabled: the caption stays visible continuously.
- Disabled: the caption is only visible while the temporary slideshow controls are visible.

## Slideshow interaction

When images are being displayed:

- Tap or click anywhere on the viewer to temporarily show the controls and hint text.
- Use `Next` to skip to the next artwork immediately.
- Use `Stop` to exit the slideshow and return to the settings screen.
- Press the `Right Arrow` key to advance to the next artwork.
- Press `Escape` to stop the slideshow.

The temporary controls fade away automatically after a short delay. If `Always show caption` is disabled, the caption follows the same visibility behavior.

## Running the app

This repo currently consists of a single `index.html` file. Open it in a browser to use the app.
