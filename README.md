# muscle-mem# muscle-mem

A small shell script for practicing typing passwords. Passwords are never stored in plain text — only a SHA-256 hash is saved, locally in a hidden `.passwds/` folder, one file per entry.

## Requirements

- Bash
- `sha256sum` (available by default on most Linux distributions)

## Usage

```bash
./muscle-mem [MODE] [OPTION]
```

### Adding a password

```bash
./muscle-mem add entry-name
```

Prompts for the password twice (hidden input) and writes the hash to `./.passwds/entry-name`. If the two entries don't match, nothing is written.

If `entry-name` already exists, it asks whether you want to change it:

```
entry-name is already defined. Do you want to change it? [Y/n]
```

Enter or `y`/`Y` confirms the change; anything else cancels it.

### Practicing

```bash
./muscle-mem practise entry-name
```

Prompts for the password (hidden input) and compares its hash against the stored one. Prints `Correct` or `False` after each attempt and **keeps looping** — use `Ctrl+C` to exit practice mode.

### Deleting a password

```bash
./muscle-mem delete entry-name
```

Deletes `./.passwds/entry-name`. If the file doesn't exist, prints `File not found`.

### Listing saved passwords

```bash
./muscle-mem show
```

Lists the names (not the hashes) of all currently saved entries.

## File structure

```
.passwds/
├── entry-name-1
├── entry-name-2
└── ...
```

Each file contains only a SHA-256 hash (no salt, no other metadata).

## Notes

- Passwords are never passed as command-line arguments — they're entered exclusively through an interactive `read -s` prompt, so they don't end up visible in `ps` output or in `bash_history`.
- This is designed for local use (home computer). For a shared/multi-user server, you'd want to add proper permissions (`chmod 700 .passwds`) and possibly a per-entry salt.
- The script doesn't add a salt before hashing — fine for local practice, but worth keeping in mind if the format is ever extended.

A small shell script for practicing typing passwords. Passwords are never stored in plain text — only a SHA-256 hash is saved, locally in a hidden `.passwds/` folder, one file per entry.

## Requirements

- Bash
- `sha256sum` (available by default on most Linux distributions)

## Usage

```bash
./muscle-mem [MODE] [OPTION]
```

### Adding a password

```bash
./muscle-mem add entry-name
```

Prompts for the password twice (hidden input) and writes the hash to `./.passwds/entry-name`. If the two entries don't match, nothing is written.

If `entry-name` already exists, it asks whether you want to change it:

```
entry-name is already defined. Do you want to change it? [Y/n]
```

Enter or `y`/`Y` confirms the change; anything else cancels it.

### Practicing

```bash
./muscle-mem practice entry-name
```

Prompts for the password (hidden input) and compares its hash against the stored one. Prints `Correct` or `False` after each attempt and **keeps looping** — use `Ctrl+C` to exit practice mode.

### Deleting a password

```bash
./muscle-mem delete entry-name
```

Deletes `./.passwds/entry-name`. If the file doesn't exist, prints `File not found`.

### Listing saved passwords

```bash
./muscle-mem show
```

Lists the names (not the hashes) of all currently saved entries.

## File structure

```
.passwds/
├── entry-name-1
├── entry-name-2
└── ...
```

Each file contains only a SHA-256 hash (no salt, no other metadata).

## Notes

- Passwords are never passed as command-line arguments — they're entered exclusively through an interactive `read -s` prompt, so they don't end up visible in `ps` output or in `bash_history`.
- This is designed for local use (home computer).
- The script doesn't` add a salt before hashing — fine for local practice, but worth keeping in mind if the format is ever extended.
