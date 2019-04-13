---
description: Проблемы и решения некоторых случаев
---

# Problems and decisions

Проблема : sudo не видит переменные среды. Решение: 

```text
sudo env "PATH=$PATH" your_command
```

