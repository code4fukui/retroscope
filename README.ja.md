# Retroscope Sabae

[
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
](https://opensource.org/licenses/MIT)

現代のベースマップに歴史的な地図タイルを重ね合わせ、「スポットライト」や「スパイグラス（虫眼鏡）」効果を使って過去と現在の地理を比較できるインタラクティブな地図ビューアーです。本プロジェクトは、[retroscope](https://github.com/frogcat/retroscope) を鯖江エリア向けに特化させた実装です。

## デモ

**ライブアプリケーション:** **[http://fukuno.jig.jp/app/retroscope-sabae/](http://fukuno.jig.jp/app/retroscope-sabae/)**

開発者のブログ記事もあわせてご覧ください: [http://fukuno.jig.jp/1333](http://fukuno.jig.jp/1333)

## 機能

*   **スポットライトビュー:** マウスを動かす（タッチデバイスの場合はタップする）と、現在の地図上に歴史地図レイヤーが円形に浮かび上がります。スポットライトの中心には十字カーソル（クロスヘア）が表示されます。
*   **動的なレイヤー切り替え:** 現在表示されている地図の範囲（ビューポート）に応じて、利用可能な歴史地図のリストが自動的に更新されます。
*   **ベースマップの切り替え:** 現代の地理院オルソ画像（衛星・航空写真）と標準地図を切り替えることができます。
*   **ベクター注記:** 地名（町字など）をベクター形式のラベルとして表示し、どのズームレベルでも鮮明に表示されます。

## 動作原理

本アプリケーションは [Leaflet.js](https://leafletjs.com/) を使用して構築されており、以下のプラグインを活用して機能を実現しています。

*   コアとなるスポットライト効果は `leaflet-tileoverlay-mask` を使用して作成されており、カーソルから指定された半径内にのみタイルレイヤーを描画します。
*   ベースマップは標準の `L.tileLayer` インスタンスであり、`L.control.layers` スイッチャーによって管理されています。
*   歴史地図のオーバーレイレイヤーは `layers.json` で定義され、動的に読み込まれます。現在の地図の中心座標でタイルが利用可能かをチェックし、それに応じてUIを更新します。
*   地名の注記は国土地理院の実験的なベクトルタイル提供サービスから読み込まれ、`L.divIcon` マーカーとして描画されます。
*   地図のURLは `leaflet-hash` を使用して、現在の位置とズームレベルが反映されるよう更新されます。

## データソースとクレジット

本プロジェクトは、複数のソースから提供される地図タイルやデータを利用しています。利用条件については、各提供元のサイトをご確認ください。

*   **ベースマップ (背景地図タイル):**
    *   出典: 国土地理院 (GSI) 地理院タイル
    *   クレジット: [オルソ画像](http://maps.gsi.go.jp/development/ichiran.html#ort), [標準地図](http://maps.gsi.go.jp/development/ichiran.html#std) (国土地理院)

*   **歴史地図オーバーレイ (前景地図タイル):**
    *   出典: 国土地理院 国土画像情報 (第一期 1974～1978年撮影)
    *   クレジット: [国土画像情報 第一期1974～1978年撮影(地理院タイル)](http://maps.gsi.go.jp/development/ichiran.html#gazo1)

*   **注記:**
    *   出典: 国土地理院 ベクトルタイル提供実験
    *   クレジット: [注記(ベクトルタイル提供実験)](https://github.com/gsi-cyberjapan/experimental_anno/)

*   **歴史地図の利用可能エリアデータ (NIAES):**
    *   オリジナル版では、歴史的農業環境閲覧システムのデータを利用していました。
    *   出典: [歴史的農業環境閲覧システム(NIAES)](http://habs.dc.affrc.go.jp/)

## 依存関係

*   [Leaflet.js](https://leafletjs.com/) (v1.0.0-beta.2)
*   [jQuery](https://jquery.com/)
*   [leaflet-tileoverlay-mask](https://github.com/frogcat/leaflet-tileoverlay-mask)
*   [Leaflet Hash](https://github.com/mlevans/leaflet-hash)

## オリジナルプロジェクト

本リポジトリは、[@frogcat](https://github.com/frogcat) 氏によるオリジナルの `retroscope` プロジェクトをフォークし、特定の地域向けに実装したものです。

*   **オリジナルリポジトリ:** **[https://github.com/frogcat/retroscope](https://github.com/frogcat/retroscope)**

## ライセンス

本プロジェクトは MIT License のもとで公開されています。
