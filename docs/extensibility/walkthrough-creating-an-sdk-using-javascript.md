---
title: 'Tutorial: crear un SDK con JavaScript | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 29dac6cca7936dde8be2ebc57366f6370b8bcbc6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904941"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>Tutorial: crear un SDK mediante JavaScript
En este tutorial se enseña cómo usar JavaScript para crear un SDK de Math sencillo como extensión de Visual Studio (VSIX).  El tutorial se divide en estas partes:

- [Para crear el proyecto de SDK de extensión SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [Para crear una aplicación de ejemplo que usa el SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  En JavaScript, no hay ningún tipo de proyecto de biblioteca de clases. En este tutorial, el archivo de *arithmetic.js* de ejemplo se crea directamente en el Proyecto VSIX. En la práctica, se recomienda compilar y probar primero los archivos JavaScript y CSS como una aplicación de la tienda Windows (por ejemplo, usando la plantilla **aplicación vacía** ) antes de colocarlos en un proyecto VSIX.

## <a name="prerequisites"></a>Requisitos previos
 Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea el [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a> Para crear el proyecto de SDK de extensión SimpleMathVSIX

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

2. En la lista de categorías de plantilla, en **Visual C#**, seleccione **extensibilidad**y, a continuación, seleccione la plantilla de **Proyecto VSIX** .

3. En el cuadro de texto **nombre** , especifique `SimpleMathVSIX` y elija el botón **Aceptar** .

4. Si aparece el **Asistente para paquetes de Visual Studio** , elija el botón **siguiente** en la página de **bienvenida** y, a continuación, en la **Página 1 de 7**, elija el botón **Finalizar** .

     Aunque se abra el **Diseñador de manifiestos** , mantendremos este tutorial sencillo modificando directamente el archivo de manifiesto.

5. En **Explorador de soluciones**, abra el menú contextual del archivo **source. Extension. vsixmanifest** y, a continuación, elija **Ver código**. Use este código para reemplazar el contenido existente en el archivo.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
      <Metadata>
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />
        <DisplayName>Simple Math</DisplayName>
        <Description>Does basic arithmetic calculations.</Description>
      </Metadata>
      <Installation Scope="Global" AllUsers="true">
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />
      </Installation>
      <Dependencies>
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />
      </Dependencies>
      <Assets>
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
      </Assets>
    </PackageManifest>
    ```

6. En **Explorador de soluciones**, abra el menú contextual del proyecto **SimpleMathVSIX** y, a continuación, elija **Agregar**  >  **nuevo elemento**.

7. En la categoría de **datos** , seleccione **archivo XML**, asigne un nombre al archivo `SDKManifest.xml` y elija el botón **Agregar** .

8. En **Explorador de soluciones**, abra el menú contextual del archivo de **SDKManifest.xml** y, a continuación, elija **abrir** para mostrar el archivo en el **Editor XML**.

9. Agregue el código siguiente al archivo **SDKManifest.xml** .

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <FileList
      DisplayName="Simple Math"
      MinVSVersion="14.0"
      AppliesTo="JavaScript+WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">

      <!-- JS -->
      <File Content="js\arithmetic.js" />
    </FileList>

    ```

10. En **Explorador de soluciones**, en el menú contextual del archivo de **SDKManifest.xml** , elija **propiedades**.

11. En la ventana **propiedades** , establezca la propiedad **incluir en VSIX en** **true**.

12. En **Explorador de soluciones**, en el menú contextual del proyecto **SimpleMathVSIX** , elija **Agregar**  >  **nueva carpeta**y, a continuación, asigne un nombre a la carpeta `Redist` .

13. Agregue subcarpetas en Redist para crear esta estructura de carpetas:

     *\Redist\CommonConfiguration\Neutral\SimpleMath\js\\*

14. En el menú contextual de la carpeta **\js \\ ** , elija **Agregar**  >  **nuevo elemento**.

15. En **elementos de Visual C#**, seleccione la categoría **Web** y, a continuación, seleccione el elemento **archivo de JavaScript** . Asigne un nombre al archivo `arithmetic.js` y, a continuación, elija el botón **Agregar** .

16. Inserte el código siguiente en *arithmetic.js*:

    ```csharp
    (function (global) {
        "use strict";
        global.Arithmetic = {
            add: function (firstNumber, secondNumber) {
                return firstNumber + secondNumber;
            },

            subtract: function (firstNumber, secondNumber) {
                return firstNumber - secondNumber;
            },

            multiply: function (firstNumber, secondNumber) {
                return firstNumber * secondNumber;
            },

            divide: function (firstNumber, secondNumber) {
                return firstNumber / secondNumber;
            }
        };
    })(this);

    ```

17. En **Explorador de soluciones**, en el menú contextual del archivo de **arithmetic.js** , elija **propiedades**. Realice estos cambios de propiedad:

    - Establezca la propiedad **incluir en VSIX en** **true**.

    - Establezca la propiedad **Copiar en el directorio de salida** en **copiar siempre**.

18. En **Explorador de soluciones**, en el menú contextual del proyecto **SimpleMathVSIX** , elija **compilar**.

19. Una vez que la compilación se complete correctamente, en el menú contextual del proyecto, elija **Abrir carpeta en el explorador de archivos**. Vaya a **\bin\debug \\ **y ejecute `SimpleMathVSIX.vsix` para instalarlo.

20. Elija el botón **instalar** y deje que se complete la instalación.

21. Reinicie Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a> Para crear una aplicación de ejemplo que usa el SDK

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

2. En la lista de categorías de plantilla, en **JavaScript**, seleccione **tienda Windows**y, a continuación, seleccione la plantilla **aplicación vacía** .

3. En el cuadro **nombre** , especifique `ArithmeticUI` . Elija el botón **Aceptar** .

4. En **Explorador de soluciones**, abra el menú contextual del proyecto **ArithmeticUI** y, a continuación, elija **Agregar**  >  **referencia**.

5. En **Windows**, elija **extensiones**y observe que se muestra **matemáticas simples** .

6. Active la casilla **matemáticas simples** y, a continuación, elija el botón **Aceptar** .

7. En **Explorador de soluciones**, en **referencias**, observe que se muestra la referencia **matemática simple** . Expándalo y observe que hay una carpeta **\js \\ ** que incluye **arithmetic.js**. Puede abrir **arithmetic.js** para confirmar que el código fuente está instalado.

8. Use el código siguiente para reemplazar el contenido de *default.htm*.

   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="utf-8" />
       <title>ArithmeticUI</title>

       <!-- WinJS references -->
       <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />
       <script src="//Microsoft.WinJS.1.0/js/base.js"></script>
       <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>

       <!-- ArithmeticUI references -->
       <link href="/css/default.css" rel="stylesheet" />
       <script src="/js/default.js"></script>
       <script src="/SimpleMath/js/arithmetic.js"></script>
   </head>
   <body>
       <form>
       <div id="calculator" class="ms-grid">
           <input name="firstNumber" id="firstNumber" type="number" step="any">
           <div id="operators">
               <button class="operator" type="button">+</button>
               <button class="operator" type="button">-</button>
               <button class="operator" type="button">*</button>
               <button class="operator" type="button">/</button>
           </div>
           <input id="secondNumber" type="number">
           <button class="calculate" type="button">=</button>
           <input id="result" type="number" name="result" disabled="" readonly="">
       </div>
       </form>
   </body>
   </html>
   ```

9. Use el código siguiente para reemplazar el contenido de *\js\default.js*.

    ```csharp
    (function () {
        "use strict";

        var app = WinJS.Application;
        var operation = null;

        function calculateResult() {
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),
                result = 0;

            if (isNaN(firstNumber) || isNaN(secondNumber)) {
                result = 0;
            }
            else {
                switch (operation) {
                    case "+":
                        result = Arithmetic.add(firstNumber, secondNumber);
                        break;
                    case "-":
                        result = Arithmetic.subtract(firstNumber, secondNumber);
                        break;
                    case "*":
                        result = Arithmetic.multiply(firstNumber, secondNumber);
                        break;
                    case "/":
                        result = Arithmetic.divide(firstNumber, secondNumber);
                        break;
                    default:
                }
            }
            document.querySelector("#result").value = result.toString();
        }

        app.onactivated = function (args) {
            document.querySelector("#calculator").addEventListener("click", function (event) {
                if (event.target.tagName.toLowerCase() === "button") {
                    switch (event.target.className) {
                        case "operator":
                            operation = event.target.innerText;
                            break;
                        case "calculate":
                            calculateResult();
                            break;
                        default:
                            break;
                    }
                }
            });
        };

        app.start();
    })();
    ```

10. Reemplace el contenido de *\css\default.CSS* por este código:

    ```xml
    form {
        display: -ms-grid;
        -ms-grid-rows: 1fr auto 1fr;
        -ms-grid-columns: 1fr auto 1fr;
        height: 100%;
        width: 100%;
    }

    button, input[type=number] {
        margin-right: 5px;
        -ms-grid-row-align: center;
    }

    #calculator {
        -ms-grid-column: 2;
        -ms-grid-row: 2;
        display: -ms-grid;
        -ms-grid-rows: 1fr;
        -ms-grid-columns: auto min-content auto auto auto;
    }

    .ms-grid input {
        width: 5em;
    }

    #firstNumber {
        -ms-grid-column: 1;
        -ms-grid-row-align: center;
    }

    #operators {
        -ms-grid-column: 2;
        -ms-grid-row-align: center;
    }

        #operators button.operator {
            margin-bottom: 5px;
            height: 40px;
        }

    #secondNumber {
        -ms-grid-column: 3;
    }

    button.calculate {
        -ms-grid-column: 4;
        -ms-grid-row-align: center;
        height: 40px;
    }

    #result {
        -ms-grid-column: 5;
    }

    ```

11. Elija la tecla **F5** para compilar y ejecutar la aplicación.

12. En la interfaz de usuario de la aplicación, escriba dos números cualesquiera, seleccione una operación y, a continuación, elija el **=** botón. Aparece el resultado correcto.

## <a name="see-also"></a>Consulte también
- [Creación de un kit de desarrollo de software](../extensibility/creating-a-software-development-kit.md)
