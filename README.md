# Git Tac Toe

A shared tic-tac-toe board for practicing Git and GitHub. Participants make every move by editing HTML, then use Git to share it. There is no JavaScript, automatic turn handling, or winner detection. Agree on turns and check the board together.

## Open the board

Clone this repository, then open `index.html` in a web browser (double-click it in your file manager). Open the same file in a text editor to make changes. No installation, build step, server, internet connection, or external resources are needed to view the board after cloning.

```sh
git clone https://github.com/WalkerTexasCoder-CH/git-tac-toe.git
cd git-tac-toe
```

## Make a move

Rows are A, B, and C from top to bottom. Columns are 1, 2, and 3 from left to right. Each square has a stable ID from `cell-a1` through `cell-c3`, and each cell occupies its own source line under the `MAKE YOUR MOVE` comment.

Find an empty cell in `index.html`, for example:

```html
<div class="cell" id="cell-a1"></div>
```

Insert just your mark between the tags:

```html
<div class="cell" id="cell-a1">X</div>
```

Use `O` for the other player. Keep the cell's ID and class unchanged, and leave occupied cells alone. Save the file, refresh the browser, and check that your mark appears in the intended square. Coordinate labels come from CSS; they do not need editing.

## Share a move with Git

Git tracks versions on your computer. GitHub hosts the shared repository. `add` stages your change, `commit` records it locally, `push` shares commits, and `pull` brings in other people's commits.

For the first round, take turns pushing directly to `main` **only if you already have collaborator write access and the repository's rules allow direct pushes**. Otherwise, follow the facilitator's branch and pull request workflow. Cloning a public repository does not grant push access.

Start each turn with a clean working tree and get the latest board before editing:

```sh
git switch main
git pull --ff-only origin main
```

After editing one cell and checking the browser:

```sh
git diff
git add index.html
git commit -m "Play X in A1"
git push origin main
```

Use a commit message matching your actual move. If a push is rejected because someone else pushed first, stop and coordinate with the facilitator, pull the latest work, and resolve any conflict together. Never force push or overwrite another player's move.

## Branches and pull requests

For the next round, start from an up-to-date `main` and create a branch with a unique name for your move:

```sh
git switch main
git pull --ff-only origin main
git switch -c move/your-name-x-b2
```

Edit an empty cell, save, refresh the browser, then share the branch:

```sh
git diff
git add index.html
git commit -m "Play X in B2"
git push -u origin move/your-name-x-b2
```

On GitHub, open a pull request from your branch into `main`. Review the changed cell together, then merge using the workshop's agreed process and repository rules. After the merge, everyone updates their local board:

```sh
git switch main
git pull --ff-only origin main
```

Refresh the browser to see the merged move. Pushing a branch to this shared repository also requires write access; the facilitator must confirm participant access before the workshop.
