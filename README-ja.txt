Nagios Plugin "check_cloudwatch" 使用方法

1) CloudWatch API Tools をインストールする
   pre-requirement: Amazon CloudWatch API Tools installed
   http://developer.amazonwebservices.com/connect/entry.jspa?externalID=2534&categoryID=88 

2) check_cloudwatch スクリプトを、Nagiosユーザが読める任意の位置にコピーする($USER1$ = /usr/lib/nagios/plugins/等 推奨)

3) aws.cfgを所定の位置(/etc/nagios/objects/等)にコピーし、nagios.cfg に登録する
---
cfg_file=/etc/nagios/objects/aws.cfg
---

4) aws.cfgを編集する
 - Instance を登録 (* EC2 instance の alias にはInstanceIdを、RDS instance の alias には DB Instance Nmae を指定します )
 - Instance を region = Hostgroup に登録する
 - Service 指定のhost_nameにcheck対象ホストの名前を追加

tips
5分毎に呼び出すと仮定した場合、呼び出した直前のデータが取れない可能性があるので、360秒＝6分という指定をしています。
実際にコマンドラインから何度か実行して調整するのがよいでしょう。

■historry
1.2 - us-east-1 決め打ちだったのを、複数リージョン対応に伴い、引数変更
1.1 - 閾値が正常状態よりも低くなるような監視の追加(warning > criticalとなるように指定します)
1.0 - 1st release

■TODO
- ELBのチェックをテストする
- UnitがBytes系の表示が見づらいので、KB/MB/GB等表示の実装

■免責事項

本スクリプトを使用して生じたいかなる損害も一切の責任を負いません。
自己の責任の元でご使用ください。

twitter: @j3tm0t0
