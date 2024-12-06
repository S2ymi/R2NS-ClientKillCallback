# R2NS-ClientKillCallback

### `AddClientCallback_OnPlayerKilled ( void functionref ( ObituaryCallbackParams {entity victim, entity attacker, int damageSourceId, int scriptDamageType} ) customCallback)`

With the <a href="https://github.com/S2ymi/R2NS-ClientKillCallback/pull/1">new update made by Uniboi</a>, the arguments of current callbacks need to be replaced with an `ObituaryCallbackParams` struct.<br>
The struct currently contains:
- entity attacker
- entity victim
- int damageSourceId
- int scriptDamageType
- bool victimIsOwnedTitan

#### Example:

```
void function afterClientInit(){
    AddCallback_OnPlayerKilled ( myCallbackFunction )
}

void function myCallbackFunction ( ObituaryCallbackParams inputParams ) {
    if(inputParams.attacker == GetLocalClientPlayer() && DamageSourceIDToString(inputParams.damageSourceId) == "mp_weapon_sniper")
        thread myOnKillFunction()
}
```

Note: this is triggered each time a player gets killed in a match, **not just by the client player**. If you only care about client player's kills, simply check if `inputParams.attacker == GetLocalClientPlayer()`
