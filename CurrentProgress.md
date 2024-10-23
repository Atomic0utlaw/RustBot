# 🌟 RCE Discord Bot V2

## 📜 Current PROGRESS

### Current status:
PS git> npm ls qoop mysql underscore
rce-discord-bot-v2@1.0.0 .\git
+-- mysql-sync@0.0.5
| +-- mysql@2.18.1
| +-- qoop@0.1.0 deduped
| -- underscore@1.13.7 deduped
+-- qoop@0.1.0
| +-- mysql@2.4.2
| -- underscore@1.6.0
-- underscore@1.13.7



** From the output, we can see the following: **

### Multiple Versions of mysql and underscore:
- mysql-sync uses mysql@2.18.1.
- qoop uses mysql@2.4.2 and underscore@1.6.0.
- also have underscore@1.13.7 listed as a deduped version.

### Vulnerabilities:
- The mysql versions being used have vulnerabilities.
- The underscore version used by qoop (1.6.0) has critical vulnerabilities

# Whats Next
## Considering Removing qoop: 
Since it introduces older and vulnerable versions of dependencies, I have been considering removing it if it's not essential. I will be checking the code for any direct dependencies on qoop and refactor as needed.
Command if needed:
```
npm uninstall qoop
```

## 2. Upgrade Direct Dependencies:
If we still need functionality provided by qoop, we will look for alternatives that do not have these vulnerabilities.

## 3. Force a Resolution: 
If we need to keep qoop and want to force a particular version of underscore or mysql, we can use npm's overrides feature in the package.json:
```
{
  "overrides": {
    "underscore": "1.13.7",
    "mysql": "2.18.1"
  }
}
```

then run `npm install` agian

## Additional Possibilities:
- reach out to `qoop` maintainers to ask about plans for updating the vulnerable dependencies.
- Manual Updates: As a last resort, I will consider forking qoop and updating its dependencies myself. This approach is more technical but ensures we will have control over the library.
