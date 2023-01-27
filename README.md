# Ansible Playbook を localhost で実行するサンプル

(Japanese) `ansible-playbook` のタスクを localhost で実行するサンプルです。

## 前提条件

- Python 3.11
- Poetry 1.x
- Ansible 7.x

いくつかの方法があります。

- 方法 A) コマンドラインオプションで指定する
- 方法 B) インベントリ設定で指定する
- 方法 C) プレイブックで指定する
- 方法 D) タスクで指定する

以下のコマンドではすべて事前に `poetry shell` を実行してある前提となっています。

```bash
poetry shell
```

## 方法 A) コマンドラインオプションで指定する

```bash
ansible-playbook \
  --connection=local \
  -i localhost, \
  --limit=localhost \
  playbooks/show-term.yml
```

`ansible-playbook` コマンドにオプション `--connection=local` `-i localhost,` `--limit=localhost` を渡して実行します。

## 方法 B) インベントリ設定で指定する

```bash
ansible-playbook \
  -i inventory/local.yml \
  playbooks/show-term.yml
```

インベントリ設定で `ansible_connection: local` と `ansible_host: localhost` を指定します。

## 方法 C) プレイブックで指定する

```bash
ansible-playbook playbooks/show-term-on-local.yml
```

プレイブック内で `hosts: localhost` と `connection: local` を指定します。

```text
[WARNING]: No inventory was parsed, only implicit localhost is available
[WARNING]: provided hosts list is empty, only localhost is available. Note that the
implicit localhost does not match 'all'
```

## 方法 D) タスクで指定する

```bash
ansible-playbook -i xyz, playbooks/show-term-on-local-task-only.yml
```

プレイブックのタスク内で `delegate_to: localhost` を指定します。
