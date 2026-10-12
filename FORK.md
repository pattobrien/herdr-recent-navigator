# pattobrien/herdr-recent-navigator

This repository is a fork of
[beyondlex/herdr-recent-navigator](https://github.com/beyondlex/herdr-recent-navigator). It lets
Patt run plugin changes that upstream has not merged yet.

## What this fork carries

- Grouped and priority sort modes for the Agents tab, opened by the `focus-agents-grouped` and
  `focus-agents-priority` actions through `--sort`. Upstream PR:
  [beyondlex/herdr-recent-navigator#23](https://github.com/beyondlex/herdr-recent-navigator/pull/23).

Remove an item from this list once upstream merges its PR and a sync brings the change in.

## Using the fork

```sh
git clone https://github.com/pattobrien/herdr-recent-navigator ~/dev/pattobrien/herdr-recent-navigator
cd ~/dev/pattobrien/herdr-recent-navigator
cargo build --release
herdr plugin link "$PWD"
```

After pulling `main`, run `cargo build --release` again. If `herdr-plugin.toml` changed, run
`herdr plugin unlink beyondlex.herdr-recent-navigator`, then `herdr plugin link "$PWD"`, so herdr
reads the new actions.

## Syncing from upstream

Add the upstream remote once with
`git remote add upstream https://github.com/beyondlex/herdr-recent-navigator.git`.

1. Create a branch from `main`.
2. Merge upstream into the branch:

   ```sh
   git fetch upstream
   git merge --no-ff upstream/main
   ```

3. Run `cargo build --release` and `cargo test`.
4. Open a PR into `main`.

Never rebase or force-push `main` or any pushed branch.
