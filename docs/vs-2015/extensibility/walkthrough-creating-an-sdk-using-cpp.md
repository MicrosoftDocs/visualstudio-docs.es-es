---
title: 'Tutorial: crear un SDK con C++ | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1312d61b2d287a5dd8cb757b73e818a9e9cb2241
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202067"
---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Tutorial: Creación de un SDK con C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial se muestra cómo crear un SDK de la biblioteca matemática de C++ nativo, empaquetar el SDK como extensión de Visual Studio (VSIX) y usarlo para crear una aplicación. El tutorial se divide en estos pasos:  
  
- [Para crear las bibliotecas nativas y de Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
- [Para crear el proyecto de extensión NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
- [Para crear una aplicación de ejemplo que usa la biblioteca de clases](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Prerrequisitos  
 Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea el [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a> Para crear las bibliotecas nativas y de Windows Runtime  
  
1. En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2. En la lista de plantillas, expanda **Visual C++**, **tienda Windows**y, a continuación, seleccione la plantilla **dll (aplicaciones de la tienda Windows)** . En el cuadro **nombre** , especifique `NativeMath` y, a continuación, elija el botón **Aceptar** .  
  
3. Actualice NativeMath. h para que coincida con el código siguiente.  
  
     [!code-cpp[CreatingAnSDKUsingCpp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h#1)]  
  
4. Actualice NativeMath. cpp para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp#2)]  
  
5. En **Explorador de soluciones**, abra el menú contextual de la **solución ' NativeMath '** y, a continuación, elija **Agregar**, **nuevo proyecto**.  
  
6. En la lista de plantillas, expanda **Visual C++** y, a continuación, seleccione la plantilla **componente de Windows Runtime** . En el cuadro **nombre** , especifique `NativeMathWRT` y, a continuación, elija el botón **Aceptar** .  
  
7. Actualice Class1. h para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h#3)]  
  
8. Actualice Class1. cpp para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCpp#4](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp#4)]  
  
9. En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> Para crear el proyecto de extensión NativeMathVSIX  
  
1. En **Explorador de soluciones**, abra el menú contextual de la **solución ' NativeMath '** y, a continuación, elija **Agregar**, **nuevo proyecto**.  
  
2. En la lista de plantillas, expanda **Visual C#**, **extensibilidad**y, a continuación, seleccione **paquete VSIX**. En el cuadro **nombre** , especifique **NativeMathVSIX**y elija el botón **Aceptar** .  
  
3. Cuando aparezca el diseñador de manifiestos VSIX, ciérrelo.  
  
4. En **Explorador de soluciones**, abra el menú contextual de **source. Extension. vsixmanifest**y, a continuación, elija **Ver código**.  
  
5. Utilice el siguiente código XML para reemplazar el XML existente.  
  
    [!code-xml[CreatingAnSDKUsingCpp#6](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]
  
6. En **Explorador de soluciones**, abra el menú contextual del proyecto **NativeMathVSIX** y, a continuación, elija **Agregar**, **nuevo elemento**.  
  
7. En la lista de **elementos de Visual C#**, expanda **datos**y, a continuación, seleccione **archivo XML**. En el cuadro **nombre** , especifique `SDKManifest.xml` y, a continuación, elija el botón **Aceptar** .  
  
8. Use este XML para reemplazar el contenido del archivo:  
  
     [!code-xml[CreatingAnSDKUsingCpp#5](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml#5)]  
  
9. En **Explorador de soluciones**, en el proyecto **NativeMathVSIX** , cree esta estructura de carpetas:  
  
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
  
10. En **Explorador de soluciones**, abra el menú contextual de la **solución ' NativeMath '** y, a continuación, elija **Abrir carpeta en el explorador de archivos**.  
  
11. En el **Explorador de archivos**, copie \NativeMath\NativeMath.h y, a continuación, en **Explorador de soluciones**, en el proyecto **NativeMathVSIX** , péguelo en la carpeta \DesignTime\CommonConfiguration\Neutral\Include\  
  
     Copie \Debug\NativeMath\NativeMath.lib y, a continuación, péguelo en la carpeta \DesignTime\Debug\x86\  
  
     Copie \Debug\NativeMath\NativeMath.dll y péguelo en la carpeta \Redist\Debug\x86\.  
  
     Copie DebugNativeMathWRTNativeMathWRT.dll y péguelo en la carpeta RedistDebugx86.  
  
     Copie DebugNativeMathWRTNativeMathWRT. winmd y péguelo en la carpeta ReferencesCommonConfigurationNeutral  
  
     Copie DebugNativeMathWRTNativeMathWRT. PRI y péguelo en la carpeta ReferencesCommonConfigurationNeutral  
  
12. En la carpeta \DesignTime\Debug\x86\, cree un archivo de texto denominado NativeMathSDK. props y, a continuación, pegue el siguiente contenido en él:  
  
    [!code-xml[CreatingAnSDKUsingCpp#7](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. En la barra de menús, elija **Ver**, **otras ventanas**, **ventana Propiedades** (teclado: elija la tecla F4).  
  
14. En **Explorador de soluciones**, seleccione el archivo **NativeMathWRT. winmd** . En la ventana **propiedades** , cambie la propiedad **acción de compilación** a **contenido**y, a continuación, cambie la propiedad **incluir en VSIX** a **true**.  
  
     Repita este proceso para el archivo **SimpleMath. PRI** .  
  
     Repita este proceso para el archivo **NativeMath. lib** .  
  
     Repita este proceso para el archivo **NativeMathSDK. props** .  
  
15. En **Explorador de soluciones**, seleccione el archivo **NativeMath. h** . En la ventana **propiedades** , cambie la propiedad **incluir en VSIX** a **true**.  
  
     Repita este proceso para el archivo de **NativeMath.dll** .  
  
     Repita este proceso para el archivo de **NativeMathWRT.dll** .  
  
     Repita este proceso para el archivo de **SDKManifest.xml** .  
  
16. En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
17. En **Explorador de soluciones**, abra el menú contextual del proyecto **NativeMathVSIX** y, a continuación, elija **Abrir carpeta en el explorador de archivos**.  
  
18. En el **Explorador de archivos**, vaya a la carpeta \bin\Debug\ y, a continuación, ejecute NativeMathVSIX. VSIX para comenzar la instalación.  
  
19. Elija el botón **instalar** , espere a que finalice la instalación y, a continuación, reinicie Visual Studio.  
  
## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Para crear una aplicación de ejemplo que usa la biblioteca de clases  
  
1. En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2. En la lista de plantillas, expanda **Visual C++**, **tienda Windows**y, a continuación, seleccione **aplicación vacía**. En el cuadro **nombre** , especifique **NativeMathSDKSample**y elija el botón **Aceptar** .  
  
3. En **Explorador de soluciones**, abra el menú contextual del proyecto **NativeMathSDKSample** y, a continuación, elija **Agregar**, **referencia**.  
  
4. En la página **propiedades comunes**, **marco de trabajo y referencias** , en la lista de tipos de referencia, expanda **Windows**y, a continuación, seleccione **extensiones**. En el panel de detalles, seleccione la extensión **nativa del SDK de matemáticas** y, a continuación, elija el botón **Agregar nueva referencia** .  
  
5. En el cuadro de diálogo **Agregar referencia** , active la casilla **SDK de Math nativo** y, a continuación, elija el botón **Aceptar** .  
  
6. Muestra las propiedades del proyecto para NativeMathSDKSample.  
  
    Las propiedades que definió en NativeMathSDK. props se aplicaron al agregar la referencia. Para comprobarlo, examine la propiedad **directorios de VC + +** de las propiedades de **configuración**del proyecto.  
  
7. En **Explorador de soluciones**, abra mainpage. XAML y, a continuación, use el siguiente código XAML para reemplazar su contenido:  
  
    [!code-xml[CreatingAnSDKUsingCppDemoApp#1](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml#1)]  
  
8. Actualice mainpage. Xaml. h para que coincida con este código:  
  
    [!code-cpp[CreatingAnSDKUsingCppDemoApp#2](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h#2)]  
  
9. Actualice MainPage. Xaml. cpp para que coincida con este código:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp#3](../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp#3)]  
  
10. Elija la tecla F5 para ejecutar la aplicación.  
  
11. En la aplicación, escriba dos números cualesquiera, seleccione una operación y, a continuación, elija el **=** botón.  
  
     Aparece el resultado correcto.  
  
    En este tutorial se ha mostrado cómo crear y usar un SDK de extensión para llamar a una [!INCLUDE[wrt](../includes/wrt-md.md)] biblioteca y a una biblioteca que no es de [!INCLUDE[wrt](../includes/wrt-md.md)] .  
  
## <a name="next-steps"></a>Pasos siguientes  
  
## <a name="see-also"></a>Consulte también  
 [Tutorial: crear un SDK mediante C# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Creación de un kit de desarrollo de software](../extensibility/creating-a-software-development-kit.md)
