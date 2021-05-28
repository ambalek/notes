## Norns

* [Script reference](https://monome.org/docs/norns/reference/)

### Editing over ssh

* Editing files on Norns with ssh/vim: https://gist.github.com/sloanlance/f481b7b8ffc0bfa3f46a1c942c7e7b78

Setting up the connection:

```sh
ssh -MN we@norns.local
```

Opening a file in vim:

```
:e scp://we@norns.local//home/we/dust/code/ambalek/midichords.lua
```

Script restart:

```sh
ssh we@norns.local
maiden-repl
norns.script.load()
```

### MIDI stuff

#### Panic

```lua
function panic()
  m = getMidiDevice()
  for note = 1, 127 do
    for channel = 1, 16 do
      for device = 1, 4 do
        m:note_off(note, 0, channel)
      end
    end
  end
end
```

#### Norns implementation

https://github.com/monome/norns/blob/e8ddf657830f8db99465965d45ade11e9dbbc831/lua/core/midi.lua

