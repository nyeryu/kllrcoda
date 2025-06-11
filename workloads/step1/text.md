# Pod

ともかく最初はPodからです。

以下手順を実行しpodを作成しましょう。
（コピペもいいですが、打ち込んでみましょう。）

```
kubectl apply -f pod.yaml
```

次に作ったPodを見てみましょう。

```
kubectl get pods -n default
```

ここで、Podにアクセスしてみましょう。
わけあって、このままだとPodにアクセスできないのでいったん以下を実行してください。（コピペできます）
`kubectl port-forward pod/hello-once 8080:8080`

実行後、画面右上の≡から「New Terminal Window」を選択してください。
新しいターミナルが開かれるのでpodにアクセスしてみましょう。
`curl localhost:8080`

helloworldが変えるのが確認出来たら次へ行きましょう。