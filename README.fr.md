# ap--`auto-pager`

ap est un utilitaire shell qui permet à la sortie d'autres commandes shell d'entrer automatiquement en mode de retournement de page interactif.

ap se compose de deux parties, un programme binaire écrit en Go qui capture la sortie des commandes et prend en charge le retournement de page, et un ensemble de scripts shell qui créent un wrapper du même nom pour une liste de commandes spécifiée par l'utilisateur.

L'utilisation des commandes après le wrap est la même qu'avant et ne devrait pas changer les habitudes de l'utilisateur ni causer de problèmes.

Lisez ceci dans d'autres langues :[Anglais](README.en.md),[Chinois simplifié](README.md),[chinois traditionnel](README.zh-TW.md),[arabe](README.ar.md),[Français](README.fr.md),[Non](README.hi.md)

ap est un outil shell qui permet à la sortie d'autres commandes shell d'entrer automatiquement en mode de tournage de page interactif.

ap se compose de deux parties, un programme binaire écrit en langage Go, chargé de capturer le résultat de la commande et de prendre en charge le tournage des pages,
et un ensemble de scripts shell chargés de créer des wrappers du même nom pour les listes de commandes spécifiées par l'utilisateur.

L'utilisation de la commande après le wrap est la même qu'avant, et les habitudes de fonctionnement de l'utilisateur ne doivent pas être modifiées, et cela ne causera pas de problèmes à l'utilisateur.

## Installer

    go install github.com/flw-cn/ap@master

## configuration

-   `bash`(#frapper)
-   `fish`(#`fish`)
-   `zsh`(#`zsh`)

### frapper

À votre`~/.bashrc`Ajoutez-y ce qui suit :

```sh
eval "$(ap --bash)"
```

ap encapsule un lot de commandes par défaut. Si vous n'êtes pas satisfait, vous pouvez re-personnaliser via des variables d'environnement :

```sh
AUTO_PAGER_CMDS=(go cargo make)
eval "$(ap --bash)"
```

Ou ajoutez simplement de nouvelles commandes en haut de la liste par défaut :

```sh
AUTO_PAGER_CMDS_EXTRA=(ps last)
eval "$(ap --bash)"
```

De plus, ap peut également être utilisé avec[grc](https://github.com/garabik/grc)En travaillant ensemble, grc peut être installé à l'aide de Homebrew sous macOS :

```sh
brew install grc
```

ap + grc encapsule un lot de commandes par défaut. Si vous n'êtes pas satisfait, vous pouvez re-personnaliser via des variables d'environnement :

```sh
AUTO_PAGER_CMDS_WITH_GRC=(ps last dig diff)
eval "$(ap --bash)"
```

Ou ajoutez simplement de nouvelles commandes en haut de la liste par défaut :

```sh
AUTO_PAGER_CMDS_WITH_GRC_EXTRA=(ps last)
eval "$(ap --bash)"
```

De plus, la variable d'environnement`$AUTO_PAGER_MIN_HEIGHT`Vous pouvez contrôler le nombre minimum de lignes avec lesquelles démarrer la pagination :

```sh
AUTO_PAGER_MIN_HEIGHT=30        # 输出超过 30 行时才开始分页
eval "$(ap --bash)"
```

S'il est configuré comme un nombre négatif, il représente un pourcentage de la hauteur de la fenêtre du terminal :

```sh
AUTO_PAGER_MIN_HEIGHT='-50'     # 输出超过终端窗口高度的 50% 时才开始分页
eval "$(ap --bash)"
```

si non précisé`AUTO_PAGER_MIN_HEIGHT`,La valeur par défaut est`-80`,Tout de suite`80%`。

### `fish`

À votre`~/.config/fish/config.fish`Ajoutez-y ce qui suit :

```sh
ap --fish | source
```

ap encapsule un lot de commandes par défaut. Si vous n'êtes pas satisfait, vous pouvez re-personnaliser via des variables d'environnement :

```sh
set AUTO_PAGER_CMDS go cargo make
ap --fish | source
```

Ou ajoutez simplement de nouvelles commandes en haut de la liste par défaut :

```sh
set AUTO_PAGER_CMDS_EXTRA ps last
ap --fish | source
```

De plus, ap peut également être utilisé avec[grc](https://github.com/garabik/grc)En travaillant ensemble, grc peut être installé à l'aide de Homebrew sous macOS :

```sh
brew install grc
```

ap + grc encapsule un lot de commandes par défaut. Si vous n'êtes pas satisfait, vous pouvez re-personnaliser via des variables d'environnement :

```sh
set AUTO_PAGER_CMDS_WITH_GRC ps last dig diff
ap --fish | source
```

Ou ajoutez simplement de nouvelles commandes en haut de la liste par défaut :

```sh
set AUTO_PAGER_CMDS_WITH_GRC_EXTRA ps last
ap --fish | source
```

De plus, la variable d'environnement`$AUTO_PAGER_MIN_HEIGHT`Vous pouvez contrôler le nombre minimum de lignes avec lesquelles démarrer la pagination :

```sh
set AUTO_PAGER_MIN_HEIGHT 30        # 输出超过 30 行时才开始分页
ap --fish | source
```

S'il est configuré comme un nombre négatif, il représente un pourcentage de la hauteur de la fenêtre du terminal :

```sh
set AUTO_PAGER_MIN_HEIGHT -50     # 输出超过终端窗口高度的 50% 时才开始分页
ap --fish | source
```

si non précisé`AUTO_PAGER_MIN_HEIGHT`,La valeur par défaut est`-80`,Tout de suite`80%`。

### `zsh`

À votre`~/.zshrc`Ajoutez-y ce qui suit :

```sh
eval "$(ap --zsh)"
```

ap encapsule un lot de commandes par défaut. Si vous n'êtes pas satisfait, vous pouvez re-personnaliser via des variables d'environnement :

```sh
AUTO_PAGER_CMDS=(go cargo make)
eval "$(ap --zsh)"
```

Ou ajoutez simplement de nouvelles commandes en haut de la liste par défaut :

```sh
AUTO_PAGER_CMDS_EXTRA=(ps last)
eval "$(ap --zsh)"
```

De plus, ap peut également être utilisé avec[grc](https://github.com/garabik/grc)En travaillant ensemble, grc peut être installé à l'aide de Homebrew sous macOS :

```sh
brew install grc
```

ap + grc encapsule un lot de commandes par défaut. Si vous n'êtes pas satisfait, vous pouvez re-personnaliser via des variables d'environnement :

```sh
AUTO_PAGER_CMDS_WITH_GRC=(ps last dig diff)
eval "$(ap --zsh)"
```

Ou ajoutez simplement de nouvelles commandes en haut de la liste par défaut :

```sh
AUTO_PAGER_CMDS_WITH_GRC_EXTRA=(ps last)
eval "$(ap --zsh)"
```

De plus, la variable d'environnement`$AUTO_PAGER_MIN_HEIGHT`Vous pouvez contrôler le nombre minimum de lignes avec lesquelles démarrer la pagination :

```sh
AUTO_PAGER_MIN_HEIGHT=30        # 输出超过 30 行时才开始分页
eval "$(ap --zsh)"
```

S'il est configuré comme un nombre négatif, il représente un pourcentage de la hauteur de la fenêtre du terminal :

```sh
AUTO_PAGER_MIN_HEIGHT='-50'     # 输出超过终端窗口高度的 50% 时才开始分页
eval "$(ap --zsh)"
```

si non précisé`AUTO_PAGER_MIN_HEIGHT`,La valeur par défaut est`-80`,Tout de suite`80%`。

## utiliser

Les commandes qui ont été enveloppées doivent simplement être utilisées comme d'habitude.
S'il y a trop de sortie, la variable d'environnement sera appelée automatiquement`$PAGER`Le téléavertisseur spécifié effectue la pagination.

si ton`$PAGER`Les variables sont spéciales et ne peuvent pas être adaptées à ap, vous pouvez également utiliser des variables d'environnement`$AP_PAGER`Réglez le téléavertisseur individuellement pour ap.

si`$AP_PAGER`et`$PAGER`Ni l'un ni l'autre n'est spécifié, alors le`less -Fr`。

Les conditions suivantes ne démarreront pas le téléavertisseur :

-   Lorsque le contenu de sortie est trop petit, voir`$AUTO_PAGER_MIN_HEIGHT`。
-   Lorsqu'ap détecte que la sortie de la commande contient`ESC [?1049h` 序列时，此时命令被判定为全荧幕应用。
-   Lorsque la commande n’a pas terminé son exécution. Le téléavertisseur ne démarrera pas tant que l'exécution de la commande n'est pas terminée.
    -   `ping`et`tcpdump`Ces commandes doivent d'abord être appuyées`Ctrl-C`La pagination ne démarre pas tant que la commande n'est pas terminée.
    -   `python`et`gdb`De telles commandes doivent attendre la fin de la commande avant de lancer la pagination.

## Problème commun

-   Cela affectera-t-il la sortie colorée de la commande ?
    -   Ne le fera pas.
-   Une commande qui détecte un terminal et fournit une sortie différente pour les modes terminal et non terminal modifie-t-elle sa sortie ?
    -   Ne le fera pas.
-   Comment puis-je diagnostiquer si je soupçonne qu'ap affecte la sortie d'une commande ?
    -   tu peux l'utiliser`command foo`éxécuter`foo`, pour que ap ne soit pas appelé.
-   Si j'ajoute habituellement après la commande ap`| less`, est-ce que quelque chose va mal ?
    -   Ne le fera pas.
-   Une commande ap peut-elle également rediriger sa sortie ?
    -   Peut.
-   La saisie semi-automatique des commandes ap'd sera-t-elle interrompue ?
    -   Ne le fera pas.
-   support ap comme`python`、`gdb`Une telle application interactive ?
    -   soutien. Cependant, étant donné que ces applications génèrent certains caractères de contrôle, le contenu que vous voyez après la pagination peut être un peu désordonné.
-   support ap comme`htop`、`vim`Une telle application en plein écran ?
    -   Comment le dire, ça ne peut pas se tromper de toute façon, mais je n'arrive pas à comprendre quel est l'intérêt pratique de coupler ap avec eux.
