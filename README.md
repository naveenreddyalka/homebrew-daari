# homebrew-daari

Homebrew tap for [daari](https://github.com/naveenreddyalka/daari) — a local-first
LLM execution router that caches before it reaches the cloud.

## Install

```bash
brew tap naveenreddyalka/daari
brew install daari
```

The formula builds the Rust extensions in `pydantic-core` and `watchfiles` from
source, so the first install pulls the Rust toolchain and takes a few minutes.

## Then

daari routes to local models through [Ollama](https://ollama.com), so pull one
before starting the daemon:

```bash
ollama pull llama3.2:3b
daari serve
daari doctor
```

The daemon listens on `http://127.0.0.1:11435`. Point an editor at it with
`daari setup cursor` (also `vscode`, `claude-code`, `intellij`), and undo any of
those with `daari setup --undo <tool>`.

## Updating this tap

`Formula/daari.rb` is generated in the main repo — do not edit it here. Each
release regenerates the tarball hash and every dependency resource, because
Homebrew builds without network access and installs only declared resources:

```bash
# in naveenreddyalka/daari
python scripts/update_formula.py --version X.Y.Z
```

Then copy the result into this tap. See
[RELEASING.md](https://github.com/naveenreddyalka/daari/blob/main/docs/RELEASING.md).

## Links

- [Documentation](https://naveenreddyalka.github.io/daari/)
- [Issues](https://github.com/naveenreddyalka/daari/issues)
