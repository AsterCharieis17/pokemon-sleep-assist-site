# 2026-10-26 master update

## Species

Added Misdreavus (#200) and Mismagius (#429), both Ghost / Skills specialists.

|Species|Ingredient rate|Base skill rate|Base frequency (seconds)|Base carry limit|Main skill|
|---|---:|---:|---:|---:|---|
|Misdreavus|15.0%|4.7%|2800|13|Cooking Power-Up S|
|Mismagius|14.2%|3.6%|2400|22|Mystical Fire (Cooking Advance S)|

Both: potato 1/2/4, coffee 2/3, tomato 4. Standard EXP group 600. Added their evolution chain. All previous 249 species are unchanged, including Gengar's corrected 16.6% ingredient rate.

Sources checked 2026-10-26:
- https://www.pokemonsleep.net/news/343532353938363734313136303530393531/
- https://pks.raenonx.cc/en/pokedex/200
- https://pks.raenonx.cc/en/pokedex/429
- https://github.com/nitoyon/pokesleep-tool/blob/main/src/data/pokemon.json (EXP group and evolution metadata; its other new-species fields are still placeholders and were not used)

Rates are community reference data, not an official publication of hidden game probabilities.

## Current recipe audit

All 81 existing recipes were matched against Neroli's Lab source by ingredient combination and meal category. Ingredient quantities and total counts match. Eight bonus fields were outdated; their already-current base energy values are retained:

- ニンジャカレー: 0.35 -> 0.48
- めいそうスイートサラダ: 0.35 -> 0.48
- ピヨピヨパンチ辛口カレー: 0.25 -> 0.35
- だいばくはつポップコーン: 0.25 -> 0.35
- みだれづきコーンサラダ: 0.2051 -> 0.25
- ちからもちソイドーナッツ: 0.25 -> 0.35
- はなびらのまいチョコタルト: 0.2051 -> 0.25
- うるおいとうふサラダ: 0.2051 -> 0.25

Sources:
- https://github.com/nerolis-lab/nerolis-lab/blob/main/common/src/types/recipe/curry.ts
- https://github.com/nerolis-lab/nerolis-lab/blob/main/common/src/types/recipe/salad.ts
- https://github.com/nerolis-lab/nerolis-lab/blob/main/common/src/types/recipe/dessert.ts
- https://pks.raenonx.cc/en/meal (directly checked all three categories)

Small 18.72% versus 18.7% representation differences are left unchanged. The avocado gratin energy remains 24802 as displayed by RaenonX; the other source's formula rounds to 24803, so that computed difference was not blindly applied. November's unreleased nut recipes are not included.

## New skill effects

main_skill_effects.json separates actual effects from SP scoring coefficients.

Mystical Fire level 1-7 pot increases: 7, 10, 12, 17, 22, 27, 31.
Extra Tasty percentage-point increases: 1, 2, 2, 3, 3, 4, 5.
Source: https://pks.raenonx.cc/en/mainskill/info/41 (datamined effects).

SP coefficient is not yet verified. The existing SP_main_skill_factor.json is not changed to fabricated pot-capacity values. Known effect magnitudes cannot uniquely determine the internal SP coefficient. The nitoyon calculation code currently reaches its generic 880/1251/1726/2383/3290/4546/5843 branch for Mystical Fire, but this is not a Mystical Fire-specific verification. A real in-game SP sample with the full individual conditions is needed for a validated fit. Until the coefficient is supplied, older clients may omit Mismagius's skill contribution from SP and limit its skill-level picker; the effects file alone does not change client calculation code.
