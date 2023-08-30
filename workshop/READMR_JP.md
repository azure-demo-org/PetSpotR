#  GitHub Copilot と Codespaces による開発者の生産性の向上

👋 ようこそ！

このワークショップでは、最も人気のある 2 つの機能である GitHub Codespaces と GitHub Copilot に関する多くのエキサイティングなスキルを学びます。

## 👩‍💻 GitHub Codespaces

クラウドコンピューティングは過去数十年で爆発的に増加しました。しかし、クラウドは運用環境のワークロードを実行するだけでなく、開発環境をホストすることもできます。

[GitHub Codespaces](https://github.com/features/codespaces) を使用すると、世界中のほぼどこからでもコーディングできるため、数秒で起動し、作業中のコードに完全に合うようにカスタマイズできる高パフォーマンス VM に支えられた Visual Studio Code が提供されます。

ローカル開発よりもコードスペースを使用する利点はたくさんあります。プロジェクトの一連の依存関係を標準化し、新しい開発者を数日ではなく数秒でオンボーディングし、コンテキスト対応のCodespacesを瞬時にスピンアップおよび破棄できます。

🤯 _おもしろい事実:GitHub自体がCodespacesを使用してGitHubを開発しています!新しいエンジニアは、約10秒でゼロからコーディングの準備をすることができます。そして、それは11GBのコードベースにあります!_

このワークショップでは、次のことを行います:

- コードスペースとは何か、そしてその利点を学ぶ
- 新しいコードスペースを作成する
- コードスペースでのマルチプロセスアプリケーションの実行とデバッグ
- 開発コンテナーについて学習する
- コードスペースの設定変更を行う

## 🤖 GitHub Copilot

2023年には、人工知能(AI)ツールが爆発的に主流になり、生産性の向上と忙しい作業の排除が約束されました。 [GitHub Copilot](https://github.com/features/copilot)  は AI ペアプログラマであり、大規模言語モデル (LLM) に基づく最初の商用ツールの 2021 つでした。2022 年 <> 月にテクニカル プレビューとして最初にリリースされ、<> 年後の <> 年 <> 月に個人向けに一般公開されました。

GitHub Copilotは、コードと関数全体を提案して、コーディングを高速化し、定型文よりもビジネスロジックに集中し、より幸せで生産性の高い開発者になるのに役立ちます。

このワークショップでは、次のことを行います:

- コードスペースで GitHub Copilot を使用する
- GitHub Copilotの助けを借りて、アプリのさまざまな部分に触れる新機能を追加します
- GitHub コパイロットを使用してテストを記述する
- 効果的なコンテキストと、GitHub Copilot から最良の結果を得る方法について学ぶ

# 👟 始めましょう!

このワークショップで何を学ぶかがわかったので、手順を見ていきましょう。

PetSpotRと呼ばれるAIを利用したペットの遺失物アプリを使用します。この Web アプリは C# と Python で、Dapr、Kubernetes と Keda、Bicep、Azure Machine Learning など、さまざまなフレームワークとテクノロジを使用しています。

😨 _これらに精通していなくても心配しないでください。そこで役立つのが Codespaces と GitHub Copilot です。_

## 1. 新しい Codespace を開始する 

すべての依存関係とツールがすでにインストールされている新しいコードスペースを作成することから始めましょう。

1. ブラウザーで https://github.com/gh-productivity-workshops/PetSpotR に移動します。

2. `<> Code` ボタンをクリックしてから, `Codespaces` タブをクリックします。

3. Make sure you can see the note at the bottom - "Codespace usage for this repository is paid for by *gh-productivity-workshops*. If you can't, let one of the workshop team know!
![New Codespace](images/1-new-codespace.png)

4. このウィンドウの上部にある省略記号 (...) をクリック、 `+ New with options...`

![New Codespace with Options](images/2-new-codespace-options.png)

5. *Machine type*のドロップダウンをクリックし、オプションを確認します。使用可能なのは 1 つだけです。これは、組織の管理者によってポリシーとして設定されています。
![Available machine types](images/3-new-codespace-machines.png)

6. "Create codespace"ボタンをクリックして、コードスペースのビルドを確認します

_インストラクターは、コードスペースがスピンアップするのを待っている間にポリシーの設定について話します。_

## 2. Codespace での実行とデバッグ

1. [実行とデバッグ] ペインに移動します (![Run and Debug](images/run-and-debug.png))

2. 上部のドロップダウンが "✅ Debug with Dapr" 構成に設定されていることを確認し、緑色の再生ボタンをクリックします。
![Run and Debug](images/4-run-and-debug.png)

_アプリケーションのバックエンド コンポーネントとフロントエンド コンポーネントの両方が、他の多くのサービスと共に起動する必要があります。これには数分以上かかる場合があります。実行中は、ドロップダウンを使用してデバッグ中のプロセスを確認できます。_

![Debugging](images/5-debugging.png)

3. エディターの下部にある [ポート] ペインに移動し、実行中のコンポーネントを公開するために開かれているポートを確認します。約10になります。
![Open ports](images/6-ports.png)

_これらのポートの表示を変更して、組織内の他のユーザに公開したり、公開したりすることができます。_

4. ポート 5114 のローカルアドレスにカーソルを合わせ、 "Open in Browser" アイコン (![Open in Browser](images/open-in-browser.png)) をクリックして、ブラウザでアプリを開きます。

5. エクスプローラーペイン (![Explorer](images/explorer.png)), に戻り、`src/backend/app.py` を見つけて開きます。

6. 45 行目にブレークポイントを設定します (`print(f'Pet state retrieved', flush=True)`)

7. ブラウザで実行されているアプリケーションで、*I lost my pet* に移動し、フォームに入力します。あなたはあなたのマシン上でどんな画像でも使うことができます、私たちは実際にそれらを処理しません!

8. ブラウザー タブで、ブレークポイントにヒットしたことに注目してください。ブラウザのVSCodeで `data` オブジェクトを直接調べることができます。 
![Breakpoints in Codespaces](images/7-breakpoint.png)

9. 実行中のデバッガーを停止するには、デバッグ ペインの [停止] ボタンをクリックします。これは、実行中のプロセスごとに 1 回、2 回行う必要があります。
![Debugging](images/5-debugging.png)

## 3. Specifying what a Codespace needs

In the Explorer pane, open the `.devcontainer/devcontainer.json` file and explore. Focus on the following:
  - `image` - this is the docker image the Codespace uses. You can also use your own dockerfile, or have a docker compose file for multi-stage builds.
  - `onCreateCommand` - this lets us run our own scripts when the Codespace is created. There's also `postCreateCommand` if you need to wait until everything is otherwise ready to go.
  - `features` - this is the easiest way to add broader features to your Codespace. In our case we've added python and docker-in-docker (which allows us to run multiple containers inside our Codespace!). You can find out more at https://containers.dev/features
  - `customizations.vscode.extensions` - These are the extensions you want VSCode to have when you start a Codespace.

If you change the devcontainer in your Codespace, you can rebuild and see the changes (we'll do this in a minute). But if you commit and push to your repository, every Codespace created after that point by anyone can use this devcontainer specification.

You can also have multiple devcontainers and choose which to use for your Codespace. You may have seen that option when we created our Codespace right at the start.

## 4. Making a devcontainer change

Now that you're up and running with your Codespace, let's get ready to use GitHub Copilot!

Let's add the GitHub Copilot extension, but let's add it to the devcontainer rather than just install it.

1. Open the "Extensions" (![Extensions](images/extensions.png)) pane

2. Search for "Copilot" and select the GitHub Copilot extension
![GitHub Copilot extension](images/8-copilot-extension.png)

3. Don't click the green "Install in Codespaces" button! Instead, click the cog icon (⚙️) and select "Add to devcontainer.json".
![Add extension to devcontainer](images/9-copilot-extension-devcontainer.png)

4. Go back to the `devcontainer.json` file and see the change. Note that the extension hasn't been installed in your Codespace at this point.
![Extension added to the devcontainer](images/10-copilot-devcontainer-change.png)

_To see the change, we'll need to rebuild our Codespace._

6. Using your keyboard, press `Ctrl/Cmd-Shift-P`, then type "rebuild" to find the "Codespaces: Rebuild Container" option. Select it and press Enter, or click it with the mouse.
![Rebuilding your Codespace](images/11-rebuild-codespace.png)

7. Confirm your choice by clicking "Rebuild" and wait for your Codespace to reload.
![Confirm the rebuild](images/12-rebuild-codespace-confirm.png)

 _This may take a little longer than your first build! This is because we're taking advantage of a feature called Prebuilds. Your instructor will show you how to set these up and explain why they're useful._

8. Once reloaded, you'll be able to see GitHub Copilot installed - both in the Extensions pane, as well as via the GitHub Copilot logo at the bottom right of the status bar!

![Copilot Logo](images/13-copilot-icon.png)

## 5. Add to the Lost Pet form using GitHub Copilot

Let's add some more details to our lost pets form. We want to also track where the pet was last seen. Let's take a look at the Lost Pet page.

⚠️ _NOTE: GitHub Copilot is non-deterministic! It syntheses code just for you, so you will likely see different suggestions than the person next to you! We'll talk about how to get the best out of Copilot a little later._

1. In the Explorer pane, Go to the `LostPet.razor` file (you can get there quickly with `Ctrl/Cmd-P`, then typing the filename)

2. Ensure GitHub Copilot is turned on using the icon at the right of the status bar. You can click this icon to turn GitHub Copilot on or off.

![Copilot Logo](images/13-copilot-icon.png)

3. Go to line 50 and add a new line after the `</div>` but before `@if (isLoading)`

4. Type the following HTML comment explaining what we want to do next. It's a great prompt to help GitHub Copilot help us!

```<!-- Step 2.5 - pet's last location h2 element followed by a dropdown -->```

5. Press Enter to go to the next line.

6. GitHub Copilot should make a suggestion in grey with an `h2` heading. Hit `Tab` to accept the suggestion.
![GitHub Copilot Ghost text](images/14-copilot-h2-suggestion.png)

🤔 _We refer to this suggestion mechanism as "ghost text". You can hit Tab to accept a suggestion, or simply ignore it and keep typing._

7. On the next line, write the following comment and hit Enter.

```<!-- Dropdown menu with location -->```

8. GitHub Copilot should suggest an HTML dropdown with several locations
![Dropdown with cities](images/15-copilot-dropdown-suggestion.png)

_In this case, GitHub Copilot was helpful, but they're not the cities we need, so let's provide more context._

9. Go back and Update the comment to the below, replacing [your city] with the name of your city and hit Enter again.

 ```<!-- Dropdown menu with 5 locations in [your city] -->```

10.  GitHub Copilot should make some more accurate suggestions. Hit Tab to accept.
![Updated cities dropdown](images/16-copilot-better-dropdown.png)

11.  Make further changes to ensure the HTML is valid and all `div` elements are closed. You may need to make some small modifications and GitHub Copilot is likely to help here as well.

## 6. Add to the PetModel

You might notice that there's no `Location` field in `PetModel` (the red squiggles show there's an error), so let's fix that.
![Error in Location property](images/17-location-error.png)

1. Use `Ctrl/Cmd-P` to search for `PetModel.cs` and open that file.

2. Add a new line after line 13 (`public List<string> Images { get; set; }`)

3. Add `public string Location { get; set; }`. GitHub Copilot may start helping you at some point, but if not, don't worry, just keep typing!

4. Add a new line after line 25 (`Images = new();`). GitHub Copilot will almost certainly fill in what we need (`Location = "";`), so hit Tab to accept.
![PetModel updated suggestion](images/18-copilot-petmodel-suggestion.png)

## 7. Let's run to see our changes

Now we've made some changes with the help of GitHub Copilot, let's see the results!

1. Ensure you've saved the files you've edited. You can do this by pressing CTRL+S on the keyboard.

2. Navigate to the "Run and Debug" pane (![Run and debug](images/run-and-debug.png)) and use the "✅ Debug with Dapr" configuration again to debug.

3. Again, open the application by clicking on the "Open in Browser" icon (![Open in Browser](images/open-in-browser.png)) in the Ports pane.

3. Go to the "I lost my pet" page and you should see your changes.
![Last seen page update](images/19-last-seen-update.png)

## OPTIONAL (time dependent) Back end changes

If there's time during the workshop, or you're ahead of the class, try out this optional step.

So far we've only made front-end changes and the extra data won't persist in the backend. See if you can use GitHub Copilot to help you make backend changes as well!

_🔎 Hint: look for where to add details about the pet's last known location in `petspotr.py` and `app.py`_

## 8. Use GitHub Copilot to write tests

Finally, we're going to use GitHub Copilot to help us write some tests around our pages. This application already uses Playwright for testing, so let's build on that.

1. In the `tests/playwright/tests` folder, create a new file called `lostpage.spec.ts`
![New test file](images/20-new-test-file.png)

2. In that file, write a comment that says:

```// create playwright tests for LostPet.razor```

_ℹ️  Note that you should leave the LostPet.razor file open in VSCode so you're providing better context!_

_GitHub Copilot uses other open files to construct useful information to send back to the server. This "prompt crafting" can make a big difference in the results you'll get._

3. On the next line, write the following comment and hit Enter

```// import dependencies```

4. GitHub Copilot should suggest something like `import { test, expect } from @playwright/test`. If this doesn't work, try opening another test file for better context.

5. Write the comment below and hit Enter. 

```// test that h2 element with the words "Step 1: Tell us about your pet and how to contact you" renders```

_GitHub Copilot should do a good job of giving you the test function, although it may give it to you line by line. Hit Tab to accept until you're happy._

7. Write a comment that with the following and hit Enter

```// test that dropdown menu renders```

8. GitHub Copilot again should do a good job - it may even suggest looking for `Dog` in the dropdown!

9. Finally, try adding the comment below and hitting Enter.

```// test that you can upload images when you click Choose Files button```

😖 _Note that last one is more temperamental and might need extra prompting. You should end up with something similar to the following._
![New tests with Copilot](images/21-copilot-test-suggestions.png)

# 🥳 Congratulations!

 Great work! You've completed the workshop. You've learned how to use Codespaces and GitHub Copilot to improve your productivity as a developer.

In a very short time, you have:
1. Been able to edit and debug a brand new application with several moving parts and a collection of frameworks and technologies. All within a few minutes!
2. Seen how you can customize that cloud-based developer environment to minimize onboarding time, let you work from anywhere, and provide consistency for your team
3. Used GitHub Copilot to help create a new feature for your application.
4. Used GitHub Copilot to help you write tests - possibly using a framework you were previously unfamiliar with!

Of course it's impossible to learn everything about these features in a short workshop, but we hope you've learned enough to see the power of these technologies and how it can improve your productivity and day-to-day happiness.

# Taking this home with you

This repository is public, so once you've finished the workshop, you can always come back and do it again, or share it with your colleagues!

If you're not a current user of Codespaces or Copilot, you can use up to [60 hours of free Codespaces access a month](https://github.com/features/codespaces#pricing), and sign up for a [free GitHub Copilot trial](https://github.com/github-copilot/signup).
