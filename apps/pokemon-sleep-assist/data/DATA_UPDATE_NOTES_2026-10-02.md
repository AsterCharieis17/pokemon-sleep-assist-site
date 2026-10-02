# Master data update — 2026-10-02

Species: 247 (74 additions, including forms). Recipes: 81 (78 named recipes and 3 mixed recipes; 15 additions). Main-skill SP entries: 36 (11 additions). Growth and recipe-level tables cover implemented levels through 70. Rank thresholds include Amber Canyon, Greengrass Isle EX, and Cyan Beach EX. Evaluation defaults use revision 3.

Existing Japanese species identifiers and fixed/random main-skill variants are preserved. Mew and Darkrai retain their special ingredient rules. Four recipe labels containing ingredient IDs have been corrected to Japanese. Announced but unreleased Foongus and Amoonguss are excluded as of this update date.

## Sources and attribution

Species statistics and ingredients were adapted from [Neroli's Lab](https://github.com/nerolis-lab/nerolis-lab), commit 647ddf8. Ingredient and skill probabilities are research estimates, not official published probabilities. Adaptations include Japanese identifiers, the application's JSON schema, growth categories, and preservation of existing special species rules.

Neroli's Lab is licensed under Apache-2.0. The accompanying `NEROLIS_LAB_LICENSE.txt` and `NEROLIS_LAB_NOTICE.txt` preserve the upstream license and notice.

Japanese recipe labels and base-energy observations were checked against the [recipe table](https://wikiwiki.jp/poke_sleep/料理/レシピの一覧). SP values were checked against the [SP research table](https://wikiwiki.jp/poke_sleep/SP). Growth tables were checked against [levels](https://wikiwiki.jp/poke_sleep/育成/レベル) and [experience categories](https://wikiwiki.jp/poke_sleep/育成/経験値タイプ). Field thresholds were checked against each field's Snorlax rank table. Creative recipe descriptions are not included.

Implementation dates were checked against official announcements for [Mewtwo](https://www.pokemonsleep.net/news/343333373536323134343933343436313435/), [Amber Canyon](https://www.pokemonsleep.net/news/333234393736353333383231313934323431/), [Cyan Beach EX](https://www.pokemonsleep.net/news/343231343532353138383431363437313132/), and [the upcoming Foongus line](https://www.pokemonsleep.net/news/343430323735343731303033383131383431/).

## Reconciliation decisions and limits

- Ingredient Draw S and Hyper Cutter level-6 SP use 4546 from the SP research table, resolving the 4846 value in the simulation source.
- Level-68 EXP for the 1320 category uses 6917: 3144 multiplied by 2.2 and rounded. The reference table's 6971 conflicts with its stated multiplier.
- Cumulative EXP is the sum of the required EXP entries. The legacy `required_experience_points_10800type` alias is retained alongside the correctly named 1080 key.
- Candy costs are neutral-nature reference values. Actual remaining EXP, nature and candy use can change an individual Pokémon's required cost.
- SP ingredient coefficients above implemented level 70 retain the previous speculative table and require revalidation when higher levels become available.
- Skill SP entries express SP coefficients, not necessarily skill energy effects. Adding a skill entry or field threshold does not implement its full team mechanics or EX production effects in clients.
- Recipe food-count bonuses include research estimates; the 78% category is an approximation, while base energy stores the observed recipe value.

All species, ingredient, skill and evolution references, recipe ingredient totals, uniqueness, level ranges, cumulative EXP and field thresholds were validated. Application regression checks include maximum skill levels and CSV/TSV roundtrips for all 247 species.
