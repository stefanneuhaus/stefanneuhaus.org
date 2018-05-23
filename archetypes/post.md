+++
title = "{{ replaceRE "^[0-9]*_(.*)" "$1" .TranslationBaseName | humanize }}"
slug = "{{ replaceRE "^[0-9]*_(.*)" "$1" .TranslationBaseName | urlize }}"
date = {{ .Date }}
draft = false

tags = []
categories = []

abstract = ""

highlight = false
math = false

[header]
image = ""
caption = ""
preview = true

+++


