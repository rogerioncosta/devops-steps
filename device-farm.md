## Device Farm

- Em user name e access key fazemos a sincronização da nossa automação com o device farm escolhido, como Browser Stack ou Sauce Labs, Kobiton, Aws, etc...
- Em upload app na guia do Appium, se subirmos nosso app, o device farm dará o hash do nosso app para se comunicar através das capacidades
- Exemplo: caps.setCapability("app", "bs://hash-ou-app-id")

### Como rodar teste automatizado `mobile` em um device farm com Appium
- vamos usar de exemplo o browser stack
- na tela de introdução com o java selecionado
- no cmd do git, entre na pasta onde queremos colocar nosso projeto
- no git lab ou git hub vamos clonar um projeto existente
- em clone, copie a url https ou ssh
- rode git clone + url no cmd git
- abra e adicione o projeto na IDE intellij ou vscode por exemplo
- no helper do browser stack, ele dá o que devemos inserir de configuração no código antes de começar os códigos de testes
### Exemplo

src
  java
    org
      example
        meu-projeto
          DeviceFarmLogin.java
          ScreenLogin.java
          
arquivo `DeviceFarmLogin`
```JAVA
@BeforeClass
public static void caps() throws MalformedURLException {
    DesiredCapabilities caps = new DesiredCapabilities();

    // Set your access credentials
    caps.setCapability(capabilityName: "browserstack.user", value: "user-browser-stack_N8....");
    caps.setCapability(capabilityName: "browserstack.key", value: "yxf....");

    // Set URL of the application under test
    // Aqui é o hash que gera ao subir o apk no device farm
    caps.setCapability(capabilityName: "app", value: "bs://2c5cf8......");

    // Specify device and os_version for testing
    caps.setCapability(capabilityName: "device", value: "Google Pixel 3");
    caps.setCapability(capabilityName: "os_version", value: "9.0");

    // Aqui faz a sincronização com o nosso farm
    driver = new AndroidDriver<>(new URL(spec: "http://hub.browserstack.com/wd/hub"), caps);
    ScreenLogin = new ScreenLogin(driver);
}

// Aqui começam nossos testes
@Test
public void testeLogin() {
    ScreenLogin.logar();
}
```
arquivo `ScreenLogin.java`

```JAVA```
package org.example.meu-projeto;

import io.appium.java_client.AppiumDriver;
import io.appium.java_client.pagefactory.AndroidFindBy;
import io.appium.java_client.pagefactory.AppiumFieldDecorator;
import io.appium.java_client.pagefactory.iOSFindBy;
import org.openqa.selenium.remote.RemoteWebElement;
import org.openqa.selenium.support.PageFactory;

public class ScreenLogin {

    public ScreenLogin(AppiumDriver<RemoteWebElement> driver) {
        PageFactory.initElements(new AppiumFieldDecorator(driver), this);
    }

    @AndroidFindBy(id = "login_username")
    @iOSFindBy(accessibility = "login_username")
    private RemoteWebElement campoemail;

    @AndroidFindBy(id = "login_password")
    @iOSFindBy(accessibility = "login_password")
    private RemoteWebElement camposenha;

    @AndroidFindBy(id = "login_button")
    @iOSFindBy(accessibility = "login_button")
    private RemoteWebElement botaologar;

    public void logar() {
        campoemail.sendKeys("email@gmail.com");
        camposenha.sendKeys("1234");
        botaologar.click();
    }
}
```
- Ao rodar o teste na ide, vai bater no device farm e rodar
- O appium não precisar estar rodando nem instalado na máquina local, pois está no device farm
- no device farm, em dashbord, vai estar o teste executado com todas as evidências

### Como rodar um teste web em um device farm com Selenium
- 
