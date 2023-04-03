# Bash Preloaders

### Version 1

```bash
#!/bin/bash

# Define the animation frames
frames=( "|" "/" "-" "\\" )

# Loop through the frames
while true; do
  for frame in "${frames[@]}"; do
    # Clear the current line
    printf "\033[2K\r"

    # Print the frame in blue color
    printf "\033[34m[%s] Loading...\033[0m" "$frame"

    # Sleep for a short time to create animation effect
    sleep 0.1
  done
done
```

### Version 2

```bash
#!/bin/bash

spinner() {
  local pid=$1
  local delay=0.1
  local spinstr='⠋⠙⠹⠸⠼⠴⠦⠧⠇⠏'
  local color="\033[36m"
  tput civis
  while [ "$(ps a | awk '{print $1}' | grep $pid)" ]; do
    local temp=${spinstr#?}
    printf "$color Loading... %c \033[0m\n" "$spinstr"
    local spinstr=$temp${spinstr%"$temp"}
    sleep $delay
    printf "\033[1A\033[2K"
  done
  printf "\033[2K\033[1G"
  tput cnorm
}

# Your script commands here

# ...

# Start the spinner in the background
spinner $BASHPID &

# Wait for the script commands to finish
wait $!

# Stop the spinner
printf "$color Done. \033[0m\n"

```
