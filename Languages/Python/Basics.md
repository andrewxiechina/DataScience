# lambda
map()
```python
spells = ['protego', 'accio', 'expecto patronum', 'legilimens']

# Use map() to apply a lambda function over spells: shout_spells
shout_spells = map(lambda item: item + '!!!', spells)

# Convert shout_spells to a list: shout_spells_list
shout_spells_list = list(shout_spells)
```

filter()
```python
result = filter(lambda item: len(item) > 6, spells)
```

reduce()
```python
result = reduce(lambda item1, item2: item1 + item2, spells)
```
