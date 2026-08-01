# 椎尾研究室アーカイブサイト テンプレート

お茶の水女子大学 名誉教授 椎尾一郎 研究室（2009年度〜2021年度）の活動記録を
静的HTML/CSSで保存するためのテンプレートです。PukiWikiで運用していた旧サイトの内容を
整理し、更新の必要がない静的ページとして再構成することを想定しています。

## 構成

```
lab-site/
├── index.html          Home（研究室の簡単な紹介）
├── projects.html        Projects（プロジェクト一覧）
├── publications.html    Publications（研究業績）
├── alumnae.html          Alumnae（卒業生一覧）
├── education.html        Education（担当授業）
├── news.html             News Archive（ニュースアーカイブ）
├── sites.html            Sites（外部関連サイトへのリンク）
├── css/
│   └── style.css         全ページ共通スタイル（デザイントークンあり）
├── images/               写真・図版の格納フォルダ（空。適宜追加してください）
└── projects/             プロジェクト個別ページ
    ├── ochahouse.html
    ├── syncdecor.html
    ├── mousefield.html
    └── iconsticker.html
```

## 内容の追加・編集について

- 各ページには `template-note`（黄色い注記ボックス）で、実データに差し替えるべき箇所を明記しています。
  完成後はこのボックスごと削除してください（`<div class="template-note">…</div>` を探して削除）。
- **Projects**：`projects.html` のカードを複製し、対応する個別ページを `projects/` フォルダ内に
  同じ構造（`project-header` → `project-figure` → `project-body`）で追加してください。
- **Publications / News Archive**：年ごとに `<h2 class="year-group-heading">年</h2>` で区切ると、
  項目数が多くなっても見やすさを保てます。
- **Alumnae**：氏名・進路の公開は本人の同意を得た範囲にとどめてください。

## デザインについて

お茶の水女子大学公式サイト（https://www.ocha.ac.jp）のピンク基調・白背景のトーンに合わせつつ、
「活動を終えた研究室の記録」という性格を、見出しの明朝体（Noto Serif JP）で表現しています。
色・フォントは `css/style.css` 冒頭のコメントにまとめてあります。変更する場合は
`:root` 内の CSS変数（`--c-primary` など）を書き換えるだけで全ページに反映されます。

## 大学サーバへの設置

このフォルダ一式（`index.html` 以下すべて）を、そのままサーバの公開ディレクトリに
アップロードするだけで動作します。サーバ側でのプログラム実行（PHP等）は不要です。
PukiWikiのように動的にページを生成しないため、今回問題となったような
脆弱性を突いた攻撃のリスクを大きく減らせます。

## ブラウザでの確認方法

`index.html` をブラウザで直接開くか、簡易サーバで確認できます。

```
cd lab-site
python3 -m http.server 8000
```

その後、ブラウザで `http://localhost:8000/` を開いてください。
