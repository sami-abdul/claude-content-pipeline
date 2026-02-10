# Depth Requirements

Every post needs depth. Surface-level narratives get rejected.

## The Depth Test

- **Shallow**: "We had a config bug that took down our agents." (What happened)
- **Deep**: The config had two sections that looked independent but were coupled. One controls failover. The other controls allowed models. We filled in one, left the other empty. The system failed over, got rejected silently, and sat there looking stuck. The fix was 6 lines. The lesson is about implicit coupling between config sections that don't reference each other.

## Rules

1. **Structural insight required.** Not just a narrative. What's the pattern? What's the principle?
2. **"Why" goes 2 levels deep minimum.** Not "the API was wrong" but "the API only returns open orders, so filled orders vanish from the response, and the bot reads absence as cancellation."
3. **Include what you tried first that didn't work.** The failed approach is often more interesting than the fix.
4. **Connect to a broader engineering principle.** Not "we added a config check" but "implicit coupling between config sections is a class of bug static analysis can't catch."
5. **The "why behind the why."** Every post must have at least one moment where you explain why the obvious fix wasn't obvious.
