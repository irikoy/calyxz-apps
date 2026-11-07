# Calyxz apps

The app store for Calyxz OS, a home server. Each Calyxz machine reads `index.json` once a day and shows these apps in its store, ready to install with one tap.

Every entry is a ready-filled install form. The machine checks each one exactly like a form filled in by hand, leaves out any entry that doesn't pass, and its root helper checks the install again before anything runs. So an entry can never ask for more than the form allows. No full machine access, no folders beyond its own and the media folder, and nothing beyond the fixed list of permissions, which the owner approves one by one.

Every app listed here has been tried on a real Calyxz machine first. An app that can't run on a given machine stays listed there with the reason, so it shows up by itself on a machine that can run it.

## An entry

```json
{
  "id": "jellyfin",
  "name": "Jellyfin",
  "tagline": "One line, up to 120 characters.",
  "description": "A few sentences, up to 2000 characters.",
  "category": "media",
  "icon": "film",
  "logo": "logos/jellyfin.png",
  "website": "https://jellyfin.org",
  "needs": [{ "arch": ["arm64", "amd64"] }, { "memory_mb": 1536 }],
  "form": { "source": "jellyfin/jellyfin", "port": 8096, "app_port": 8096 }
}
```

- `id`: lowercase letters, digits and dashes, up to 40.
- `category`: one of `media`, `photos`, `files`, `home`, `productivity`, `network`, `developer`, `other`.
- `icon`: one of Calyxz's own icons, shown when there's no logo.
- `logo`: optional. A PNG, WebP or JPEG under `logos/`, at most 256 KB. Never SVG.
- `website`: optional, `https://` only.
- `needs`: what the machine must have.
  - `arch`, a list of processors, like `arm64` and `amd64`
  - `memory_mb`
  - `kernel`, a kernel setting without `CONFIG_`
  - `kernel_at_least`
  - `cpu`, a processor feature
  - `disks`
  - `"https"`
  - `"graphics"`
- `form`: the install form without its name.
  - `source`, `port`, `app_port`, `reachable`, `settings`, `folders`
  - `allow`, from `graphics`, `usb` and `home_network`
  - `helpers`, up to four ready-made images beside it, like a database
  - `follow`, `releases` or `every_build`

## Credits

The Jellyfin logo belongs to the Jellyfin project and is used here to name their app.
