# Bootlegs
All of these carts:
- Come from AliExpress.
- Ignore writes to `$4000.2-7` and are therefore restricted to 32 KiB of RAM.
- Except for the multicart, they ignore writes to `$3000`, so they are restricted to 4 MiB of ROM.
- Do not specifically support MBC1.

<div style="white-space: nowrap !important;">
  
| Game            | MBC | Size | RAM | Shell       | Bat | PCB                   | ROM  | ROM IC                 | RAM | RAM IC                  | Ordered @ Ali Store                | Arrived  | CSum | Photo | CFI | Dump
| --------------- | --- | ---: | --: | ----------- | --- | --------------------- | ---: | ---------------------- | --: | ----------------------- | ---------------------------------- | -------- | ---- | ---   | ---- | ----
| Perfect Dark    |5+RBL| 4096 |   8 | DMG Grey    | yes | SD007_BGA48_BGA48_T28 | 8192 | Micron M29W640GB6AZA6E |  32 | Sony CXK58267ATM 10L    | 24.02.25 @ Pokegame                | 01.03.25 |`207D`| TBA | TBA | unchanged
| Pokémon TCG2    |   5 | 4096 |  32 | DMG Grey    | no  | SD007_BGA48_BGA48_T28 | 8192 | Samsung K8D3216UBC     |  32 | SI IC61LV256 8TG        | 24.02.25 @ Pokegame                | 01.03.25 |`ECA1`|
| Grimace's Bday  |   5 | 1024 |  32 |DMG Transblue| yes | SD007_BGA48_BGA48_T28 | 8192 | Micron M29W640GB6AZA6E | 256 | Winbond W26B02B 70LE    | 02.03.25 @ Treasure Game Accessory | 11.03.25 |`207D`| TBA | TBA | unchanged
| Hime's Quest    |   5 | 2048 |  32 | DMG Orange  | yes | SD007_BGA48_BGA48_T28 | 8192 | Micron M29W640GB6AZA6E |  32 | Cypress CY7C199L 15ZC   | 02.03.25 @ Pokegame                | 11.03.25 |`207D`| TBA | TBA | unchanged
| Perfect Dark    |5+RBL| 4096 |   8 | DMG Grey    | yes | SD007_BGA48_BGA48_T28 | 8192 | Samsung K8D3216UBC     |  32 | Toshiba TC55257DFTI 85L | 02.03.25 @ Pokegame                | 11.03.25 |`ECA1`| TBA | TBA | unchanged
| Pokémon Crystal |3+RTC| 2048 |  32 | CGB Crystal | no  | unknown               | 4096 | MXIC 29LV320DTTI-70G   |  32 | Hynix HY62256A          | 02.03.25 @ Pokemon Card            | 11.03.25 |`207D`|
| 18-in-1         |   1 |   32 |   2 | DMG Blue    | yes | SD008_512ND_4M        |32768 | MXIC 29CL256EHT27-90Q  |1024 | Samsung K6F8016U6D XF55 | 05.03.25 @ Glygame                 | 12.03.25 |`C17D`|

</div>

- Shells tagged as CGB prevent you from turning on a DMG.
- All sizes are given in Kibibytes. Grimace has a nominal 128 Kibiwords and 18-in-1 has a nominal 512 Kibiwords of RAM.
- Checksum is given as individual hex bytes (aka big endian), so first two nibbles are $14E and the other two are $14F. All these checksums are invalid, but the Game Boy doesn't care.
- "unchanged" in Dump column means that the invalid checksum is the only change compared to No-Intro.

## Battery
Batteryless games save to ROM. This is fine, as all ROM ICs are designed to withstand 100,000 writes. However, you're supposed to write at 3.3V, but most carts lack a level shifter to 5V. You can recognize batteryless ROM images by the music stopping for around 1 second when they write back your save to ROM.

Because of the 64 KiB erase sector size of the above ROM ICs (ROM sectors must be erased before being written), batteryless saving is only possible in games with 64 KiB of unused space at an address divisable by 64 KiB (called an aligned 64 KiB sector). As explained earlier, no single-game repro cart supports 8 MiB of ROM, so it's safe to assume that all carts shipping with a 4 MiB image will have a battery if the ROM image does not have an aligned 64 KiB sector of free space. Here's a list of commonly-available 4 MiB games on AliExpress:
- Games without a free 64 KiB sector (safe to assume that these battery-save): Dragon Warrior III, Grandia - Parallel Trippers, Perfect Dark, Resident Evil (if second prototype)
- Games with free 64 KiB sector in-between: Daikatana (if US prototype; JP is only 1 MiB), Donkey Kong Country, Resident Evil (if first prototype), Tomb Raider, Tomb Raider - Curse of the Sword
- Games that leave at least 64 KiB free space at the end: Cannon Fodder, Ghostly Labyrinth 2, Metal Gear Solid (EU; US is only 2 MiB), Pokémon TCG2 (fan translation; JP is only 2 MiB; see below for more info), Shantae (known to not have a battery)

This is the reason why Perfect Dark is usually recommended to anyone who wants to get a cart with standard SRAM (meaning you do not need a modified ROM to be able to save).

Due to the way GB Studio saves, most GB Studio games are batteryless as well, though the lavender Grimace's Birthday is batteryless. GB Studio has a feature to save batteryless ROMs, but such ROMs are rarely published.

## Notes on the Games
## TCG2
This is the artemis251 translation. It saves at `$292000-$293FFF`, `$296000-$297FFF`, `$29A000-$29BFFF` and `$29E000-$29FFFF`. This is inside the defined ROM size, but the ROM actually only uses the first $284000 bytes. Before being translated, the game was only a 2 MiB ROM.

Duel autosave is not written to ROM (lags would be very annoying), so this is lost if you turn off power during a duell. If you want to access your duel autosave to return to the state before you attacked, you must therefore press Start+Select+A+B.

## Crystal
It saves at `$212000-$213FFF`, `$216000-$217FFF`, `$21A000-$29BFFF` and `$21E000-$21FFFF`. This is outside of the 2 MiB ROM.

This batteryless version is based on the Rev A (Rev 1) version of the ROM.

### Grimace's Birthday
This is v1.7. It was the only one to come without a case.

### 18-in-1 (GB HICOL)
By default, the multicart is a 8 MiB cart with 32 KiB of RAM. You can just burn _Densha De Go! 2_ or _Kanji Shishuu_. (I did not burn anything yet, though.)

The menu does not access its 2 KiB of RAM.

The multicart stores four values per game starting at $46FE. They end up in A, $7002, $7001 and $7000.
- A: See [here](https://gbdev.io/pandocs/Power_Up_Sequence.html#cpu-registers).
- $7002.0-1: The 8 MiB multirom bank.
- $7002.2-3: Unknown, probably unused.
- $7002.4: Unknown, always set.
- $7002.5: Unknown, never set.
- $7002.6: SRAM disable.
- $7002.7: Lock mapper (so you cannot change multirom bank anymore). Useful for burning. Annoying when reading.
- $7001: 256 - [ROM size in bytes]/32768.
- $7000: [ROM offset in multirom bank]/32768

Because they are first pushed to the stack and then read from there, these four bytes are written in reverse (A is written last). Unlike e.g. EZ-Flash Jr., this cart does not reset but jump to the ROM's entry point at $100. As the first three writes already trigger the ROM switch (so the menu ROM is no longer available), the code that writes these four bytes and the stack resides in HRAM. After switching the ROM but before loading A and resetting, it configures the cart's MBC5 to bank 1 ($3000=0, $2000=1).

ROMs at floor([ROM offset]/2 MiB) share 32 KiB of RAM. As there's 16 chunks of 2 MiB in the 32 MiB ROM, there's 16 SRAM slots for a total of 512 KiB.
