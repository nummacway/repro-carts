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

- Shells tagged as CGB prevent you from turning on the DMG.
- All sizes are given in Kibibytes. Grimace has a 128 Kibiwords of RAM, 18-in-1 has 512 Kibiwords of RAM.
- Checksum is given as individual hex bytes (aka big endian), so first two nibbles are $14E and the other two are $14F. All these checksums are invalid.
- Unchanged in Dump column means that there invalid checksum is the only change compared to No-Intro.

## Notes on Games
## TCG2
This is the artemis251 translation. It saves at $292000-$293FFF, $296000-$297FFF, $29A000-$29BFFF and $29E000-$29FFFF. This is inside the defined ROM size, but the ROM actually only uses the first $284000 bytes. Before being translated, the game was only a 2 MiB ROM.

## Crystal
It saves at $212000-$213FFF, $216000-$217FFF, $21A000-$29BFFF and $21E000-$21FFFF. This is outside of the 2 MiB ROM.

### Grimace's Birthday
This is v1.7. It was the only one to come without a case.

### 18-in-1
By default, the multicart is a 8 MiB cart with 32 KiB of RAM. You can just burn _Densha De Go! 2_ or _Kanji Shishuu_.

The menu does not access its 2 KiB of RAM.

The multicart stores four values per game starting at $46FE. They end up in A, $7002, $7001 and $7000.
- A: See [here](https://gbdev.io/pandocs/Power_Up_Sequence.html#cpu-registers). Unlike e.g. EZ-Flash Jr., this cart does not reset but jump to the ROM's entry point at $100. The code that writes these four bytes and the stack therefore reside in HRAM.
- $7002.0-1: The 8 MiB multirom bank.
- $7002.2-3: Unknown, probably unused.
- $7002.4: Unknown, always set.
- $7002.5: Unknown, never set.
- $7002.6: SRAM disable.
- $7002.7: Lock mapper (so you cannot change multirom bank anymore). Useful for burning. Annoying when reading.
- $7001: 256 - [ROM size in bytes]/32768.
- $7000: [ROM offset in multirom bank]/32768

Because they are first pushed to the stack and then read from there, these four bytes are written in reverse.

ROMs at floor([ROM offset]/2 MiB) share 32 KiB of RAM. As there's 16 chunks of 2 MiB in the 32 MiB ROM, there's 16 SRAM slots.
