---
title: 'Tutorial: Creación de un SDK mediante JavaScript ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3a3fa110bd6521443521449898474299dd267d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697503"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>Tutorial: Crear un SDK con JavaScript
En este tutorial se enseña cómo usar JavaScript para crear un SDK matemático simple como una extensión de Visual Studio (VSIX).  El tutorial se divide en estas partes:

- [Para crear el proyecto SDK de extensión SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [Para crear una aplicación de ejemplo que use el SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  Para JavaScript, no hay ningún tipo de proyecto de biblioteca de clases. En este tutorial, el archivo *arithmetic.js* de ejemplo se crea directamente en el proyecto VSIX. En la práctica, se recomienda compilar y probar primero los archivos JavaScript y CSS como una aplicación de la Tienda Windows (por ejemplo, mediante la plantilla Aplicación en **blanco)** antes de colocarlos en un proyecto VSIX.

## <a name="prerequisites"></a>Prerrequisitos
 Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea SDK de [Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a>Para crear el proyecto SDK de extensión SimpleMathVSIX

1. En la barra de menús, elija **Archivo** > **nuevo** > **proyecto**.

2. En la lista de categorías de plantilla, en **Visual C,** seleccione **Extensibilidad**y, a continuación, seleccione la plantilla **Proyecto VSIX.**

3. En el cuadro de `SimpleMathVSIX` texto **Nombre,** especifique y elija el botón **Aceptar.**

4. Si aparece el **Asistente para paquetes** de Visual Studio, elija el siguiente botón en el **bienvenida** página y, a continuación, en la página 1 de **7**, elija el **finalizar** botón. **Next**

     Aunque se abre el Diseñador de **manifiestos,** mantendremos este tutorial simple modificando el archivo de manifiesto directamente.

5. En el **Explorador**de soluciones , abra el menú contextual del archivo **source.extension.vsixmanifest** y, a continuación, elija **Ver código**. Utilice este código para reemplazar el contenido existente en el archivo.

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

6. En el **Explorador**de soluciones , abra el menú contextual del proyecto **SimpleMathVSIX** y, a continuación, elija **Agregar** > **nuevo elemento**.

7. En la categoría **Datos,** seleccione Archivo `SDKManifest.xml` **XML**, asigne un nombre al archivo y elija el botón **Agregar.**

8. En el **Explorador**de soluciones , abra el menú contextual del archivo **SDKManifest.xml** y, a continuación, elija **Abrir** para mostrar el archivo en el **Editor XML**.

9. Agregue el código siguiente al archivo **SDKManifest.xml.**

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

10. En **el Explorador**de soluciones , en el menú contextual del archivo **SDKManifest.xml,** elija **Propiedades**.

11. En la ventana **Propiedades,** establezca la propiedad **Incluir en VSIX en** **True**.

12. En el **Explorador**de soluciones , en el menú contextual del proyecto **SimpleMathVSIX** , elija **Agregar** > **nueva carpeta**y, a continuación, asigne un nombre a la carpeta `Redist`.

13. Agregue subcarpetas en Redist para crear esta estructura de carpetas:

     *•Redist,CommonConfiguration, Neutral, SimpleMath, js\\*

14. En el menú contextual de la carpeta **.js\\ ** , elija **Agregar** > **nuevo elemento**.

15. En **Elementos de Visual C,** seleccione la categoría **Web** y, a continuación, seleccione el elemento **Archivo de JavaScript.** Asigne un `arithmetic.js`nombre al archivo y, a continuación, elija el botón **Agregar.**

16. Inserte el siguiente código en *arithmetic.js:*

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

17. En **el Explorador**de soluciones , en el menú contextual del archivo **arithmetic.js,** elija **Propiedades**. Realice estos cambios de propiedad:

    - Establezca la propiedad **Incluir en VSIX en** **True**.

    - Establezca la propiedad **Copiar en directorio** de salida en Copiar **siempre**.

18. En **el Explorador**de soluciones , en el menú contextual del proyecto **SimpleMathVSIX,** elija **Compilar**.

19. Una vez completada correctamente la compilación, en el menú contextual del proyecto, elija **Abrir carpeta en**el Explorador de archivos . Navegue a **la\\opción de depuración**y ejecútela `SimpleMathVSIX.vsix` para instalarlo.

20. Elija el botón **Instalar** y deje que la instalación se complete.

21. Reinicie Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a>Para crear una aplicación de ejemplo que use el SDK

1. En la barra de menús, elija **Archivo** > **nuevo** > **proyecto**.

2. En la lista de categorías de plantilla, en **JavaScript**, seleccione **Tienda Windows**y, a continuación, seleccione la plantilla Aplicación **en blanco.**

3. En el cuadro `ArithmeticUI` **Nombre,** especifique . Elija el botón **Aceptar** .

4. En el **Explorador**de soluciones , abra el menú contextual del proyecto **ArithmeticUI** y, a continuación, elija **Agregar** > **referencia**.

5. En **Windows**, elija **Extensiones**y observe que se muestra **Simple Math.**

6. Active la casilla de verificación **Simple Math (Matemáticasimple)** y, a continuación, elija el botón **OK (Aceptar).**

7. En **el Explorador**de soluciones , en **Referencias**, observe que se muestra la referencia **Simple Math.** Expándalo y observe que hay una carpeta **.js\\ ** que incluye **arithmetic.js**. Puede abrir **arithmetic.js** para confirmar que se ha instalado el código fuente.

8. Utilice el código siguiente para reemplazar el contenido de *default.htm*.

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

9. Utilice el código siguiente para reemplazar el contenido de *.js.default.js*.

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

10. Sustituya el contenido de la dirección de *archivo .css-default.css* por este código:

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

12. En la interfaz de usuario de la aplicación, **=** escriba dos números, seleccione una operación y, a continuación, elija el botón. Aparece el resultado correcto.

## <a name="see-also"></a>Vea también
- [Creación de un kit de desarrollo de software](../extensibility/creating-a-software-development-kit.md)
