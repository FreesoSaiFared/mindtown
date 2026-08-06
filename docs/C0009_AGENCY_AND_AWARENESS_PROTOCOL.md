# MindTown C0009 — Agency and awareness protocol

## The player cannot command a body directly

A click on the ground creates a `MINDTOWN_NUDGE/1` packet. It records direction, destination, strength and the fact that the pressure came from the hand of God. The packet explicitly says that it is not an order.

The character may:

- protest;
- refuse;
- wait;
- inspect something else;
- meditate;
- reinterpret the pressure;
- decide later to adopt the destination for a personality-consistent reason.

## Character descriptor

Each character carries a natural-language personality description plus four small behavioral tendencies:

- autonomy;
- initiative;
- probability of remaining still;
- affinity for meditation.

The descriptor and tendencies become part of the bootstrap prompt for that character's attached browser tab.

## Calm awareness

When the character is not acting, MindTown sends `MINDTOWN_AWARENESS/1` packets. They include only local perception, recent memory, current stillness depth, meditation state, any pending nudge and currently available actions.

Stillness is productive rather than empty. Each idle cycle increases awareness depth. Deeper awareness adds more environmental detail and faint, non-commanding inclinations. A meditating character may remain still deliberately; most ordinary characters have enough initiative that indefinite inactivity is unlikely.

## Decision output

Preferred provider output:

```text
[[MINDTOWN
{"characterId":"mira","speech":"I was becoming curious about the workshop anyway.","mode":"act","action":{"type":"move_to","target":[3,-2]}}
]]
```

Supported actions are bounded semantic operations such as `move_to`, `move_relative`, `inspect`, `wait` and `meditate`. The town validates the turn, character and action before changing the world.

For experimentation, the parser also accepts a restricted legacy form such as:

```text
[[mira:move:4 left]]
```

## Tab architecture

The Manifest V3 extension maintains:

```text
character identity ↔ browser tab ↔ provider conversation
```

The town sends awareness to the extension. The provider content script inserts the prompt into ChatGPT or Gemini, observes the answer, extracts a strict decision envelope and returns it through the extension to the town. The adapter fails closed when insertion, submission or extraction cannot be verified.

A separate orchestrator tab may poll character tabs, but it is not allowed to rewrite their decisions. It schedules awareness turns, detects completed output and submits validated decisions to the town.

## WebGL boundary

The ChromeOS recording showed:

```text
WebGL: CONTEXT_LOST_WEBGL: loseContext: context lost
```

The black scene began when DevTools docked and the canvas was sharply resized. C0009 uses a stable ChromeOS drawing buffer, updates camera aspect during dock and undock, logs context-loss/restoration events and displays graphics diagnostics inside the page. The VM's dock-style resize test completed on WebGL2 with zero context losses.

## Unproven boundary

A live authenticated ChatGPT or Gemini conversation has not yet completed this entire loop. That is the next empirical test; the local protocol, extension routing and deterministic fallback are already tested.
