# Bootlegs
All of these carts:
- Come from AliExpress.
- Ignore writes to `$4000.2-7` and are therefore restricted to 32 KiB of RAM.
- Except for the multicart, they ignore writes to `$3000`, so they are restricted to 4 MiB of ROM.
- Are MBC5. Except for the multicart, they do not aim to support MBC1.
- Except for TCG Neo, were bought via Choice.

<div style="white-space: nowrap !important;">
  
| Game            | MBC | Size | RAM | Shell       | Bat | PCB                   | ROM  | ROM Chip               | RAM | RAM Chip                | Ordered @ Ali Store                | Arrived  | CSum | Photo | CFI@ | Dump
| --------------- | --- | ---: | --: | ----------- | --- | --------------------- | ---: | ---------------------- | --: | ----------------------- | ---------------------------------- | -------- | ---- | ---   | ---- | ----
| Perfect Dark    |5+RBL| 4096 |   8 | DMG Grey    | yes | SD007_BGA48_BGA48_T28 | 8192 | Micron M29W640GB6AZA6E |  32 | Sony CXK58267ATM 10L    | 24.02.25 @ Pokegame                | 01.03.25 |`207D`| TBA | `00AA` | unchanged
| Pokémon TCG2    |   5 | 4096 |  32 | DMG Grey    | no  | SD007_BGA48_BGA48_T28 | 8192 | Samsung K8D3216UBC     |  32 | SI IC61LV256 8TG        | 24.02.25 @ Pokegame                | 01.03.25 |`ECA1`| TBA | `00AA` |
| Grimace's Bday  |   5 | 1024 |  32 |DMG Transblue| yes | SD007_BGA48_BGA48_T28 | 8192 | Micron M29W640GB6AZA6E | 256 | Winbond W26B02B 70LE    | 02.03.25 @ Treasure Game Accessory | 11.03.25 |`207D`| TBA | `00AA` | unchanged
| Hime's Quest    |   5 | 2048 |  32 | DMG Orange  | yes | SD007_BGA48_BGA48_T28 | 8192 | Micron M29W640GB6AZA6E |  32 | Cypress CY7C199L 15ZC   | 02.03.25 @ Pokegame                | 11.03.25 |`207D`| TBA | `00AA` | unchanged
| Perfect Dark    |5+RBL| 4096 |   8 | DMG Grey    | yes | SD007_BGA48_BGA48_T28 | 8192 | Samsung K8D3216UBC     |  32 | Toshiba TC55257DFTI 85L | 02.03.25 @ Pokegame                | 11.03.25 |`ECA1`| TBA | `00AA` | unchanged
| Pokémon Crystal |3+RTC| 2048 |  32 | CGB Crystal | no  | unknown               | 4096 | MXIC 29LV320DTTI-70G   |  32 | Hynix HY62256A          | 02.03.25 @ Pokemon Card            | 11.03.25 |`207D`| TBA | `00AA` |
| Pokémon TCG Neo |   5 | 2048 |  32 | DMG Black   | yes | SD007_BGA48_BGA48_T28 | 8192 | Micron M29W640GB6AZA6E |  32 | Cypress CY7C199L 15ZC   | 20.03.25 @ Carolina Game           | 27.03.25 | orig | TBA | `00AA` | unchanged
| Pokémon Crystal |3+RTC| 2048 |  32 | CGB Crystal | no  | unknown               | 4096 | MXIC 29LV320DTTI-70G   |  32 | Hynix HY62256A          | 20.03.25 @ Shop1103285009          | 28.03.25 |`207D`| TBA | `00AA` |
|Mario's Picross X|   1 |  256 |   8 | DMG Grey    | yes | SD007_BGA48_BGA48_T28 | 8192 | Micron M29W640GB6AZA6E | 256 | Winbond W26B02B 70LE    | 20.03.25 @ Shop1103923251          | 28.03.25 |`207D`| TBA | `00AA` |
| 18-in-1         |   1 |   32 |   2 | DMG Blue    | yes | SD008_512ND_4M        |32768 | MXIC 29GL256EHT27-90Q  |1024 | Samsung K6F8016U6D XF55 | 05.03.25 @ Glygame                 | 12.03.25 |`C17D`| TBA | `00AA` |
| 19-in-1         |   1 |   32 |   2 | DMG Red     | yes | (SD008_512ND_4M)      |32768 | MXIC 29GL256EHT27-90Q  |1024 | Cypress CY62158CV25LL   | 27.03.25 @ AntiqueGame             | 03.04.25 |`C17D`| TBA | `00AA` |
| 20-in-1         |   1 |   32 |   2 | DMG Green   | yes | (SD008_512ND_4M)      |32768?| (glob-top)             |2048 | NanoAmp N16T1630C1CZ 70I| 27.03.25 @ AntiqueGame             | 03.04.25 |`027D`| TBA | `0555` |
| 61-in-1         |   1 |   32 |   0 | DMG Yellow  | yes | (SD008_512ND_4M)      |16384?| (glob-top)             |2048 | NanoAmp N16T1630C1CZ 70I| 20.03.25 @ Childhood game          | 28.03.25 |`047D`| TBA | `0555` |
| 108-in-1        |   1 |   32 |   2 |DMG Transblue| yes | (SD008_512ND_4M)      |32768?| (glob-top)             |2048 | NanoAmp N16T1630C1CZ 70I| 27.03.25 @ Carolina Game           | 03.04.25 |`027D`| TBA | TBA |

</div>

- Shells tagged as CGB prevent you from turning on a DMG.
- All sizes are given in Kibibytes. Grimace has a nominal 128 Kibiwords and 18-in-1 has a nominal 512 Kibiwords of RAM.
- Checksum is given as individual hex bytes (aka big endian), so first two nibbles are $14E and the other two are $14F. All these checksums except for TCG Neo's are invalid, but the Game Boy doesn't care.
- "unchanged" in Dump column means that the invalid checksum is the only change compared to No-Intro.
- CFI@ is the hexadecimal address to write `$98` to so you can read the CFI query data. You exit CFI by writing `$F0` to any ROM address.

## Battery
If a repro cart has a battery (that is not empty), you can simply put on any ROM that does not require more RAM than the cart supports. Pokémon ROMs will also work in Pokémon Stadium in this case. Note that second-generation Pokémon games use a real-time clock (RTC) which is technically five special RAM banks ($08 to $0C). This means that if your cart has less than 128 KiB of acessible RAM, these games will corrupt their own save games (box 8 to be precise).

Batteryless games save to ROM. This is fine, as all ROM ICs are designed to withstand 100,000 writes. However, you're supposed to write at 3.3V, but most carts lack a level shifter from 5V. You can recognize batteryless ROM images by the music stopping for around 1 second when they write back your save to ROM.

Because of the 64 KiB erase sector size of the above ROM ICs (ROM sectors must be erased before being written), batteryless saving is only possible in games with 64 KiB of unused space at an address divisable by 64 KiB (called an aligned 64 KiB sector). As explained earlier, no single-game repro cart supports 8 MiB of ROM, so it's safe to assume that all carts shipping with a 4 MiB image will have a battery if the ROM image does not have an aligned 64 KiB sector of free space. Here's a list of commonly-available 4 MiB games on AliExpress:
- Games without a free 64 KiB sector (safe to assume that these battery-save): Dragon Warrior III, Grandia - Parallel Trippers, Perfect Dark, Resident Evil (if second prototype; this includes PacoChan's patch)
- Games with at least one aligned free 64 KiB sector in-between: Daikatana (if US prototype; JP is only 1 MiB), Donkey Kong Country, Resident Evil (if first prototype), Tomb Raider, Tomb Raider - Curse of the Sword
- Games that leave at least 64 KiB free space at the end: Cannon Fodder, Ghostly Labyrinth 2, Metal Gear Solid (EU; US is only 2 MiB), Pokémon TCG2 (fan translation; JP is only 2 MiB; see below for more info), Shantae (known to not have a battery)

This is the reason why Perfect Dark is usually recommended to anyone who wants to get a cart with standard battery-backed SRAM (meaning you do not need a modified ROM to be able to save).

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

This is my only shell to just say "GAME". Even the 108-in-1, which has the same color, say Nintendo GAME BOY.

### TCG Neo
This is the non-legacy 1.32 Boy Version. It is my only Pokémon repro to have a battery and the only 100% unmodified single-game cart.

The label says TCG Neo Discovery.

I did an overdump. The last 2 MiB are the last 2 MiB of Perfect Dark.

### Mario's Picross X

This is a hack by Ross Atkin (who probably goes by the name Tidus Renegade). I couldn't find it anywhere. Unlike other hacks, this is still an MBC1.

### "GB HICOL" Multicarts
By default, the multicart is a standard 8 MiB MBC5 cart with 32 KiB of RAM. If the cart is writable, you could just burn _Densha De Go! 2_ (confirmed to work) or _Kanji Shishuu_. This makes multicarts the by far cheapest carts to support the CGB's biggest ROM size of 8 MiB.

These multicarts' menus store four values per game. They end up in `A`, `$7002`, `$7001` and `$7000`.
- `A`: See [here](https://gbdev.io/pandocs/Power_Up_Sequence.html#cpu-registers). Only loaded if no reset is performed so **this bullet and its sub-bullets only apply if no reset is performed:** Even then, `A` shouldn't be hardcoded. They should have pushed `A`'s initial value (`AF` to be correct) as defined by the boot ROM to the stack and used that. Either way, there's no good resetless solution that allows the CGB to play both, CGB and DMG games from the same cart, nor will you be able to make a cart with both CGB-exclusives and CGB-enhanced games where a DMG will be able to play the CGB-enhanced ones and still have the CGB enhancements when the same cart is used in a CGB.
  - Using a hardcoded value of `$11` on the DMG will have many "GB Compatible" games try to use color palettes _instead_ of b/w palettes. Additionally, they will likely try to bank VRAM, mainly for background attributes. For example, Pokémon Yellow goes basically unaffected because its map is single-palette, but Pokémon Gold will glitch the map when you load into the map from a building or battle. Opening the menu fixes this temporarily and map parts loaded while walking will be fine from the start. Additionally, the DMG will be able to load CGB-exclusives, but will quickly bug out due to the massive lack of features.
  - Using a hardcoded value of `$01` on the CGB will make CGB-exclusives display a lockout screen. All other games will assume they're on a DMG. But because the menu's header requests CGB mode, the CGB will expect the game to write color palettes which it likely won't. This is guaranteed to happen with DMG games no matter what value is provided here. In all of these cases (except for the CGB-exclusives), the game will use the multicart menu's color palette. The menu should have set a B/W palette or something like that.
- `$7002.0-1`: The 8 MiB multirom bank (OR mask shl 23)
- `$7002.2`: Invoke MBC1 mode for `$4000-$5FFF` register. This means:
  - Bit 0 is used for 1 MiB games, bits 0-1 are used for any larger ones. The `$4000-$5FFF` register is ignored if the game is smaller than 1 MiB.
  - This register controls the `$0000-$3fff` memory area (you can set it to bank 0, 32, 64 or 96, depending on your ROM size). This is called the MBC1 Advanced Mode which you normally would have to activate first, by writing `$01` to `$6000-$7FFF`, but when `$7002.2` is set, MBC1 Advanced Mode always on and cannot be turned off.
  - If `$7002.5` is set as well, bits 5 to 7 of the `$2000-$3fff` register will be ignored. ROM bank number bits 5 and 6 for the `$4000-$7FFF` memory area are taken from the `$4000-$5FFF` register's bits 0 and 1 instead (if ROM size is large enough).  (TODO: need to test 4 MiB and up for the `$4000-$7fff` memory area)
  - For the ROM, the value is interpreted complementedly (bitwise NOT). It defaults to 0, so if you map a total area of 1 or 2 MiB, it defaults to the last 512 KiB of that. Therefore, if you want to use MBC1 mode with ROMs larger than 512 KiB, you must divide your ROM into 512 KiB blocks and write them in reserve order. Writes (over the full area) affect ROM (if at least 1 MiB) and RAM (if not locked with bit 5 or 6). If `$7001` is set to less than `$C0` (which makes no sense for MBC1; only checked `$00` though), it is instead treated as if it was `$C0` in conjunction with this register. This means that even if you map 8 MiB, writing `$03` into this register will give you the first 512 KiB of that, not the fourth-to-last from a 8 MiB or (taking `$3000` into account) 4 MiB area.
  - 0 is 0, even used in conjunction with MBC3 mode (see below).
  - There is only a single game that profits from this mode: _Super Chinese Fighter GB (Japan)_. Other games don't care (see excource below why this is even possible), are MBC1M or don't work anyway (probably because 0 is 0).
- `$7002.3`: Unknown, never set.
- `$7002.4`: Reset Game Boy.
- `$7002.5`: Does two very different things if set:
  1. Use the _last_ 8 KiB of the corresponding 32 KiB of SRAM (see below) instead of four banks. So it's like writing `$03` to `$4000` and then locking that register. If bit 5 and 6 are both set, RAM will be unavailable. The latter constellation is used by the 61-in-1 and 108-in-1 menu, while the others only set bit 6 if they don't want RAM (see bullet 2 for the possible reason). The actual 8 KiB RAM mode is only found in the 61-in-1 menu where it is used for Super Mario Land 2 and 3. It is not used to increase the number of RAM-enabled games, even though Super Mario Bros. Deluxe would qualify to share its RAM with one of these two, but there are only 7 games with a save feature on that cart anyway.
  2. Invoke MBC3 mode (if your game is 512 KiB or smaller, MBC1 and MBC3 are exactly the same), expanding the `$2000-$2fff` register to `$2000-$3fff`. Bugs:
     - Bank 0 is bank 0. This is the most important bug here. There are over hundred gams that still profit from this mode.
     - Supports 4 MiB of ROM. This is invalid but won't hurt anyone. It has the advantage that you can use this for MBC5 games with 8 KiB RAM and up to 4 MiB of ROM to make the mapper ignore writes to `$4000-$5fff` registers completely (unless `$7002.2` is set), so your games cannot bank RAM should they try to.
  - If `$7002.5` is clear, memory at `$4000-$7fff` will be in MBC5 mode. This means that if `$7002.2` is set but `$7002.5` is clear, memory at `$0000-$3fff` _and_ `$a000-$bfff` will both be in MBC1 Advanced Mode (e.g. RAM will be determined by exactly two bits of the `$4000-$5fff` register and ROM will be determined by the same up to two bits (which doesn't even make sense with 32 KiB of RAM), meaning you can map up to 4 different ROM banks there, namely 0, 32, 64 and 96), but `$4000-$7fff` will be in MBC5 mode (meaning you can map up to 512 different banks there).
  This also means that you cannot use MBC3/MBC1 with 32 KiB of RAM. Only two MBC5-incompatible MBC1 games with 32 KiB of RAM are known to exist, _Fushigi no Dungeon - Fuurai no Shiren GB - Tsukikage Mura no Kaibutsu (Japan)_ and _Nihon Daihyou Team France de Ganbare! - J.League Supporter Soccer (Japan)_). I believe this locking of the RAM register might have originally be intended for `$7002.2` where it actually made sense.
- `$7002.6`: SRAM disable.
- `$7002.7`: Lock mapper (so you cannot change the total mapped area anymore). Useful for burning. Annoying when reading.
- `$7001`: `256 - [ROM size in bytes]/32768.` (AND mask shl 15)
- `$7000`: `[ROM offset in multirom bank]/32768` (OR mask shl 15)

The use of masks requires a game's offset to be divisible by its own size.

Writing to `$4000` and `$0000` while these registers don't have any effect (due to flags written to `$7000.5-6`) will affect them as soon as they are enabled again. Things I checked about `$7002.3`:
* It does not restrict the mapper, e.g. you can still map bank 0 to `$4000` even if the total mapped area is only 32768 bytes (`$7001` was set to `$ff`).
* It does not change the mapped SRAM when used in conjuntion with bit 5.
* It does not allow for more then 32 KiB of RAM.
* It does not invoke MBC2, even with bit 1 or bit 5 set.
* It does not invoke MBC1M. It doesn't really matter since you can very easily convert MBC1M to MBC1, though the result will consume double the ROM - or you can just split the multicart into separate ROMs and use them individually since you already have multicart.
* It does not prevent MBC3+TIMER carts from corrupting SRAM (writes to SRAM bank `$08` and above aren't discarded - they are redirected to the given bank modulo the number of banks (4 or 1) just like always).

Because they are first pushed to the stack and then read from there, these four bytes are written in reverse. This means A is written last, and only if the reset is not possible (e.g. by applying tape to the third pin from the right). In the latter case, it jumps to the entry point at $100 which works fine if the conditions above are met. As the first three writes already trigger the ROM switch (so the menu ROM is no longer available), the code that writes these four bytes and the stack both reside in HRAM (WRAM would have worked, too). After switching the ROM but before loading A and jumping to the entry point, it configures the cart's MBC5 to bank 1 (`[$2000]=1`, `[$3000]=0`). Because MBC1 is not MBC5 and 0 is 0 in MBC1 mode, this can trigger the aforementioned bug in MBC1 mode, expecially in games that cannot soft-reset (Select+Start+A+B).

ROMs at the same `floor([ROM offset]/2 MiB)` share 32 KiB of RAM if RAM is enabled. As there's 16 chunks of 2 MiB in the 32 MiB ROM, there's 16 SRAM slots of 32 KiB each, for a total of 512 KiB. You can have ROMs use the last 8 KiB of their chunk only, which will allow more ROMs with RAM if ones with up to 1 MiB ROM and 8 KiB ROM are in the same 2 MiB block.

**[Excourse]** Some may ask: Why can MBC1 games larger than 512 KiB even work as MBC5? Accessing areas beyond 512 KiB is completely different!

Here's an example from _Super Black Bass Pocket 2 (Japan)_, and say we're loading bank `A = $32` and the old bank was between `$00` and `$1f`:
```asm
; This method can be found at $a79.
; This method maintains a history of the last 9 bank switches in HRAM (addresses F8-AE-AF-B0-B1-B2-B3-B4-B5, ordered newest to oldest) presumably for debug purposes, which is updates before the bank is switched.
; The following excerpt starts at $a9d:
LD [$2000], A ; maps ROM bank $12 on MBC1 because bits 5-7 are ignored; maps ROM bank $32 on MBC5
AND $60       ; sets A = $20; note that $60 is used although this is a 1 MiB ROM whose last bank is $3f; also note that the entire operation is useless because mappers ignore bits that don't apply to them
RRCA          ; sets A = $10
SWAP A        ; sets A = $01
LD [$4000], A ; maps ROM bank $32 on MBC1; maps RAM bank 0 on MBC5 because all bits are ignored (too little RAM to be banked)
```
This means this game relies on the fact that MBC1 discards `$2000.5-7` and respects `$4000`. However, if a game with 0 to 8 KiB RAM of RAM is run as MBC5, the opposite is the case which works out by conincidence.

Because physical mappers do not care about the header, note that Pokémon Gin/Kin Spaceworld demos and Zelta DX betas do not belong into this category because they are _not_ actual MBC1 games. Using MBC1 will break them. _Art School Pocket_ also doesn't belong into this category because it only uses banks 0–1, 3–10 and 12–15 (so it's essentially a 256 KiB ROM instead of 1 MiB).

#### 18-in-1 (GB HICOL MC03, MC003)
The four bytes of data are starting at `$46FE`. The menu does not access its 2 KiB of RAM. There are 6 items per page.

Bomberman Quest has `[$014E]=$2D`, `[$0146]=$F5`. All other CGB games had `[$014F]` changed to `[$0148]-1`. DMG games (the last four) are No-Intro verified. The Resident Evil is using the PacoChan v1.0 patch which is publicly available. Cannon Fodder has a Cracktro described in a [reddit post](https://www.reddit.com/r/Gameboy/comments/6x64qd/ordered_a_bunch_of_bootleg_gbc_games_this_is_what/).

| Menu Item          |  A | 7k2| 7k1| 7k0| Offset      | No-Intro Name |
| ------------------ | -- | -- | -- | -- | ----------- | ------------- |
| `1 WARRIOR 1+2   ` |`11`|`90`|`C0`|`40`| `$00200000` | Dragon Warrior 1 & 2 (USA)
| `2 WARRIOR 3     ` |`11`|`90`|`80`|`80`| `$00400000` | Dragon Warrior 3 (USA)
| `3 RESDEN EVIL   ` |`11`|`91`|`80`|`00`| `$00800000` | Resident Evil (Unknown) (Proto)
| `4 CANNON FODDER ` |`11`|`91`|`80`|`80`| `$00C00000` | Cannon Fodder (Europe) (En,Fr,De,Es,It)
| `5 METAL GEAR SOL` |`11`|`92`|`80`|`00`| `$01000000` | Metal Gear Solid (Europe) (En,Fr,De,Es,It)
| `6 ZELDA AGES    ` |`11`|`92`|`C0`|`80`| `$01400000` | Legend of Zelda, The - Oracle of Ages (Europe) (En,Fr,De,Es,It)
| `7 ZELDA AWAKENIN` |`11`|`92`|`E0`|`C0`| `$01600000` | Legend of Zelda, The - Link's Awakening DX (USA, Europe) (Rev A)
| `8 ZELDA SEASONS ` |`11`|`93`|`C0`|`00`| `$01800000` | Legend of Zelda, The - Oracle of Seasons (Europe) (En,Fr,De,Es,It)
| `9 BIONIC COMMAND` |`11`|`93`|`C0`|`40`| `$01A00000` | Bionic Commando - Elite Forces (USA, Australia)
| `10 BOMBERMAN QUE` |`11`|`93`|`C0`|`80`| `$01C00000` | Bomberman Quest (Europe) (En,Fr,De)
| `11 R-TYPE DX    ` |`11`|`93`|`E0`|`C0`| `$01E00000` | R-Type DX (USA, Europe)
| `12 SURVIVAL KIDS` |`11`|`90`|`E0`|`20`| `$00100000` | Survival Kids (USA)
| `13 SPY VS SPY   ` |`11`|`D3`|`E0`|`E0`| `$01F00000` | Spy vs. Spy (Europe) (En,Fr,De,Es,It,Nl,Sv)
| `14 THE SIMPSONS ` |`11`|`D2`|`E0`|`E0`| `$01700000` | Simpsons, The - Night of the Living Treehouse of Horror (USA, Europe)
| `15 ADVEN ISLAND1` |`01`|`D0`|`FC`|`0C`| `$00060000` | Adventure Island (USA, Europe)
| `16 ADVEN ISLAND2` |`01`|`D0`|`F8`|`10`| `$00080000` | Adventure Island II - Aliens in Paradise (USA, Europe)
| `17 SUPER CONTRA1` |`01`|`D0`|`FC`|`18`| `$000C0000` | Contra - The Alien Wars (USA)
| `18 SUPER CONTRA2` |`01`|`D0`|`FC`|`1C`| `$000E0000` | Contra (Japan) (En)

There is a 19th, inaccessible item, which only has a name (`19 ARMY MEN 3   `) but no description or register data. Said game is the 19th game in the 19-in-1. 352 KiB of this cart go unused. They are located in a continuous area between the menu and Adventure Island.

Surprisingly, they used the US version of Survival Kids when they chose the European versions in all other cases (when one was available). Probably they didn't know that the European release is called Stranded Kids.

If you prevent the reset, the four DMG games use the menu's palette when running on a CGB, making them basically unplayble. Preventing the reset is actually quite nice for the CGB ones because they load much faster.

#### 20-in-1 (GB HICOL MC01, MC001)
19 is claimed by sellers to be Kirby's Dream Land, but it is actually Castlevania 2 (Belmont's Revenge). Spud's Adventure's `$7001` claims it was 512 KiB in size, when it is only 64 KiB.

#### 61-in-1 (GB HICOL MC06, MC006)
This cart is really bad. There are many bitflips (around 1 in 10000 bytes) where a bit is _often_ (but not on every read) cleared but should be set (the opposite does not happen). Although I used a Game Boy for dumping, I did not encounter issues in-game.

You can retrieve CFI by writing `$98` to `$0555` instead of the usual `$00AA`. CFI doesn't really contain useful info and it's only `$80` bytes long.

Entering ROM areas beyond 16 MiB and reading from the same addresses again and again returns slightly different data on each read (more different than the aforementioned random bitflips), but you can recognize many similarities. They persist over power and bank cycles.

The four bytes of data are starting at `$47FF`. The menu doesn't have no RAM, but has 0 KiB of RAM. BGB complains that this makes no sense. There are 11 items per page.


While the 108-in-1 is densely packed with ROMs for 0 free space, the 61-in-1 has three empty areas (all `$FF` - with no bit errors) due to bad placement and two other things they could have done better:
1. The menu is 32 KiB, but the first game in ROM is 64 KiB. Therefore, 32 KiB are wasted after the menu.
2. Spud's Adventure is a 64 KiB game that has its own 512 KiB block, probably because its `$7001` value also claims it was 512 KiB. Makes you think if a different game was in its place originally. It is also the only 64 KiB game on this cart to not be featured in the 108-in-1.
3. The last 256 KiB go unused.
4. There is a duplicate of Belmont's Revenge right after the first one. The menu links to the first one.
5. You get random data when read from beyond 16 MiB, but it bears a lot of similarities.

#### 108-in-1
My copy has four bit flips that persisted over multiple reads. Again, these bits are cleared when it should be set.
|  # | Game                            | L.Offset |   G.Offset | Good | Bad  |
| -: | ------------------------------- | -------: | ---------: | ---- | ---- |
| 10 | Mega Man Xtreme (USA, Europe)   | `$3720A` | `$123720A` |`0x6E`|`0x66`|
| 11 | Mega Man Xtreme 2 (USA, Europe) | `$938E9` | `$14938E9` |`0x2E`|`0x2C`|
| 65 | F-15 Strike Eagle (USA, Europe) | `$19C89` | `$1319C89` |`0x0F`|`0x0D`|
|103 | Balloon Kid (USA, Europe)       |  `$7522` | `$1547522` |`0xAF`|`0xAE`|

Two other bit flips on the first dump went away on the second dump:
|  # | Game                            | L.Offset |   G.Offset | Good | Bad  |
| -: | ------------------------------- | -------: | ---------: | ---- | ---- |
| 74 | Casper (USA) [DMG]              |  `$CB97` | `$172CB97` |`0xC5`|`0x85`|
|105 | Tom & Jerry (USA, Europe) [DMG] | `$1FE8F` | `$159FE8F` |`0xF3`|`0x73`|
