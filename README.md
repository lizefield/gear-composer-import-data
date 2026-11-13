# Gear Composer Import Data
Unofficial HIT: The World catalog transcribed from supplied screenshots.
- [Japanese guide](docs/README.ja.md)
- [Import JSON](games/hit2/ja/import.json)

Revision **49**: **457 records, 81 attributes, 2826 numeric values**.
365 equipment items,32 cards,38 pets,22 souls. 457 primary images map one-to-one to records; one additional Edda Incarnation image confirms the same six values.59 records lacking supplied-image evidence were removed; no name-only items remain.

All457 records are calculation-enabled using the displayed numeric values from supplied images. No values were converted or estimated. Each kind is represented as one item. Displayed values are not claimed to be initial or maximum values.

Limits:4 cards,1 pet,1 soul and one shared weapon slot. The current app does not enforce same-card/restricted-ring duplicate rules. Class selection filters weapon compatibility; leaving class unspecified searches across all classes. Displayed percentages are simply summed, not a complete damage model. Storage/disassembly rows, two lower icon values and collection details are excluded. Power-stone points are included as a selectable, summable attribute for 365 equipment items.

Mount records were removed in revision41; records lacking image evidence were removed in revision42. Merge imports do not automatically delete previously imported records, ownership or saved-set references. Back up personal data before manual cleanup. Do not delete the game merely to match counts. Existing image-supported item IDs remain stable. JSON import currently requires Pro.

Only README.md,docs/README.ja.md,games/hit2/ja/import.json and.gitignore are intended for Git. Images,source indexes,checklists and validation scripts remain private. Superseded work files are recoverably archived locally.

Not official or endorsed. Game rights belong to their owners. No game artwork or copied long-form descriptions are published. Check applicable terms before redistribution.

Rarity colors: common gray, uncommon green, rare blue, heroic purple, ancient yellow, legendary orange, immortal red. Display palette matched visually to supplied images, not exact official RGB. The app adjusts text contrast; individual item colors override rank colors. Reimport the updated catalog to apply rank colors.


## 装備先の表示順
各装備先に任意の `displayOrder` を追加しました。対応するアプリでは次の順で表示します。未対応の旧版アプリでは先にアプリを更新してください。

武器 → ヘルム → 上衣 → グローブ → 下衣 → 靴 → マント → ネックレス → リング → ブレスレット → ベルト → 勲章 → アミュレッタ → カンパネラ → ペット → 闘魂 → カード


## 対応クラス（revision 46）
クラスを `game.classes` に定義し、対応が限定される141件の武器には `classIds` を設定しました。既存metadataに記録されていた対応クラスを移し、能力値・アイテムIDは変更していません。各アイテムは複数クラスを指定できます。`classIds` の省略・空配列は全クラス対応です。共通装備・ペット・闘魂・カードはクラス未設定としています。

クラスはタグとは独立しています。更新したアプリでJSONを再インポートしてください。セットのクラスは初期値「指定なし」で、クラス選択後はそのクラス対応と全クラス対応のアイテムが候補になります。既存の保存セットの検索条件は自動変更しません。


## レアリティの高さ（revision 47）
各ランクに `rank` を追加しました。大きい数ほど高レアリティです。一般1・高級2・希少3・英雄4・古代5・伝説6・不滅7です。アイテム一覧では同じ装備先の中で高レアリティ順、置き換え候補では指定属性の値が大きい順（同じ値は高レアリティ順）に表示します。指定属性がない候補は、属性がある候補の後で高レアリティ順になります。従来のhit2データも対応アプリではこの順序で表示します。アイテムID・能力値・所持情報は変更しません。


## 装備先と重複するタグの整理（revision 48）
アイテムのタグから「カード」32件・「ペット」38件・「闘魂」22件を削除しました。これらは装備先で絞り込めます。その他のタグは保持しています。更新JSONを再インポートすると反映されます。


## パワーストーンポイント（revision 49）
通常装備365件のmetadataに保存していたポイントを、属性 `attr.power-stone-points` にも登録しました。属性選択・合計・セット検索に使用できます。表示値0の25件も0として登録し、値のないカード・ペット・闘魂には補完していません。単位はなし、小数なしです。更新JSONを再インポートしてください。
