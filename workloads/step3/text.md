# Deployment

## Deploymentを作ろう
ReplicaSetはPodを管理していました。DeploymentはReplicaSetを内部的に作ってそれを管理します。


まずはDeploymentを作りましょう。

```
kubectl apply -f deployment-v1.yaml
```

Podを確認してみてください。またどれか一つ、Podの詳細を見てみましょう。
Container定義の中のImage定義を覚えておいてください。

```
kubectl describe pod <pod名>
```

## バージョンアップを試してみよう

さきほどDeploymentのバージョン2を作ってみます。

```
kubectl apply -f deployment-v2.yaml
```

ちょっと時間がかかるので、ついでに以下のコマンドでローリングアップデートされている様を見ておきましょう。Ctrl+Cで見るのをやめられます。

```
kubectl get pod -w
```

全部Runningになったら、同様にPodの確認と詳細を見てみましょう。

バージョン1のときのPodのpythonバージョンよりバージョンが上がっていることが分かると思います。

## ロールバックもしてみよう

しかし！ ここで新しいpythonバージョンにしたことによる不具合がでたとしましょう。

バージョン1にロールバックしなきゃなので、このコマンドでロールバックします。

```
kubectl rollout undo deployment/hello-deploy
```

また、以下コマンドで進捗を確認できます。
```
kubectl rollout status deployment/hello-deploy
```

Podの確認と詳細を見てみるとpythonのバージョンが戻っていることが分かると思います。

## ReplicaSetの機能も兼ね備えているよ

適当にどれかPodを消してみてください。
その後Podを確認するとPodの数が削除前と変わらないのがわかりますね。


DeploymentはReplicaSetの機能を備えつつ、バージョン管理ができるということですね。


次に行きましょう。