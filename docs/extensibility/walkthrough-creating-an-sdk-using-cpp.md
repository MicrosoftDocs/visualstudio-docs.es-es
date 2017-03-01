---
title: 'Tutorial: Crear un SDK usando C++ | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 32
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d4458cb2cf0f3f198b2931beec15f8eead446ba6
ms.openlocfilehash: 3baf914755f0cdd4e0aa0a6c1405126faeec0364
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Tutorial: Crear un SDK con C++
Este tutorial muestra cómo crear una nativo C++ biblioteca matemática SDK, el paquete del SDK como una extensión Visual de Studio (VSIX) y, a continuación, utilizarlo para crear una aplicación. El tutorial está dividido en estos pasos:  
  
-   [Para crear la enumeración nativa y bibliotecas en tiempo de ejecución de Windows](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Para crear el proyecto de extensión NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Para crear una aplicación de ejemplo que utiliza la biblioteca de clases](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para seguir este tutorial, debe instalar el Visual Studio SDK. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
##  <a name="a-namecreateclasslibrarya-to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>Para crear la enumeración nativa y bibliotecas en tiempo de ejecución de Windows  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En la lista de plantillas, expanda **Visual C++**, **tienda Windows**y, a continuación, seleccione la **DLL (aplicaciones de tienda Windows)** plantilla. En el **nombre** , especifique `NativeMath`y, a continuación, elija la **Aceptar** botón.  
  
3.  Actualizar NativeMath.h para que coincida con el código siguiente.  
  
     [!code-cpp[1 CreatingAnSDKUsingCpp](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  Actualizar NativeMath.cpp para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp&#2;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  En **el Explorador de soluciones**, abra el menú contextual de **solución 'NativeMath'**y, a continuación, elija **agregar**, **nuevo proyecto**.  
  
6.  En la lista de plantillas, expanda **Visual C++**y, a continuación, seleccione la **componente de tiempo de ejecución de Windows** plantilla. En el **nombre** , especifique `NativeMathWRT`y, a continuación, elija la **Aceptar** botón.  
  
7.  Actualizar Class1.h para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp&3;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  Actualizar Class1.cpp para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp Nº&4;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
##  <a name="a-namecreatevsixa-to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a>Para crear el proyecto de extensión NativeMathVSIX  
  
1.  En **el Explorador de soluciones**, abra el menú contextual de **solución 'NativeMath'**y, a continuación, elija **agregar**, **nuevo proyecto**.  
  
2.  En la lista de plantillas, expanda **Visual C#**, **extensibilidad**y, a continuación, seleccione **paquete VSIX**. En el **nombre** , especifique **NativeMathVSIX**y, a continuación, elija la **Aceptar** botón.  
  
3.  Cuando aparezca el Diseñador de manifiestos VSIX, ciérrelo.  
  
4.  En **el Explorador de soluciones**, abra el menú contextual de **source.extension.vsixmanifest**y, a continuación, elija **ver código**.  
  
5.  Utilice el siguiente XML para reemplazar el documento XML.  
  
    [!code-xml[CreatingAnSDKUsingCpp Nº&6;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

6.  En **el Explorador de soluciones**, abra el menú contextual para el **NativeMathVSIX** del proyecto y, a continuación, elija **agregar**, **nuevo elemento**.  
  
7.  En la lista de **elementos de Visual C#**, expanda **datos**y, a continuación, seleccione **archivo XML**. En el **nombre** , especifique `SDKManifest.xml`y, a continuación, elija la **Aceptar** botón.  
  
8.  Utilice este código XML para reemplazar el contenido del archivo:  
  
     [!code-xml[CreatingAnSDKUsingCpp&#5;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
9. En **el Explorador de soluciones**, en la **NativeMathVSIX** de proyectos, crear esta estructura de carpetas:  
  
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
  
10. En **el Explorador de soluciones**, abra el menú contextual de **solución 'NativeMath'**y, a continuación, elija **Abrir carpeta en el Explorador de archivos**.  
  
11. En **Explorador de archivos**, copie \NativeMath\NativeMath.h y, a continuación, en **el Explorador de soluciones**, en la **NativeMathVSIX** proyecto, péguelo en la carpeta \DesignTime\CommonConfiguration\Neutral\Include\.  
  
     Copie \Debug\NativeMath\NativeMath.lib y, a continuación, péguelo en la carpeta \DesignTime\Debug\x86\.  
  
     Copie \Debug\NativeMath\NativeMath.dll y péguelo en la carpeta \Redist\Debug\x86\.  
  
     Copie DebugNativeMathWRTNativeMathWRT.dll y péguelo en la carpeta RedistDebugx86.  
  
     Copie DebugNativeMathWRTNativeMathWRT.winmd y péguelo en la carpeta ReferencesCommonConfigurationNeutral.  
  
     Copie DebugNativeMathWRTNativeMathWRT.pri y péguelo en la carpeta ReferencesCommonConfigurationNeutral.  
  
12. En la carpeta \DesignTime\Debug\x86\, cree un archivo de texto denominado NativeMathSDK.props y, a continuación, pegue el siguiente contenido en él:  
  
    [!code-xml[CreatingAnSDKUsingCpp&#7;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. En la barra de menús, elija **vista**, **otras ventanas**, **ventana propiedades** (teclado: elija la tecla F4).  
  
14. En **el Explorador de soluciones**, seleccione la **NativeMathWRT.winmd** archivo. En el **propiedades** ventana, cambiar la **acción de compilación** propiedad **contenido**y, a continuación, cambie la **incluir en VSIX** propiedad **True**.  
  
     Repita este proceso para el **SimpleMath.pri** archivo.  
  
     Repita este proceso para el **NativeMath.Lib** archivo.  
  
     Repita este proceso para el **NativeMathSDK.props** archivo.  
  
15. En **el Explorador de soluciones**, seleccione la **NativeMath.h** archivo. En el **propiedades** ventana, cambiar la **incluir en VSIX** propiedad **True**.  
  
     Repita este proceso para el **NativeMath.dll** archivo.  
  
     Repita este proceso para el **NativeMathWRT.dll** archivo.  
  
     Repita este proceso para el **SDKManifest.xml** archivo.  
  
16. En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
17. En **el Explorador de soluciones**, abra el menú contextual para el **NativeMathVSIX** del proyecto y, a continuación, elija **Abrir carpeta en el Explorador de archivos**.  
  
18. En **Explorador de archivos**, vaya a la carpeta \bin\Debug\ y, a continuación, ejecute NativeMathVSIX.vsix para iniciar la instalación.  
  
19. Elija la **instalar** botón, espere a que finalice la instalación y, a continuación, reinicie Visual Studio.  
  
##  <a name="a-namecreatesamplea-to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Para crear una aplicación de ejemplo que utiliza la biblioteca de clases  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En la lista de plantillas, expanda **Visual C++**, **tienda Windows**y, a continuación, seleccione **aplicación vacía**. En el **nombre** , especifique **NativeMathSDKSample**y, a continuación, elija la **Aceptar** botón.  
  
3.  En **el Explorador de soluciones**, abra el menú contextual para el **NativeMathSDKSample** del proyecto y, a continuación, elija **agregar**, **referencia**.  
  
4.  En el **propiedades comunes**, **Framework y referencias** página de propiedades, en la lista de tipos de referencia, expanda **Windows**y, a continuación, seleccione **extensiones**. En el panel de detalles, seleccione la **nativo SDK matemáticas** extensión y, a continuación, elija la **agregar nueva referencia** botón.  
  
5.  En el **Agregar referencia** cuadro de diálogo, seleccione la **nativo SDK matemáticas** y, a continuación, elija la **Aceptar** botón.  
  
6.  Muestra las propiedades del proyecto para NativeMathSDKSample.  
  
     Las propiedades que definen en NativeMathSDK.props se aplicaron al agregar la referencia. Puede comprobar examinando la **directorios de VC ++** propiedad del proyecto **propiedades de configuración**.  
  
7.  En **el Explorador de soluciones**, abra MainPage.xaml y, a continuación, utilice el siguiente código XAML para reemplazar su contenido:  
  
     [!code-xml[1 CreatingAnSDKUsingCppDemoApp](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
8.  Actualizar Mainpage.xaml.h para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp&#2;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
9. Actualizar MainPage.xaml.cpp para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp&3;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
10. Elija la tecla F5 para ejecutar la aplicación.  
  
11. En la aplicación, escriba los dos números, seleccione una operación y, a continuación, elija la ** = ** botón.  
  
     Aparecerá el resultado correcto.  
  
 Este tutorial ha mostrado cómo crear y usar el SDK de extensión para llamar a un [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteca y no[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] biblioteca.  
  
## <a name="next-steps"></a>Pasos siguientes  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Crear un SDK usando C# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Crear un Kit de desarrollo de Software](../extensibility/creating-a-software-development-kit.md)
