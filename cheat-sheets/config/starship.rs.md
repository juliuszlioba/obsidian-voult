customized prompt configuration
[website](https://starship.rs/)

`~/.config/starship.toml`

```ini
# Get editor completions based on the config schema
"$schema" = 'https://starship.rs/config-schema.json'

# Inserts a blank line between shell prompts
add_newline = true

# Change command timeout from 500 to 1000 ms
command_timeout = 1000

# Change the default prompt format
[character]
# success_symbol = "[❯](#db4521)" // orange color for Ubuntu
success_symbol = "[❯](green)"
error_symbol = "[❯](bold red)"
vimcmd_symbol = "[❮](bold green)"

# Shows the username
[username]
style_user = "white"
style_root = "white"
format = "[$user]($style) "
disabled = false
show_always = false

[hostname]
ssh_only = true
format = "on [$hostname](bold yellow) "
disabled = false

[directory]
truncation_length = 3
truncation_symbol = "…/"
home_symbol = "home ~"
read_only_style = "197"
read_only = " ReadOnly "
format = "at [$path]($style)[$read_only]($read_only_style) " 

[git_branch]
symbol = "git "
format = "via [$symbol $branch]($style) "
truncation_length = 16
truncation_symbol = "…/"
style = "bold green"  

[git_commit]
tag_symbol = " tag "

[git_status]
disabled = false
format = '[$all_status$ahead_behind]($style) '
style = "bold green"
conflicted = "-conflicted "
untracked = "-untracked "
ahead = "-ahead(${count})"
behind = "-behind(${count})"
stashed = "-stashed "
modified = "-modified "
staged = '[++\($count\)](green)'
renamed = "-renamed "
deleted = "-deleted "

[docker_context]
symbol = "docker "

[nodejs]
symbol = "nodejs "

[package]
symbol = "is [$symbol$version]($style)"

[php]
symbol = "php "

[os.symbols]
Raspbian = "rasp "
Ubuntu = "ubnt "
Windows = "win "

[status]
symbol = "[x](bold red) "
```