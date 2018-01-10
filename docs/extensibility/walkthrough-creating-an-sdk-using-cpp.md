---
title: 'Tutorial: Crear un SDK usando C++ | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: "32"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7a4091506bcd16222ff02600bd924d3526d57c38
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2018
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Tutorial: Crear un SDK usando C++
Este tutorial muestra cómo crear una biblioteca nativa de C++ matemáticas SDK, el paquete del SDK como una extensión Visual de Studio (VSIX) y, a continuación, usarla para crear una aplicación. El tutorial está dividido en estos pasos:  
  
-   [Para crear la enumeración nativa y bibliotecas en tiempo de ejecución de Windows](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Para crear el proyecto de extensión NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Para crear una aplicación de ejemplo que utiliza la biblioteca de clases](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a>Para crear la enumeración nativa y bibliotecas en tiempo de ejecución de Windows  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En la lista de plantillas, expanda **Visual C++**, **universales de Windows**y, a continuación, seleccione la **DLL (aplicaciones universales de Windows)** plantilla. En el **nombre** , especifique `NativeMath`y, a continuación, elija la **Aceptar** botón.  
  
3.  Actualizar NativeMath.h para que coincida con el código siguiente.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  Actualizar NativeMath.cpp para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  En **el Explorador de soluciones**, abra el menú contextual para **solución 'NativeMath'**y, a continuación, elija **agregar**, **nuevo proyecto**.  
  
6.  En la lista de plantillas, expanda **Visual C++**y, a continuación, seleccione la **componente de Windows en tiempo de ejecución** plantilla. En el **nombre** , especifique `NativeMathWRT`y, a continuación, elija la **Aceptar** botón.  
  
7.  Actualizar Class1.h para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  Actualizar Class1.cpp para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
##  <a name="createVSIX"></a>Para crear el proyecto de extensión NativeMathVSIX  
  
1.  En **el Explorador de soluciones**, abra el menú contextual para **solución 'NativeMath'**y, a continuación, elija **agregar**, **nuevo proyecto**.  
  
2.  En la lista de plantillas, expanda **Visual C#**, **extensibilidad**y, a continuación, seleccione **proyecto VSIX**. En el **nombre** , especifique **NativeMathVSIX**y, a continuación, elija la **Aceptar** botón.
  
3.  En **el Explorador de soluciones**, abra el menú contextual para **source.extension.vsixmanifest**y, a continuación, elija **ver código**.  
  
4.  Utilice el siguiente código XML para reemplazar el código XML existente.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

5.  En **el Explorador de soluciones**, abra el menú contextual para el **NativeMathVSIX** del proyecto y, a continuación, elija **agregar**, **nuevo elemento**.  
  
6.  En la lista de **elementos de Visual C#**, expanda **datos**y, a continuación, seleccione **archivo XML**. En el **nombre** , especifique `SDKManifest.xml`y, a continuación, elija la **Aceptar** botón.  
  
7.  Use este código XML para reemplazar el contenido del archivo:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
8. En **el Explorador de soluciones**, en la **NativeMathVSIX** proyecto de equipo y crear esta estructura de carpetas:  
  
    ```  
  
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
  
9. En **el Explorador de soluciones**, abra el menú contextual para **solución 'NativeMath'**y, a continuación, elija **Abrir carpeta en el Explorador de archivos**.  
  
10. En **Explorador de archivos**, copie $SolutionRoot$\NativeMath\NativeMath.h y, a continuación, en **el Explorador de soluciones**, en la **NativeMathVSIX** proyecto de equipo y péguelo en el $SolutionRoot$ \ Carpeta NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include\.  
  
     Copie $SolutionRoot$\Debug\NativeMath\NativeMath.lib y, a continuación, péguelo en la carpeta de \NativeMathVSIX\DesignTime\Debug\x86\ $SolutionRoot$.  
  
     Copie $SolutionRoot$\Debug\NativeMath\NativeMath.dll y péguelo en la carpeta de \NativeMathVSIX\Redist\Debug\x86\ $SolutionRoot$.  
  
     Copie $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.dll y péguelo en la carpeta de \NativeMathVSIX\Redist\Debug\x86 $SolutionRoot$.  
  
     Copie $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.winmd y péguelo en la carpeta de \NativeMathVSIX\References\CommonConfiguration\Neutral $SolutionRoot$.  
  
     Copie $SolutionRoot$\Debug\NativeMathWRT\NativeMathWRT.pri y péguelo en la carpeta de \NativeMathVSIX\References\CommonConfiguration\Neutral $SolutionRoot$.  
  
11. En la carpeta de \NativeMathVSIX\DesignTime\Debug\x86\ $SolutionRoot$, cree un archivo de texto denominado NativeMathSDK.props y, a continuación, pegue el siguiente contenido en ella:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
12. En la barra de menús, elija **vista**, **otras ventanas**, **ventana propiedades** (teclado: elija la tecla F4).  
  
13. En **el Explorador de soluciones**, seleccione la **NativeMathWRT.winmd** archivo. En el **propiedades** ventana, cambiar la **acción de compilación** propiedad **contenido**y, a continuación, cambie la **incluir en VSIX** propiedad  **True**.  
  
     Repita este proceso para el **NativeMath.h** archivo.  
  
     Repita este proceso para el **NativeMathWRT.pri** archivo.  
  
     Repita este proceso para el **NativeMath.Lib** archivo.  
  
     Repita este proceso para el **NativeMathSDK.props** archivo.  
  
14. En **el Explorador de soluciones**, seleccione la **NativeMath.h** archivo. En el **propiedades** ventana, cambiar la **incluir en VSIX** propiedad **True**.  
  
     Repita este proceso para el **NativeMath.dll** archivo.  
  
     Repita este proceso para el **NativeMathWRT.dll** archivo.  
  
     Repita este proceso para el **SDKManifest.xml** archivo.  
  
15. En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
16. En **el Explorador de soluciones**, abra el menú contextual para el **NativeMathVSIX** del proyecto y, a continuación, elija **Abrir carpeta en el Explorador de archivos**.  
  
17. En **Explorador de archivos**, navegue hasta la carpeta de \NativeMathVSIX\bin\Debug\ $SolutionRoot$ y, a continuación, ejecute NativeMathVSIX.vsix para iniciar la instalación.  
  
18. Elija la **instalar** botón, espere a que finalice la instalación y, a continuación, inicie Visual Studio.  
  
##  <a name="createSample"></a>Para crear una aplicación de ejemplo que utiliza la biblioteca de clases  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En la lista de plantillas, expanda **Visual C++**, **universales de Windows**y, a continuación, seleccione **aplicación vacía**. En el **nombre** , especifique **NativeMathSDKSample**y, a continuación, elija la **Aceptar** botón.  
  
3.  En **el Explorador de soluciones**, abra el menú contextual para el **NativeMathSDKSample** del proyecto y, a continuación, elija **agregar**, **referencia**.  
  
4.  En el **Agregar referencia** cuadro de diálogo, en la lista de tipos de referencia, expanda **Windows Universal**y, a continuación, seleccione **extensiones**. Por último, seleccione la **nativo SDK matemáticas** casilla de verificación y, a continuación, elija la **Aceptar** botón.
  
5.  Mostrar las propiedades del proyecto para NativeMathSDKSample.  
  
     Las propiedades que definen en NativeMathSDK.props se aplicaron cuando se agrega la referencia. Puede comprobarlo mediante el examen de la **directorios de VC ++** propiedad del proyecto **propiedades de configuración**.  
  
6.  En **el Explorador de soluciones**, abra el archivo MainPage.xaml y, a continuación, utilice el siguiente código XAML para reemplazar su contenido:  
  
     [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
7.  Actualizar Mainpage.xaml.h para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
8. Actualizar MainPage.xaml.cpp para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
9. Presione la tecla F5 para ejecutar la aplicación.  
  
10. En la aplicación, escriba los dos números, seleccione una operación y, a continuación, elija la  **=**  botón.  
  
     Aparece el resultado correcto.  
  
 En este tutorial se ha explicado cómo crear y usar un SDK de extensión para llamar a un [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteca y no[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteca.  
  
## <a name="next-steps"></a>Pasos siguientes  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Crear un SDK usando C# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Creación de un kit de desarrollo de software](../extensibility/creating-a-software-development-kit.md)