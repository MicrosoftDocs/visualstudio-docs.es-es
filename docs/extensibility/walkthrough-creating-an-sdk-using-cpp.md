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
ms.openlocfilehash: 065d5b16e99ce7c1356f710ab2a6cc42bbd6cde4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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
  
2.  En la lista de plantillas, expanda **Visual C++**, **tienda Windows**y, a continuación, seleccione la **DLL (aplicaciones de la tienda Windows)** plantilla. En el **nombre** , especifique `NativeMath`y, a continuación, elija la **Aceptar** botón.  
  
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
  
2.  En la lista de plantillas, expanda **Visual C#**, **extensibilidad**y, a continuación, seleccione **paquete VSIX**. En el **nombre** , especifique **NativeMathVSIX**y, a continuación, elija la **Aceptar** botón.  
  
3.  Cuando aparezca el Diseñador de manifiestos VSIX, ciérrela.  
  
4.  En **el Explorador de soluciones**, abra el menú contextual para **source.extension.vsixmanifest**y, a continuación, elija **ver código**.  
  
5.  Utilice el siguiente código XML para reemplazar el código XML existente.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

6.  En **el Explorador de soluciones**, abra el menú contextual para el **NativeMathVSIX** del proyecto y, a continuación, elija **agregar**, **nuevo elemento**.  
  
7.  En la lista de **elementos de Visual C#**, expanda **datos**y, a continuación, seleccione **archivo XML**. En el **nombre** , especifique `SDKManifest.xml`y, a continuación, elija la **Aceptar** botón.  
  
8.  Use este código XML para reemplazar el contenido del archivo:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
9. En **el Explorador de soluciones**, en la **NativeMathVSIX** proyecto de equipo y crear esta estructura de carpetas:  
  
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
  
10. En **el Explorador de soluciones**, abra el menú contextual para **solución 'NativeMath'**y, a continuación, elija **Abrir carpeta en el Explorador de archivos**.  
  
11. En **Explorador de archivos**, copie \NativeMath\NativeMath.h y, a continuación, en **el Explorador de soluciones**, en la **NativeMathVSIX** proyecto de equipo y péguelo en el \DesignTime\ Carpeta CommonConfiguration\Neutral\Include\.  
  
     Copie \Debug\NativeMath\NativeMath.lib y, a continuación, péguelo en la carpeta \DesignTime\Debug\x86\.  
  
     Copie \Debug\NativeMath\NativeMath.dll y péguelo en la carpeta \Redist\Debug\x86\.  
  
     Copie DebugNativeMathWRTNativeMathWRT.dll y péguelo en la carpeta RedistDebugx86.  
  
     Copie DebugNativeMathWRTNativeMathWRT.winmd y péguelo en la carpeta ReferencesCommonConfigurationNeutral.  
  
     Copie DebugNativeMathWRTNativeMathWRT.pri y péguelo en la carpeta ReferencesCommonConfigurationNeutral.  
  
12. En la carpeta \DesignTime\Debug\x86\, cree un archivo de texto denominado NativeMathSDK.props y, a continuación, pegue el siguiente contenido en ella:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. En la barra de menús, elija **vista**, **otras ventanas**, **ventana propiedades** (teclado: elija la tecla F4).  
  
14. En **el Explorador de soluciones**, seleccione la **NativeMathWRT.winmd** archivo. En el **propiedades** ventana, cambiar la **acción de compilación** propiedad **contenido**y, a continuación, cambie la **incluir en VSIX** propiedad  **True**.  
  
     Repita este proceso para el **SimpleMath.pri** archivo.  
  
     Repita este proceso para el **NativeMath.Lib** archivo.  
  
     Repita este proceso para el **NativeMathSDK.props** archivo.  
  
15. En **el Explorador de soluciones**, seleccione la **NativeMath.h** archivo. En el **propiedades** ventana, cambiar la **incluir en VSIX** propiedad **True**.  
  
     Repita este proceso para el **NativeMath.dll** archivo.  
  
     Repita este proceso para el **NativeMathWRT.dll** archivo.  
  
     Repita este proceso para el **SDKManifest.xml** archivo.  
  
16. En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
17. En **el Explorador de soluciones**, abra el menú contextual para el **NativeMathVSIX** del proyecto y, a continuación, elija **Abrir carpeta en el Explorador de archivos**.  
  
18. En **Explorador de archivos**, navegue hasta la carpeta \bin\Debug\ y, a continuación, ejecute NativeMathVSIX.vsix para iniciar la instalación.  
  
19. Elija la **instalar** botón, espere a que finalice la instalación y, a continuación, reinicie Visual Studio.  
  
##  <a name="createSample"></a>Para crear una aplicación de ejemplo que utiliza la biblioteca de clases  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En la lista de plantillas, expanda **Visual C++**, **tienda Windows**y, a continuación, seleccione **aplicación vacía**. En el **nombre** , especifique **NativeMathSDKSample**y, a continuación, elija la **Aceptar** botón.  
  
3.  En **el Explorador de soluciones**, abra el menú contextual para el **NativeMathSDKSample** del proyecto y, a continuación, elija **agregar**, **referencia**.  
  
4.  En el **propiedades comunes**, **Framework y referencias** página de propiedades, en la lista de tipos de referencia, expanda **Windows**y, a continuación, seleccione **extensiones** . En el panel de detalles, seleccione la **nativo SDK matemáticas** extensión y, a continuación, elija la **agregar nueva referencia** botón.  
  
5.  En el **Agregar referencia** cuadro de diálogo, seleccione la **nativo SDK matemáticas** casilla de verificación y, a continuación, elija la **Aceptar** botón.  
  
6.  Mostrar las propiedades del proyecto para NativeMathSDKSample.  
  
     Las propiedades que definen en NativeMathSDK.props se aplicaron cuando se agrega la referencia. Puede comprobarlo mediante el examen de la **directorios de VC ++** propiedad del proyecto **propiedades de configuración**.  
  
7.  En **el Explorador de soluciones**, abra el archivo MainPage.xaml y, a continuación, utilice el siguiente código XAML para reemplazar su contenido:  
  
     [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
8.  Actualizar Mainpage.xaml.h para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
9. Actualizar MainPage.xaml.cpp para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
10. Presione la tecla F5 para ejecutar la aplicación.  
  
11. En la aplicación, escriba los dos números, seleccione una operación y, a continuación, elija la  **=**  botón.  
  
     Aparece el resultado correcto.  
  
 En este tutorial se ha explicado cómo crear y usar un SDK de extensión para llamar a un [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteca y no[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteca.  
  
## <a name="next-steps"></a>Pasos siguientes  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Crear un SDK usando C# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Creación de un kit de desarrollo de software](../extensibility/creating-a-software-development-kit.md)