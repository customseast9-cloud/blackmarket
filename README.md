







<img width="974" height="625" alt="Screenshot 2026-05-18 173449" src="https://github.com/user-attachments/assets/a138ea95-d5da-446b-8109-44381737696e" />


# Black Market System for FiveM (QBCore)

A clean, QBCore-only black market resource for FiveM. Players can visit a location, open the shop UI, and buy items defined in `config.lua`.

## What this script has

- QBCore-only support
- NUI shop menu with categories
- Shared item validation against `shared/items.lua`
- Item purchase notifications
- Optional black market blip toggle
- Local or external image support
- Close button inside the menu

## Requirements

- `qb-core`
- `qb-inventory`
- QBCore server environment

## Installation

1. Copy the `blackmarket` folder into your server's `resources` directory.
2. Add this to your `server.cfg`:

```cfg
ensure blackmarket
```

3. Restart your server or run `refresh` and `ensure blackmarket`.

## Configuration

Edit `config.lua` to set up the shop.

### Main settings

```lua
Config.SharedItemsPath = '../[qb]/qb-core/shared/items.lua' -- Path to QBCore shared items
Config.InventoryType = 'qb' -- QBCore inventory only
Config.ImageBasePath = 'nui://qb-inventory/html/images/' -- Local or QB inventory image path
Config.ShowBlip = true -- Toggle shop blip on/off
Config.PedModel = 'a_m_m_business_01' -- Shop NPC model
Config.Framework = 'qbcore'
```

### Shop locations

Add or change one or more black market points:

```lua
Config.Locations = {
    { x = 621.68, y = 656.18, z = 128.91, h = 139.9 },
}
```

### Shop items

Define items by category:

```lua
Config.Items = {
    Weapons = {
        { name = 'security_card_01', label = 'Security Card Level 1', description = 'Access to basic secure areas.', price = 5000, amount = 50 },
    },
    Tools = {
        { name = 'electronickit', label = 'Electronic Kit', description = 'Used for advanced electronic jobs.', price = 5000, amount = 50 },
    },
}
```

#### Item fields

- `name` — must match a QBCore shared item entry
- `label` — displayed in the UI
- `description` — shown in the menu
- `price` — cash cost
- `amount` — stock count shown in menu
- `image` (optional) — custom image filename

## Image setup

### QB Inventory image folder

Use the built-in QB inventory image path:

```lua
Config.ImageBasePath = 'nui://qb-inventory/html/images/'
```

Then item images should be named like `item_name.png`.

### Local image folder

For images stored inside this resource, use:

```lua
Config.ImageBasePath = 'images/'
```

Place your PNGs in `blackmarket/nui/images/`.

### Custom image names

Example:

```lua
{ name = 'special_item', label = 'Special', description = '...', price = 1000, amount = 5, image = 'custom.png' }
```

### Fallback image

If no image is found, the menu uses `fallback.png`.

## How to use

- Go to a configured black market location.
- Press `E` to open the shop.
- Browse categories and click `BUY`.
- Close the menu with the `CLOSE` button or `ESC`.

## Commands

- `/blackmarketblip` — toggle the black market blip on or off.

## Troubleshooting

- **No notify on purchase?**
  - Ensure `qb-core` is active and `QBCore:Notify` is available.
- **Images missing?**
  - Confirm `Config.ImageBasePath` and image filenames.
  - If using local images, place them in `blackmarket/nui/images/`.
- **Purchase blocked?**
  - Verify `Config.SharedItemsPath` points to your QBCore shared item file.
  - Check server logs for errors.

---

### Notes

- This resource is built for QBCore only.
- The shop validates item names before purchase.
- Notifications show the purchased item and amount spent.
