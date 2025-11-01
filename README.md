# Unity Essentials

This module is part of the Unity Essentials ecosystem and follows the same lightweight, editor-first approach.
Unity Essentials is a lightweight, modular set of editor utilities and helpers that streamline Unity development. It focuses on clean, dependency-free tools that work well together.

All utilities are under the `UnityEssentials` namespace.

```csharp
using UnityEssentials;
```

## Installation

Install the Unity Essentials entry package via Unity's Package Manager, then install modules from the Tools menu.

- Add the entry package (via Git URL)
    - Window → Package Manager
    - "+" → "Add package from git URL…"
    - Paste: `https://github.com/CanTalat-Yakan/UnityEssentials.git`

- Install or update Unity Essentials packages
    - Tools → Install & Update UnityEssentials
    - Install all or select individual modules; run again anytime to update

---

# UI Fonts

> Quick overview: Curated UI font families, an emoji sprite sheet, TextMeshPro style sheet, and a full set of TMP shaders (Built‑in/URP/HDRP/Mobile) to make text look consistent across pipelines.

This module bundles several high‑quality fonts for UI/HUD, an EmojiOne sheet you can import as a TMP Sprite Asset, a default TextMeshPro Style Sheet, and the full suite of TMP shaders (including URP/HDRP variants) so you can pick the right material per target platform and render pipeline.

![screenshot](Documentation/Screenshot.png)

## Features
- Fonts included (raw TTF/OTF; some with ready‑made TMP assets)
  - Cascadia Mono (includes `Cascadia Mono SDF.asset`)
  - Inter (variable fonts; static set in `Fonts/Inter/static`)
  - Courier, Rajdhani, VCR OSD Mono, Verily Serif Mono, Escobario, EAS Again Alt 2 Mono, Liberation Sans
- Emoji sprite sheet
  - `Sprites/EmojiOne.png` + `EmojiOne.json` + attribution (EmojiOne Attribution.txt)
  - Importable as a TextMeshPro Sprite Asset for inline emoji in text
- TextMeshPro shaders for all pipelines
  - Built‑in: SDF/Bitmap, Overlay, Mobile, SSD, Surface
  - URP/HDRP ShaderGraph variants included (Lit/Unlit)
- Default TMP Style Sheet
  - `Resources/Style Sheets/Default Style Sheet.asset` for shared tags/styles

## Requirements
- Unity 6000.0+
- TextMeshPro (bundled with Unity)
- URP/HDRP only if you plan to use the corresponding shadergraph variants

## Usage

### 1) Create TMP Font Assets from the included fonts
- For families without a prebuilt asset (e.g., Inter, Rajdhani, …):
  - Project window: right‑click the `.ttf` → Create → TextMeshPro → Font Asset
  - Or use Window → TextMeshPro → Font Asset Creator, then Save
- For Cascadia Mono, you can use the provided `Cascadia Mono SDF.asset` directly
- Optional: set fallback fonts on your Font Assets (e.g., emoji sprite asset) for broader coverage

### 2) Import the EmojiOne sprite asset
- Window → TextMeshPro → Sprite Importer (or Sprite Asset creator)
  - Texture: `Assets/…/Unity.UI.Fonts/Sprites/EmojiOne.png`
  - JSON/Mapping: `Assets/…/Unity.UI.Fonts/Sprites/EmojiOne.json` (if your importer supports a mapping file)
  - Save the generated TMP Sprite Asset
- Assign the sprite asset globally (Project Settings → TextMeshPro → Default Sprite Asset)
  - Or assign per Text component via the “Sprite Asset” field
- Use in text via `<sprite name="...">` or the mapped Unicode

### 3) Apply the default TMP Style Sheet (optional)
- Project Settings → TextMeshPro → Default Style Sheet
- Set to: `Resources/Style Sheets/Default Style Sheet.asset`

### 4) Choose appropriate shaders/materials
- Built‑in RP: use standard TMP SDF/Bitmap shaders (Mobile/Overlay variants for performance)
- URP/HDRP: use the included ShaderGraph variants (Lit/Unlit) for pipeline‑native rendering
- If materials look pink after changing RP, swap to the matching URP/HDRP shader variant

## Notes and Limitations
- Licensing
  - Each font includes its own license (e.g., Inter under OFL). The EmojiOne attribution file is included; ensure compliance when redistributing
- Coverage and glyph sets vary by family; set fallbacks for missing characters/emoji
- Sprite Asset importers differ by Unity/TMP version; if JSON mapping isn’t supported, create the sprite asset and map glyphs manually
- ShaderGraph variants require the corresponding pipeline packages; otherwise use the Built‑in shaders

## Files in This Package
- `Fonts/*` – Family folders (Cascadia Mono, Inter, Courier, Rajdhani, VCR OSD Mono, Verily Serif Mono, Escobario, EAS Again Alt 2 Mono, Liberation Sans)
  - Example: `Fonts/Cascadia Mono.ttf`, `Fonts/Cascadia Mono SDF.asset`
- `Sprites/EmojiOne.png`, `Sprites/EmojiOne.json`, `Sprites/EmojiOne Attribution.txt` – Emoji sprite sheet and mapping
- `Shaders/*` – Full TextMeshPro shader set (SDF/Bitmap, Mobile, Overlay, Surface, SSD, URP/HDRP ShaderGraphs)
- `Resources/Style Sheets/Default Style Sheet.asset` – Default TextMeshPro Style Sheet
- `LICENSE.md` – Licenses for packaged assets

## Tags
unity, ui, text, font, tmp, textmeshpro, emoji, sprite asset, style sheet, shaders, urp, hdrp
