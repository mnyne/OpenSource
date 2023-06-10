# OpenSource
OpenSource (get it?) is a large list of guitar-game source icons, and source names, in different languages!

![Banner](./ignore/banner.png)

# 📝 Specifications for Use

The icons are split into two folders: `base`, and `extra`. `base` is meant for super-common, widely-used icons, and should only contain icons of official games. `extra` is meant for everything else! The reason for this is due to file sizes, and updates. In YARG, the `base` folder is included in the game, while the `extra` folder is updated and stored on its own.

Everything in the `ignore` folder can be ignored, and are only used for repo stuff (like the banner in this README).

In each of these folders, there is a `index.json` file, which contains the index of icons, IDs, and source names. Specifications for that are below.

**All icons must be in `.png` and must follow the design guidelines!**

## `index.json`

| Key | Description | Data type / Possible values |
| --- | --- | --- |
| `type` | The type of index. | `"base"` or `"extra"`
| `sources` | The array containing all of the source information. | `Source[]`

## `Source`

| Key | Description | Data type / Possible values | Example |
| --- | --- | --- | --- |
| `ids` | An array of strings containing all of the possible IDs for the specific source. This is the same ID that shows up in `song.ini`'s `icon` tag, etc. **All IDs should be unique, and must be all lowercase!** The `$DEFAULT$` ID is reserved for the fallback source and is defined in `base/index.json`. | `string[]` | `"ids": [ "gh", "gh1" ]` |
| `names` | An object of display names in different locales. `en-US` must be present (as that is the fallback). | `locale: name` where `locale` is from [this list](https://learn.microsoft.com/en-us/bingmaps/rest-services/common-parameters-and-types/supported-culture-codes), and `name` is a display name in that locale. | `"names": { "en-US": "Guitar Hero" }` |
| `icon` | The name of the icon file. Omit the `.png`. Icons from `base` can be used in `extra`, but **not** vice-versa. | `string` | `"icon": "gh"` |
| `type` | The type of source. | `"custom"`, `"game"`, `"charter"`, `"rb"`, or `"gh"`. `"rb"` and `"gh"` are limited to those specific game types. | `"type": "gh"` |

# ✅ Verifying Indexes

If you run the `verify.py` file in the repo's folder, it will verify both `index.json` files and look for issues. Possible issues are:
- Duplicate icons in `base` and `extra` (error)
- Duplicate source IDs (error)
- Duplicate en-US names (warning)
- Icon file doesn't exist (error)
- Unused icons (warning)

# 🆕 Guidelines for NEW Sources

> **Note**
> This is for adding **NEW** sources. Sources already that exist in other games should just use their already assigned IDs for compatibility purposes.

Sources may be added when:
- A new guitar-game releases
- A popular charter wants their icon in the game
- A non-small charting project is finished

Obviously, "popular" and "non-small" are quite vague, but we just don't want icons to be added if only one or two songs use it. That's wasteful.

When assigning an ID to a source, **make sure to be as specific as possible**. For example, a source named "Elite's Songs" shouldn't use the ID of `es`, but rather `elites_songs`. This eliminates the possibility of ID conflicts, as someone else's source named "Enraged Singing" could also use `es` (which is not allowed).

Names **should not** use trailing or leading underscores (`_`) to solve ID conflicts. That is misleading, and can cause confusion. For example, if a discography project of band named "Grave Hunter" wanted to use `gh`, but chose to use `gh_` or `_gh` as their ID since `gh` was taken, that is bad. Use `gravehunter` or `grave_hunter` instead.

Charters **should always** use their full name as their ID, and only their name in the display name. For example, I should not be using "Elite's Songs" and `elites_songs`, but rather "EliteAsian" and `eliteasian`.

# 🛡️ License

OpenSource is licensed under the Unlicense License (completely public domain) - see the [`LICENSE`](../master/LICENSE) file for details.

Credit would be nice, but is definately not required.