# maven-multi-project-example
Mavenを使ったマルチモジュールの構成例

## 構成

- Java11
- Maven（Maven Wrapper）

## プロジェクトの構成

プロジェクトの構成は1つのライブラリモジュールを1つのコマンドラインアプリケーション（batch）と2つのWebアプリケーション（webapp、webservice）で参照する以下の様な構成

```bash
maven-multi-module-example
├ core        # 他のモジュールで共用するモジュール
├ batch       # バッチアプリケーションのモジュール
├ schema      # データベースマイグレーション
├ webapp      # Webアプリケーションのモジュール
└ webservice  # Webサービスのモジュール
```

- core - webapp、webservice、batch から参照されるライブラリモジュール
- batch - SpringBoot を利用したコマンドラインアプリケーション
- schema - データベースマイグレーション
- webapp - SpringBoot を利用したのWebアプリケーション
- webservice - SpringBoot を利用したのWebアプリケーション

## データベースマイグレーション

- flywayの実行

```bash
./mvnw  -f schema flyway:migrate
```

## 依存関係の更新

```bash
./mvnw versions:display-dependency-updates
```


## リファレンス

- [Guide to Working with Multiple Modules](https://maven.apache.org/guides/mini/guide-multiple-modules.html)
- [First Steps: Maven](https://flywaydb.org/documentation/getstarted/firststeps/maven)
- [Maven/Gradleでdependencyのupdateをチェックする](https://hirakida29.hatenablog.com/entry/2019/11/13/151358)
