# やわらかい説明文の書き方

READMEや画面の案内を、読みやすい日本語に整えるAIエージェント用スキルです。
短い文とふだんの言葉で、読み手が次にすることを伝えます。
コマンド、設定名、画面のボタン名はそのまま残します。

たとえば、次のように頼めます。

```text
yawaraka-setsumeiを使って、このREADMEを読みやすくしてください。
手順や条件は省かず、コマンドと画面の言葉は変えないでください。
```

## どんなときに使うか

- READMEや使い方の説明を書くとき
- 英語の説明を日本語にするとき
- CLIの`--help`やエラーメッセージを書くとき
- 画面の案内が長い、かたいと感じたとき

コードのコメント、コミットメッセージ、社外への正式な文書は対象外です。
説明の意味が正しいかは、元のコードや資料と合わせて確かめます。

## 実際に使ってみた例

[Skeb Local Following](https://github.com/h4lmirn/skeb-local-following)は、作者の公開プロジェクトです。
Skebで手動保存した情報を、フォロー中の一覧に表示するChrome拡張です。

このREADMEを作る際に、Codexで本スキルを使いました。
次の2例は、そのとき実際に書き直した文章です。
比較用にここへ載せており、元のプロジェクトには反映していません。
元の文は[2026年9月24日に確認したREADME](https://github.com/h4lmirn/skeb-local-following/blob/e5510d6caff8cdbc0c662a1922942c0ffe8ac226/README.md)から引用しています。

### 情報が古いときの案内

元の文：

> 本拡張は自動更新しません。クリエイターページを再度開き、「一覧用情報を更新」を押してください。

書き直した文：

> クリエイターページをもう一度開きます。
> 「一覧用情報を更新」を押してください。
> この拡張は、保存した情報を自動では更新しません。

操作を先に置き、理由をあとに分けました。
「本拡張」「再度」を、ふだん使う言葉に変えています。
ボタン名の「一覧用情報を更新」は変えていません。

### 保存した情報の置き場所

元の文：

> 情報は `chrome.storage.local` に保存され、ブラウザの同期領域や開発者のサーバーには送信されません。画像ファイル自体は保存しません。

書き直した文：

> 情報は、この端末の `chrome.storage.local` に保存します。
> ブラウザの同期用の保存先や、開発者のサーバーには送りません。
> 画像ファイルそのものは保存しません。

保存先と送り先の説明を分けました。
`chrome.storage.local`は、保存先を示す名前として残しています。
「外へは何も送りません」のように、元の文より広い約束には変えていません。

## 始め方

使っているAIエージェントの手順を1つ選んでください。
スキルの中身はMarkdownファイル2つです。
このスキル専用のAPIキーや、追加のプログラムは要りません。
AIエージェント自体の利用条件や料金は、それぞれのサービスに従います。

以下のコマンドは、Gitが使えるmacOS、Linux、WSL向けです。
`~`は、自分のホームフォルダを表します。
同じ名前のフォルダがすでにある場合は、先に中身を確認してください。
このリポジトリをすでに入れている場合は、後述の更新手順を使います。

### Codex

自分のプロジェクトで共通して使う場合は、次を実行します。

```sh
mkdir -p ~/.agents/skills
git clone https://github.com/h4lmirn/yawaraka-setsumei.git ~/.agents/skills/yawaraka-setsumei
```

Codexに次のように頼みます。

```text
$yawaraka-setsumei を使って、README.mdを読みやすくしてください。
```

CLIやIDE拡張では、`/skills`からも選べます。
見つからない場合は、Codexを開き直してください。
以前に`~/.codex/skills`へ入れて認識されている場合は、重ねて入れる必要はありません。
上の手順は、現在の公式資料にある保存先に合わせています。

出典：[Codexのスキルと保存先](https://learn.chatgpt.com/docs/build-skills)

### Claude Code

自分のMacやPC上のClaude Codeで使う場合は、次を実行します。

```sh
mkdir -p ~/.claude/skills
git clone https://github.com/h4lmirn/yawaraka-setsumei.git ~/.claude/skills/yawaraka-setsumei
```

Claude Codeで次のように頼みます。

```text
/yawaraka-setsumei README.mdを読みやすくしてください。
```

この保存先は、ローカルのClaude Code用です。
Coworkやクラウドのセッションには、そのままでは引き継がれません。

出典：[Claude Codeのスキル](https://code.claude.com/docs/en/skills)

### Cursor

自分のPC上のCursorで使う場合は、次を実行します。

```sh
mkdir -p ~/.cursor/skills
git clone https://github.com/h4lmirn/yawaraka-setsumei.git ~/.cursor/skills/yawaraka-setsumei
```

Agentのチャットで、次のように頼みます。

```text
yawaraka-setsumeiスキルを使って、README.mdを読みやすくしてください。
```

クラウドのエージェントで使う場合は、別途スキルの同期が必要です。
プロジェクト内にスキルを置く方法もあります。

出典：[CursorのAgent Skills](https://cursor.com/docs/skills)

### GitHub Copilot

自分用に入れる場合は、次を実行します。

```sh
mkdir -p ~/.copilot/skills
git clone https://github.com/h4lmirn/yawaraka-setsumei.git ~/.copilot/skills/yawaraka-setsumei
```

スキルに対応したCopilotのエージェントで、次のように頼みます。

```text
yawaraka-setsumeiスキルを使って、README.mdを読みやすくしてください。
```

クラウドのエージェントやチームでも使う場合は、プロジェクト内に置きます。
保存先は`.github/skills/yawaraka-setsumei/`です。
そのフォルダもGitHubに反映してください。

出典：[GitHub CopilotのAgent Skills](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills)

### Gemini CLI

Gemini CLIのインストール機能を使います。

```sh
gemini skills install https://github.com/h4lmirn/yawaraka-setsumei.git --scope user
gemini skills list
```

確認が出たら、内容を読んでインストールします。
すでに開いているセッションでは、`/skills reload`を実行してください。
そのあと、次のように頼みます。

```text
yawaraka-setsumeiスキルを使って、README.mdを読みやすくしてください。
```

出典：[Gemini CLIのAgent Skills](https://geminicli.com/docs/cli/skills/)

### 1つのプロジェクトだけで使う場合

GitHubの「Code → Download ZIP」でファイルをダウンロードします。
ZIPを開き、`SKILL.md`と`references`を次の保存先へコピーします。
表の保存先は、使いたいプロジェクトのルートから見た場所です。

| AIエージェント | 保存先 |
| --- | --- |
| Codex | `.agents/skills/yawaraka-setsumei/` |
| Claude Code | `.claude/skills/yawaraka-setsumei/` |
| Cursor | `.cursor/skills/yawaraka-setsumei/` |
| GitHub Copilot | `.github/skills/yawaraka-setsumei/` |

たとえば、Codexなら次の形にします。

```text
あなたのプロジェクト/
└── .agents/
    └── skills/
        └── yawaraka-setsumei/
            ├── SKILL.md
            └── references/
                └── kotoba.md
```

Gemini CLIでは、プロジェクトのフォルダで次を実行します。

```sh
gemini skills install https://github.com/h4lmirn/yawaraka-setsumei.git --scope workspace
```

Windowsで手動コピーする場合も、同じフォルダ構成にします。
ホームフォルダは通常`C:\Users\ユーザー名`です。
WSLでエージェントを動かしている場合は、WSL側に置いてください。

## どう頼むか

直したいものと、残したい条件を一緒に伝えます。

READMEなら：

```text
yawaraka-setsumeiを使って、初めて使う人向けにREADMEを直してください。
導入の手順、できないこと、データの送り先は省かないでください。
数や初期値はコードで確かめてください。
```

エラーメッセージなら：

```text
yawaraka-setsumeiを使って、このエラーメッセージを2文にしてください。
1文目に何が起きたか、2文目に次にすることを書いてください。
```

画面の文言なら：

```text
yawaraka-setsumeiを使って、この設定画面の説明を短くしてください。
ボタン名、設定名、保存するデータの範囲は変えないでください。
```

## 更新したいとき

`git clone`で入れた場合は、そのフォルダで更新します。
Codexの保存先なら、次のコマンドです。

```sh
git -C ~/.agents/skills/yawaraka-setsumei pull --ff-only
```

ほかのエージェントでは、パスを実際の保存先に置き換えます。
手動でコピーした場合は、新しいZIPから2つのファイルを入れ直します。
自分で編集した内容がある場合は、先に別の場所へ保存してください。

## うまく読み込まれないとき

- `SKILL.md`が、`yawaraka-setsumei`のすぐ下にあるか確かめます。
- `references/kotoba.md`も一緒に置きます。
- チャットで`yawaraka-setsumei`という名前を明示します。
- エージェントを開き直すか、スキル一覧を更新します。
- 使っている版がAgent Skillsに対応しているか、公式資料で確かめます。

導入方法は、2026年9月24日に各社の公式資料で確認しました。
Codexでは、ローカルへの導入と、このREADMEでの使用を確認しています。
ほかの4つは公式資料に基づく手順で、実機での確認はしていません。

## 中のファイル

| ファイル | 内容 |
| --- | --- |
| [SKILL.md](SKILL.md) | 文の長さ、言葉の選び方、書いたあとの点検 |
| [references/kotoba.md](references/kotoba.md) | かたい言葉を言い換える例 |

本スキルは、この2つだけで使えます。
ほかの文章スキルを入れる必要はありません。
`japanese-tech-writing`も使う場合は、役割の分け方を`SKILL.md`に記しています。
