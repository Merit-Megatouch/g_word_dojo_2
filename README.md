# WORD DOJO 2 (g_word_dojo_2)

One game of [megatouch-port](https://github.com/Merit-Megatouch/megatouch-port):
original Megatouch ION cabinet games running on Linux / WSL2.

This repo holds the port's configuration and notes — no cabinet code or assets. Use it from
the main repo, where it lives at `games/g_word_dojo_2`:

```
git clone --recurse-submodules https://github.com/Merit-Megatouch/megatouch-port
cd megatouch-port && make setup && make new GAME=g_word_dojo_2 && make run GAME=g_word_dojo_2
```

| File | What |
| --- | --- |
| [game.conf](game.conf) | GameId, library, asset folder, window size, language |
| [NOTES.md](NOTES.md) | Status, checklist, dated log |
| [notes/scaffold.md](notes/scaffold.md) | Facts found when scaffolding |
| [notes/unresolved.txt](notes/unresolved.txt) | Cabinet loader functions still needed |
