# Pod

ともかく最初はPodからです。

以下手順を実行しpodを作成しましょう。

```
kubectl apply -f pod.yaml
```

次に作ったPodを見てみましょう。

```
kubectl get pods -n default
```

ここで、Podにアクセスしてみましょう。

わけあってこのままだとPodにアクセスできないのでいったん以下を実行してください。（ポートフォワーディングという仕組みですがここでは触れません）

1. 画面右上の≡から「New Terminal Window」を選択
2. 開いたターミナルで以下を実行
   `kubectl port-forward pod/hello-pod 8080:8080`

そしたらもとのターミナルに戻り以下でpodにアクセスしてみましょう。

`curl localhost:8080 -I`


200OKが返るのが確認出来たら新しく開いたターミナルは閉じてしまってOKです。

次へ行きましょう。