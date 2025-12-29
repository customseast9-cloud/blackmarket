







<img width="1092" height="1079" alt="Screenshot 2025-12-27 220845" src="https://github.com/user-attachments/assets/96c1dee9-3d31-4af5-820b-0a5795e273af" />
<img width="1015" height="1072" alt="Screenshot 2025-12-27 220820" src="https://github.com/user-attachments/assets/68ba92a2-9891-4069-a015-bc874ec83f17" />
<img width="1199" height="1052" alt="Screenshot 2025-12-27 220856" src="https://github.com/user-attachments/assets/08fc9b79-5da5-4ffb-b5b7-5bc2cea87b28" />










# Black Market System for FiveM (QBCore/ESX)

## Installation

1. **Download & Extract**
   - Download this resource and place the `blackmarket` folder in your server's `resources` directory.

2. **Add to server.cfg**
   - Add the following line to your `server.cfg`:
     ```
     ensure blackmarket
     ```

3. **Dependencies**
   - QBCore: Requires `qb-core` and `qb-inventory`.
   - ESX: Requires `es_extended` and `ox_inventory`.
   - Make sure your framework and inventory match your config settings.

## Configuration

Open `config.lua` to customize the Black Market:

- **Framework**: Set your framework:
  ```lua
  Config.Framework = 'qbcore' -- or 'esx'
  ```
- **Inventory Type**: For ESX, set to 'ox' if using ox_inventory:
  ```lua
  Config.InventoryType = 'qb' -- or 'ox'
  ```
- **Locations**: Add or change Black Market locations:
  ```lua
  Config.Locations = {
      {x = 621.68, y = 656.18, z = 128.91, h = 139.9},
      -- Add more locations as needed
  }
  ```
- **Items**: Items are grouped by category. Example:
  ```lua
  Config.Items = {
      Weapons = {
          { name = 'security_card_01', label = 'Security Card Level 1', description = 'Access to basic secure areas.', price = 5000, amount = 50 },
          -- Add more items
      },
      Tools = {
          { name = 'electronickit', label = 'Electronic Kit', description = 'Used for advanced electronic jobs.', price = 5000, amount = 50 },
      },
      -- Add more categories/items
  }
  ```

## Adding Items

1. **Add to Config**
   - Open `config.lua` and add your item to the appropriate category, or create a new category.
   - Example:
     ```lua
     Config.Items = {
         Weapons = {
             { name = 'weapon_pistol', label = 'Pistol', description = 'A basic handgun.', price = 10000, amount = 10 },
         },
         Misc = {
             { name = 'markedbills', label = 'Marked Bills', description = 'Illegally obtained cash.', price = 5000, amount = 50 },
         }
     }
     ```
   - **Fields:**
     - `name`: The item/weapon spawn name (must match your inventory system)
     - `label`: Display name
     - `description`: Short description
     - `price`: Price in cash
     - `amount`: Stock available (not enforced by default)
     - `image` (optional): Custom image filename (see below)

## Adding Images

1. **Image Location**
   - Place your PNG images in `blackmarket/nui/images/`.
   - Image filenames should match the item `name` (e.g., `security_card_01.png`).
   - For weapons, use the weapon spawn name (e.g., `weapon_pistol.png`).

2. **Custom Image**
   - To use a custom image filename, add the `image` field to your item:
     ```lua
     { name = 'special_item', label = 'Special', description = '...', price = 1000, amount = 5, image = 'mycustomimage.png' }
     ```
   - Place `mycustomimage.png` in the `nui/images/` folder.

3. **Fallback Image**
   - If an image is missing, the menu will use `fallback.png` from the same folder. You can replace this with your own default image.

## Usage

- Approach a Black Market location and press `E` to open the menu.
- Browse categories and buy items. Items are delivered to your inventory if you have enough cash.

## Troubleshooting

- **Images not showing?**
  - Make sure the image file exists in `nui/images/` and matches the item name or custom image field.
  - Check fxmanifest.lua includes `'nui/images/*.png'`.
- **Can't buy items?**
  - Ensure your framework and inventory type are set correctly in `config.lua`.
  - Check server console for errors.
- **Menu not opening?**
  - Make sure you are at a configured location and no errors appear in F8 or server console.

## Credits
- UI inspired by modern admin panels

---
For support, open an issue or contact the author.
