---
title: 玉川大学コスモス祭 3Dマップ 仕様書 v0.3
published: 2026-04-22
description: 玉川大学コスモス祭向け Web 3Dマップの仕様書・構築方針・実装方針。Fuwari貼り付け用。
tags: [Tamagawa, Cosmos Festival, MapLibre, PLATEAU, Scaniverse, 3D Map, Fuwari]
category: Project Spec
draft: false
---

> [!IMPORTANT]
> この文書は **「コスモス祭までに公開できる現実的な範囲」を定める仕様書兼・構築設計書** です。  
> 目的は、構想を実装可能な形に落とし、迷いなく開発を進められる状態にすることです。

# 玉川大学コスモス祭 3Dマップ 仕様書 v0.3

---

## 1. このプロジェクトで作るもの

玉川大学コスモス祭の来場者向けに、  
**現在地付きの Web 3D マップ**を提供する。

このプロジェクトの目的は、単に「3D で見えてすごい」ではない。  
以下ができることを重視する。

- 今、自分が **どこにいるか** 分かる
- 模擬店・トイレ・受付・ステージなどを **すぐ探せる**
- 初めて来た人でも **迷いにくい**
- スマホで **ストレスなく使える**

---

## 2. ベンチマーク

本プロジェクトは、大学祭向けの実用的な 3D マップ体験をベンチマークにする。  
ただし、完全再現を目標にはせず、玉川大学コスモス祭向けに次を重視する。

- スマホでの使いやすさ
- 現在地表示
- 模擬店・トイレ・受付・ステージの探しやすさ
- 大学祭当日に「本当に使える」こと

> [!NOTE]
> 目標は「全部入りの Google マップ風アプリ」ではなく、  
> **“大学祭来場者向けに必要十分な案内アプリ”** を作ることです。

---

## 3. 目的

本アプリの目的は、  
**玉川大学コスモス祭の来場者が、キャンパス内で迷わず目的地を見つけられるようにすること** である。

3D 表示は目的ではなく手段であり、  
広いキャンパスの位置関係を直感的に理解しやすくするために採用する。

---

## 4. 解決したい課題

### 4.1 想定課題

- 初来場者にはキャンパスの地理が分かりにくい
- 平面マップだけでは位置関係を把握しづらい
- トイレ、受付、模擬店、ステージなどを探すのに時間がかかる
- 現在地が分からないと案内情報の価値が下がる

### 4.2 解決方針

本アプリでは、以下の 3 本柱で解決する。

1. **3D マップ**で場所の関係を把握しやすくする
2. **現在地表示**で「今どこにいるか」を明確にする
3. **施設情報の検索・表示**で目的地にたどり着きやすくする

---

## 5. 対象ユーザー

### 5.1 最重要ターゲット
- **外部来場者**
  - 玉川大学キャンパスに不慣れ
  - スマホで会場案内を見たい
  - 受付、模擬店、トイレ、ステージを探したい

### 5.2 次点ターゲット
- **在学生**
  - 行きたい企画や模擬店を素早く探したい
- **運営スタッフ**
  - 来場者案内の補助として使いたい

> [!TIP]
> MVP では、**外部来場者向けの分かりやすさ**を最優先する。  
> 在学生向けの利便性は歓迎だが、初見ユーザーが迷わないことを優先する。

---

## 6. コンセプト

**「迷わない大学祭マップ」**

キーワード：

- 3D
- 現在地
- スマホ特化
- 施設検索
- 学園祭向け案内

---

## 7. 成功条件

以下を満たしたら、初期リリースとして成功とみなす。

- スマホブラウザで問題なく開ける
- 現在地が表示できる
- 主要施設（模擬店、トイレ、受付、ステージ等）が見つけられる
- 施設をタップすると詳細が見られる
- 来場者にとって「使える案内アプリ」になっている

---

## 8. MVP（祭りまでに必ず実装する機能）

### 8.1 3Dマップ表示
- キャンパス周辺の 3D 表示
- 建物や地形を含む全体俯瞰
- 回転、ズーム、移動に対応

### 8.2 現在地表示
- ブラウザの位置情報 API を利用
- 現在地を地図上に表示
- 現在地ボタンで自位置へ戻れる

### 8.3 施設・会場表示
以下のカテゴリを地図上に表示する。

- 模擬店
- トイレ
- 総合受付
- ステージ
- 休憩所
- 学食
- 出入口
- その他案内対象施設

### 8.4 施設詳細表示
施設をタップしたとき、以下を表示する。

- 名前
- カテゴリ
- 簡単な説明
- 営業時間 / 開催時間
- 写真（可能なら）
- 現在地からの距離

### 8.5 カテゴリフィルター
- 食べ物
- 展示
- ステージ
- トイレ
- 受付
- 休憩所
などのカテゴリごとの表示切り替え

### 8.6 近くの施設表示
- 現在地付近の施設を簡易表示する
- 例：「近くのトイレ」「近くの模擬店」

---

## 9. 初期版ではやらないこと

- 本格的な経路探索
- ターンバイターン案内
- 屋内ナビゲーション
- 室内現在地推定
- ログイン / アカウント機能
- 投稿 / レビュー
- リアルタイム混雑可視化
- 通知機能
- 多言語対応（必要なら後日）

> [!WARNING]
> **経路探索は初期版ではやらない。**  
> ルートデータ整備・ノード管理・再探索処理まで必要になり、  
> 開発難易度とデータ整備コストが一段上がる。

---

## 10. 将来拡張

### 10.1 室内対応の方向性
将来的には、以下を拡張候補とする。

- 特定建物だけフロア切替に対応
- 教室 / 展示室 / ホールなどの室内 POI 表示
- 特定入口から先の案内情報
- 室内 3D モデルの重ね合わせ

### 10.2 初期版でやらない理由
- 室内モデル作成コストが高い
- 室内現在地推定は別難易度
- 学園祭までの期間を考えると、まずは屋外案内を完成させる方が価値が高い

> [!NOTE]
> 室内は「今年の必須機能」ではなく、**将来拡張として仕様に位置付ける**。  
> ただし、**入口・受付・特徴的な会場の 3D 化**は、必要に応じて部分的に取り入れる。

---

## 11. 画面構成

### 11.1 マップ画面（メイン）
主画面。基本的にここで完結させる。

#### 表示要素
- 3Dマップ
- 現在地ボタン
- カテゴリフィルター
- 検索ボタン
- 施設詳細の下部シート
- 「近くの施設」表示（任意）

### 11.2 施設一覧画面
地図が苦手なユーザー向け。

#### 表示要素
- カテゴリ別一覧
- 検索
- タップで地図へ移動

### 11.3 施設詳細画面 / 下部シート
#### 表示要素
- 施設名
- 写真
- 説明
- カテゴリ
- 開催 / 営業時間
- 距離
- 地図で見るボタン

### 11.4 イベント情報画面（余裕があれば）
- ステージイベント
- 時間帯別スケジュール
- 特別企画

---

## 12. 技術構成（採用方針）

### 12.1 フロントエンド
- Vite
- React
- TypeScript
- CSS Modules（または素の CSS / SCSS）

### 12.2 地図エンジン
- MapLibre GL JS

### 12.3 3D 表示
- Three.js
- 必要に応じて 3D Tiles

### 12.4 背景データ
- PLATEAU 町田市 2025 年度データを背景ベース候補とする

### 12.5 学祭データ
- GeoJSON / JSON で POI・カテゴリ・イベント情報を管理する

### 12.6 公開
- Cloudflare Pages

> [!TIP]
> CSS は **Tailwind 前提にしない**。  
> 今回は、UI を追い込みやすく、HTML / JSX 構造を見失いにくい  
> **CSS Modules か SCSS** を基本方針とする。

---

## 13. 全体アーキテクチャ

### 13.1 構成イメージ

```txt title="architecture-overview.txt"
[ブラウザ]
   ├─ React UI
   ├─ MapLibre GL JS
   ├─ Three.js custom layer
   ├─ Geolocation API
   ├─ GeoJSON / JSON 読み込み
   └─ 必要に応じて Scaniverse 由来 GLB 読み込み

[静的ファイル]
   ├─ public/data/pois.geojson
   ├─ public/data/categories.json
   ├─ public/data/events.json
   ├─ public/models/*.glb
   └─ public/images/*

[背景3D]
   └─ PLATEAU 町田市 3D Tiles / 必要範囲のみ利用

[デプロイ]
   └─ Cloudflare Pages
```

### 13.2 役割分担

- **MapLibre**：Web 地図の土台
- **PLATEAU**：町田市 / 玉川大学周辺の背景 3D
- **GeoJSON / JSON**：模擬店・トイレ・受付・イベントなどの本体データ
- **Geolocation API**：現在地表示
- **Scaniverse（必要に応じて）**：玉川大学固有の目印や局所空間の 3D 化

---

## 14. なぜこの構成にするのか

### 14.1 MapLibre を使う理由
- Web で扱いやすい
- 静的サイトと相性が良い
- 3D モデルや 3D Tiles と組み合わせ可能
- Mapbox に比べて公開時のコスト設計を単純化しやすい

### 14.2 PLATEAU を使う理由
- 町田市の背景 3D を最初から使える
- 建築物や道路の 3D データがある
- 背景をゼロから作らなくてよい
- 学祭に必要な見た目の土台を早く作れる

### 14.3 学祭データを自作する理由
- 本当に重要なのは「何がどこにあるか」
- 模擬店、トイレ、受付、ステージ、休憩所などは学祭固有データ
- 学祭当日の情報は自前で管理する必要がある

### 14.4 Scaniverse を補助的に使う理由
- 校門、入口、看板、特徴物を 3D 化できる
- 玉川大学らしさを足せる
- 背景全体ではなく「目印」を強くできる

---

## 15. 構築手段・方法・方針（かなり詳しく）

## 15.1 開発環境を作る

### 15.1.1 プロジェクト作成
まずは Vite + React + TypeScript で静的サイトとして始める。

```bash title="create-project.sh"
npm create vite@latest tamagawa-cosmos-map -- --template react-ts
cd tamagawa-cosmos-map
npm install
```

### 15.1.2 必要ライブラリ導入
最低限、以下を入れる。

```bash title="install-deps.sh"
npm install maplibre-gl three
npm install 3d-tiles-renderer
npm install @turf/distance @turf/helpers
```

必要なら以下も候補にする。

```bash title="optional-deps.sh"
npm install zod
npm install clsx
npm install sass
```

### 15.1.3 開発用サーバ起動

```bash title="run-dev.sh"
npm run dev
```

> [!NOTE]
> 最初の段階では、**地図が出ること**だけを目標にする。  
> まだ 3D も POI も入れなくてよい。

---

## 15.2 ディレクトリを先に切る

```txt title="project-structure.txt"
src/
  main.tsx
  App.tsx

  app/
    map/
      MapView.tsx
      map.style.css
      layers/
        plateauLayer.ts
        modelLayer.ts
      controls/
        CurrentLocationButton.tsx
        FilterPanel.tsx
    ui/
      BottomSheet.tsx
      SearchPanel.tsx
      FacilityList.tsx
    data/
      loadPois.ts
      loadCategories.ts
      loadEvents.ts
      schemas.ts
    features/
      nearby.ts
      geolocation.ts
      filtering.ts
    state/
      useMapState.ts

  styles/
    globals.css

public/
  data/
    pois.geojson
    categories.json
    events.json
  models/
  images/
```

### 15.2.1 役割
- `app/map/`：地図と 3D 関連
- `app/ui/`：下部シートや一覧 UI
- `app/data/`：データ読み込み
- `app/features/`：距離計算、位置取得などのロジック
- `public/data/`：実データ
- `public/models/`：GLB など

> [!TIP]
> 最初にフォルダを切っておくと、  
> 後で「地図ロジック」と「UI ロジック」と「データ処理」が混ざりにくい。

---

## 15.3 まずは地図だけ表示する

### 15.3.1 最初の到達目標
- 画面いっぱいに地図が表示される
- 中心が玉川大学周辺
- スマホでも表示される

```tsx title="src/app/map/MapView.tsx"
import { useEffect, useRef } from 'react'
import maplibregl from 'maplibre-gl'
import 'maplibre-gl/dist/maplibre-gl.css'

export default function MapView() {
  const mapRef = useRef<HTMLDivElement | null>(null)

  useEffect(() => {
    if (!mapRef.current) return

    const map = new maplibregl.Map({
      container: mapRef.current,
      style: 'https://tiles.openfreemap.org/styles/bright',
      center: [139.48, 35.57],
      zoom: 16,
      pitch: 45,
      bearing: 0,
      hash: true
    })

    map.addControl(new maplibregl.NavigationControl(), 'top-right')

    return () => map.remove()
  }, [])

  return <div style={{ width: '100%', height: '100dvh' }} ref={mapRef} />
}
```

> [!IMPORTANT]
> タイル提供元は **開発用** と **本番用** を分けて考える。  
> 最初は動作確認を優先し、本番前に利用条件・配信方式・キャッシュ方針を確認する。

---

## 15.4 現在地表示を入れる

### 15.4.1 方針
- `navigator.geolocation.watchPosition` を使う
- 現在地マーカーを更新する
- 現在地ボタンで追従できるようにする

### 15.4.2 ロジックの分離
`app/features/geolocation.ts` にまとめる。

```ts title="src/app/features/geolocation.ts"
export type UserLocation = {
  lng: number
  lat: number
  accuracy?: number
}

export function watchUserLocation(
  onUpdate: (loc: UserLocation) => void,
  onError?: (error: GeolocationPositionError) => void
) {
  if (!navigator.geolocation) return null

  const id = navigator.geolocation.watchPosition(
    (pos) => {
      onUpdate({
        lng: pos.coords.longitude,
        lat: pos.coords.latitude,
        accuracy: pos.coords.accuracy
      })
    },
    (err) => onError?.(err),
    {
      enableHighAccuracy: true,
      maximumAge: 5000,
      timeout: 10000
    }
  )

  return id
}

export function clearUserLocationWatch(id: number | null) {
  if (id !== null && navigator.geolocation) {
    navigator.geolocation.clearWatch(id)
  }
}
```

### 15.4.3 UI の考え方
- 初回は「現在地を使う」ボタンを出す
- 許可後、青い点を出す
- 精度が悪いときは「やや不正確」表示も検討する

> [!NOTE]
> 室内では GPS 精度が落ちる前提で設計する。  
> 初期版では **屋外の現在地表示が主用途** である。

---

## 15.5 学祭データを先に作る

### 15.5.1 先にコードを書かない
まず POI データ構造を確定する。

```json title="public/data/pois.geojson"
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "geometry": {
        "type": "Point",
        "coordinates": [139.4800, 35.5700]
      },
      "properties": {
        "id": "info-main",
        "name": "総合受付",
        "category": "info",
        "description": "来場者向けの総合受付です",
        "hours": "10:00-16:00",
        "image": "/images/info-main.jpg",
        "tags": ["reception", "guide"]
      }
    }
  ]
}
```

### 15.5.2 カテゴリも分離する

```json title="public/data/categories.json"
[
  { "id": "food", "label": "食べ物", "color": "#f97316" },
  { "id": "stage", "label": "ステージ", "color": "#8b5cf6" },
  { "id": "toilet", "label": "トイレ", "color": "#3b82f6" },
  { "id": "info", "label": "受付", "color": "#10b981" },
  { "id": "rest", "label": "休憩所", "color": "#06b6d4" }
]
```

### 15.5.3 データを先に整える理由
- UI を作る前に、必要項目が確定する
- 後から DB を入れなくてもよい
- 静的ホスティングと相性が良い

> [!TIP]
> 学園祭アプリでは、  
> **「どの技術を使うか」より「データをどう持つか」** の方が後々効く。

---

## 15.6 POI を地図に出す

### 15.6.1 実装方法
- GeoJSON を fetch する
- `map.addSource` で追加
- `circle` / `symbol` レイヤで表示
- タップ時に下部シートを開く

### 15.6.2 まずはシンプルに始める
- 1レイヤ 1カテゴリでもいい
- 先に動かしてから色分けする

---

## 15.7 近くの施設機能を作る

### 15.7.1 初期版の考え方
ルート案内ではなく、**現在地から近い施設を出す** だけでもかなり便利。

### 15.7.2 実装方法
- ユーザー位置と POI の距離を計算
- 上位 3〜5 件を出す
- タップで地図移動

```ts title="src/app/features/nearby.ts"
import distance from '@turf/distance'
import { point } from '@turf/helpers'

export function calcDistanceMeters(
  from: [number, number],
  to: [number, number]
) {
  return distance(point(from), point(to), { units: 'kilometers' }) * 1000
}
```

> [!NOTE]
> 初期版で必要なのは **最短経路** ではなく、  
> **「近くに何があるか」** を返すこと。

---

## 15.8 背景 3D を入れる

### 15.8.1 背景 3D の役割
- 玉川大学周辺の立体感を出す
- 広いキャンパスの位置関係を把握しやすくする
- “大学祭アプリっぽさ”を強める

### 15.8.2 方法
背景 3D は **PLATEAU 町田市データ** をベース候補とする。  
まずは「玉川大学周辺だけ表示」することを前提に考える。

### 15.8.3 実装のやり方
選択肢は 2 つ。

#### 方法 A：3D Tiles を背景として読む
- PLATEAU の 3D Tiles を読み込む
- Three.js custom layer として MapLibre 上に重ねる
- 背景として使う

#### 方法 B：必要な部分だけ軽量化して使う
- 玉川大学周辺だけ切り出す
- 必要なら GLB 化や別形式化して軽くする
- 重点エリアだけ表示する

> [!IMPORTANT]
> 初期版では **「町田市全域」ではなく「玉川大学周辺だけ」** を対象にする。  
> データが重いとスマホ体験が悪化する。

### 15.8.4 custom layer 用の責務
`plateauLayer.ts` にまとめる。

```ts title="src/app/map/layers/plateauLayer.ts"
export function createPlateauLayer() {
  // Three.js + 3D Tiles 読み込み処理
  // localTransform / MercatorCoordinate / camera sync をここに閉じ込める
}
```

---

## 15.9 Scaniverse の使い方（補助的な 3D 資産作成）

### 15.9.1 Scaniverse の位置づけ
Scaniverse は、**室内ナビ完成ツールではなく、3D 資産作成ツール** として使う。

### 15.9.2 何をスキャンするか
優先順位は以下。

1. 校門・建物入口・案内看板
2. 学祭のゲートや特徴的な目印
3. 屋外オブジェ・モニュメント
4. 特定会場の入口周辺
5. 必要なら特定室内空間の簡易 3D 化

### 15.9.3 どう使うか
1. Scaniverse でスキャンする  
2. GLB などで書き出す  
3. `public/models/` に配置する  
4. MapLibre + Three.js 上で現実座標に配置する

### 15.9.4 期待しないこと
- 室内現在地の推定
- 室内経路探索
- 全建物室内対応

> [!WARNING]
> Scaniverse は **「場所を 3D 化する」ことには強い** が、  
> それだけで **「ナビゲーション」や「測位」まで完成するわけではない**。

---

## 16. 詳しい実装順序

## Step 1：地図だけ出す
- MapLibre を表示
- 玉川大学周辺に中心を合わせる
- スマホで動作確認

## Step 2：現在地を出す
- Geolocation API を接続
- 青い点を表示
- 現在地ボタンを追加

## Step 3：POI を出す
- GeoJSON を読み込む
- トイレ、受付、模擬店を表示
- タップで詳細を出す

## Step 4：カテゴリフィルター
- food / stage / toilet / info などを切り替え
- 一覧 UI も追加

## Step 5：近くの施設
- 距離を計算
- 近い順で数件表示

## Step 6：背景 3D
- PLATEAU 背景を統合
- パフォーマンス確認
- 必要なら範囲縮小

## Step 7：必要に応じて Scaniverse 追加
- 校門や入口の目印を 3D 化
- 玉川大学らしさを足す

## Step 8：最終調整
- モバイル UI
- 説明文
- イベント情報
- 公開準備

---

## 17. データ設計

### 17.1 施設データ
施設情報は **GeoJSON** を基本とする。

```json title="public/data/pois.geojson"
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "geometry": {
        "type": "Point",
        "coordinates": [139.48, 35.56]
      },
      "properties": {
        "id": "stall-001",
        "name": "たこ焼き研究会",
        "category": "food",
        "description": "学生団体のたこ焼き模擬店",
        "hours": "10:00-16:00",
        "image": "/images/stall-001.jpg",
        "tags": ["food", "outdoor"]
      }
    }
  ]
}
```

### 17.2 カテゴリデータ
```json title="public/data/categories.json"
[
  { "id": "food", "label": "食べ物", "color": "#f97316" },
  { "id": "stage", "label": "ステージ", "color": "#8b5cf6" },
  { "id": "toilet", "label": "トイレ", "color": "#3b82f6" },
  { "id": "info", "label": "受付", "color": "#10b981" }
]
```

### 17.3 イベントデータ
```json title="public/data/events.json"
[
  {
    "id": "event-001",
    "title": "軽音ライブ",
    "placeId": "stage-main",
    "start": "2026-11-01T11:00:00+09:00",
    "end": "2026-11-01T11:30:00+09:00",
    "description": "メインステージでのライブ企画"
  }
]
```

---

## 18. UI 設計方針

### 18.1 画面の基本原則
- 1画面で完結できることを優先
- 2〜3 タップ以内で欲しい情報に到達
- 情報を詰め込みすぎない

### 18.2 下部シートを主役にする
施設詳細は別ページ遷移より、  
**下部シート** の方がモバイル体験に向く。

### 18.3 一覧画面は補助
地図が苦手な人向けに一覧は用意するが、  
主導線はあくまで地図画面に置く。

---

## 19. Cloudflare Pages での公開方法

### 19.1 GitHub 連携前提
- GitHub に push
- Cloudflare Pages でリポジトリ接続
- Vite の build 結果 `dist` を配信

### 19.2 代表設定
```txt title="cloudflare-pages-build.txt"
Framework preset: Vite
Build command: npm run build
Build output directory: dist
```

### 19.3 注意点
- `public/` 配下の静的ファイルがそのまま配信される
- 大きすぎるモデルは避ける
- 相対パスの確認を行う

> [!TIP]
> 最初は **静的サイトとして成立する形** を優先する。  
> サーバサイド処理や DB は入れない。

---

## 20. テスト方針

### 20.1 最低限確認すること
- iPhone / Android で開けるか
- 現在地が取れるか
- POI が表示されるか
- タップで詳細が出るか
- フィルターが効くか
- 近くの施設が出るか
- 地図が重すぎないか

### 20.2 実地確認
可能なら玉川大学キャンパスで確認する。

- 受付位置が正しいか
- ステージ位置が正しいか
- GPS が現場で使い物になるか
- 入口周辺の案内にズレがないか

---

## 21. リスクと対策

### リスク1：3Dデータが重い
**対策**
- 玉川大学周辺だけに絞る
- 背景 3D は必要範囲のみ
- Scaniverse モデルは後から追加

### リスク2：現在地精度が安定しない
**対策**
- 屋外中心で使う
- 「だいたいの位置」で使う前提
- 入口案内・施設検索中心にする

### リスク3：機能を盛りすぎる
**対策**
- 経路探索は入れない
- 室内ナビは入れない
- MVP 以外は後回し

### リスク4：開発が長引く
**対策**
- 先に地図＋現在地＋POI を完成させる
- 背景 3D は後からでもよい
- Scaniverse は余力追加にする

---

## 22. リリース判定基準

以下を満たしたら初期版を公開可能と判断する。

- スマホで地図が開く
- 現在地が表示できる
- 主要カテゴリの施設が表示できる
- 施設詳細が見られる
- UI が最低限破綻していない
- 学園祭当日に来場者が使って意味がある

---

## 23. 未決事項

- 掲載対象施設の最終一覧
- 施設詳細の文章と画像の準備方法
- 玉川大学キャンパス内でどこまで 3D 表示対象にするか
- イベント情報を初期版に含めるか
- 学園祭終了後も公開を継続するか

---

## 24. 優先順位

### 最優先
- 地図
- 現在地
- 施設情報

### 次点
- 3D の見栄え向上
- 一覧画面
- 近くの施設機能

### 後回し
- 経路探索
- 室内ナビ
- 混雑表示
- 高度な演出

---

## 25. 一言で表すなら

**「玉川大学コスモス祭の来場者向け、現在地付き 3D 案内マップ」**

---

## 26. Fuwari 用メモ

### 26.1 GitHub Syntax の注意
以下のように書く。

```md title="github-admonition-example.md"
> [!NOTE]
> これは GitHub Syntax の NOTE です。

> [!TIP]
> これは TIP です。

> [!WARNING]
> これは WARNING です。
```

### 26.2 GitHub リポジトリカード
```md title="github-card.md"
::github {repo="yourname/your-repo"}
```

### 26.3 動画埋め込み
```html title="embed-video.html"
<iframe
  width="100%"
  height="468"
  src="https://www.youtube.com/embed/XXXXXXXXXXX"
  title="YouTube video player"
  frameborder="0"
  allowfullscreen>
</iframe>
```

### 26.4 実装メモ欄
- [ ] 地図の初期表示
- [ ] 現在地表示
- [ ] POI データ作成
- [ ] 施設詳細 UI
- [ ] カテゴリフィルター
- [ ] 近くの施設
- [ ] 背景 3D
- [ ] スマホでの動作確認
- [ ] Cloudflare Pages 公開
- [ ] 必要なら Scaniverse モデル追加

---
