---
title: 'Tutorial: Creación de un SDK con C++ Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65643e65490eacb79eea4d76aa49ff10d6cccf66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697627"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Tutorial: Crear un SDK con C++
En este tutorial se muestra cómo crear un SDK de biblioteca matemática nativo de C++, empaquetar el SDK como una extensión de Visual Studio (VSIX) y, a continuación, usarlo para crear una aplicación. El tutorial se divide en estos pasos:

- [Para crear las bibliotecas nativas y de Windows runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Para crear el proyecto de extensión NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Para crear una aplicación de ejemplo que use la biblioteca de clases](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Prerrequisitos
 Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea SDK de [Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>Para crear las bibliotecas nativas y de Windows runtime

1. En la barra de menús, elija **Archivo** > **nuevo** > **proyecto**.

2. En la lista de plantillas, expanda **Visual C++** > **Windows Universal**y, a continuación, seleccione la plantilla DLL **(aplicaciones universales** de Windows). En el cuadro `NativeMath` **Nombre,** especifique y, a continuación, elija el botón **Aceptar.**

3. Actualice *NativeMath.h* para que coincida con el código siguiente.

     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]

4. Actualice *NativeMath.cpp* para que coincida con este código:

     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]

5. En el **Explorador**de soluciones , abra el menú contextual **de la solución 'NativeMath'** y, a continuación, elija **Agregar** > **nuevo proyecto**.

6. En la lista de plantillas, expanda **Visual C++** y, a continuación, seleccione la plantilla Componente de Windows en tiempo de **ejecución.** En el cuadro `NativeMathWRT` **Nombre,** especifique y, a continuación, elija el botón **Aceptar.**

7. Actualice *Class1.h* para que coincida con este código:

     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]

8. Actualice *Class1.cpp* para que coincida con este código:

     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]

9. En la barra de menús, elija **Compilar** > **Compilar solución**.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a>Para crear el proyecto de extensión NativeMathVSIX

1. En el **Explorador**de soluciones , abra el menú contextual **de la solución 'NativeMath'** y, a continuación, elija **Agregar** > **nuevo proyecto**.

2. En la lista de plantillas, expanda**Extensibilidad**de **Visual C-** > y, a continuación, seleccione **Proyecto VSIX**. En el cuadro **Nombre,** especifique **NativeMathVSIX**y, a continuación, elija el botón **Aceptar.**

3. En el **Explorador**de soluciones , abra el menú contextual **de source.extension.vsixmanifest**y, a continuación, elija **Ver código**.

4. Utilice el siguiente XML para reemplazar el XML existente.

    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5. En el **Explorador**de soluciones , abra el menú contextual del proyecto **NativeMathVSIX** y, a continuación, elija **Agregar** > **nuevo elemento**.

6. En la lista de elementos de **Visual C,** expanda **Datos**y, a continuación, seleccione **Archivo XML**. En el cuadro `SDKManifest.xml` **Nombre,** especifique y, a continuación, elija el botón **Aceptar.**

7. Utilice este XML para reemplazar el contenido del archivo:

     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]

8. En **el Explorador**de soluciones , en el proyecto **NativeMathVSIX,** cree esta estructura de carpetas:

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

9. En el **Explorador**de soluciones , abra el menú contextual **de la solución 'NativeMath'** y, a continuación, elija **Abrir carpeta en el Explorador**de archivos .

10. En el **Explorador**de archivos , copie *$SolutionRoot$ , NativeMath , NativeMath .h*y, a continuación, en el **Explorador**de soluciones , en el proyecto **NativeMathVSIX** , péguelo en la carpeta *$SolutionRoot$-NativeMathVSIX-DesignTime-CommonConfiguration-Neutral-Include.\\ *

     Copiar *$SolutionRoot$-Debug-NativeMath-NativeMath.lib*y, a continuación, pegarlo en la carpeta *$SolutionRoot$-NativeMathVSIX-DesignTime-Debug-x86.\\ *

     Copiar *$SolutionRoot$-Debug-NativeMath-NativeMath.dll* y pegarlo en la carpeta *$SolutionRoot$-NativeMathVSIX-Redist-Debug-x86.\\ *

     Copie *$SolutionRoot$-Debug-NativeMathWRT-NativeMathWRT.dll* y péguelo en la carpeta *$SolutionRoot$-NativeMathVSIX-Redist-Debug-x86.*
     Copiar *$SolutionRoot$-Debug-NativeMathWRT-NativeMathWRT.winmd* y péguelo en la carpeta *$SolutionRoot$-NativeMathVSIX-References-CommonConfiguration-Neutral.*

     Copiar *$SolutionRoot$-Debug-NativeMathWRT-NativeMathWRT.pri* y pegarlo en la carpeta *$SolutionRoot$-NativeMathVSIX-References-CommonConfiguration-Neutral.*

11. En la carpeta *$SolutionRoot$-NativeMathVSIX-DesignTime-Debug-x86,\\ * cree un archivo de texto denominado *NativeMathSDK.props*y, a continuación, pegue el siguiente contenido en él:

    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]

12. En la barra de menús, elija Ver**la** > ventana **Otras** > **propiedades** de Windows (Teclado: elija la tecla **F4).**

13. En el Explorador de **soluciones**, seleccione el archivo **NativeMathWRT.winmd.** En la ventana **Propiedades** , cambie la propiedad Acción de **compilación** a **Contenido**y, a continuación, cambie la propiedad **Incluir en VSIX** a **True**.

     Repita este proceso para el archivo **NativeMath.h.**

     Repita este proceso para el archivo **NativeMathWRT.pri.**

     Repita este proceso para el archivo **NativeMath.Lib.**

     Repita este proceso para el archivo **NativeMathSDK.props.**

14. En el Explorador de **soluciones**, seleccione el archivo **NativeMath.h.** En la ventana **Propiedades,** cambie la propiedad **Incluir en VSIX** a **True**.

     Repita este proceso para el archivo **NativeMath.dll.**

     Repita este proceso para el archivo **NativeMathWRT.dll.**

     Repita este proceso para el archivo **SDKManifest.xml.**

15. En la barra de menús, elija **Compilar** > **Compilar solución**.

16. En el **Explorador**de soluciones , abra el menú contextual del proyecto **NativeMathVSIX** y, a continuación, elija **Abrir carpeta en el Explorador**de archivos .

17. En el **Explorador**de archivos , desplácese hasta la carpeta *$SolutionRoot$-NativeMathVSIX-bin-Debug* y, a continuación, ejecute *NativeMathVSIX.vsix* para iniciar la instalación.

18. Elija el botón **Instalar,** espere a que finalice la instalación y, a continuación, abra Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Para crear una aplicación de ejemplo que use la biblioteca de clases

1. En la barra de menús, elija **Archivo** > **nuevo** > **proyecto**.

2. En la lista de plantillas, expanda **Visual C++** > **Windows Universal** y, a continuación, seleccione Aplicación en **blanco**. En el cuadro **Nombre** , especifique **NativeMathSDKSample**y, a continuación, elija el botón **Aceptar.**

3. En el **Explorador**de soluciones , abra el menú contextual del proyecto **NativeMathSDKSample** y, a continuación, elija **Agregar** > **referencia**.

4. En el cuadro de diálogo **Agregar referencia,** en la lista de tipos de referencia, expanda **Windows universal**y, a continuación, seleccione **Extensiones**. Por último, active la casilla de verificación **Native Math SDK** y, a continuación, elija el botón **Aceptar.**

5. Mostrar las propiedades del proyecto para NativeMathSDKSample.

    Las propiedades que definió en *NativeMathSDK.props* se aplicaron al agregar la referencia. Puede comprobar que las propiedades se aplicaron examinando la propiedad **Directorios VC++** de las Propiedades de **configuración**del proyecto .

6. En **el Explorador**de soluciones , abra **MainPage.xaml**y, a continuación, use el siguiente XAML para reemplazar su contenido:

    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]

7. Actualice *Mainpage.xaml.h* para que coincida con este código:

    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]

8. Actualice *MainPage.xaml.cpp* para que coincida con este código:

     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]

9. Elija la tecla **F5** para ejecutar la aplicación.

10. En la aplicación, escriba dos números, seleccione **=** una operación y, a continuación, elija el botón.

     Aparece el resultado correcto.

    En este tutorial se muestra cómo crear y [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] usar un[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] SDK de extensión para llamar a una biblioteca y a una biblioteca que no es de biblioteca.

## <a name="next-steps"></a>Pasos siguientes

## <a name="see-also"></a>Vea también
- [Tutorial: Crear un SDK con C o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Crear un kit de desarrollo de software](../extensibility/creating-a-software-development-kit.md)
