# Ansible Playbook を localhost で実行するサンプル

(Japanese) `ansible-playbook` のタスクを localhost で実行するサンプルです。

## 必須条件

- Python 3.9
- Poetry 1.x
- Ansible 4.x

いくつかの方法があります。

- 方法 A) コマンドラインオプションで指定する
- 方法 B) インベントリ設定で指定する
- 方法 C) プレイブックで指定する
- 方法 D) タスクで指定する

## 方法 A) コマンドラインオプションで指定する

```bash
poetry run ansible-playbook \
  --connection=local \
  -i localhost, \
  --limit localhost \
  playbooks/show-term.yml
```

## 方法 B) インベントリ設定で指定する

```bash
poetry run ansible-playbook \
  -i inventory/local.yml \
  playbooks/show-term.yml
```

## 方法 C) プレイブックで指定する

```bash
poetry run ansible-playbook playbooks/show-term-on-local.yml 
```

## 方法 D) タスクで指定する

```bash
poetry run ansible-playbook -i xyz, playbooks/show-term-on-local-task-only.yml
```
