---
title: 'Tutorial: Crear un SDK con C++ | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6311526df299da860c829520a2087ecc8d786600
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930653"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Tutorial: Crear un SDK con C++
Este tutorial muestra cómo crear una biblioteca nativa de C++ matemáticas SDK, el SDK como una extensión de Visual de Studio (VSIX), paquete y, a continuación, usarla para crear una aplicación. El tutorial está dividido en estos pasos:  
  
-   [Para crear la enumeración nativa y bibliotecas en tiempo de ejecución de Windows](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Para crear el proyecto de extensión NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Para crear una aplicación de ejemplo que usa la biblioteca de clases](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> Para crear la enumeración nativa y bibliotecas en tiempo de ejecución de Windows  
  
1.  En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.  
  
2.  En la lista de plantillas, expanda **Visual C++** > **Windows Universal**y, a continuación, seleccione el **DLL (aplicaciones universales de Windows)** plantilla. En el **nombre** , especifique `NativeMath`y, a continuación, elija el **Aceptar** botón.  
  
3.  Actualización *NativeMath.h* para que coincida con el código siguiente.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  Actualización *NativeMath.cpp* para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  En **el Explorador de soluciones**, abra el menú contextual para **solución 'NativeMath'** y, a continuación, elija **agregar** > **nuevo proyecto**.  
  
6.  En la lista de plantillas, expanda **Visual C++** y, a continuación, seleccione el **componente de Windows en tiempo de ejecución** plantilla. En el **nombre** , especifique `NativeMathWRT`y, a continuación, elija el **Aceptar** botón.  
  
7.  Actualización *Class1.h* para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  Actualización *Class1.cpp* para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. En la barra de menús, elija **Compilar** > **Compilar solución**.  
  
##  <a name="createVSIX"></a> Para crear el proyecto de extensión NativeMathVSIX  
  
1.  En **el Explorador de soluciones**, abra el menú contextual para **solución 'NativeMath'** y, a continuación, elija **agregar** > **nuevo proyecto**.  
  
2.  En la lista de plantillas, expanda **Visual C#** > **extensibilidad**y, a continuación, seleccione **proyecto VSIX**. En el **nombre** , especifique **NativeMathVSIX**y, a continuación, elija el **Aceptar** botón.
  
3.  En **el Explorador de soluciones**, abra el menú contextual para **source.extension.vsixmanifest**y, a continuación, elija **ver código**.  
  
4.  Utilice el siguiente código XML para reemplazar el documento XML.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5.  En **el Explorador de soluciones**, abra el menú contextual para el **NativeMathVSIX** del proyecto y, a continuación, elija **agregar** > **nuevo elemento**.  
  
6.  En la lista de **elementos de Visual C#**, expanda **datos**y, a continuación, seleccione **archivo XML**. En el **nombre** , especifique `SDKManifest.xml`y, a continuación, elija el **Aceptar** botón.  
  
7.  Use este código XML para reemplazar el contenido del archivo:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
8. En **el Explorador de soluciones**, en el **NativeMathVSIX** del proyecto, cree esta estructura de carpetas:  
  
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
  
9. En **el Explorador de soluciones**, abra el menú contextual para **solución 'NativeMath'** y, a continuación, elija **Abrir carpeta en el Explorador de archivos**.  
  
10. En **Explorador de archivos**, copia *$SolutionRoot$\NativeMath\NativeMath.h*y, a continuación, en **el Explorador de soluciones**, en el **NativeMathVSIX**del proyecto, péguelo en el *$SolutionRoot$ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include\\*  carpeta.  
  
     Copia *$SolutionRoot$\Debug\NativeMath\NativeMath.lib*y, a continuación, péguelo en el *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\*  carpeta.  
  
     Copia *$SolutionRoot$\Debug\NativeMath\NativeMath.dll* y péguelo en el *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86\\*  carpeta.  
  
     Copia *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll* y péguelo en el *$SolutionRoot$ \NativeMathVSIX\Redist\Debug\x86* carpeta.  
     Copia *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd* y péguelo en el *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral* carpeta.  
  
     Copia *$SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri* y péguelo en el *$SolutionRoot$ \NativeMathVSIX\References\CommonConfiguration\Neutral* carpeta.  
  
11. En el *$SolutionRoot$ \NativeMathVSIX\DesignTime\Debug\x86\\*  carpeta, cree un archivo de texto que se denomina *NativeMathSDK.props*y, a continuación, pegue el siguiente contenido en él:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
12. En la barra de menús, elija **vista** > **Other Windows** > **ventana propiedades** (teclado: elija la **F4**clave).  
  
13. En **el Explorador de soluciones**, seleccione el **NativeMathWRT.winmd** archivo. En el **propiedades** ventana, cambie el **acción de compilación** propiedad **contenido**y, a continuación, cambie el **incluir en VSIX** propiedad  **True**.  
  
     Repita este proceso para el **NativeMath.h** archivo.  
  
     Repita este proceso para el **NativeMathWRT.pri** archivo.  
  
     Repita este proceso para el **NativeMath.Lib** archivo.  
  
     Repita este proceso para el **NativeMathSDK.props** archivo.  
  
14. En **el Explorador de soluciones**, seleccione el **NativeMath.h** archivo. En el **propiedades** ventana, cambie el **incluir en VSIX** propiedad **True**.  
  
     Repita este proceso para el **NativeMath.dll** archivo.  
  
     Repita este proceso para el **NativeMathWRT.dll** archivo.  
  
     Repita este proceso para el **SDKManifest.xml** archivo.  
  
15. En la barra de menús, elija **Compilar** > **Compilar solución**.  
  
16. En **el Explorador de soluciones**, abra el menú contextual para el **NativeMathVSIX** del proyecto y, a continuación, elija **Abrir carpeta en el Explorador de archivos**.  
  
17. En **Explorador de archivos**, navegue hasta la *$SolutionRoot$ \NativeMathVSIX\bin\Debug* carpeta y, a continuación, ejecute *NativeMathVSIX.vsix* para comenzar la instalación.  
  
18. Elija la **instalar** button, esperar a que finalice la instalación y, a continuación, inicie Visual Studio.  
  
##  <a name="createSample"></a> Para crear una aplicación de ejemplo que usa la biblioteca de clases  
  
1. En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.  
  
2. En la lista de plantillas, expanda **Visual C++** > **Windows Universal** y, a continuación, seleccione **aplicación vacía**. En el **nombre** , especifique **NativeMathSDKSample**y, a continuación, elija el **Aceptar** botón.  
  
3. En **el Explorador de soluciones**, abra el menú contextual para el **NativeMathSDKSample** del proyecto y, a continuación, elija **agregar** > **referencia**.  
  
4. En el **Agregar referencia** cuadro de diálogo, en la lista de tipos de referencia, expanda **Windows Universal**y, a continuación, seleccione **extensiones**. Por último, seleccione el **SDK nativo de matemáticas** casilla de verificación y, a continuación, elija el **Aceptar** botón.
  
5. Mostrar las propiedades del proyecto para NativeMathSDKSample.  
  
    Las propiedades que definen en *NativeMathSDK.props* se aplicaron cuando se agrega la referencia. Puede comprobar las propiedades que se aplicaron examinando el **directorios de VC ++** propiedad del proyecto **propiedades de configuración**.  
  
6. En **el Explorador de soluciones**, abra **MainPage.xaml**y, a continuación, use el siguiente XAML para reemplazar su contenido:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
7. Actualización *Mainpage.xaml.h* para que coincida con este código:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
8. Actualización *MainPage.xaml.cpp* para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
9. Elija la **F5** clave para ejecutar la aplicación.  
  
10. En la aplicación, escriba los dos números, seleccione una operación y, a continuación, elija el **=** botón.  
  
     Aparece el resultado correcto.  
  
    Este tutorial ha mostrado cómo crear y usar un SDK de extensión para llamar a un [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteca y que no es[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteca.  
  
## <a name="next-steps"></a>Pasos siguientes  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Crear un SDK usando C# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Crear un kit de desarrollo de software](../extensibility/creating-a-software-development-kit.md)
