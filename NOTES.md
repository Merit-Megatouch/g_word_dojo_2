# WORD DOJO 2 (g_word_dojo_2)

Status: **playable** — full rounds: word entry and scoring, power-ups, final score, game-over screen, saved hi-score. Scaffolded 2026-10-07. Facts: [notes/scaffold.md](notes/scaffold.md).

## Checklist
- [x] Window size in game.conf matches the largest PNG (notes/scaffold.md)
- [x] Every symbol in notes/unresolved.txt has a stand-in in src/host/loader_services.cpp
      (`make analyze GAME=g_word_dojo_2` until it reports 0)
- [x] First run: `make run GAME=g_word_dojo_2 DEBUG=shots` — crash trace + screenshots in notes/shots
- [ ] Paths: `make run GAME=g_word_dojo_2 DEBUG=files`; engine trace: `mkdir -p data/var/merit/debug/files && touch data/var/merit/debug/files/resource_locator`
- [ ] Reference code: `make decompile GAME=g_word_dojo_2`
- [ ] Translations + help text appear (gamedata/translations/g_word_dojo_2.utf8)
- [x] Sound and music play (`DEBUG=sound`)
- [x] A full game plays through (`DEBUG=profile` to catch stalls and old-malloc bugs)

## Log
- 2026-10-07 — 8 new loader stand-ins in src/host/loader_services.cpp:
  HighScoresManager::HighestScore/HighestName (Hi-Score panel; 0 / ""),
  Locale::LanguageManager::GetInstance/Active (0 = English → scripts/dictionaries/english/),
  Allegro UTF-8 helpers ustrlen, ugetat (negative index from the end), ustrcmp, ustrupr.
- 2026-10-07 — g_word_dojo_2.so lists libinput_sprite.so as NEEDED but imports nothing from it:
  the build now ships empty stubs for the three old *_sprite libraries; new-game.sh links them.
- 2026-10-07 — Verified headless: instructions → board with lantern letters, 2:00 timer,
  round music loop, tile sounds, dictionary.txt/alphabet/letter tables opened.
  Not yet verified by hand: entering words and scoring, bonus round, game over.
- 2026-10-07 — Played a full round by hand: words score (e.g. "BAD" 22,000), shuriken power-ups,
  final score 421,000. Game over now shows the cabinet's shared screen (games/default, now part of
  shared data); the Hi-Score panel shows the saved best (data/var/merit/highscores/258.txt).
  Still to check: bonus round, help screen.
