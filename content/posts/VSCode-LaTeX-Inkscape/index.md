---
title: "$ code --add LaTeX Inkscape"
tags: ["macOS", "LaTeX", "notes"]
date: 2022-03-01
path: "posts/VSCode-LaTeX-Inkscape"
excerpt: 🖋 My perfect LaTeX workflow.
cover: "./preview.png"
---

## VSCode-LaTeX-Inkscape

I use $\LaTeX$ heavily for both academic work and professional work, and I think I'm quite proficient in terms of typing things out in $\LaTeX$. But when I see the mind-blowing blog posts from **Gilles Castel (RIP)**-[How I'm able to take notes in mathematics lectures using $\LaTeX$ and Vim](https://castel.dev/post/lecture-notes-1/) and also [How I draw figures for my mathematical lecture notes using Inkscape](https://castel.dev/post/lecture-notes-2/), I realize that I'm still far from *fast*, so I decided to adapt the whole setup from Linux-Vim to macOS-VS Code.[^1]

[^1]: This setup is universal for VS Code users indeed. The only part that'll be macOS-specific is the Inkscape part ([Inkscape-figure-manager](#inkscape-figure-manager) and [Inkscape-shortcut-manager](#inkscape-shortcut-manager)). While the first part can be replaced by [super-figure](https://github.com/Joao-Peterson/super-figure) (while I still prefer my setup, you can still try it out even if you're in macOS), and you can certainly achieve a similar result in Windows as in my [Notes](../Notes), the drawing speed will be slower without the shortcut manager. Just keep that in mind.

If you still don't know what to expect, please check out my [Notes](../Notes) taken in this setup. Also, due to the VS Code recent update (1.76.1), we have the [profile](https://code.visualstudio.com/docs/editor/profiles) functionality available. Specifically, this is [my current minimal profile](https://vscode.dev/profile/github/70b175ba903a4f1cc5dcd271ce8fcb51) for $\LaTeX$ I'm currently using, but since some configurations are not included in the [profile](https://code.visualstudio.com/docs/editor/profiles), you should still read through everything.

<div align="center">
	<img src="./figures/note.png"/>
</div>

## Disclaimer

Please look through the two blog posts above by Gilles Castel! They are incredible and worth spending your time to understand how all things work, and what's the motivation behind all these. I'm only mimicking his workflow, with a little patience to set up the whole thing in my environment. Show respect to the original author!

Before we start anything serious, just copy the [`keybindings.json`](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/VSCode-setting/keybindings.json) and [`settings.json`](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/VSCode-setting/settings.json) into your own `keybindings.json` and `settings.json`. Don't worry, I'll explain what they do later.

Also, create a snippet file for $\LaTeX$ in the following steps:

1. Press `shift`+`cmd`+`p` to open the VS Code command.
2. Type `snippets`, and choose `Preferences: Configure User Snippets`.
3. Choose `New Global Snippets file...`.
4. Enter `latex` to create a new file.
5. Paste the [`latex.json`](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/VSCode-setting/Snippets/latex.json)  into that file.

## Setup For Typing Blasting Fast

First thing first, please set up your [VS Code](https://code.visualstudio.com/) with $\LaTeX$ properly with [$\LaTeX$ Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop), there are lots of tutorials online, just check them out and set them up properly. Basically, it can be done in the following steps:

1. Download [MacTex](https://www.tug.org/mactex/). This can be replaced by something more lightweight, but in my opinion, this doesn't really help much in terms of speed or wasting your disk. But if you want something like this, check out [TeXLive](https://www.tug.org/texlive/).
2. Download [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)
3. Copy-pasting the following configuration file into your `settings.json`

	```JSON
	"latex-workshop.latex.autoBuild.run": "onSave"
	```

	> This will save your time by compiling your $\LaTeX$ project whenever you save your file by `cmd`+`s`.

Now, we go through things one by one following Gilles Castel's blog post.

### Tex Conceal

To achieve a similar result as in Gilles Castel's setup, there is an extension called [vsc-conceal](https://github.com/Pancaek/vsc-conceal) for VS Code. All the setup is in the `setting.json`, and since this setup is quite straightforward, I'll just give a snapshot to show how it looks in practice.

<div align="center">
	<img src="./figures/conceal.png"/>
</div>

Note that I set the `"conceal.revealOn"` to `"active-line"`, which is why you will see the source code in line 51. There are other options you can choose, see the original repo for details.

### HyperSnips

If you look around in the VS Code extension marketplace to find UltiSnips' equivalence, you probably will find [Vsnips](https://marketplace.visualstudio.com/items?itemName=corvofeng.Vsnips). But I'm not sure why this is the case, I can't figure out how to set it up properly. Hence, I find another alternative, which is [HyperSnips](https://marketplace.visualstudio.com/items?itemName=draivin.hsnips). Please first download [HyperSnips](https://marketplace.visualstudio.com/items?itemName=draivin.hsnips) and just follow the instructions, copy [`latex.hsnips`](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/VSCode-setting/Snippets/latex.hsnips) into `$HOME/Library/Application Support/Code/User/hsnips/`, and you're good to go!

To modify this file, you can either go to this file in your finder or use the VS Code built-in command function. For commands function,

1. Press `shift+cmd+space` to type in some commands to VS Code.
2. Type `>HyperSnips: Open Snippet File`
3. Choose `latex.hsnips`

After doing this, you're all set. But a big question is, what exactly is a snippet?

#### Snippets

A snippet is a short reusable piece of text that can be triggered by some other text. For example, when I type `dm` (stands for display math), the word `dm` will be expanded to a display math environment:

<div align="center">
	<img src="./gifs/dm.gif"/>
</div>

If you are a math guy, you may need to type some inline math like `\(\)`, which is kind of painful. But with snippets, you can have

<div align="center">
	<img src="./gifs/fm.gif"/>
</div>

See? You just type `fm` (not the best choice here, but since `im` is a common prefix, so can't really use that as our snippet 🥲), and then your snippet not only automatically types `\(\)` for you, and it also sends your cursor between `\(\)`! With this, you can type something **really** fast:

<div align="center">
	<img src="./gifs/fast.gif"/>
</div>

Note that in the above demo, I use a very common snippet, `qs` for `^{2}`.

As you can imagine, this can be quite complex. For example, you can even have something like this:

<div align="center">
	<img src="./gifs/table.gif"/>
</div>

or this:

<div align="center">
	<img src="./gifs/pmatrix.gif"/>
</div>

For the first snippet, I type `table2 5`, and then it generates a table with 2 rows and 5 columns. For the second one, I type `pmat` for matrix, and then type `2 5` to indicate that I want a 2 by 5 matrix, then boom! My snippets do that for me in an instant!

My snippet file includes commonly used snippets as suggested in the original posts, you can look into it to better understand how it works. And maybe you can create your snippets also! Here are some useful snippets for you.

<div align="center">
	<img src="./gifs/useful.gif"/>
</div>

#### Math Environment

In the recent update of [HyperSnips](https://marketplace.visualstudio.com/items?itemName=draivin.hsnips), the *context* functionality is implemented, which is very useful, and you should understand how it works. If you look at the top of the snippet file, you will see

```javascript
global
function math(context) {
    return  context.scopes.findLastIndex(s => s.startsWith("meta.math")) > context.scopes.findLastIndex(s => s.startsWith("comment") || s.startsWith("meta.text.normal.tex"));
}
endglobal
```

And for some snippets, you will see `context math(context)` in front of which, e.g., the *greater or equal* snippet:

```javascript
context math(context)
snippet `>=|(?<!\\)geq` "greater or equal to" A
\geq $0
endsnippet
```

while some do not, e.g., the *display math* snippet:

```javascript
snippet dm "display Math" bA
\[
	${1}
\]$0
endsnippet
```

Basically, the `context` specifies when the snippet will be triggered, and I define the function `math(context)` to determine when we are in the *math* environment. This is quite important since the official `math(context)` function for detecting math scope for $\LaTeX$ is given by

```javascript
global
function math(context) {
    return context.scopes.some(s => s.startsWith("meta.math")) && !context.scopes.some(s => s.startsWith("comment") || s.startsWith("meta.text.normal.tex"));
}
endglobal
```

However, this leads to some problems. For example, sometimes, in the equation, I want to write

```latex
\[
    x_n = x \text{ for some \(n\) large enough},
\]
```

Such a case is fine since the math I want to write in the text scope is simple, just `\(n\)`. However, in the current (and perhaps most popular) scope function, it happens that `\(\text{ \( not in the math mode \) }\)`.

To overcome this, I write the following more generic version:

```javascript
global
function math(context) {
    return  context.scopes.findLastIndex(s => s.startsWith("meta.math")) > context.scopes.findLastIndex(s => s.startsWith("comment") || s.startsWith("meta.text.normal.tex"));
}
endglobal
```

So, since the nested environment is ordered in the scope, this will always return the correct mode. Even better, there will be no undefined behavior since if the `.findLastIndex` can't find either, it will return `-1` instead of something undefined, so everything is handled.

### Sympy and Mathematica

Unlike Gilles Castel's approach, there is an available extension out there for you to simplify your math calculation already! Please go check out [Latex SYMPY Calculator](https://marketplace.visualstudio.com/items?itemName=OrangeX4.latex-sympy-calculator). It works like follows:

<div align="center">
	<img src="./gifs/integral.gif"/>
</div>

Magic right? Let's set it up! First, please look at the installation document provided by [Latex Sympy Calculator](https://marketplace.visualstudio.com/items?itemName=OrangeX4.latex-sympy-calculator). After your installation, you can set up the keybinding for calculating the math expression. I use `shift`+`e`, where `e` stands for evaluating, to calculate so that it will append an equal sign and the answer right after your formula, just like above. And if you want to avoid showing the intermediate steps of your calculation, you can use `shift`+`r`, where `r` stands for replacing, to directly replace the whole formula and give me the answer only. See the demo below:

<div align="center">
	<img src="./gifs/integral2.gif"/>
</div>

> This plugin is indeed more powerful than just this, see the documentation for detail.

Let's go to the last thing covered in Gilles Castel's post, correcting spelling mistakes.

### Correcting Spelling Mistakes on the Fly

Although my typing speed is quite high, I have typos all the time. So this is a must for me. And surprisingly, this is the hardest thing until now for me to set it upright. Let's see how we can configure this functionality in VS Code! There are three plugins we need:

1. [multi-command](https://marketplace.visualstudio.com/items?itemName=ryuta46.multi-command): This is a very powerful extension, which allows you to do a sequence of actions in one shortcut. We will use this later on also, and that's the place it shines.

2. [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker): This is a popular spelling checker out there which meets our needs.

3. [LTeX](https://marketplace.visualstudio.com/items?itemName=valentjn.VSCode-ltex): If you are bad at grammar like me, you definitely want to install to check some simple grammar mistakes for you. Although it's not powerful like [Grammarly](https://www.grammarly.com/), not even comparable, it's still a good reference for you to keep your eyes on some simple mistakes you may overlook.
	 > There is an unofficial API for Grammarly, and the plugin can be found [here](https://marketplace.visualstudio.com/items?itemName=znck.grammarly). Though it's quite slow...

Here is a quick demo of how it works when typing:

<div align="center">
	<img src="./gifs/spell.gif"/>
</div>

Additionally, if you also want to correct your grammar error, I use the shortcut `cmd`+`k` to trigger a quick-fix for a general error.

<details>

<summary><b>Detail Explanation</b></summary>

> You can skip this part if you don't want to know the working mechanism. But if you're interested, please follow! The following code snippet in `settings.json` is responsible for correcting your spelling mistakes by just clicking `cmd`+`l`.
>
> ```json
> {
>     "key": "cmd+l",
>     "command": "extension.multiCommand.execute",
>     "args": {
>         "sequence": [
> 	    "cSpell.goToPreviousSpellingIssue",
> 	    {
> 	        "command": "editor.action.codeAction",
> 	        "args": {
> 	            "kind": "quickfix",
> 		    "apply": "first"
>                 }
> 	    },
> 	    "cursorUndo",
>         ]
>     }
> },
> ```
>
> > Make sure that the curly braces above have a trailing comma, otherwise, VS Code will complain about it.
>
> The working mechanism is as follows. When you press `cmd`+`l`, the [multi-command](https://marketplace.visualstudio.com/items?itemName=ryuta46.multi-command) will do the following:
>
> 1. Use one of the default function from cSpell's: `goToPreviousSpellingIssue`, which jump your cursor on that spelling error word
> 2. Triggered a default editor action, with the argument being `quickfix` to open a quick fix drop-down list, and choose the `first` suggestion
> 3. Move your cursor back by `cursorUndo`
>
> And likewise, the following code snippet is responsible for correcting grammar mistakes.
>
> ```json
> {
>     "key": "cmd+k",
>     "command": "extension.multiCommand.execute",
>     "args": {
>         "sequence": [
>             "editor.action.marker.prev",
>             {
>                 "command": "editor.action.codeAction",
>                 "args": {
>                     "kind": "quickfix",
>                     "apply": "first"
>                 }
>             },
>             "cursorUndo",
>         ]
>     }
>  },
> ```

</details>

Now, the first part is over. Let's go to the next truly beautiful, elegant, and exciting world, drawing with [Inkscape](https://inkscape.org/zh-hant/).

## Drawing Like a Pro - With Inkscape

<div align="center">
	<img src="./figures/inkscape_example.png"/>
</div>

For more examples, check out the original blog. Or for more figures I draw, you can check out [Note](../Notes).

One last thing is that I'll assume you have already installed [VS Code Vim](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim). While this is not required, if you don't want to use it, then you'll need to assign different keybinding. Anyway, you'll see what I mean until then!

### Inkscape

A big question is, why Inkscape? In the original blog, he had already explained it. One reason is that although $\texttt{TikZ}$ can do the job of drawing vector figures in $\LaTeX$ with original support, it's too slow to set all diagrams right. This is so true since my experience with $\texttt{TikZ}$ is *nice looking* and *intuitive* but also *slow* and *bulky*. Also, the $\texttt{TikZ}$ code tends to be **long**. A large file will take [*latexindent*](https://ctan.org/pkg/latexindent) and *pdfLaTeX* **a minute** to compile for one save. That's not efficient at all, especially when you want some instant feedback for some small changes.

#### Download Inkscape

You need to install [Inkscape](https://inkscape.org/zh-hant/) first. I recommend you install this in a terminal. I assume that you have your [`homebrew`](https://brew.sh/) installed. Then, just type the following into your terminal:

```sh
> brew install --cask inkscape
```

#### Set up the Environment in LaTeX

First thing first, include the following in your preamble

```latex
\usepackage{import}
\usepackage{xifthen}
\usepackage{pdfpages}
\usepackage{transparent}

\newcommand{\incfig}[1]{%
    \def\svgwidth{\columnwidth}
    \import{./Figures/}{#1.pdf_tex}
}
```

And to use it in your code, it's like the following:

```latex
\begin{figure}[H]
    \centering
    \incfig{figure's name}
    \caption{Your caption}
    \label{fig:label}
\end{figure}
```

And then you're done! Also, the compilation time for this is shorter than you can ever expect. Let's get started then!

This assumes that your $\LaTeX$ project's home directory looks like this:

```sh
LaTeX_project
    ├── main.tex
    ├── main.pdf
    ├── Figures
    │    ├── fig.pdf
    │    ├── fig.pdf_tex
    │    ├── fig.svg
    │    .
    .
```

Now, let's get into the fun part, i.e., setting up the shortcut for this.

### Inkscape Figure Manager

This is a figure manager developed by Gilles Castel, and here is the [repo](https://github.com/gillescastel/inkscape-figures). I recommend you follow the installation instructions there. Here is just some guideline for you.

1. Install [choose](https://github.com/chipsenkbeil/choose) (specifically for macOS, [rofi](https://github.com/davatorium/rofi) for Linux instead):

   ```sh
   > brew install choose-gui
   ```

2. Install [fswatch](https://github.com/emcrisostomo/fswatch):

   ```sh
   > brew install fswatch
   ```

3. Install the Inkscape figure manager:

   ```sh
   > pip3 install inkscape-figures
   ```

   > After installing it, type `inkscape-figures` in your terminal to make sure you have corrected install it.

If you're using Linux and Vim, then you are done already. But since you're using macOS and VS Code, please follow me, there is some more thing for you to configure.

> If you're using Windows, then check out [super-figure](https://github.com/Joao-Peterson/super-figure). It implements similar functionalities but in a more chunky way. Even if you're using macOS, you can try it too, although I prefer my setup.

#### Set up Inkscape Figure Manager

Firstly, install the [Command Runner](https://marketplace.visualstudio.com/items?itemName=edonet.vscode-command-runner). This will allow you to send commands into a terminal with the shortcut. The configuration is in [`settings.json`](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/VSCode-setting/settings.json), and we'll see how it works later. Now, this is a tricky part: you need to find the source code of the inkscape-figures manager. In my case, it's in `/Users/pbb/opt/anaconda3/lib/python3.8/site-packages/inkscapefigures`.

> Using global finding may be helpful...

Open this directory by VS Code, there is something for you to modify. Ok, I know you probably don't have that much patience now, so I have a modified version available [here](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/Inkscape-setting/Inkscape-figure-manager/). Just replace the whole directory with mine, and you're good to go.

> Notice that the directory in this repo is named `Inkscape-figure-manager`, while in your system, it should be `inkscapefigures`.

<details>

<summary><b>Detail Explanation</b></summary>

> In Gilles Castel's approach, he uses the shortcut `ctrl`+`f` to trigger this script, which will copy the whole line's content depending on the cursor's position, and the script will send the snippets by the function
>
> ```python
> def latex_template(name, title):
>     return '\n'.join((r"\begin{figure}[ht]",
>                       r"    This is a custom LaTeX template!",
>                       r"    \centering",
>                       rf"    \incfig[1]{{{name}}}",
>                       rf"    \caption{{{title}}}",
>                       rf"    \label{{fig:{name}}}",
>                       r"\end{figure}"))
> ```
>
> to `stdout`, and then create a figure by the `name`, which is the content of the line.
>
> But this in VS Code is impossible, hence we don't need this, we'll use command line. And if we leave this function as it was, then it will send all these snippets into our terminal, which is quite annoying. So the modified version just removes this snippet completely.
>
> But let me explain it to you, in case you want to modify it to meet your need later on. First thing first, we see that in the given code in [`keybindings.json`](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/VSCode-setting/keybindings.json) and [`settings.json`](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/VSCode-setting/settings.json), we're using [Command Runner](https://marketplace.visualstudio.com/items?itemName=edonet.vscode-command-runner), so let me tell you how to set this up first.

</details>

We're now prepared to see a detailed explanation of commands provided in [Inkscape figure manager](https://github.com/gillescastel/inkscape-figures). There are three different commands in the [Inkscape figure manager](https://github.com/gillescastel/inkscape-figures). We break it down one by one.

#### Watch

Since Inkscape by default does not save the file in `pdf+latex`, we need [Inkscape figure manager](https://github.com/gillescastel/inkscape-figures) to help us. We need to first open the file watcher to *watch* the file for any changes. If there is any, then the file watcher will tell Inkscape to save the file in `pdf+latex` format.

To open the file watcher, you can type `inkscape-figures watch` in the terminal. But remember the [Command Runner](https://marketplace.visualstudio.com/items?itemName=edonet.vscode-command-runner) we just installed? We can assign this command with a keybinding! In my case, since I don't want to introduce more than one keybinding for Inkscape-figures manager, I use `mode` provided by `vim` to help us. In `VISUAL` mode (enter by `v` in `NORMAL` mode), press `ctrl`+`f`.

> You should trigger this at the beginning. i.e., use this after you open your project folder. To check whether `watch` is triggered correctly, you can simply open the terminal and see what's the output when you press `ctrl`+`f`: If it's already triggered, then it'll show
>
> ```sh
> > inkscape-figures watch 
> Unable to lock on the pidfile.
> ```
>
> Otherwise, it'll simply show nothing. (Remember to select the terminal corresponds to `runCommand`!)

<details>

<summary><b>Detail Explanation</b></summary>

> In [`keybindings.json`](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/VSCode-setting/keybindings.json), we have
>
> ```json
> {
>     "key": "ctrl+f",
>     "command": "command-runner.run",
>     "args": {
>         "command": "inkscapeStart",
>         "terminal": {
>             "name": "runCommand",
>             "shellArgs": [],
>             "autoClear": true,
>             "autoFocus": false
>         }
>     },
>     "when": "editorTextFocus && vim.active && vim.use<C-f> && !inDebugRepl && vim.mode == 'Visual'"
> }
> ```
>
> for starting the [Inkscape figure manager](https://github.com/gillescastel/inkscape-figures). And the command is defined in [`settings.json`](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/VSCode-setting/settings.json):
>
> ```json
> "command-runner.commands": {
>     "inkscapeStart": "inkscape-figures watch"
> }
> ```
>
> In detail, we just use [Command Runner](https://marketplace.visualstudio.com/items?itemName=edonet.vscode-command-runner) to run the command we defined in [`settings.json`](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/VSCode-setting/settings.json), in this case, I explicitly tell the keybinding `ctrl`+`f` will trigger `inkscapeStart` when I'm in `VISUAL` mode in Vim, which is just `inkscape-figures watcher` as defined above.
>
> Notice that we set the `autoFocus=false` for the terminal [Command Runner](https://marketplace.visualstudio.com/items?itemName=edonet.vscode-command-runner) uses since we don't want a pop-up terminal to distract us. If you want to see whether the command is triggered correctly every time, you can set it to `true`.

</details>

#### Create

Same as above, we also use `ctrl`+`f` to trigger `inkscape-figures create` command. But in this case, we use `INSERT` for creating a new Inkscape figure. Specifically, we first type out the image's name we want our image to be called, then, in this case, we're already in `INSERT` mode, we just press `ctrl`+`f` to create this image after naming.

<details>

<summary><b>Detail Explanation</b></summary>

> We set up our ['keybindings.json'](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/VSCode-setting/keybindings.json) as
>
> ```json
> {
>     "key": "ctrl+f",
>     "command": "extension.multiCommand.execute",
>     "args": {
>         "sequence": [
> 	    "editor.action.clipboardCopyAction",
> 	    "editor.action.insertLineAfter",
> 	    "cursorUp",
> 	    "editor.action.deleteLines",
> 	    {
> 	        "command": "editor.action.insertSnippet",
> 		"args": {
> 		    "name": "incfig"
> 		}
>             },
>             {
> 	        "command": "command-runner.run",
> 		"args": {
> 		    "command": "inkscapeCreate",
> 		},
> 		"terminal": {
> 		    "name": "runCommand",
> 		    "shellArgs": [],
> 		    "autoClear": true,
> 		    "autoFocus": false
> 		}
>             },
> 	]
>     },
>     "when": "editorTextFocus && vim.active && vim.use<C-f> && !inDebugRepl && vim.mode == 'Insert'"
> },
> ```
>
> and also in [`settings.json`](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/VSCode-setting/settings.json):
>
> ```json
> "command-runner.commands": {
>     "inkscapeCreate": "inkscape-figures create ${selectedText} ${fileDirname}/Figures/"
> }
> ```
>
> We break down what `ctrl`+`f` do in `INSERT` mode exactly step by step. We see that when we press `ctrl`+`f` in `INSERT` mode, we trigger `multiCommand.execute` to execute a sequence of instructions, which are
>
> 1. Copy the content into your clipboard of the line your cursor at
> 2. Insert a blank line after since we need to insert a snippet, and that's will delete an additional line. You can try to delete this and the next instruction, and see what happens.
> 3. Move back our cursor after inserting that new line.
> 4. Delete that copied content by removing this line.
> 5. Insert a snippet defined in [`latex.json`](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/VSCode-setting/Snippets/latex.json). **Notice that this is the default snippet functionality built-in VS Code, not [HyperSnips](https://marketplace.visualstudio.com/items?itemName=draivin.hsnips) we have used before**. I'll explain where to copy this file in a minute.
> 6. Lastly, we send a command in a terminal by [Command Runner](https://marketplace.visualstudio.com/items?itemName=edonet.vscode-command-runner), with the command `inkscapeCreate` we defined in [`settings.json`](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/VSCode-setting/settings.json).
>
> In the fifth instruction, the snippet we used is
>
> ```json
>  { 
>  	"incfig": { 
>  		"prefix": "incfig", 
>  		"body": [ 
>  			"\\begin{figure}[H]", 
>  			"\t\\centering", 
>  			"\t\\incfig{${1:$CLIPBOARD}}", 
>  			"\t\\caption{${2:title}}", 
>  			"\t\\label{fig:${1:$CLIPBOARD}}", 
>  			"\\end{figure}", 
>  		], 
>  		"description": "Inserts mathematical diagram" 
>  	} 
>  } 
> ```
>
> which is just the snippet we remove from [Inkscape figure manager](https://github.com/gillescastel/inkscape-figures)'s source code! It's back again, in a different approach.
>

</details>

<div align="center">
	<img src="./gifs/demo-create-inkscape.gif"/>
</div>

Let me break it down for you. Firstly, I changed into `INSERT` mode in VS Code Vim and typed my new figure's name `figure-test`. Then, I press `ctrl`+`f` to trigger the keybinding, which will automatically create an Inkscape figure named `figure-test` for me and open it.

> The three files will be created along the way: `figure-test.pdf`, `figure-test.pdf_tex` and `figure-test.svg`. Unfortunately, to rename a file, you'll need to manually rename three of them.

#### Edit

Again, we also use `ctrl`+`f` to trigger `inkscape-figures edit` command, but this time in `NOMAL` mode. Here, [choose](https://github.com/chipsenkbeil/choose) comes into play. After you select the image you want to edit in Inkscape, you simply press `enter` and it'll open that image for you to edit.

> You can modify the styling of [choose](https://github.com/chipsenkbeil/choose). For example, in [`picker.py`](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/Inkscape-setting/Inkscape-figure-manager/picker.py), we have the following:
>
> ```python
> def get_picker_cmd(picker_args=None, fuzzy=True):
>     """
>     Create the shell command that will be run to start the picker.
>     """
>     if SYSTEM_NAME == "Darwin":
>         args = ["choose"]
>     #   args = ["choose", "-u", "-n", "15", "-c", "BB33B7", "-b", "BF44C8"]
> ```
>
> We see that we don't have any additional argument for `choose`, but if you want, you can replace this line by the next line, which modify the style of `choose`. For detail information, type `choose -h` to see all the options.

<details>

<summary><b>Detail Explanation</b></summary>

> The corresponding keybinding in ['keybindings.json'](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/VSCode-setting/keybindings.json) is:
>
> ```json
> {
>     "key": "ctrl+f",
>     "command": "command-runner.run",
>     "args": {
>         "command": "inkscapeEdit",
>         "terminal": {
>             "name": "runCommand",
>             "shellArgs": [],
>             "autoClear": true,
>             "autoFocus": false
>         }
>     },
>     "when": "editorTextFocus && vim.active && vim.use<C-f> && !inDebugRepl && vim.mode == 'Normal'"
> },
> ```
>
> and also in [`settings.json`](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/VSCode-setting/settings.json):
>
> ```json
> "command-runner.commands": {
>     "inkscapeEdit": "inkscape-figures edit ${fileDirname}/Figures/"
> }
> ```
>
> I think now it's clear enough how all these work together to trigger the corresponding command. When you press `ctrl`+`f` in `NORMAL` mode, you'll trigger the `inkscape-figures edit` command, and it'll look into your `Figures/` subfolder to see what figures you have and pop out a window for you to choose, which is the functionality provided by [choose](https://github.com/chipsenkbeil/choose).

</details>

In the following demo, I create another figure named `figure-test2`, then modify it a little, and compile it again.

<div align="center">
	<img src="./gifs/demo-edit-inkscape.gif"/>
</div>

### Inkscape Shortcut Manager

In this section, we'll set up a very efficient shortcut manager to help you draw any mathematical figures faster than you can ever imagine! Notice that this setup is quite complicated, but the result is quite good. It depends on

* [Hammerspoon](https://www.hammerspoon.org/): For windows focus.
* [Karabiner Elements](https://karabiner-elements.pqrs.org/): For capturing the overlapping key chords.

Please download the above two apps.

> This section is contributed **purely** by [@kiryph](https://github.com/kiryph) in [#1](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/issues/1).

#### Karabiner Elements

We'll need [Karabiner Elements](https://karabiner-elements.pqrs.org)' [Complex Modifications](https://karabiner-elements.pqrs.org/docs/json/root-data-structure/#custom-json-file-in-configkarabinerassetscomplex_modifications) to help us. The steps are the following (adapted from [️⌨ How to type?](../How2TypeFast#import-settings)).

1. Open [Karabiner-Elements](https://karabiner-elements.pqrs.org/), go to *Misc* and click on *Export & Import*.
    <div align="center">
		<img width="80%" src="figures/sourcecode-1.png"/>
	</div>
2. Copy [`Inkscape.json`](../How2TypeFast/Inkscape.json) into `.config/karabiner/assets/complex_modifications`.
    <div align="center">
		<img width="80%" src="figures/sourcecode-2.png"/>
	</div>
3. Again open [Karabiner-Elements](https://karabiner-elements.pqrs.org/), go to *Complex Modifications* and click on *Add rule*.
	<div align="center">
		<img width="80%" src="figures/sourcecode-3.png"/>
	</div>
4. Enable it.
	<div align="center">
		<img width="80%" src="figures/sourcecode-4.png"/>
	</div>

If you're interested in how [`Inkscape.json`](../How2TypeFast/Inkscape.json) is created, see the following.

<details>

<summary><b>Detail Explanation</b></summary>

The [`Inkscape.json`](../How2TypeFast/Inkscape.json) is created by using a [`jsonnet`](https://jsonnet.org) file. The file can be found [here](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/Inkscape-setting/Inkscape-shortcut-manager/karabiner-Inkscape.jsonnet), and the `jsonnet` tool can be installed via `> brew install jsonnet`.

Converting the `jsonnet` file into the `json` file for [Karabiner Elements](https://karabiner-elements.pqrs.org/) can be done as follows

```sh
> jsonnet karabiner-Inkscape.jsonnet > ~/.config/karabiner/assets/complex_modifications/karabiner-Inkscape.json
```

</details>

#### Hammerspoon

Firstly, open the [Hammerspoon](https://www.hammerspoon.org/) console and run `hs.ipc.cliInstall()` to install the cli command `hs`. Then, just add the following code to your [`~/.hammerspoon/init.lua`](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/Inkscape-setting/Inkscape-shortcut-manager/init.lua).

#### Reference Card for Key Chords

As a reference for the key chords I add the original picture from [the original blog](https://castel.dev/post/lecture-notes-2/) but with the key chords included in the picture.

<div align="center">
	<img src="./figures/inkscape_shortcut.png"/>
</div>

#### Missing Key Chords

I did not add the *ergonomic* rebinding `x`, `w`, `f`, and `shift`+`z`. This should be possible in Inkscape itself. This setup also misses the bindings `t`, `shift`+`t`, `a`, `shift`+`a`, `s`, and `shift`+`s`. Since I encountered issues I did not pursue these.

### Summary

This is the whole setup I have, and let's wrap this up since I know this may be quite overwhelming.

1. Before you start your project, enter the `VISUAL` mode by pressing `v` in `NORMAL` mode. And then press `ctrl`+`f`. This will set up the file watcher.
2. When you want to create a new figure, go into a new line, type the name of your figure in `INSERT` mode, then press `ctrl`+`f`. This will create a new figure with the name you typed, and open it in Inkscape for you.
3. When you have drawn your figure, as long as you press `cmd`+`s` in Inkscape, it will automatically save the figure in `pdf+latex` for you, then you can close Inkscape.
4. When you want to edit one of your figures, you press `ctrl`+`f` in `NORMAL` mode, it will pop out a window for you to choose the figure you want to edit. And the rest is the same as 3.

## Updates

### ~~About Inkscape Shortcut Manager (09.27.21)~~

~~After some research, although there is a way to let the original script in [inkscape-shortcut-manager](https://github.com/gillescastel/inkscape-shortcut-manager) run correctly since it depends on `xlib`, which is no longer used by macOS for almost every application(including Inkscape, as expected), hence the only thing I can do now is to give up. In a perceivable future, if I have time to find an alternative way to interrupt the window activity in macOS, I'll try to configure it for macOS.~~

> Now the Inkscape Shortcut Manager is fully functional, see [here](#inkscape-shortcut-manager).

### Quiver - For commutative diagram (01.24.22)

I have been working on Category Theory for a while, and I found out that [quiver](https://q.uiver.app/) is quite appealing, hence I integrate it into my workflow. You can also pull it to your local environment, configure the VS Code Task, and combine it with a hotkey to use it **locally**. Specifically, I added the following code to my [`keybindings.json`](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/VSCode-setting/keybindings.json):

```json
{
    "key": "ctrl+c",
    "command": "command-runner.run",
    "args": {
        "command": "quiver",
        "terminal": {
            "name": "runCommand",
            "shellArgs": [],
            "autoClear": true,
            "autoFocus": false
        }
    },
    "when": "editorTextFocus"
},
```

and also, define the command `quiver` as

```json
"command-runner.commands": {
    "quiver": "open -na 'Google Chrome' --args --new-window <path-to-quiver>/quiver/src/index.html"
},
```

Notice that you'll need to build it first if you want to use it offline! Please follow the tutorial [here](https://github.com/varkor/quiver). Otherwise, it's totally fine to use `"quiver": "open -na 'Google Chrome' --args --new-window https://q.uiver.app/"` as your command.

This is how the workflow looks like.

<div align="center">
	<img src="./gifs/quiver.gif"/>
</div>

To use the package `tikz-cd`, you need to include the following in your header:

```latex
% quiver style
\usepackage{tikz-cd}
% `calc` is necessary to draw curved arrows.
\usetikzlibrary{calc}
% `pathmorphing` is necessary to draw squiggly arrows.
\usetikzlibrary{decorations.pathmorphing}

% A TikZ style for curved arrows of a fixed height, due to AndréC.
\tikzset{curve/.style={settings={#1},to path={(\tikztostart)
					.. controls ($(\tikztostart)!\pv{pos}!(\tikztotarget)!\pv{height}!270:(\tikztotarget)$)
					and ($(\tikztostart)!1-\pv{pos}!(\tikztotarget)!\pv{height}!270:(\tikztotarget)$)
					.. (\tikztotarget)\tikztonodes}},
	settings/.code={\tikzset{quiver/.cd,#1}
			\def\pv##1{\pgfkeysvalueof{/tikz/quiver/##1}}},
	quiver/.cd,pos/.initial=0.35,height/.initial=0}

% TikZ arrowhead/tail styles.
\tikzset{tail reversed/.code={\pgfsetarrowsstart{tikzcd to}}}
\tikzset{2tail/.code={\pgfsetarrowsstart{Implies[reversed]}}}
\tikzset{2tail reversed/.code={\pgfsetarrowsstart{Implies}}}
% TikZ arrow styles.
\tikzset{no body/.style={/tikz/dash pattern=on 0 off 1mm}}
```

You can certainly follow my [Template](https://github.com/sleepymalc/Academic-Template), which already includes all the requirement headers for you.

### Migrate to HyperSnips (02.18.22)

Now, instead of using [HyperSnips for Math](https://marketplace.visualstudio.com/items?itemName=OrangeX4.hsnips), we're using [HyperSnips](https://marketplace.visualstudio.com/items?itemName=draivin.hsnips), namely the **original one**! Since I just found out that we can trigger the snippets **only in math mode** by using the special keyword called `context`, I migrated to the original one. To migrate, you just need to uninstall [HyperSnips for Math](https://marketplace.visualstudio.com/items?itemName=OrangeX4.hsnips), install [HyperSnips](https://marketplace.visualstudio.com/items?itemName=draivin.hsnips) with the updated [latex.hsnips](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape/blob/main/VSCode-setting/Snippets/latex.hsnips) I prepared for you, and then enjoy!

### Documenting Inkscape Shortcut Manager (07.30.22)

I finally have time to document the configuration of the [Inkscape shortcut manager](#inkscape-shortcut-manager) and make some changes to make this document more readable. Personally, I have used this workflow for more than half of a year, so I think this is stable and will not be changed shortly.

## Credits

Again, thanks to Gilles Castel, this workflow fits my style. Although it originally worked in Linux+Vim only, the idea is the most important thing. Without his wonderful post, I can't even imagine this is possible. But now it is! Go to his original post to show him some love.

## Related Project

1. [VSCode-LaTeX-Inkscape](https://github.com/sleepymalc/VSCode-LaTeX-Inkscape) (The GitHub repo for this setup)
2. [LeTeX-Template](https://github.com/sleepymalc/LaTeX-Template)
3. [Notes](https://github.com/sleepymalc/Notes)
4. [gillescastel/inkscape-figures](https://github.com/gillescastel/inkscape-figures)
5. [gillescastel/inkscape-shortcut-manager](https://github.com/gillescastel/inkscape-shortcut-manager)
6. [chipsenkbeil/choose](https://github.com/chipsenkbeil/choose)
7. [varkor/quiver](https://github.com/varkor/quiver)
