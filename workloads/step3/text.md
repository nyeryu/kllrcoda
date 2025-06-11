# Deployment

ReplicaSetはPodを管理していました。DeploymentはReplicaSetを内部的に作ってそれを管理します。


まずはDeploymentを作りましょう。

```
kubectl apply -f deployment-v1.yaml
```

Podを確認してみてください。またどれか一つ、Podの詳細を見てみましょう。

```
kubectl describe pod <pod名>
```

そしたら、さきほどDeploymentのバージョン2を作りましょう。

```
kubectl apply -f deployment-v2.yaml
```

同様にPodの確認と詳細を見てみましょう。

バージョン1のときのPodのpythonバージョンよりバージョンが上がっていることが分かると思います。
しかし！ ここで新しいバージョンにしたことによる不具合がでたとしましょう。

バージョン1にロールバックしなきゃなので、このコマンドでロールバックします。

```
kubectl rollout undo deployment/hello-deploy
```

また、以下コマンドで進捗を確認できます。
```
kubectl rollout status deployment/hello-deploy
```

Podの確認と詳細を見てみるとpythonのバージョンが戻っていることが分かると思います。


ついでに適当にどれかPodを消してみてください。

その後Podを確認するとPodの数が削除前と変わらないのがわかりますね。

DeploymentはReplicaSetの機能を備えつつ、バージョン管理ができるということですね。
