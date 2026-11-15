# UMP fixes for Horizon and the Horizon Java Bridge

Fixes made while getting real Fabric 26.3 modpacks (100-300 mods) to run plug-and-play in
[Horizon](https://github.com/horizon-rust/horizon) through the
[Horizon Java Bridge](https://github.com/iaxivers/horizon-java-bridge). MIT, like both projects.
Source changes only: no Minecraft files, no mod jars or mod assets.

They are `git format-patch` files made on the bridge's `java-bridge` branch (99e8ba8049, 2026-11-10,
Horizon of 2026-11-05). Apply in order with `git am <folder>/*.patch` on that branch.

## for-official-horizon (30 patches)

General Horizon fixes and speed-ups that don't need the Java bridge: big-pack loading, far terrain,
commands, data packs, start-up time. Candidates for pull requests to horizon-rust/horizon. Some touch
code that upstream has reorganised since 2026-11-05 (game.rs split into game/*.rs) and need rebasing.

- `0005-commands-time-gamerule-queries-respect-quiet-sources.patch`: commands: time/gamerule queries respect quiet sources
- `0006-port-pack-write-block-declarations-compact.patch`: port-pack: write block declarations compact
- `0030-java-mods-the-Java-mods-tick-is-its-own-span-in-the-.patch`: java mods: the Java mods' tick is its own span in the
- `0036-dev-keep-mod-content-across-game-builds-on-request-l.patch`: dev: keep mod content across game builds on request;
- `0039-A-named-world-s-preload-reads-the-plain-worldgen-bun.patch`: A named world's preload reads the plain worldgen bundle
- `0042-Data-pack-JSON-files-are-read-without-a-byte-order-m.patch`: Data pack JSON files are read without a byte-order mark
- `0045-Far-terrain-s-upload-is-timed-by-its-steps.patch`: Far terrain's upload is timed by its steps
- `0046-With-Java-mods-the-worker-pools-leave-two-cores-free.patch`: With Java mods, the worker pools leave two cores free
- `0047-Shader-packs-get-lightningBoltPosition.patch`: Shader packs get lightningBoltPosition
- `0049-Far-terrain-draws-snow-snow-layers-of-saved-chunks-a.patch`: Far terrain draws snow: snow layers of saved chunks and
- `0051-Far-decoration-HORIZON_FAR_DECORATION_THREADS-overri.patch`: Far decoration: HORIZON_FAR_DECORATION_THREADS
- `0052-Far-decoration-places-only-what-shows-on-the-surface.patch`: Far decoration places only what shows on the surface
- `0053-Mods-content-overlay-files-linked-and-copied-by-seve.patch`: Mods' content: overlay files linked and copied by
- `0054-Faster-loads-with-big-mod-packs-shapes-deduplicated-.patch`: Faster loads with big mod packs: shapes deduplicated by
- `0055-Faster-starts-with-big-mod-packs-blockstates-mods-co.patch`: Faster starts with big mod packs: blockstates, mods'
- `0056-Faster-starts-with-big-mod-packs-loot-tables-recipes.patch`: Faster starts with big mod packs: loot tables, recipes
- `0057-Mods-content-root-bundled-into-one-data-file-as-the-.patch`: Mods' content root bundled into one data file, as the
- `0058-Java-mods-start-beside-the-reading-of-their-content-.patch`: Java mods start beside the reading of their content
- `0060-Advancements-read-namespace-by-namespace-at-once.patch`: Advancements read namespace by namespace at once
- `0061-Data-packs-of-a-prepared-root-listed-and-read-from-i.patch`: Data packs of a prepared root listed and read from its
- `0062-Mods-content-files-sized-from-their-folders-listings.patch`: Mods' content files sized from their folders' listings,
- `0065-Far-terrain-no-square-boxes-from-one-tree-or-one-hig.patch`: Far terrain: no square boxes from one tree or one high
- `0069-Block-facts-from-a-binary-snapshot-instead-of-3.3-GB.patch`: Block facts from a binary snapshot instead of 3.3 GB of
- `0072-Worldgen-data-load-outside-the-shared-list-s-lock.patch`: Worldgen data: load outside the shared list's lock
- `0073-Mods-forced-chunks-generate-as-near-as-the-player-s.patch`: Mods' forced chunks generate as near as the player's
- `0074-Preload-the-Nether-s-and-the-End-s-decoration-with-t.patch`: Preload the Nether's and the End's decoration with the
- `0077-Behaviour-registry-snapshots-key-big-source-files-by.patch`: Behaviour/registry snapshots: key big source files by
- `0082-With-Java-mods-preload-a-new-world-s-worldgen-data-a.patch`: With Java mods, preload a new world's worldgen data at
- `0088-Selectors-entity-type-tags-from-memory-nbt-patterns-.patch`: Selectors: entity type tags from memory, nbt= patterns
- `0089-Far-forests-wide-cells-draw-trees-as-often-as-real-c.patch`: Far forests: wide cells draw trees as often as real

## for-java-bridge (60 patches)

Fixes to the Java bridge itself (crates/horizon-jvm, the game's java_* modules, the launcher's
Java-mods pages): mods' blocks, mobs, screens, HUD, worldgen, networking, and plug-and-play mod
downloads. Candidates for pull requests to iaxivers/horizon-java-bridge.

- `0001-worldgen-lock-per-dimension-not-per-chunk-fixes-gene.patch`: worldgen: lock per dimension, not per chunk (fixes
- `0002-java-mods-leave-out-performance-only-mods-like-rende.patch`: java mods: leave out performance-only mods like
- `0003-java-mods-animate-mods-mobs-client-twins-walk-animat.patch`: java mods: animate mods' mobs (client twins, walk
- `0004-java-mods-leave-out-unreadable-mod-recipes-advanceme.patch`: java mods: leave out unreadable mod
- `0007-jvm-short-default-network-timeouts-for-mods-online-c.patch`: jvm: short default network timeouts for mods' online
- `0008-launcher-download-the-mods-Java-mods-require-plug-an.patch`: launcher: download the mods Java mods require (plug and
- `0009-java-mods-name-the-slow-mod-initializers.patch`: java mods: name the slow mod initializers
- `0010-java-mods-hold-a-new-player-3-s-for-load-scheduled-f.patch`: java mods: hold a new player 3 s for load-scheduled
- `0011-launcher-show-left-out-mods-and-unreadable-mod-data-.patch`: launcher: show left-out mods and unreadable mod data on
- `0012-launcher-fetch-Java-mods-missing-required-mods-when-.patch`: launcher: fetch Java mods' missing required mods when
- `0013-launcher-fix-Java-mods-version-conflicts-before-Play.patch`: launcher: fix Java mods' version conflicts before Play
- `0014-launcher-find-required-mods-whose-id-is-one-run-toge.patch`: launcher: find required mods whose id is one
- `0015-java-mods-open-the-mods-GPU-device-before-the-window.patch`: java mods: open the mods' GPU device before the
- `0016-java-mods-don-t-report-constructor-hooks-of-another-.patch`: java mods: don't report constructor hooks of another
- `0017-java-mods-give-mods-Share-Local-reference-parameters.patch`: java mods: give mods' @Share/@Local reference
- `0018-java-mods-block-colours-exist-at-the-client-s-start-.patch`: java mods: block colours exist at the client's start,
- `0019-java-mods-level-constructor-hooks-get-the-world-stor.patch`: java mods: level constructor hooks get the world
- `0020-java-mods-the-server-has-its-world-spawn-when-SERVER.patch`: java mods: the server has its world spawn when
- `0021-java-mods-run-mixins-field-initializers-on-the-headl.patch`: java mods: run mixins' field initializers on the
- `0022-java-mods-server-configs-defaults-before-the-mods-ge.patch`: java mods: server configs' defaults before the mods
- `0023-java-mods-the-entity-render-context-has-equipment-as.patch`: java mods: the entity render context has equipment
- `0024-launcher-also-follow-Modrinth-s-own-dependency-links.patch`: launcher: also follow Modrinth's own dependency links
- `0025-java-mods-the-mods-worldgen-runs-on-every-worker-aga.patch`: java mods: the mods' worldgen runs on every worker
- `0026-java-mods-the-HUD-s-reflective-lookups-are-made-once.patch`: java mods: the HUD's reflective lookups are made once
- `0027-java-mods-a-big-GPU-texture-on-the-HUD-is-sent-cropp.patch`: java mods: a big GPU texture on the HUD is sent cropped
- `0028-java-mods-the-JVM-collects-with-ZGC.patch`: java mods: the JVM collects with ZGC
- `0029-java-mods-far-terrain-s-land-from-the-mods-noise-is-.patch`: java mods: far terrain's land from the mods' noise is
- `0031-java-mods-structure-templates-brought-up-to-date-are.patch`: java mods: structure templates brought up to date are
- `0032-java-mods-the-mirror-s-levels-are-made-one-at-a-time.patch`: java mods: the mirror's levels are made one at a time
- `0033-java-mods-far-terrain-asks-whether-the-mods-generate.patch`: java mods: far terrain asks whether the mods generate
- `0034-java-mods-every-mirrored-level-has-a-structure-manag.patch`: java mods: every mirrored level has a structure manager
- `0035-java-mods-far-canopies-take-the-mods-biomes-own-tree.patch`: java mods: far canopies take the mods' biomes' own tree
- `0037-java-mods-a-mods-folder-and-loot-tables-a-mod-ships-.patch`: java mods: a mods/ folder and loot tables a mod ships
- `0038-java-mods-the-client-s-levels-have-the-level-extract.patch`: java mods: the client's levels have the level
- `0040-java-mods-a-warning-mods-give-thousands-of-times-is-.patch`: java mods: a warning mods give thousands of times is
- `0041-launcher-pre-release-parts-compare-as-Fabric-compare.patch`: launcher: pre-release parts compare as Fabric compares
- `0043-java-mods-the-headless-client-s-delta-tracker-is-a-r.patch`: java mods: the headless client's delta tracker is a
- `0044-java-mods-a-data-load-that-fails-names-the-mods-whos.patch`: java mods: a data load that fails names the mods whose
- `0048-launcher-the-mod-browser-installs-Fabric-mods-and-sh.patch`: launcher: the mod browser installs Fabric mods and
- `0050-Java-mods-profile-each-HUD-part-s-time-and-the-pictu.patch`: Java mods' profile: each HUD part's time, and the
- `0059-Structure-template-palettes-safe-for-the-mods-worldg.patch`: Structure template palettes safe for the mods' worldgen
- `0063-Java-class-archive-named-for-the-game-build-too-so-a.patch`: Java class archive named for the game build too, so an
- `0064-Mirror-connections-complete-enough-for-mods-device-m.patch`: Mirror connections complete enough for mods; device-mod
- `0066-Mods-mobs-animate-smoothly-mods-first-person-hands-s.patch`: Mods' mobs animate smoothly; mods' first-person hands
- `0067-Test-a-mod-mob-s-pose-redrawn-every-few-ticks-moves-.patch`: Test: a mod mob's pose redrawn every few ticks moves
- `0068-Mods-HUD-built-every-2nd-tick.patch`: Mods' HUD built every 2nd tick
- `0070-Remember-Shapes.joinIsNotEmpty-answers-by-shape-iden.patch`: Remember Shapes.joinIsNotEmpty answers by shape
- `0071-Updated-structure-templates-read-ahead-from-one-pack.patch`: Updated structure templates read ahead from one pack
- `0075-Remember-Shapes.join-results-by-shape-identity-too.patch`: Remember Shapes.join results by shape identity too
- `0076-Equal-boxes-are-one-shape-Shapes.create-shares-insta.patch`: Equal boxes are one shape: Shapes.create shares
- `0078-A-world-with-no-saved-dimension-opens-without-waitin.patch`: A world with no saved dimension opens without waiting
- `0079-Joined-shapes-with-the-same-boxes-become-one-instanc.patch`: Joined shapes with the same boxes become one instance
- `0080-Knot-s-class-lookups-through-a-package-to-jar-index.patch`: Knot's class lookups through a package-to-jar index
- `0081-Name-the-slow-mod-listeners-at-the-world-s-start.patch`: Name the slow mod listeners at the world's start
- `0083-The-Java-client-s-first-frame-runs-while-the-player-.patch`: The Java client's first frame runs while the player is
- `0084-Mirror-connections-keep-a-handler-in-their-pipeline.patch`: Mirror connections keep a handler in their pipeline
- `0085-The-client-s-entity-render-dispatcher-exists-before-.patch`: The client's entity render dispatcher exists before its
- `0086-The-client-s-reload-runs-the-mods-listeners-in-the-g.patch`: The client's reload runs the mods' listeners in the
- `0087-Big-packs-leave-out-the-largest-content-mods-instead.patch`: Big packs: leave out the largest content mods instead
- `0090-Java-mods-content-remove-the-build-s-own-inputs-from.patch`: Java mods' content: remove the build's own inputs from

## Measured with these fixes (Ryzen 5 7600, RX 7600, Windows 11)

- 184 Fabric mods: warm start ~60-70 s (was 2+ min), click-to-world ~27 s.
- 300 mods (348 content mods loaded, 1 left out for the block-state limit): flying 199 fps average,
  59 fps 1% low (was 164 / 41).
- Test suite: 77/77 checks on real mod packs (blocks, items, mobs, screens, machines, save/reload,
  shaders, a new-player run).

## Where the code lives

- Full branch with all 90 commits, on the Java bridge: https://github.com/lanepon224/horizon-java-bridge/tree/ump-fixes
- Offered to the bridge as a draft pull request: https://github.com/iaxivers/horizon-java-bridge/pull/2

Anyone is welcome to fork it and build on it.

## Not finished

- Merging Horizon's newer main (16,161 commits since 2026-11-05) is in progress.
- Targets still open: join <= 15 s, 110+ fps with 300 mods and with shaders, Voxy-quality far terrain.
