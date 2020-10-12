# vsphere-public
ここを参考にしたやつ。
* https://github.com/hiro52/tower-demo
* https://qiita.com/chataro0/items/4276985a67b531fb32b0

# メモ


## create_guestvm-static-ip.yml
任意のIPアドレスを設定できる。ただし、DNSはWindowsのみ対応くさい。


## hostsの指定について(awx利用時)
プレイブック内のhostsに「localhost」を指定すると一部のプラグインで動作しないことがある。(vmwaer_tag_hogehogeが動かなかった)  
awxよくわからんが「localhost」を指定するとawx(docker)でプレイブック実行している？ので、  
ここで動作しているansible/もしくはpythonのバージョンに依存したりするのかと。  
なのでhostsにはホストサーバのIPを直接指定すれば問題なく動作した。
### その後追加
localhostでもいける方法について。awxインベントリツリー内の「変数名:awxホストのIPアドレス」を記載するといける
```
---
ansible_host: 192.168.10.9
ansible_python_interpreter: /usr/bin/python3 # これはおまけ

```
