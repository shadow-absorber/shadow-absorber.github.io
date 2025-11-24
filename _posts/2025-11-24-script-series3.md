---
title: "Script series 3"
date:   2025-11-24
categories:
  - Scripts
tags:
  - Scripts
  - tools
  - linux
  - posix
---

Ello again time for day 3

Today's script will be dictionary scripts using curl to get the meaning of words:

The first 2 scripts uses dict.org to look up words
```bash
dict1() {
    curl -s dict://dict.org/d:$1
}
```

```bash
dict1m() {
    curl -s dict://dict.org/m:$1
}
```

Lastly this one is special using an API that responds using JSON and then uses jq to extract the meanings
it also has error handling for words that don't have found definitions :D
```bash
dict2() {
    local response=$(curl -s "https://api.dictionaryapi.dev/api/v2/entries/en_US/$1")

    # Check if the response is a JSON array (indicating valid results)
    if ! echo "$response" | jq -e 'type == "array"' > /dev/null; then
        echo "No definitions found or invalid word: '$1'."
        return 1
    fi

    # Extract and format the meanings
    echo "$response" | jq -r '.[].meanings[] | "\(.partOfSpeech): \(.definitions[].definition)\n"'
}
```