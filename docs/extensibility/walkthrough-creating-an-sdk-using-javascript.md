---
title: 'Tutorial: Creación de un SDK con JavaScript | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f15dc7ef3c5ab06857307081511f1c9aa2285566
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796348"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>Tutorial: Crear un SDK con JavaScript
En este tutorial se enseña cómo usar JavaScript para crear un simple cálculo matemático SDK como una extensión de Visual Studio (VSIX).  El tutorial está dividido en estas partes:

- [Para crear el proyecto SDK de extensión SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [Para crear una aplicación de ejemplo que usa el SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  Para JavaScript, no hay ningún tipo de proyecto de biblioteca de clases. En este tutorial, el ejemplo *arithmetic.js* se crea el archivo directamente en el proyecto VSIX. En la práctica, se recomienda que primero compila y probar los archivos JavaScript y CSS como una aplicación de Windows Store, por ejemplo, mediante el uso de la **aplicación vacía** plantilla — antes de colocarlos en un proyecto de VSIX.

## <a name="prerequisites"></a>Requisitos previos
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="createSimpleMathVSIX"></a> Para crear el proyecto SDK de extensión SimpleMathVSIX

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

2. En la lista de categorías de plantillas, en **Visual C#**, seleccione **extensibilidad**y, a continuación, seleccione el **proyecto VSIX** plantilla.

3. En el **nombre** texto, especifique `SimpleMathVSIX` y elija el **Aceptar** botón.

4. Si el **Asistente para paquetes de Visual Studio** aparece, elija el **siguiente** situado en la **bienvenida** página y, a continuación, en **página 1 de 7**, elija el **Finalizar** botón.

     Aunque el **Diseñador de manifiestos** se abre, mantendremos en este tutorial sencillo modificando directamente el archivo de manifiesto.

5. En **el Explorador de soluciones**, abra el menú contextual para el **source.extension.vsixmanifest** de archivo y, a continuación, elija **ver código**. Use este código para reemplazar el contenido existente en el archivo.

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

6. En **el Explorador de soluciones**, abra el menú contextual para el **SimpleMathVSIX** del proyecto y, a continuación, elija **agregar** > **nuevo elemento**.

7. En el **datos** categoría, seleccione **archivo XML**, asigne el nombre `SDKManifest.xml`y elija el **agregar** botón.

8. En **el Explorador de soluciones**, abra el menú contextual para el **SDKManifest.xml** de archivo y, a continuación, elija **abrir** para mostrar el archivo en el **Editor XML**.

9. Agregue el código siguiente a la **SDKManifest.xml** archivo.

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

10. En **el Explorador de soluciones**, en el menú contextual para el **SDKManifest.xml** de archivos, elija **propiedades**.

11. En el **propiedades** ventana, establezca el **incluir en VSIX** propiedad **True**.

12. En **el Explorador de soluciones**, en el menú contextual para el **SimpleMathVSIX** del proyecto, elija **agregar** > **nueva carpeta**, y a continuación, nombre de la carpeta `Redist`.

13. Agregue las subcarpetas de redistribución para crear esta estructura de carpetas:

     *\Redist\CommonConfiguration\Neutral\SimpleMath\js\\*

14. En el menú contextual para el **\js\\**  carpeta, elija **agregar** > **nuevo elemento**.

15. En **elementos de Visual C#**, seleccione el **Web** categoría y, a continuación, seleccione el **archivo JavaScript** elemento. Nombre del archivo `arithmetic.js`y, a continuación, elija el **agregar** botón.

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

17. En **el Explorador de soluciones**, en el menú contextual para el **arithmetic.js** de archivos, elija **propiedades**. Realice estos cambios de propiedad:

    - Establecer el **incluir en VSIX** propiedad **True**.

    - Establecer el **Copy to Output Directory** propiedad **copiar siempre**.

18. En **el Explorador de soluciones**, en el menú contextual para el **SimpleMathVSIX** del proyecto, elija **compilar**.

19. Después de la compilación se completa correctamente, en el menú contextual para el proyecto, elija **Abrir carpeta en el Explorador de archivos**. Vaya a **\bin\debug\\**y ejecute `SimpleMathVSIX.vsix` para instalarlo.

20. Elija la **instalar** botón y permiten la instalación completa.

21. Reinicie Visual Studio.

## <a name="createSampleApp"></a> Para crear una aplicación de ejemplo que usa el SDK

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

2. En la lista de categorías de plantillas, en **JavaScript**, seleccione **Windows Store**y, a continuación, seleccione el **aplicación vacía** plantilla.

3. En el **nombre** , especifique `ArithmeticUI`. Elija el botón **Aceptar** .

4. En **el Explorador de soluciones**, abra el menú contextual para el **ArithmeticUI** del proyecto y, a continuación, elija **agregar** > **referencia**.

5. En **Windows**, elija **extensiones**y tenga en cuenta que **Simple cálculo matemático** se muestra.

6. Seleccione el **Simple cálculo matemático** casilla de verificación y, a continuación, elija el **Aceptar** botón.

7. En **el Explorador de soluciones**, en **referencias**, tenga en cuenta que el **Simple cálculo matemático** referencia se muestra. Expandirla y observe que hay un **\js\\**  carpeta que incluye **arithmetic.js**. Puede abrir **arithmetic.js** para confirmar que el código fuente se ha instalado.

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

10. Reemplace el contenido de *\css\default.css* con este código:

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

11. Elija la **F5** clave para compilar y ejecutar la aplicación.

12. En el interfaz de usuario de la aplicación, escriba los dos números, seleccione una operación y, a continuación, elija el **=** botón. Aparece el resultado correcto.

## <a name="see-also"></a>Vea también
- [Crear un Kit de desarrollo de Software](../extensibility/creating-a-software-development-kit.md)
