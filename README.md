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
If a repro cart has a battery (that is not empty), you can simply put on any ROM. Pokémon ROMs will also work in Pokémon Stadium.

Batteryless games save to ROM. This is fine, as all ROM ICs are designed to withstand 100,000 writes. However, you're supposed to write at 3.3V, but most carts lack a level shifter from 5V. You can recognize batteryless ROM images by the music stopping for around 1 second when they write back your save to ROM.

Because of the 64 KiB erase sector size of the above ROM ICs (ROM sectors must be erased before being written), batteryless saving is only possible in games with 64 KiB of unused space at an address divisable by 64 KiB (called an aligned 64 KiB sector). As explained earlier, no single-game repro cart supports 8 MiB of ROM, so it's safe to assume that all carts shipping with a 4 MiB image will have a battery if the ROM image does not have an aligned 64 KiB sector of free space. Here's a list of commonly-available 4 MiB games on AliExpress:
- Games without a free 64 KiB sector (safe to assume that these battery-save): Dragon Warrior III, Grandia - Parallel Trippers, Perfect Dark, Resident Evil (if second prototype)
- Games with free 64 KiB sector in-between: Daikatana (if US prototype; JP is only 1 MiB), Donkey Kong Country, Resident Evil (if first prototype), Tomb Raider, Tomb Raider - Curse of the Sword
- Games that leave at least 64 KiB free space at the end: Cannon Fodder, Ghostly Labyrinth 2, Metal Gear Solid (EU; US is only 2 MiB), Pokémon TCG2 (fan translation; JP is only 2 MiB; see below for more info), Shantae (known to not have a battery)

This is the reason why Perfect Dark is usually recommended to anyone who wants to get a cart with standard SRAM (meaning you do not need a modified ROM to be able to save).

Due to the way GB Studio saves, most GB Studio games are batteryless as well, though the lavender Grimace's Birthday is batteryless. GB Studio has a feature to save batteryless ROMs, but such ROMs are rarely published (because they primarily profit bootleggers).

## Notes on the Carts
### TCG2
This is the artemis251 translation. It saves at `$292000-$293FFF`, `$296000-$297FFF`, `$29A000-$29BFFF` and `$29E000-$29FFFF`. This is inside the defined ROM size, but the ROM actually only uses the first $284000 bytes. Before being translated, the game was only a 2 MiB ROM.

Duel autosave is not written to ROM (lags would be very annoying), so autosave is gone if you turn off power during a duel. If you want to access your duel autosave to return to the state before you attacked, you must therefore press Start+Select+A+B.

### Crystal
It saves at `$212000-$213FFF`, `$216000-$217FFF`, `$21A000-$29BFFF` and `$21E000-$21FFFF`. This is outside of the 2 MiB ROM.

This batteryless version is based on the Rev A (Rev 1) version of the ROM.

This is my only shell to say "GAME BOY COLOR" and the only one with the original screw location. I think the shell is very pretty.

### Grimace's Birthday
This is v1.7. It was the only one to come without a case.

This is my only shell to just say "GAME".

### 18-in-1 (GB HICOL MC03, MC003)
By default, the multicart is a standard 8 MiB MBC5 cart with 32 KiB of RAM. You can just burn _Densha De Go! 2_ or _Kanji Shishuu_. (I did not burn anything yet, though.) This makes multicarts the by far cheapest carts to support the CGB's biggest ROM size of 8 MiB.

The menu does not access its 2 KiB of RAM.

The multicart stores four values per game starting at $46FE. They end up in `A`, `$7002`, `$7001` and `$7000`.
- A: See [here](https://gbdev.io/pandocs/Power_Up_Sequence.html#cpu-registers). This shouldn't be hardcoded. They should have pushed `A`'s initial value (`AF` to be correct) to the stack and used that. The way this is done, many DMG-compatible CGB games will either not run on DMG or CGB, depending on the value, because the menu's cartridge header sets the CGB into CGB mode. DMG-only games will not work properly on the CGB, because they keep the menu's color palette. The menu should have set a B/W palette or something like that.
- $7002.0-1: The 8 MiB multirom bank.
- $7002.2: Some bias, needs more research.
- $7002.3: Unknown, probably unused.
- $7002.4: Unknown, always set.
- $7002.5: Use the _last_ 8 KiB of the corresponding 32 KiB of SRAM instead of four banks. So it's like writing `$03` to `$4000` and then locking this register.
- $7002.6: SRAM disable.
- $7002.7: Lock mapper (so you cannot change multirom bank anymore). Useful for burning. Annoying when reading.
- $7001: `256 - [ROM size in bytes]/32768.`
- $7000: `[ROM offset in multirom bank]/32768`

Because they are first pushed to the stack and then read from there, these four bytes are written in reverse (A is written last). Unlike e.g. EZ-Flash Jr., this cart does not reset but jump to the ROM's entry point at $100. As the first three writes already trigger the ROM switch (so the menu ROM is no longer available), the code that writes these four bytes and the stack resides in HRAM. After switching the ROM but before loading A and resetting, it configures the cart's MBC5 to bank 1 (`[$3000]=0`, `[$2000]=1`).

ROMs at `floor([ROM offset]/2 MiB)` share 32 KiB of RAM. As there's 16 chunks of 2 MiB in the 32 MiB ROM, there's 16 SRAM slots for a total of 512 KiB.

#### Contents
Bomberman Quest has `[$014E]=$2D`, `[$0146]=$F5`. All other CGB games had `[$014F]` changed to `[$0148]-1`. DMG games (the last four) are No-Intro verified. The PacoChan patch is publicly available. The Cannon_Fodder_MULTI_GBC-CPL patch is described in a [reddit post](https://www.reddit.com/r/Gameboy/comments/6x64qd/ordered_a_bunch_of_bootleg_gbc_games_this_is_what/). The crack intro from that post is visible.

1. `$00200000` Dragon Warrior 1 & 2 (USA)
2. `$00400000` Dragon Warrior 3 (USA)
3. `$00800000` Resident Evil (Unknown) (Proto) [PacoChan patch v1.0]
4. `$00C00000` Cannon Fodder (Europe) (En,Fr,De,Es,It) [MULTI CGB-CPL]
5. `$01000000` Metal Gear Solid (Europe) (En,Fr,De,Es,It)
6. `$01400000` Legend of Zelda, The - Oracle of Ages (Europe) (En,Fr,De,Es,It)
7. `$01600000` Legend of Zelda, The - Link's Awakening DX (USA, Europe) (Rev A)
8. `$01800000` Legend of Zelda, The - Oracle of Seasons (Europe) (En,Fr,De,Es,It)
9. `$01A00000` Bionic Commando - Elite Forces (USA, Australia)
10. `$01C00000` Bomberman Quest (Europe) (En,Fr,De)
11. `$01E00000` R-Type DX (USA, Europe)
12. `$00100000` Survival Kids (USA)
13. `$01F00000` Spy vs. Spy (Europe) (En,Fr,De,Es,It,Nl,Sv)
14. `$01700000` Simpsons, The - Night of the Living Treehouse of Horror (USA, Europe)
15. `$00060000` Adventure Island (USA, Europe)
16. `$00080000` Adventure Island II - Aliens in Paradise (USA, Europe)
17. `$000C0000` Contra - The Alien Wars (USA)
18. `$000E0000` Contra (Japan) (En)

Surprisingly, they used the US version of Survival Kids when they chose the European versions in all other cases (when one was available). Probably they didn't know that the European release is called Stranded Kids.

Because they use the menu's palette, all four DMG games are basically unplayble.
