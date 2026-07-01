# ai5-sdl2-yuno-latin

Fork of [nunuhara/ai5-sdl2](https://github.com/nunuhara/ai5-sdl2) with a
patch for Latin accented character support, made specifically for **YU-NO**
(この世の果てで恋を唄う少女).

Original: https://github.com/nunuhara/ai5-sdl2

---

## English

### Changes from the original (nunuhara/ai5-sdl2)

This patch was made specifically for YU-NO. It has **not been tested on
other games supported by the engine** (Doukyuusei, Kakyuusei, Isaku,
Shuusaku, Aishimai, etc.), so compatibility with them is not guaranteed.

#### src/utfsjis.c
Added a remap table for the SJIS half-width katakana byte range
(0xA1-0xB8) to Latin accented characters (á, é, í, ó, ú, ñ, Á, É, etc.),
plus an extended table using the unused 0xF0 lead byte to cover
additional characters (À, Â, Ç, Œ, Š, Č, etc.). This allows the game to
display Spanish and other Latin-based language text without breaking
compatibility with the original katakana mapping.

Updated `sjis_char_is_valid`, `sjis_char2unicode`, and
`utf8_char_to_sjis` to use these tables in both directions
(SJIS→UTF-8 and UTF-8→SJIS).

#### meson.build
Added compilation of Windows resources (ai5.rc / ai5.ico) when targeting
Windows, to include a custom YU-NO icon in the executable.

#### src/gfx.c
Changed the game window title: the " - AI5-SDL2" suffix is no longer
appended when a name is set, and the default title changed from
"AI5-SDL2" to "YU-NO".

#### New files
- `src/ai5.rc` — Windows resource file referencing the icon
- `src/ai5.ico` — custom YU-NO icon for the executable

### Note
Tested only with YU-NO. If used with another game from this engine,
verify that the SJIS remap table doesn't interfere with text or
filenames specific to that title.

---

## Español

### Cambios respecto al original (nunuhara/ai5-sdl2)

Este parche fue realizado específicamente para YU-NO
(この世の果てで恋を唄う少女). No fue probado en otros juegos soportados
por el engine (Doukyuusei, Kakyuusei, Isaku, Shuusaku, Aishimai, etc.),
por lo que su compatibilidad con ellos no está garantizada.

#### src/utfsjis.c
Se agregó una tabla de remapeo de caracteres SJIS half-width katakana
(rango 0xA1-0xB8) hacia caracteres latinos acentuados (á, é, í, ó, ú, ñ,
Á, É, etc.), más una tabla extendida usando el lead byte 0xF0 (no usado
en SJIS) para cubrir caracteres adicionales (À, Â, Ç, Œ, Š, Č, etc.).
Esto permite representar texto en español y otros idiomas latinos en el
juego sin perder compatibilidad con el katakana original.

Se actualizaron `sjis_char_is_valid`, `sjis_char2unicode` y
`utf8_char_to_sjis` para usar estas tablas en ambas direcciones
(SJIS→UTF-8 y UTF-8→SJIS).

#### meson.build
Se agregó la compilación de recursos de Windows (ai5.rc / ai5.ico) cuando
el sistema objetivo es Windows, para incluir un ícono personalizado de
YU-NO en el ejecutable.

#### src/gfx.c
Se cambió el título de la ventana del juego: ya no se agrega el sufijo
" - AI5-SDL2" cuando hay un nombre, y el título por defecto pasó de
"AI5-SDL2" a "YU-NO".

#### New files
- `src/ai5.rc` — recurso de Windows que referencia el ícono
- `src/ai5.ico` — ícono personalizado de YU-NO para el ejecutable

---

## License

This project is based on ai5-sdl2 by nunuhara.

Original project:
https://github.com/nunuhara/ai5-sdl2

This fork is distributed under the GNU General Public License
version 2 or later (GPL-2.0-or-later).

See the LICENSE file for the full license text.

The corresponding source code for this version is available in this repository.

The source code corresponding to this build is included in:
ai5-sdl2-yuno-latin-patch.zip
