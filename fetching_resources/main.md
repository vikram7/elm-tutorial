# Main

## Main Model

Remove the hardcoded list of players in __src/Model.elm__

```elm
initialModel : AppModel
initialModel =
  { players = []
  , routing = Routing.initialModel
  }
```




## Main

Finally we need to run the `fetchAll` when starting the application.

Update __src/Main.elm__:

```elm
...
import Players.Effects

init =
  let
    fxs =
      [ Effects.map PlayersAction Players.Effects.fetchAll
      ]

    fx =
      Effects.batch fxs
  in
    ( Models.initialModel, fx )
```

`init` now returns a list of effects to run when the application starts. For now is a list of one but we will adding more to this list soon. `Effects.batch` batches a list of effects into one `Effects`.