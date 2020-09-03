---
title: 'Tutorial: crear un SDK con C++ | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15fa0714097efda31b52f1d389d3a26cf581e506
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905014"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Tutorial: crear un SDK con C++
En este tutorial se muestra cómo crear un SDK de la biblioteca matemática de C++ nativo, empaquetar el SDK como extensión de Visual Studio (VSIX) y usarlo para crear una aplicación. El tutorial se divide en estos pasos:

- [Para crear las bibliotecas nativas y de Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Para crear el proyecto de extensión NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Para crear una aplicación de ejemplo que usa la biblioteca de clases](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Requisitos previos
 Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea el [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a> Para crear las bibliotecas nativas y de Windows Runtime

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

2. En la lista de plantillas, expanda **Visual C++**  >  **universal de Windows**y, a continuación, seleccione la plantilla **dll (aplicaciones universales de Windows)** . En el cuadro **nombre** , especifique `NativeMath` y, a continuación, elija el botón **Aceptar** .

3. Actualice *NativeMath. h* para que coincida con el código siguiente.

     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]

4. Actualice *NativeMath. cpp* para que coincida con este código:

     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]

5. En **Explorador de soluciones**, abra el menú contextual de la **solución ' NativeMath '** y, a continuación, elija **Agregar**  >  **nuevo proyecto**.

6. En la lista de plantillas, expanda **Visual C++** y, a continuación, seleccione la plantilla **componente de Windows Runtime** . En el cuadro **nombre** , especifique `NativeMathWRT` y, a continuación, elija el botón **Aceptar** .

7. Actualice *Class1. h* para que coincida con este código:

     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]

8. Actualice *Class1. cpp* para que coincida con este código:

     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]

9. En la barra de menús, elija **Compilar** > **Compilar solución**.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> Para crear el proyecto de extensión NativeMathVSIX

1. En **Explorador de soluciones**, abra el menú contextual de la **solución ' NativeMath '** y, a continuación, elija **Agregar**  >  **nuevo proyecto**.

2. En la lista de plantillas, expanda extensibilidad de **Visual C#**  >  **Extensibility**y, a continuación, seleccione **proyecto de VSIX**. En el cuadro **nombre** , especifique **NativeMathVSIX**y elija el botón **Aceptar** .

3. En **Explorador de soluciones**, abra el menú contextual de **source. Extension. vsixmanifest**y, a continuación, elija **Ver código**.

4. Utilice el siguiente código XML para reemplazar el XML existente.

    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5. En **Explorador de soluciones**, abra el menú contextual del proyecto **NativeMathVSIX** y, a continuación, elija **Agregar**  >  **nuevo elemento**.

6. En la lista de **elementos de Visual C#**, expanda **datos**y, a continuación, seleccione **archivo XML**. En el cuadro **nombre** , especifique `SDKManifest.xml` y, a continuación, elija el botón **Aceptar** .

7. Use este XML para reemplazar el contenido del archivo:

     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]

8. En **Explorador de soluciones**, en el proyecto **NativeMathVSIX** , cree esta estructura de carpetas:

    ```xml
    \DesignTime
          \CommonConfiguration
                \Neutral
                      \Include
          \Debug
                \x86
    \Redist
          \Debug
                \x86
    \References
          \CommonConfiguration
                \Neutral
    ```

9. En **Explorador de soluciones**, abra el menú contextual de la **solución ' NativeMath '** y, a continuación, elija **Abrir carpeta en el explorador de archivos**.

10. En el **Explorador de archivos**, copie *$SolutionRoot $ \NativeMath\NativeMath.h*y, a continuación, en **Explorador de soluciones**, en el proyecto **NativeMathVSIX** , péguelo en la carpeta * \\ $SolutionRoot $ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include* .

     Copie *$SolutionRoot $ \Debug\NativeMath\NativeMath.lib*y, a continuación, péguelo en la carpeta *$SolutionRoot \\ $ \NativeMathVSIX\DesignTime\Debug\x86* .

     Copie *$SolutionRoot $\Debug\NativeMath\NativeMath.dll* y péguelo en la carpeta *$SolutionRoot $ \NativeMathVSIX\Redist\Debug\x86 \\ * .

     Copie *$SolutionRoot $\Debug\NativeMathWRT\NativeMathWRT.dll* y péguelo en la carpeta *$SolutionRoot $ \NativeMathVSIX\Redist\Debug\x86* .
     Copie *$SolutionRoot $ \Debug\NativeMathWRT\NativeMathWRT.winmd* y péguelo en la carpeta *$SolutionRoot $ \NativeMathVSIX\References\CommonConfiguration\Neutral* .

     Copie *$SolutionRoot $ \Debug\NativeMathWRT\NativeMathWRT.PRI* y péguelo en la carpeta *$SolutionRoot $ \NativeMathVSIX\References\CommonConfiguration\Neutral* .

11. En la carpeta *$SolutionRoot $ \\ \NativeMathVSIX\DesignTime\Debug\x86* , cree un archivo de texto denominado *NativeMathSDK. props*y, a continuación, pegue el siguiente contenido en él:

    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]

12. En la barra de menús, elija **Ver**  >  **otras ventanas**  >  **propiedades** de Windows (teclado: elija la tecla **F4** ).

13. En **Explorador de soluciones**, seleccione el archivo **NativeMathWRT. winmd** . En la ventana **propiedades** , cambie la propiedad **acción de compilación** a **contenido**y, a continuación, cambie la propiedad **incluir en VSIX** a **true**.

     Repita este proceso para el archivo **NativeMath. h** .

     Repita este proceso para el archivo **NativeMathWRT. PRI** .

     Repita este proceso para el archivo **NativeMath. lib** .

     Repita este proceso para el archivo **NativeMathSDK. props** .

14. En **Explorador de soluciones**, seleccione el archivo **NativeMath. h** . En la ventana **propiedades** , cambie la propiedad **incluir en VSIX** a **true**.

     Repita este proceso para el archivo de **NativeMath.dll** .

     Repita este proceso para el archivo de **NativeMathWRT.dll** .

     Repita este proceso para el archivo de **SDKManifest.xml** .

15. En la barra de menús, elija **Compilar** > **Compilar solución**.

16. En **Explorador de soluciones**, abra el menú contextual del proyecto **NativeMathVSIX** y, a continuación, elija **Abrir carpeta en el explorador de archivos**.

17. En el **Explorador de archivos**, vaya a la carpeta *$SolutionRoot $ \NativeMathVSIX\bin\Debug* y, a continuación, ejecute *NativeMathVSIX. vsix* para comenzar la instalación.

18. Elija el botón **instalar** , espere a que finalice la instalación y, a continuación, abra Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Para crear una aplicación de ejemplo que usa la biblioteca de clases

1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.

2. En la lista de plantillas, expanda **Visual C++**  >  **universal de Windows** y, a continuación, seleccione **aplicación en blanco**. En el cuadro **nombre** , especifique **NativeMathSDKSample**y elija el botón **Aceptar** .

3. En **Explorador de soluciones**, abra el menú contextual del proyecto **NativeMathSDKSample** y, a continuación, elija **Agregar**  >  **referencia**.

4. En el cuadro de diálogo **Agregar referencia** , en la lista de tipos de referencia, expanda **universal Windows**y, a continuación, seleccione **extensiones**. Por último, active la casilla **SDK de Math nativo** y, a continuación, elija el botón **Aceptar** .

5. Muestra las propiedades del proyecto para NativeMathSDKSample.

    Las propiedades que definió en *NativeMathSDK. props* se aplicaron al agregar la referencia. Puede comprobar que las propiedades se aplicaron examinando la propiedad **directorios de VC + +** de las **propiedades de configuración**del proyecto.

6. En **Explorador de soluciones**, Abra **mainpage. Xaml**y, a continuación, use el siguiente código XAML para reemplazar su contenido:

    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]

7. Actualice *mainpage. Xaml. h* para que coincida con este código:

    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]

8. Actualice *mainpage. Xaml. cpp* para que coincida con este código:

     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]

9. Elija la tecla **F5** para ejecutar la aplicación.

10. En la aplicación, escriba dos números cualesquiera, seleccione una operación y, a continuación, elija el **=** botón.

     Aparece el resultado correcto.

    En este tutorial se ha mostrado cómo crear y usar un SDK de extensión para llamar a una [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteca y a una biblioteca que no es de [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] .

## <a name="next-steps"></a>Pasos siguientes

## <a name="see-also"></a>Consulte también
- [Tutorial: crear un SDK mediante C# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Crear un kit de desarrollo de software](../extensibility/creating-a-software-development-kit.md)
