---
title: 'Tutorial: Crear un SDK con C++ | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0932759213d064c3df717b7b6735c1201e62ce14
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773475"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Tutorial: Creación de un SDK con C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tutorial muestra cómo crear una biblioteca nativa de C++ matemáticas SDK, el SDK como una extensión de Visual de Studio (VSIX), paquete y, a continuación, usarla para crear una aplicación. El tutorial está dividido en estos pasos:  
  
-   [Para crear la enumeración nativa y bibliotecas en tiempo de ejecución de Windows](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Para crear el proyecto de extensión NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Para crear una aplicación de ejemplo que usa la biblioteca de clases](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createClassLibrary"></a> Para crear la enumeración nativa y bibliotecas en tiempo de ejecución de Windows  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En la lista de plantillas, expanda **Visual C++**, **Windows Store**y, a continuación, seleccione el **DLL (aplicaciones de Windows Store)** plantilla. En el **nombre** , especifique `NativeMath`y, a continuación, elija el **Aceptar** botón.  
  
3.  Actualizar NativeMath.h para que coincida con el código siguiente.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4.  Actualizar NativeMath.cpp para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5.  En **el Explorador de soluciones**, abra el menú contextual para **solución 'NativeMath'** y, a continuación, elija **agregar**, **nuevo proyecto**.  
  
6.  En la lista de plantillas, expanda **Visual C++** y, a continuación, seleccione el **componente de Windows en tiempo de ejecución** plantilla. En el **nombre** , especifique `NativeMathWRT`y, a continuación, elija el **Aceptar** botón.  
  
7.  Actualizar Class1.h para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8.  Actualizar Class1.cpp para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
##  <a name="createVSIX"></a> Para crear el proyecto de extensión NativeMathVSIX  
  
1.  En **el Explorador de soluciones**, abra el menú contextual para **solución 'NativeMath'** y, a continuación, elija **agregar**, **nuevo proyecto**.  
  
2.  En la lista de plantillas, expanda **Visual C#**, **extensibilidad**y, a continuación, seleccione **paquete VSIX**. En el **nombre** , especifique **NativeMathVSIX**y, a continuación, elija el **Aceptar** botón.  
  
3.  Cuando aparezca el Diseñador de manifiestos VSIX, ciérrelo.  
  
4.  En **el Explorador de soluciones**, abra el menú contextual para **source.extension.vsixmanifest**y, a continuación, elija **ver código**.  
  
5.  Utilice el siguiente código XML para reemplazar el documento XML.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6.  En **el Explorador de soluciones**, abra el menú contextual para el **NativeMathVSIX** del proyecto y, a continuación, elija **agregar**, **nuevo elemento**.  
  
7.  En la lista de **elementos de Visual C#**, expanda **datos**y, a continuación, seleccione **archivo XML**. En el **nombre** , especifique `SDKManifest.xml`y, a continuación, elija el **Aceptar** botón.  
  
8.  Use este código XML para reemplazar el contenido del archivo:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. En **el Explorador de soluciones**, en el **NativeMathVSIX** del proyecto, cree esta estructura de carpetas:  
  
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
  
10. En **el Explorador de soluciones**, abra el menú contextual para **solución 'NativeMath'** y, a continuación, elija **Abrir carpeta en el Explorador de archivos**.  
  
11. En **Explorador de archivos**, copie \NativeMath\NativeMath.h y, a continuación, en **el Explorador de soluciones**, en el **NativeMathVSIX** project, péguelo en el \DesignTime\ Carpeta CommonConfiguration\Neutral\Include\.  
  
     Copie \Debug\NativeMath\NativeMath.lib y, a continuación, péguelo en la carpeta \DesignTime\Debug\x86\.  
  
     Copie \Debug\NativeMath\NativeMath.dll y péguelo en la carpeta \Redist\Debug\x86\.  
  
     Copie DebugNativeMathWRTNativeMathWRT.dll y péguelo en la carpeta RedistDebugx86.  
  
     Copie DebugNativeMathWRTNativeMathWRT.winmd y péguelo en la carpeta ReferencesCommonConfigurationNeutral.  
  
     Copie DebugNativeMathWRTNativeMathWRT.pri y péguelo en la carpeta ReferencesCommonConfigurationNeutral.  
  
12. En la carpeta \DesignTime\Debug\x86\, cree un archivo de texto que se denomina NativeMathSDK.props y, a continuación, pegue el siguiente contenido en él:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. En la barra de menús, elija **vista**, **Other Windows**, **ventana propiedades** (teclado: presione la tecla F4).  
  
14. En **el Explorador de soluciones**, seleccione el **NativeMathWRT.winmd** archivo. En el **propiedades** ventana, cambie el **acción de compilación** propiedad **contenido**y, a continuación, cambie el **incluir en VSIX** propiedad  **True**.  
  
     Repita este proceso para el **SimpleMath.pri** archivo.  
  
     Repita este proceso para el **NativeMath.Lib** archivo.  
  
     Repita este proceso para el **NativeMathSDK.props** archivo.  
  
15. En **el Explorador de soluciones**, seleccione el **NativeMath.h** archivo. En el **propiedades** ventana, cambie el **incluir en VSIX** propiedad **True**.  
  
     Repita este proceso para el **NativeMath.dll** archivo.  
  
     Repita este proceso para el **NativeMathWRT.dll** archivo.  
  
     Repita este proceso para el **SDKManifest.xml** archivo.  
  
16. En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
17. En **el Explorador de soluciones**, abra el menú contextual para el **NativeMathVSIX** del proyecto y, a continuación, elija **Abrir carpeta en el Explorador de archivos**.  
  
18. En **Explorador de archivos**, vaya a la carpeta \bin\Debug\ y, a continuación, ejecutar NativeMathVSIX.vsix para comenzar la instalación.  
  
19. Elija la **instalar** button, esperar a que finalice la instalación y, a continuación, reinicie Visual Studio.  
  
##  <a name="createSample"></a> Para crear una aplicación de ejemplo que usa la biblioteca de clases  
  
1. En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2. En la lista de plantillas, expanda **Visual C++**, **Windows Store**y, a continuación, seleccione **aplicación vacía**. En el **nombre** , especifique **NativeMathSDKSample**y, a continuación, elija el **Aceptar** botón.  
  
3. En **el Explorador de soluciones**, abra el menú contextual para el **NativeMathSDKSample** del proyecto y, a continuación, elija **agregar**, **referencia**.  
  
4. En el **propiedades comunes**, **Framework y referencias** página de propiedades, en la lista de tipos de referencia, expanda **Windows**y, a continuación, seleccione **extensiones** . En el panel de detalles, seleccione el **SDK nativo de matemáticas** extensión y, a continuación, elija el **agregar nueva referencia** botón.  
  
5. En el **Agregar referencia** cuadro de diálogo, seleccione el **SDK nativo de matemáticas** casilla de verificación y, a continuación, elija el **Aceptar** botón.  
  
6. Mostrar las propiedades del proyecto para NativeMathSDKSample.  
  
    Las propiedades que definen en NativeMathSDK.props se aplicaron cuando se agrega la referencia. Puede comprobar examinando el **directorios de VC ++** propiedad del proyecto **propiedades de configuración**.  
  
7. En **el Explorador de soluciones**, abra MainPage.xaml y, a continuación, use el siguiente XAML para reemplazar su contenido:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. Actualizar Mainpage.xaml.h para que coincida con este código:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. Actualizar MainPage.xaml.cpp para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. Elija la tecla F5 para ejecutar la aplicación.  
  
11. En la aplicación, escriba los dos números, seleccione una operación y, a continuación, elija el **=** botón.  
  
     Aparece el resultado correcto.  
  
    Este tutorial ha mostrado cómo crear y usar un SDK de extensión para llamar a un [!INCLUDE[wrt](../includes/wrt-md.md)] biblioteca y que no es[!INCLUDE[wrt](../includes/wrt-md.md)] biblioteca.  
  
## <a name="next-steps"></a>Pasos siguientes  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Crear un SDK usando C# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Creación de un kit de desarrollo de software](../extensibility/creating-a-software-development-kit.md)

