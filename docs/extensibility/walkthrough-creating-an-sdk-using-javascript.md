---
title: 'Tutorial: Crear un SDK usando JavaScript | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2a53b10f3d9a69c0181a432dad491bebd177f5be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-sdk-using-javascript"></a>Tutorial: Crear un SDK usando JavaScript
En este tutorial se enseña cómo utilizar JavaScript para crear un sencillo matemáticas SDK como una extensión de Visual Studio (VSIX).  El tutorial se divide en las partes siguientes:  
  
-   [Para crear el proyecto SDK de extensión SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)  
  
-   [Para crear una aplicación de ejemplo que usa el SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)  
  
 Para JavaScript, no hay ningún tipo de proyecto de biblioteca de clases. En este tutorial, se crea el archivo de ejemplo arithmetic.js directamente en el proyecto VSIX. En la práctica, se recomienda que primero compilar y probar los archivos JavaScript y CSS como una aplicación de la tienda de Windows, por ejemplo, mediante la **aplicación vacía** plantilla: antes de colocarlos en un proyecto VSIX.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createSimpleMathVSIX"></a>Para crear el proyecto SDK de extensión SimpleMathVSIX  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En la lista de categorías de plantillas, en **Visual C#**, seleccione **extensibilidad**y, a continuación, seleccione la **proyecto VSIX** plantilla.  
  
3.  En el **nombre** texto, especifique `SimpleMathVSIX` y elija la **Aceptar** botón.  
  
4.  Si el **Asistente para paquetes de Visual Studio** aparece, elija la **siguiente** situado en la **bienvenida** página y, a continuación, en **página 1 de 7**, elija la **Finalizar** botón.  
  
     Aunque la **Diseñador de manifiestos** se abre, se conservará en este tutorial simple modificando directamente el archivo de manifiesto.  
  
5.  En **el Explorador de soluciones**, abra el menú contextual del archivo source.extension.vsixmanifest y, a continuación, elija **ver código**. Utilice este código para reemplazar el contenido existente en el archivo.  
  
    ```  
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
  
6.  En **el Explorador de soluciones**, abra el menú contextual para el proyecto SimpleMathVSIX y, a continuación, elija **agregar**, **nuevo elemento**.  
  
7.  En el **datos** categoría, seleccione **archivo XML**, un nombre al archivo `SDKManifest.xml`y elija la **agregar** botón.  
  
8.  En **el Explorador de soluciones**, abra el menú contextual para el archivo SDKManifest.xml y, a continuación, elija **abrir** para mostrar el archivo en el **Editor XML**.  
  
9. Agregue el código siguiente al archivo SDKManifest.xml.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <FileList  
      DisplayName="Simple Math"  
      MinVSVersion="14.0"  
      AppliesTo="JavaScript+WindowsAppContainer"  
      SupportsMultipleVersions="Error"  
      MoreInfo="http://www.msdn.microsoft.com/">  
  
      <!-- JS -->  
      <File Content="js\arithmetic.js" />  
    </FileList>  
  
    ```  
  
10. En **el Explorador de soluciones**, en el menú contextual para el archivo SDKManifest.xml, elija **propiedades**.  
  
11. En el **propiedades** ventana, establezca el **incluir en VSIX** propiedad **True**.  
  
12. En **el Explorador de soluciones**, en el menú contextual para el proyecto SimpleMathVSIX, elija **agregar**, **nueva carpeta**y, a continuación, nombre de la carpeta `Redist`.  
  
13. Agregar subcarpetas de paquetes redistribuibles para crear esta estructura de carpetas:  
  
     \Redist\CommonConfiguration\Neutral\SimpleMath\js\  
  
14. En el menú contextual para la carpeta \js\, elija **agregar**, **nuevo elemento**.  
  
15. En **elementos de Visual C#**, seleccione la **Web** categoría y, a continuación, seleccione la **archivo JavaScript** elemento. Asignar nombre al archivo `arithmetic.js`y, a continuación, elija la **agregar** botón.  
  
16. Inserte el código siguiente en arithmetic.js:  
  
    ```  
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
  
17. En **el Explorador de soluciones**, en el menú contextual para el archivo arithmetic.js, elija **propiedades**. Realice estos cambios de propiedad:  
  
    -   Establecer el **incluir en VSIX** propiedad **True**.  
  
    -   Establecer el **copiar en el directorio de salida** propiedad **copiar siempre**.  
  
18. En **el Explorador de soluciones**, en el menú contextual para el proyecto SimpleMathVSIX, elija **generar**.  
  
19. Cuando la compilación finalice correctamente, en el menú contextual para el proyecto, elija **Abrir carpeta en el Explorador de archivos**. Vaya a \bin\debug\\y ejecute `SimpleMathVSIX.vsix` para instalarlo.  
  
20. Elija la **instalar** botón y permita que la instalación completa.  
  
21. Reinicie Visual Studio.  
  
##  <a name="createSampleApp"></a>Para crear una aplicación de ejemplo que usa el SDK  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En la lista de categorías de plantillas, en **JavaScript**, seleccione **tienda Windows**y, a continuación, seleccione la **aplicación vacía** plantilla.  
  
3.  En el **nombre** , especifique `ArithmeticUI`. Elija el botón **Aceptar** .  
  
4.  En **el Explorador de soluciones**, abra el menú contextual para el proyecto ArithmeticUI y, a continuación, elija **agregar**, **referencia**.  
  
5.  En **Windows**, elija **extensiones**y tenga en cuenta que **matemática Simple** se muestra.  
  
6.  Seleccione el **matemática Simple** casilla de verificación y, a continuación, elija la **Aceptar** botón.  
  
7.  En **el Explorador de soluciones**, en **referencias**, tenga en cuenta que la **matemática Simple** se muestra la referencia. Expandirla y observa que hay una carpeta \js\ que incluye arithmetic.js. También puede abrir arithmetic.js para confirmar que el código fuente se ha instalado.  
  
8.  Utilice el código siguiente para reemplazar el contenido del archivo default.htm.  
  
    ```  
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
  
9. Utilice el código siguiente para reemplazar el contenido de \js\default.js.  
  
    ```  
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
  
10. Reemplace el contenido de \css\default.css con este código:  
  
    ```  
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
  
11. Presione la tecla F5 para compilar y ejecutar la aplicación.  
  
12. En el interfaz de usuario de la aplicación, escriba los dos números, seleccione una operación y, a continuación, elija la  **=**  botón. Aparece el resultado correcto.  
  
## <a name="see-also"></a>Vea también  
 [Creación de un kit de desarrollo de software](../extensibility/creating-a-software-development-kit.md)