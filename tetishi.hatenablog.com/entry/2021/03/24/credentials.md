---
Title: Rails 6よりサポートされているMulti Environment Credentialsを導入する
Date: 2021-03-24T11:29:14+09:00
---

# 開発環境
```
$ ruby -v
ruby 3.0.0

$ bin/rails -v
Rails 6.0.3.4
```


$ tree .
.
...
├── config
... ...
│   ├── credentials
│   │   ├── development.key
│   │   ├── development.yml.enc
│   │   ├── production.key
│   │   ├── production.yml.enc
│   │   ├── staging.key
│   │   └── staging.yml.enc
│   │   ├── test.key
│   │   └── test.yml.enc
│   ├── credentials.yml.enc
... ...
│   ├── master.key
... ...

Masterのcredentials keyを生成・秘匿情報の編集
$ EDITOR=vim bin/rails credentials:edit




環境毎のcredentials keyを生成・秘匿情報の編集
# テスト環境
```
$ EDITOR="vim" bin/rails credentials:edit -e test
```

# 開発環境
```
$ EDITOR="vim" bin/rails credentials:edit -e development
```

# ステージング環境
```
$ EDITOR="vim" bin/rails credentials:edit -e staging
```

# 本番環境
```
$ EDITOR="vim" bin/rails credentials:edit -e production
```
開発環境なら、-e developmentという感じでオプションで環境を指定します。ちなみに、--environment=developmentという指定も同じです。

環境毎のcredentialsを確認
# テスト環境
```
$ bin/rails credentials:show -e test
```

# 開発環境
```
$ bin/rails credentials:show -e development
```

# ステージング環境
```
$ bin/rails credentials:show -e staging
```

# 本番環境
```
$ bin/rails credentials:show -e production
```

aws:
  access_key_id: 123
  secret_access_key: 345
credentialsへのアクセス
# 本番環境の場合
```
$ bin/rails c -e production
```

# 設定内容を確認
```
pry(main)> Rails.application.credentials.config
=> {:aws=>{:access_key_id=>123, :secret_access_key=>345}}
```

# 設定値にアクセス
```
pry(main)> Rails.application.credentials.aws[:access_key_id]
=> 123
```

# この書き方も同じ
```
pry(main)> Rails.application.credentials.dig(:aws, :access_key_id)
=> 123
```
