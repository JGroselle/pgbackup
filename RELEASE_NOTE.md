# 2.0.0

## Breaking changes

- Replace non-visible rm_old function by usable prune function
- prune is not implicit in case of -a (all)

## Features

- Add prune (-p) option based on retention days

# 1.1.0

## Enhancements

- Add output dump path in a bash readable format

# 1.0.0

## Features

- Backup a single database
  - Ouput dump path
- Backup all databases
  - One dump per database
  - Globals in separated file
- Delete old backups
