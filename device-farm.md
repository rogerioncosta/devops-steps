### Device Farm

- Em user name e access key fazemos a sincronização da nossa automação com o device farm escolhido, como Browser Stack ou Sauce Labs, etc...
- Em upload app na guia do Appium, se subirmos nosso app, o device farm dará o hash do nosso app para se comunicar através das capacidades
- Exemplo: caps.setCapability("app", "bs://hash-ou-app-id")
