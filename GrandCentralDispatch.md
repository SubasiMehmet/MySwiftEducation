# Grand Central Dispatch

## Working with Threads

---

> There are 4 different level GCD type.

1. User Interactive
2. User Initiate
3. Utility Queue
4. Background Queue

**These are ordered by priority type. For example, "User interactive" has the most priority than the others have.**

---

> GCD uses other threads without no need of our calculation. 

> The most important think about it: If you send the process to other thread, rest of the code will not wait for it and continue. We may not want to skip the process sometimes. (Most of times)


**To send to another thread with spesific qos (Quality of service)

    DispatchQueue.global(qos: .background).async { [weak self] in   }
    DispatchQueue.global(qos: .userInitiated).async { [weak self] in   }
    DispatchQueue.global(qos: .utility).async { [weak self] in   }
    DispatchQueue.global(qos: .userInteractive).async { [weak self] in   }
    
**Take back to main thread

                    DispatchQueue.global(qos: .userInitiated).async {   }
