# React + TypeScript + Vite + Tailwind CSS ボイラープレート

Vite を使用した TypeScript と Vite と　 Tailwind CSS を設定した最小限の React ボイラープレートです。

> ボイラープレートとは、最小限の変更で再利用できる標準化されたコードセットのことです。このプロジェクトは、React、TypeScript、Vite、Tailwind CSS を使った開発をすぐに始められるように、必要な設定や構造が既に整えられています。

## 目次

- [React + TypeScript + Vite + Tailwind CSS ボイラープレート](#react--typescript--vite--tailwind-css-ボイラープレート)
  - [目次](#目次)
  - [1. 技術スタック](#1-技術スタック)
  - [2. ファイル構造](#2-ファイル構造)
  - [3. 使い方](#3-使い方)
    - [3-1. テンプレートの使用方法](#3-1-テンプレートの使用方法)
    - [3-2. 開発](#3-2-開発)
  - [4. Tailwind CSS ガイドライン](#4-tailwind-css-ガイドライン)
    - [4-1. `tailwind.config.js`で Tailwind を設定する](#4-1-tailwindconfigjsで-tailwind-を設定する)
    - [4-2. 共通スタイルには`@apply`を使用する](#4-2-共通スタイルにはapplyを使用する)
    - [4-3. 一貫したクラスの順序を維持する](#4-3-一貫したクラスの順序を維持する)
    - [4-4. レスポンシブユーティリティを慎重に適用する](#4-4-レスポンシブユーティリティを慎重に適用する)
    - [4-5. ユーティリティクラスの過剰使用を避ける](#4-5-ユーティリティクラスの過剰使用を避ける)
    - [4-6. 動的クラス名を避ける](#4-6-動的クラス名を避ける)
    - [4-7. アクセシビリティガイドラインを尊重する](#4-7-アクセシビリティガイドラインを尊重する)
    - [4-8. 本番環境で Tailwind を最小化する](#4-8-本番環境で-tailwind-を最小化する)
    - [4-9. リンターとフォーマッターを使用する](#4-9-リンターとフォーマッターを使用する)
    - [4-10. スケーリング時にデザイントークンを使用する](#4-10-スケーリング時にデザイントークンを使用する)
  - [5. VSCode 拡張機能（推奨）](#5-vscode-拡張機能推奨)
  - [6. 備考](#6-備考)

---

## 1. 技術スタック

- React 19
- TypeScript 5.7
- Tailwind CSS 4.1
- Vite 6.3
- ESLint 9

---

## 2. ファイル構造

```txt
react-ts-vite-boilerplate/
├── public/                    # 静的ファイル
│   └── vite.svg
├── src/                       # アプリケーションのソースコード
│   ├── api/                   # APIサービス、エンドポイント、ネットワークリクエスト
│   ├── assets/                # 画像、フォントなどの静的アセット
│   ├── components/            # 再利用可能なUIコンポーネント
│   ├── hooks/                 # カスタムReactフック
│   ├── pages/                 # アプリケーションのページ/ルート
│   ├── styles/                # グローバルスタイルとTailwindのカスタマイズ
│   │   └── index.css          # グローバルCSSとTailwindのインポート
│   ├── types/                 # TypeScriptの型定義とインターフェース
│   ├── utils/                 # ユーティリティ関数とヘルパーメソッド
│   ├── App.tsx                # メインのAppコンポーネント
│   ├── main.tsx               # アプリケーションのエントリーポイント
│   └── vite-env.d.ts          # Vite環境用のTypeScript宣言
├── .gitignore                 # Gitが無視すべきファイルを指定
├── eslint.config.js           # ESLint設定
├── index.html                 # メインHTMLファイル
├── package.json               # プロジェクトのメタデータと依存関係
├── tailwind.config.js         # Tailwind CSS設定
├── tsconfig.json              # TypeScript設定
├── tsconfig.app.json          # アプリケーションコード用のTypeScript設定
├── tsconfig.node.json         # Node.js環境用のTypeScript設定
└── vite.config.ts             # Vite設定
```

---

## 3. 使い方

### 3-1. テンプレートの使用方法

1. このポジトリをクローンします：

   ```bash
   git clone https://github.com/あなたのユーザー名/react-ts-vite-boilerplate.git
   cd react-ts-vite-boilerplate
   ```

2. 依存関係をインストールします：

   ```bash
   npm install
   ```

### 3-2. 開発

1. 開発サーバーを起動します：

   ```bash
   npm run dev
   ```

2. 本番環境用ビルド：

   ```bash
   npm run build
   ```

3. 本番環境ビルドのプレビュー：

   ```bash
   npm run preview
   ```

---

## 4. Tailwind CSS ガイドライン

以下のガイドラインは、React プロジェクトでの Tailwind の一般的なベストプラクティスを表しています。

チームは、特定のプロジェクト要件やチーム設定に合わせて、これらの推奨事項を調整・修正することが推奨されます。

### 4-1. `tailwind.config.js`で Tailwind を設定する

- プロジェクトの**カラーパレット**、**スペーシングスケール**、**フォントファミリー**、**ブレークポイント**をこのファイルで定義します。
- インラインの hex コードは避け、セマンティックなクラス名（例：`bg-primary`、`text-accent`）を使用してください。

**設定例：**

```js
// tailwind.config.js
module.exports = {
  content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],
  theme: {
    extend: {
      colors: {
        primary: {
          DEFAULT: "#3b82f6", // blue-500
          dark: "#2563eb", // blue-600
          light: "#60a5fa" // blue-400
        },
        secondary: {
          DEFAULT: "#10b981", // emerald-500
          dark: "#059669", // emerald-600
          light: "#34d399" // emerald-400
        },
        background: "#f9fafb", // gray-50
        surface: "#ffffff",
        error: "#ef4444" // red-500
      },
      fontFamily: {
        sans: ["Inter", "sans-serif"],
        heading: ["Montserrat", "sans-serif"]
      }
    }
  },
  plugins: []
};
```

### 4-2. 共通スタイルには`@apply`を使用する

- CSS モジュールまたはグローバルスタイルで`@apply`を介して、再利用可能なユーティリティの組み合わせをカスタムクラス名に抽出します。
- 例：`.btn-primary`にはパディング、ボーダー半径、ホバー状態を含める必要があります。

**実装例：**

```css
/* src/styles/buttons.css */
.btn-primary {
  @apply px-4 py-2 bg-primary text-white rounded-md shadow hover:bg-primary-dark transition-colors;
}

.btn-secondary {
  @apply px-4 py-2 bg-secondary text-white rounded-md shadow hover:bg-secondary-dark transition-colors;
}
```

**コンポーネントでの使用法：**

```tsx
import "../styles/buttons.css";

function ButtonExample() {
  return (
    <div className="space-x-4">
      <button className="btn-primary">プライマリーボタン</button>
      <button className="btn-secondary">セカンダリーボタン</button>
    </div>
  );
}
```

### 4-3. 一貫したクラスの順序を維持する

- ユーティリティクラスをカテゴリ別に構造化します：**レイアウト → スペーシング → タイポグラフィ → 色 → エフェクト**。

**例：**

```tsx
<div className="flex items-center justify-between gap-4 px-6 py-2 text-sm font-medium text-white bg-primary rounded-md shadow-sm hover:bg-primary-dark transition-colors" />
```

### 4-4. レスポンシブユーティリティを慎重に適用する

- 適応型レイアウトを構築するためにレスポンシブプレフィックス（`sm:`、`md:`、`lg:`）を使用します。
- 必要でない限り、ブレークポイント間でスタイルを複製しないでください。

**レスポンシブデザインの例：**

```tsx
<div className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
  <div className="p-4 bg-surface rounded-md shadow">カード1</div>
  <div className="p-4 bg-surface rounded-md shadow">カード2</div>
  <div className="p-4 bg-surface rounded-md shadow">カード3</div>
  <div className="p-4 bg-surface rounded-md shadow">カード4</div>
</div>
```

### 4-5. ユーティリティクラスの過剰使用を避ける

- クリーンで簡潔なクラスの組み合わせを優先します。
- 必要でない限り、矛盾するマージン/パディングクラスを重ねないでください。

**良い例：**

```tsx
// 良い例：クリーンで簡潔
<div className="p-4 m-2 bg-surface rounded-md">
  <h2 className="text-lg font-semibold mb-2">タイトル</h2>
  <p className="text-gray-700">コンテンツ</p>
</div>
```

**悪い例：**

```tsx
// 悪い悪い例：冗長で矛盾するクラス
<div className="px-4 py-4 pt-4 pb-4 m-2 mt-2 mb-2 ml-2 mr-2 bg-surface bg-white rounded-md">
  <h2 className="text-lg text-base font-semibold font-bold mb-2">タイトル</h2>
  <p className="text-gray-700">コンテンツ</p>
</div>
```

### 4-6. 動的クラス名を避ける

- 文字列補間やテンプレートリテラルでクラス名を生成しないでください。
- メンテナンス性とビルド時の検出のために、静的クラス文字列を優先します。

**良い例：**

```tsx
// 良い例：条件付きクラス名の使用
import clsx from "clsx";

function Button({ primary }) {
  return (
    <button
      className={clsx(
        "px-4 py-2 rounded-md",
        primary ? "bg-primary text-white" : "bg-gray-200 text-gray-800"
      )}
    >
      ボタン
    </button>
  );
}
```

**悪い例：**

```tsx
// 悪い例：クラス用の文字列補間
function Button({ primary }) {
  return (
    <button
      className={`px-4 py-2 rounded-md ${
        primary ? "bg-primary text-white" : "bg-gray-200 text-gray-800"
      }`}
    >
      ボタン
    </button>
  );
}
```

### 4-7. アクセシビリティガイドラインを尊重する

- フォーカス状態が視覚的に認識できるようにします。
- 色だけのインジケーターは避け、色覚障害のあるユーザーのためにテキストやアイコンを追加します。

**例：**

```tsx
// 良い例：視覚的なフォーカス状態と色だけに頼らない
<button className="px-4 py-2 bg-primary text-white rounded-md focus:outline-none focus:ring-2 focus:ring-primary focus:ring-offset-2">
  <span>送信</span>
  <svg
    className="w-4 h-4 ml-2"
    fill="none"
    viewBox="0 0 24 24"
    stroke="currentColor"
  >
    <path
      strokeLinecap="round"
      strokeLinejoin="round"
      strokeWidth={2}
      d="M5 13l4 4L19 7"
    />
  </svg>
</button>
```

### 4-8. 本番環境で Tailwind を最小化する

- Vite に本番環境で未使用の CSS を自動的にパージさせます。
- 特別な操作は必要ありませんが、最終的なクラスの使用は最小限かつ明確に保ちます。

### 4-9. リンターとフォーマッターを使用する

- クラス名とレイアウトの一貫性のために、ESLint + Prettier フォーマットに従います。
- ユーティリティクラスを 1 行の読みにくい行に自動フォーマットしないでください。

**Tailwind 用の ESLint 設定例：**

```js
// eslint.config.js
module.exports = {
  // ... 他のESLint設定
  rules: {
    // ... 他のルール
    "max-len": [
      "error",
      {
        code: 100,
        ignorePattern: "className|class",
        ignoreUrls: true
      }
    ]
  }
};
```

### 4-10. スケーリング時にデザイントークンを使用する

- プロジェクトサイズが大きくなる場合は、共有トークン（例：`colors.ts`、`spacing.ts`）を定義し、それらを`tailwind.config.js`で使用することを検討してください。

**実装の例：**

```ts
// src/styles/tokens/colors.ts
export const colors = {
  primary: {
    DEFAULT: "#3b82f6",
    dark: "#2563eb",
    light: "#60a5fa"
  },
  secondary: {
    DEFAULT: "#10b981",
    dark: "#059669",
    light: "#34d399"
  }
  // ... 他の色
};

// tailwind.config.js
import { colors } from "./src/styles/tokens/colors";

module.exports = {
  content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],
  theme: {
    extend: {
      colors
      // ... 他のテーマ拡張
    }
  },
  plugins: []
};
```

---

## 5. VSCode 拡張機能（推奨）

1. **Prettier ESLint** (`rvest.vs-code-prettier-eslint`) - 一貫したコードフォーマットとリンティングのために Prettier と ESLint を統合
2. **Tailwind CSS IntelliSense** (`bradlc.vscode-tailwindcss`) - Tailwind CSS クラスのオートコンプリート、構文ハイライト、リンティングを提供
3. **ES7+ React/Redux/React-Native snippets** (`dsznajder.es7-react-js-snippets`) - React 開発に役立つスニペット
4. **Auto Rename Tag** (`formulahendry.auto-rename-tag`) - HTML/JSX タグを編集すると対応するタグが自動的にリネームされる
5. **Color Highlight** (`naumovs.color-highlight`) - コード内のウェブカラー（hex、rgb、rgba）をハイライト表示
6. **vscode-icons** (`vscode-icons-team.vscode-icons`) - ファイルとフォルダのアイコンで VS Code を強化

---

## 6. 備考

`App.tsx`ファイルを変更し、`src/components`ディレクトリにコンポーネントを追加してアプリケーションの構築を始めてください。
