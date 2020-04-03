# Bogdbo customizations
* based on v3 alpha
* based on Consolas + heavily cherry-picked configuration
* built for the extended width
* focus on having characters as distinct as possible (eg: 3, 7, i, 1)
* variants: Regular, Book (extended 450), Extra bold Extended (800) and Italic (default)
* Note: check alacritty settings for latest config (book extended, XbdExt and book extended for italics)


# Iosevka ![Version](https://img.shields.io/github/release/be5invis/Iosevka.svg)
Coders’ typeface, built from code.

![](https://raw.githubusercontent.com/be5invis/Iosevka/master/images/preview-all.png)

## Installation

Quit your editor/program. Unzip and open the folder.

* **Instructions for Windows**: Download the fonts from the [Releases](https://github.com/be5invis/Iosevka/releases), select the font files and right click, then hit "Install".
  * On Windows 10 1809 or newer the default font installation is per-user, and it may cause compatibility issues for some applications, mostly written in Java. To cope with this, right click and select "Install for all users" instead. [Ref.](https://youtrack.jetbrains.com/issue/JRE-1166?p=IDEA-200145)
* **[Instructions for macOS](http://support.apple.com/kb/HT2509)**
  * Standard distribution in Homebrew: `brew tap homebrew/cask-fonts && brew cask install font-iosevka && brew cask install font-iosevka-slab`
  * Customizable install using Homebrew: see [robertgzr/homebrew-tap](https://github.com/robertgzr/homebrew-tap).
* **Linux** : Copy the TTF files to your fonts directory → Run `sudo fc-cache`. 
  - Arch Linux users can install the font from the AUR [here](https://aur.archlinux.org/packages/ttf-iosevka) using an AUR wrapper or by doing it manually. [All variants](https://aur.archlinux.org/packages/?O=0&SeB=nd&K=ttf-iosevka&SB=n&SO=a&PP=50&do_Search=Go).
  - Void Linux users can install the font with `xbps-install font-iosevka`.
* **FreeBSD**: The font can be installed with `pkg install iosevka`.
* **OpenBSD**: The font can be installed with `pkg_add iosevka-fonts-<variant>`. Run `pkg_info -Q iosevka-fonts` to see which variants are available.

## Weights, Variants and OpenType features

The typeface contains 9 weights (Thin to Heavy) alongside with both italic and oblique versions, with the same metrics as the regular one. 

![Weights sample](https://raw.githubusercontent.com/be5invis/Iosevka/master/images/weights.png)

All versions include the same ranges of characters: Latin letters, Greek letters (including Polytonic), some Cyrillic letters, IPA symbols and common punctuations and some symbols. You can check out the full list [here](http://be5invis.github.io/Iosevka/specimen.html).

![Languages Sample](https://raw.githubusercontent.com/be5invis/Iosevka/master/images/languages.png)

<!-- BEGIN Section-Language-List -->

159 Supported Languages: 

Afrikaans, Aghem, Akan, Albanian, Asturian, Asu, Azerbaijani, Bafia, Bambara, Basaa, Basque, Belarusian, Bemba, Bena, Bosnian, Breton, Bulgarian, Catalan, Cebuano, Central Atlas Tamazight, Chechen, Chiga, Colognian, Cornish, Croatian, Czech, Danish, Duala, Dutch, Embu, English, Esperanto, Estonian, Ewe, Ewondo, Faroese, Filipino, Finnish, French, Friulian, Fulah, Galician, Ganda, German, Greek, Gusii, Hausa, Hawaiian, Hungarian, Icelandic, Igbo, Inari Sami, Indonesian, Interlingua, Irish, Italian, Javanese, Jola-Fonyi, Kabuverdianu, Kabyle, Kako, Kalaallisut, Kalenjin, Kamba, Kazakh, Kikuyu, Kinyarwanda, Koyra Chiini, Koyraboro Senni, Kurdish, Kwasio, Kyrgyz, Lakota, Langi, Latvian, Lingala, Lithuanian, Low German, Lower Sorbian, Luba-Katanga, Luo, Luxembourgish, Luyia, Macedonian, Machame, Makhuwa-Meetto, Makonde, Malagasy, Malay, Maltese, Manx, Maori, Masai, Meru, Metaʼ, Mongolian, Morisyen, Mundang, Nama, Ngiemboon, North Ndebele, Northern Sami, Norwegian Bokmål, Norwegian Nynorsk, Nuer, Nyankole, Oromo, Ossetic, Polish, Portuguese, Prussian, Quechua, Romanian, Romansh, Rombo, Rundi, Russian, Rwa, Samburu, Sango, Sangu, Scottish Gaelic, Sena, Serbian, Shambala, Shona, Slovak, Slovenian, Soga, Somali, Spanish, Swahili, Swedish, Swiss German, Tachelhit (shi_latn), Taita, Tajik, Tasawaq, Tatar, Teso, Tongan, Turkish, Turkmen, Ukrainian, Upper Sorbian, Uzbek, Vai (vai_latn), Vietnamese, Volapük, Vunjo, Walser, Welsh, Western Frisian, Wolof, Xhosa, Yangben, Yoruba, Zarma, Zulu

<!-- END Section-Language-List -->


Iosevka supports accessing all letter variants using OpenType features.

![Style Sets](https://raw.githubusercontent.com/be5invis/Iosevka/master/images/stylesets.png)

![Character Variants](https://raw.githubusercontent.com/be5invis/Iosevka/master/images/charvars.png)

### Ligations

![Ligations Sample](https://raw.githubusercontent.com/be5invis/Iosevka/master/images/ligations.png)

Iosevka’s default ligation set is assigned to `calt` feature, though not all of them are enabled by default.

Iosevka supports Language-Specific Ligations, which is the ligation set enabled only under certain languages. These ligation sets are assigned to custom feature tags, like `XHS0`.

## Building from Source

To build Iosevka you should:

1. Ensure that [`nodejs`](http://nodejs.org) (≥ 8.4), [`ttfautohint`](http://www.freetype.org/ttfautohint/), [`otfcc`](https://github.com/caryll/otfcc) (≥ 0.9.3) and `otf2otc` are present.
2. Install necessary libs by `npm install`. If you’ve installed them, upgrade to the latest.
3. `npm run build -- contents::iosevka`.


You will find TTFs, as well as WOFF(2) web fonts and one Webfont CSS in the `dist/` directory.

## Build Your Own Style

Since version 2.0, Iosevka would no longer support building via `makefile`. To initialize a custom build, you need:

1. Create `private-build-plans.toml` file.

2. Add a build plan into `private-build-plans.toml`, following this format:

	```toml
	[buildPlans.iosevka-custom]            # <iosevka-custom> is your plan name
	family = "Iosevka Custom"              # Font menu family name
	design = ["common styles"]             # Common styles
	upright = ["upright-only", "styles"]   # Upright-only styles
	italic = ["italic-only", "styles"]     # Italic-only styles
	oblique = ["oblique-only", "styles"]   # Oblique-only styles
	hintParams = ["-a", "sss"]             # Optional custom parameters for ttfautohint

	# Override default building weights
	# When buildPlans.<plan name>.weights is absent
	# All weights would built and mapped to default shape/CSS
	# IMPORTANT : Currently "menu" property only support 100, 200, 300, 400, 450, 500, 600, 700, 800, 900.
	#              and "shape" properly only supports number between 100 and 900 (inclusive).
	[buildPlans.iosevka-custom.weights.regular]
	shape = 400  # Weight for glyph shapes
	menu  = 400  # Weight for menu name
	css   = 400  # Weight for webfont CSS

	[buildPlans.iosevka-custom.weights.book]
	shape = 450
	menu  = 450  # Use 450 here to name the font's weight "Book"
	css   = 450

	[buildPlans.iosevka-custom.weights.bold]
	shape = 700
	menu  = 700
	css   = 700
	
	# Override default building slant sets
	# Format: <upright|italic|oblique> = <"normal"|"italic"|"oblique">
	# When this section is absent, all slants would be built.
	[buildPlans.iosevka-custom.slants]
	upright = "normal"
	italic = "italic"
	oblique = "oblique"
	```

3. Run `npm run build -- contents::<your plan name>` and the built fonts would be avaliable in `dist/`. Aside from `contents::<plan>`, other options are:

   1. `contents::<plan>` : TTF (Hinted and Unhinted), WOFF(2) and Webfont CSS;
   2. `ttf::<plan>` : TTF;
   3. `ttf-unhinted::<plan>` : Unhinted TTF only;
   4. `woff::<plan>` : TTF and WOFF only;
   5. `woff2::<plan>` : TTF and WOFF2 only;
      - Note: Since version 2.2.0, we are using two colons (`::`) in the build target names.

The current available styles for `design`/`upright`/`italic`/`oblique` options are:

* Styles for general shape:

  * `sans` : Sans serif (default).
  * `slab` : Slab serif.

* Styles related to ligations and spacing:

  - `sp-term` : Make the symbols' width suitable for terminal emulators. Arrows and geometric symbols will become narrower.
  - `sp-fixed` : Apply `sp-term` and further:
    - Completely disable `fwid` feature. All non-combining glyphs will be exactly the same width.
	- Ligation will be removed.
  - `no-ligation` : Disable ligation only.
  - `no-cv-ss` : Prevent generation of `cv##` and `ss##` features.

<!-- BEGIN Section-Cherry-Picking-Predefined -->

* Styles for ligation sets, include:

  * `ligset-dlig`: Default ligation set would be assigned to Discretionary ligatures.
  * `ligset-javascript`: Default ligation set would be assigned to JavaScript.
  * `ligset-php`: Default ligation set would be assigned to PHP.
  * `ligset-ml`: Default ligation set would be assigned to ML.
  * `ligset-fsharp`: Default ligation set would be assigned to F#.
  * `ligset-fstar`: Default ligation set would be assigned to F*.
  * `ligset-haskell`: Default ligation set would be assigned to Haskell.
  * `ligset-idris`: Default ligation set would be assigned to Idris.
  * `ligset-elm`: Default ligation set would be assigned to Elm.
  * `ligset-purescript`: Default ligation set would be assigned to PureScript.
  * `ligset-patel`: Default ligation set would be assigned to PatEL.
  * `ligset-swift`: Default ligation set would be assigned to Swift.
  * `ligset-coq`: Default ligation set would be assigned to Coq.
  * `ligset-matlab`: Default ligation set would be assigned to Matlab.

<!-- END Section-Cherry-Picking-Predefined -->

<!-- BEGIN Section-Cherry-Picking-Ligation-Sets -->

* Styles for further customizing default (`calt`) ligation sets:

  * `calt-center-ops`: Vertically align some of the operators (like `*`) to the center position it is before or after a "center" operator (like `+`).
  * `calt-arrow`: Enable ligation set that forms arrows.
  * `calt-arrow2`: Enable ligation for more arrows, like `>>=`.
  * `calt-trig`: Enable ligation for `<|`, `|>` , `<||`, and other bar-and-angle-bracket symbols.
  * `calt-eqeqeq`: Enable special triple-line ligation for `===` only.
  * `calt-eqeq`: Enable ligation for `==` and `===`.
  * `calt-ineq`: Enable ligation for `<=` and `>=`.
  * `calt-exeqeq`: Enable special triple-line ligation for `!==` only.
  * `calt-eqexeq`: Enable special triple-line ligation for `=!=` only.
  * `calt-exeq`: Enable ligation for `!=` and `!==`.
  * `calt-tildeeq`: Enable ligation for `~=` as inequality.
  * `calt-eqslasheq`: Enable special triple-line ligation for `=/=` as inequality.
  * `calt-slasheq`: Enable ligation for `/=` and `=/=` as inequality.
  * `calt-ltgt-ne`: Enable ligation for `<>` as inequality.
  * `calt-ltgt-diamond`: Enable ligation for `<>` as diamond.
  * `calt-brst`: Center asterisk in `(*` and `*)`.
  * `calt-plusplus`: Enable ligation for `++` and further plus-chaining.
  * `calt-colons`: Enable ligation for `::` and `:::`.
  * `calt-logic`: Enable ligation for `/\` and `\/`.
  * `calt-llgg`: Enable ligation for `<<`, `>>` and other angle-bracket chaining.
  * `calt-dotoper`: Treat dot (`.`) as operator and perform chained centering.
  * `calt-arrowZALE`: Treat `<=` as arrow.
  * `calt-arrowZAGE`: Treat `>=` as co-arrow.
  * `calt-html-comment`: Enable ligation for `<!--` and `<!---`.

<!-- END Section-Cherry-Picking-Ligation-Sets -->

* Styles for changing the line space (leading):

  * `leading-750`, `leading-1000`, `leading-1250`, `leading-1500`, `leading-1750`, `leading-2000`: Change the line space. Default is `leading-1250`.
  * `win-metric-pad-0`, `win-metric-pad-50`, `win-metric-pad-100`, `win-metric-pad-150`, `win-metric-pad-200`, `win-metric-pad-250`, `win-metric-pad-300`: Add extra space to [OS/2 table’s Win metrics](https://docs.microsoft.com/en-us/typography/opentype/spec/os2#uswinascent) to avoid clipping in certain legacy software.

* Styles for changing Powerline symbols' position:

  * `powerline-scale-y-750`, `powerline-scale-y-875`, `powerline-scale-y-1000`, `powerline-scale-y-1125`, `powerline-scale-y-1250`, `powerline-scale-y-1375`, `powerline-scale-y-1500`: Resize the Powerline symbols vertically, from 75% to 150%.
  * `powerline-scale-x-750`, `powerline-scale-x-875`, `powerline-scale-x-1000`, `powerline-scale-x-1125`, `powerline-scale-x-1250`, `powerline-scale-x-1375`, `powerline-scale-x-1500`: Resize the Powerline symbols horizontally, from 75% to 150%.
  * `powerline-shift-y-n500`, `powerline-shift-y-n450`, `powerline-shift-y-n400`, `powerline-shift-y-n350`, `powerline-shift-y-n300`, `powerline-shift-y-n250`, `powerline-shift-y-n200`, `powerline-shift-y-n150`, `powerline-shift-y-n100`, `powerline-shift-y-n50`, `powerline-shift-y-0`, `powerline-shift-y-p50`, `powerline-shift-y-p100`, `powerline-shift-y-p150`, `powerline-shift-y-p200`, `powerline-shift-y-p250`, `powerline-shift-y-p300`, `powerline-shift-y-p350`, `powerline-shift-y-p400`, `powerline-shift-y-p450`, `powerline-shift-y-p500`: Shift the Powerline symbols vertically, from -0.5em to +0.5em.
  * `powerline-shift-x-n500`, `powerline-shift-x-n450`, `powerline-shift-x-n400`, `powerline-shift-x-n350`, `powerline-shift-x-n300`, `powerline-shift-x-n250`, `powerline-shift-x-n200`, `powerline-shift-x-n150`, `powerline-shift-x-n100`, `powerline-shift-x-n50`, `powerline-shift-x-0`, `powerline-shift-x-p50`, `powerline-shift-x-p100`, `powerline-shift-x-p150`, `powerline-shift-x-p200`, `powerline-shift-x-p250`, `powerline-shift-x-p300`, `powerline-shift-x-p350`, `powerline-shift-x-p400`, `powerline-shift-x-p450`, `powerline-shift-x-p500`: Shift the Powerline symbols horizontally, from -0.5em to +0.5em.

* Symbol exclusion:

  * `exclude-check-and-cross-symbol`: Exclude `✓✔✕✖✗✘` (U+2713 – U+2718) from the font.

<!-- BEGIN Section-Stylistic-Sets -->

* Styles as stylistic sets:

  * `ss01`: Set character variant to “Andale Mono Style”.
  * `ss02`: Set character variant to “Anonymous Pro Style”.
  * `ss03`: Set character variant to “Consolas Style”.
  * `ss04`: Set character variant to “Menlo Style”.
  * `ss05`: Set character variant to “Fira Mono Style”.
  * `ss06`: Set character variant to “Liberation Mono Style”.
  * `ss07`: Set character variant to “Monaco Style”.
  * `ss08`: Set character variant to “Pragmata Pro Style”.
  * `ss09`: Set character variant to “Source Code Pro Style”.
  * `ss10`: Set character variant to “Envy Code R Style”.
  * `ss11`: Set character variant to “X Window Style”.
  * `ss12`: Set character variant to “Ubuntu Mono Style”.
  * `ss13`: Set character variant to “Lucida Style”.
  * `ss14`: Set character variant to “JetBrains Mono Style”.
  * `ss20`: Set character variant to “Curly Style”.

<!-- END Section-Stylistic-Sets -->

<!-- BEGIN Section-Cherry-Picking-Styles -->

* Styles for individual characters. They are easy-to-understand names of the `cv##` styles, including:

  * Styles for `a`:
    * `v-a-doublestorey`, `cv01`: Double-storey `a` (default for Upright).
    * `v-a-singlestorey`, `cv02`: Single-storey `a` (default for Italic).
  * Styles for `f`:
    * `v-f-straight`, `cv52`: `f` without bottom hook (default for Sans Upright).
    * `v-f-tailed`, `cv53`: `f` with a leftward bottom hook (default for Italic).
    * `v-f-serifed`, `cv84`: `f` with bottom serif (default for Slab Upright).
  * Styles for `g`:
    * `v-g-doublestorey`, `cv11`: Double-storey `g`.
    * `v-g-singlestorey`, `cv12`: Single-storey `g` (default).
    * `v-g-opendoublestorey`, `cv24`: Open Double-storey `g`, like Trebuchet MS or Fira Code.
  * Styles for `i`:
    * `v-i-serifed`, `cv03`: Serifed `i` (default for Upright).
    * `v-i-italic`, `cv04`: Italic `i` (default for Italic).
    * `v-i-hooky`, `cv05`: Hooky `i`.
    * `v-i-zshaped`, `cv06`: Z-shaped `i`.
    * `v-i-line`, `cv56`: `i` like a straight line.
    * `v-i-tailed`, `cv88`: Tailed `i`.
  * Styles for `j`:
    * `v-j-line`, `cv57`: `j` like a straight line.
    * `v-j-serifed`, `cv58`: `j` with top serif (default).
  * Styles for `l`:
    * `v-l-serifed`, `cv07`: Serifed `l` (default for Upright).
    * `v-l-italic`, `cv08`: Italic, cursive `l` (default for Italic).
    * `v-l-hooky`, `cv09`: Hooky `l`.
    * `v-l-zshaped`, `cv10`: Z-shaped `i`.
    * `v-l-tailed`, `cv27`: `l` with a curved tail.
    * `v-l-hookybottom`, `cv28`: `l` with a straight tail.
    * `v-l-line`, `cv59`: `l` like a straight line.
  * Styles for `k`, `K`:
    * `v-k-straight`, `cv68`: `k` with standard shape (default for Upright).
    * `v-k-curly`, `cv69`: Slightly curly `k`, like Iosevka 2.x.
    * `v-k-cursive`, `cv70`: `k` with a cursive loop (default for Italic).
  * Styles for `m`:
    * `v-m-normal`, `cv25`: `m` with normal middle leg, touching the baseline (default).
    * `v-m-shortleg`, `cv26`: `m` with shorter middle leg, like Ubuntu Mono.
  * Styles for `r`:
    * `v-r-straight`, `cv85`: Straight, serif-less `r` (default for Sans).
    * `v-r-serifed`, `cv86`: `r` with serif at both top and bottom (default for Slab Upright).
    * `v-r-top-serifed`, `cv87`: `r` with serifs at top-left only (default for Slab Italic).
  * Styles for `t`:
    * `v-t-standard`, `cv40`: Standard `t` shape (default).
    * `v-t-cross`, `cv41`: Futura-like `t` shape.
  * Styles for `u`:
    * `v-u-with-bar`, `cv89`: Normal `u` with right bar (default).
    * `v-u-without-bar`, `cv90`: Normal `u` without right bar, like a smaller uppercase `U`.
  * Styles for `v`, `V`:
    * `v-v-straight`, `cv71`: Standard, straight `V` and `v` (default).
    * `v-v-curly`, `cv72`:  Slightly curly `V` and `v`, like Iosevka 2.x.
  * Styles for `w`, `W`:
    * `v-w-straight`, `cv75`: Standard, straight `W` and `w` (default).
    * `v-w-curly`, `cv76`: Slightly curly `W` and `w`, like Iosevka 2.x.
  * Styles for `x`, `X`:
    * `v-x-straight`, `cv77`: Standard, straight `X` and `x` (default).
    * `v-x-curly`, `cv78`: Slightly curly `X` and `x`, like Iosevka 2.x.
  * Styles for `y`:
    * `v-y-straight`, `cv48`: More-straight letter `y` (default for Upright).
    * `v-y-cursive`, `cv49`: Cursive-like `y` (default for Italic).
    * `v-y-curly`, `cv79`: More curly letter `y`, like Iosevka 2.x.
  * Styles for `A`, `Λ`, `Δ`:
    * `v-turn-v-straight`, `cv73`: Standard, straight `A`, `Λ`, `Δ` (default).
    * `v-turn-v-curly`, `cv74`: Slightly curly `A`, `Λ`, `Δ`, like Iosevka 2.x.
  * Styles for `G`:
    * `v-capital-g-tooth`, `cv91`: Toothed G (default).
    * `v-capital-g-toothless`, `cv92`: Toothless G.
  * Styles for `Q`:
    * `v-capital-q-taily`, `cv42`: `Q` with a curly tail (default).
    * `v-capital-q-straight`, `cv43`: `Q` with a straight tail like in the old versions.
  * Styles for `R`:
    * `v-capital-r-straight`, `cv82`: Standard, straight-leg `R` (default).
    * `v-capital-r-curly`, `cv83`:  Slightly curly-legged `R`, like Iosevka 2.x.
  * Styles for `Y`:
    * `v-capital-y-straight`, `cv80`: Standard, straight `Y` (default).
    * `v-capital-y-curly`, `cv81`: Slightly curly `Y`, like Iosevka 2.x.
  * Styles for `0`:
    * `v-zero-slashed`, `cv13`: Slashed Zero `0` (default).
    * `v-zero-dotted`, `cv14`: Dotted Zero `0`.
    * `v-zero-unslashed`, `cv15`: O-like `0`.
    * `v-zero-reverse-slashed`, `cv93`: Reverse-slashed `0`.
  * Styles for `1`:
    * `v-one-nobase`, `cv50`: `1` with bottom serif (default for Sans).
    * `v-one-base`, `cv51`: `1` without bottom serif (default for Slab).
  * Styles for `3`:
    * `v-three-flattop`, `cv46`: Flat top `3` (Like Museo Sans / Montserrat).
    * `v-three-twoarcs`, `cv47`: Arched top `3` (default).
  * Styles for `7`:
    * `v-seven-noserif`, `cv64`: `7` without serif (default for Sans).
    * `v-seven-serifed`, `cv65`: `7` with initial serif (default for Slab).
  * Styles for `~`:
    * `v-tilde-high`, `cv16`: Higher tilde `~`.
    * `v-tilde-low`, `cv17`: Lower tilde `~` (default).
  * Styles for `*`:
    * `v-asterisk-high`, `cv18`: Higher five-pointed asterisk `*` (default).
    * `v-asterisk-low`, `cv19`: Lower five-pointed asterisk `*`.
    * `v-asterisk-hexhigh`, `cv60`: Higher six-pointed asterisk `*`.
    * `v-asterisk-hexlow`, `cv61`: Lower six-pointed asterisk `*`.
  * Styles for `_`:
    * `v-underscore-high`, `cv20`: Higher underscore `_`, at baseline (default).
    * `v-underscore-low`, `cv21`: Lower underscore `_`, below baseline.
  * Styles for `¶`:
    * `v-paragraph-high`, `cv22`: Higher paragraph symbol `¶` (default).
    * `v-paragraph-low`, `cv23`: Lower paragraph symbol `¶`.
  * Styles for `^`:
    * `v-caret-high`, `cv29`: Higher circumflex `^` (default).
    * `v-caret-low`, `cv30`: Lower circumflex `^`.
  * Styles for `{`, `}`:
    * `v-brace-straight`, `cv36`: More straight braces.
    * `v-brace-curly`, `cv37`: More curly braces (default).
  * Styles for `@`:
    * `v-at-threefold`, `cv31`: The long, three-fold At symbol (`@`) (default).
    * `v-at-fourfold`, `cv32`: The traditional, four-fold At symbol (`@`).
    * `v-at-short`, `cv33`: The shorter, Fira-like At symbol (`@`).
  * Styles for `$`:
    * `v-dollar-open`, `cv38`: Dollar symbol with open contour.
    * `v-dollar-through`, `cv39`: Dollar symbol with strike-through vertical bar (default).
    * `v-dollar-opencap`, `cv54`: Dollar symbol with open contour, not exceeding baseline and ascender.
    * `v-dollar-throughcap`, `cv55`: Dollar symbol with strike-through vertical bar, not exceeding baseline and ascender.
  * Styles for `#`:
    * `v-numbersign-upright`, `cv44`: Number sign with vertical bars (default).
    * `v-numbersign-slanted`, `cv45`: Number sign with slanted bars.
  * Styles for `%`:
    * `v-percent-dots`, `cv62`: Percent `%`, Per-mille `‰` and basis point `‱` using rectangular dots.
    * `v-percent-rings`, `cv63`: Percent `%`, Per-mille `‰` and basis point `‱` using rings (default).
  * Styles for `<=`, `>=`:
    * `v-lig-ltgteq-flat`, `cv66`: The lower bar of `<=` and `>=` ligation is flat (default).
    * `v-lig-ltgteq-slanted`, `cv67`: The lower bar of `<=` and `>=` ligation is slanted.
  * Styles for `ß`:
    * `v-eszet-traditional`, `cv34`: Traditional, Fraktur-like Eszet.
    * `v-eszet-sulzbacher`, `cv35`: A more modern, beta-like Eszet (default).

<!-- END Section-Cherry-Picking-Styles -->

## For Chinese and Japanese users...

→ [Sarasa Gothic](https://github.com/be5invis/Sarasa-Gothic).

---

![Family Matrix](https://raw.githubusercontent.com/be5invis/Iosevka/master/images/matrix.png)
