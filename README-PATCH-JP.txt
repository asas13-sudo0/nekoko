Nekogiri v0.5.0 Steam authentication compatibility patch (1.1.0.4)

修正内容:
- 旧 SetPhotonAuthTicket / SendSteamAuthTicket のパラメータなし検索を廃止。
- Photon.Realtime.LoadBalancingClient.OpAuthenticate の全オーバーロードを検出して、
  Photon送信直前にAuthValuesをSteam認証へ差し替える。
- OpAuthenticateが見つからない場合はPhotonNetwork.ConnectUsingSettingsをフォールバックとして使用。
- Auth=none の古いINIでもSteam認証を適用。
- Facepunch.SteamworksのGetAuthSessionTicket(NetIdentity.LocalHost)を使用。
- Steam初期化とPhoton App ID差し替えの既存処理は維持。

重要:
Photon Cloud側のRealtime App IDでSteam認証プロバイダーを有効にし、
Steam Publisher Web API KeyとSteam App IDを設定する必要があります。
クライアントModだけではPhoton Dashboard側の認証プロバイダー設定を変更できません。
APIキーはKirigiri.iniやGitHubに書かないでください。

ビルド:
GitHub Actionsの「Build Nekogiri DLL」を実行し、Artifactを取得してください。
このソースはGitHub Actionsでコンパイルするためのものです。実ゲームでの動作確認は未完了です。


【Steam認証なし版 1.1.0.5】
PhotonへのSteam認証チケット注入は行いません。Steamworks Publisher Web API Key / apiKeySecret は不要です。Steam App IDの切替とKirigiri.iniのPhoton App ID設定は従来どおり残しています。Photon側が通常認証(Auth=none)を許可している必要があります。


1.1.0.6: UseDefaultRepoServers=1 selects the built-in Photon App IDs without overriding SteamAppId. This preserves the separate Steam App ID setting. Steam authentication injection remains disabled.
