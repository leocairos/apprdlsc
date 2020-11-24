# RDLSC Mobile

### Remover versão global do react-native-cli

Não instalar o react-native-cli de forma global. Caso tenha instalado, remover:
* $ npm uninstall -g react-native-cli
* $ yarn global remove react-native-cli

### Criar projeto com npx

* $ npx react-native init apprdlsc --template react-native-template-typescript

### Executar projeto
* Windows/Android abrir emulador antes de executar
    * $ yarn android
* Mac executar diretamente
    * $ yarn ios

### Copiar arquivos de projeto modelo (exceto pasta android e ios)

### Para IOS necessário rodar comandos para o React-Navigation

```
$ cd ios
$ pod install
  * cocoapods (cocoapods.org) precisa estar instalado
    * $ sudo gem install cocoapods
```

### Instalar Fonts

* Baixar fontes
* Salvar na raiz do projeto em /assets/fonts o TTFs desejados
  * ficar atento ao nome do arquivo para Android e IOS
  * Não é a mesma pasta assets do SRC
* Criar e configurar o react-native.config.js no raiz
* $ yarn react-native link

### Instalar icons (apenas IOS, no android é automatico)

* $ cd ios
* $ pod install
* $ /ios/apprdlsc/info.plist
  * incluir "<string>Feather.ttf</string>":
  * ```
    <key>UIAppFonts</key>
      <array>
        <string>RobotoSlab-Medium.ttf</string>
        <string>RobotoSlab-Regular.ttf</string>
        <string>Feather.ttf</string>
      </array>
    ```

### Ajustar /android/app/build.gradele

* incluir na ultima linha
  * ```
    project.ext.vectoricons = [
      iconsFontNames: ['Feather.ttf']
    ];

    apply from: "../../node_modules/react-native-vector-icons/fonts.gradle"
    ```

### Configurar endereço do backend (baseURL: 'http://?:3333')

```
* iOS com Emulador: localhost
* iOs com fisico: IP da maquina
* Android com Emulador: localhost ($ adb reverse tcp:3333 tcp:3333)
* Android com Emulador: 10.0.2.2 (Android Studio)
* Android com Emulador: 10.0.3.2 (Genymotion)
* Android com fisico: IP da maquina
```

### For Native Dependences as AsyncStorage (in IOS)

* $ cd ios
* $ pod install

### rebuid android

* $ cd android
* $ npx gradlew clean
* $ cd ..
* $ yarn android

### .


## Debugando app com Flipper

* https://fbflipper.com

  * Dicas de uso em Finalizando front-end mobile do app >> Agendamento
  * view settings >> components >> Hide Components wher.. (add: type equals context)
  * Nome const do style (./styles.ts). Ex.: Header.displayName = 'DashboardHeader';


## Test

* $ yarn test
* $ yarn test --watchAll true
* $ yarn test --coverage
