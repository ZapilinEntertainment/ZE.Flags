# Use case
Flags are simple objects whose presence marks a corresponding continuos event. So there is a fundamental distinct from signals - they exists continuously and can exists in multiple instances (for example: pause flag can be activated both by player actions (ecs button) and by some loading logic. So flag be active until at least one reason source exists). Second main use-case is subscribing to flag - it can be observed as exist/non-exist (bool) and as first active flag. 

# How to create a flag:
- create class implementing IFlag
- FlagManager.AddFlag(instance) if you want to enable\disable multiple times or AddFlagTemporarily to dispose one-shot flag when needed
- on receiving side use FlagManager.Subscribe(isFlagActive => Foo(isFlagActive)).AddTo(compositeDisposable);
- also use FlagManager.GetFirstFlag if you need any active flag instance
- I recommend use 2 flag managers : one for app scope (app logic flags), and one for scene scope(game logic flags)

# Dependencies:
- Requires R3
