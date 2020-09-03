---
title: 'Tutorial: crear un SDK con C# o Visual Basic | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a604e3500c0ea438c987c4cf07ded98a5e03dd61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "77558207"
---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>Tutorial: Creación de un SDK con C# o Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial, aprenderá a crear un sencillo SDK de biblioteca matemática usando Visual C# y, a continuación, empaquetará el SDK como extensión de Visual Studio (VSIX). Completará los siguientes procedimientos:  
  
- [Para crear el componente Windows Runtime de SimpleMath](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
- [Para crear el proyecto de extensión SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
- [Para crear una aplicación de ejemplo que usa la biblioteca de clases](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea el [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a> Para crear el componente Windows Runtime de SimpleMath  
  
1. En la barra de menús, elija **archivo**, **nuevo**, **nuevo proyecto**.  
  
2. En la lista de plantillas, expanda **Visual C#** o **Visual Basic**, elija el nodo de la **tienda Windows** y, a continuación, elija la plantilla **componente de Windows Runtime** .  
  
3. En el cuadro **nombre** , especifique **SimpleMath**y elija el botón **Aceptar** .  
  
4. En **Explorador de soluciones**, abra el menú contextual del nodo de proyecto **SimpleMath** y, a continuación, elija **propiedades**.  
  
5. Cambie el nombre de **Class1.CS** a **Arithmetic.CS** y actualícelo para que coincida con el código siguiente:  
  
     [!code-csharp[CreatingAnSDKUsingWinRT#3](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmath/arithmetic.cs#3)]
     [!code-vb[CreatingAnSDKUsingWinRT#3](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmath/arithmetic.vb#3)]  
  
6. En **Explorador de soluciones**, abra el menú contextual del nodo **' SimpleMath '** de la solución y, a continuación, elija **Configuration Manager**.  
  
     Se abrirá el cuadro de diálogo **Configuration Manager** .  
  
7. En la lista **configuración de soluciones activas** , elija **versión**.  
  
8. En la columna **configuración** , compruebe que **SimpleMath** fila está establecida en **liberar**y, a continuación, elija el botón **cerrar** para aceptar el cambio.  
  
    > [!IMPORTANT]
    > El SDK del componente SimpleMath incluye solo una configuración. Esta configuración debe ser la versión de lanzamiento, o las aplicaciones que usan el componente no pasarán la certificación para [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)] .  
  
9. En **Explorador de soluciones**, abra el menú contextual del nodo de proyecto **SimpleMath** y, a continuación, elija **compilar**.  
  
## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a> Para crear el proyecto de extensión SimpleMathVSIX  
  
1. En el menú contextual del nodo **' SimpleMath '** de la solución, elija **Agregar**, **nuevo proyecto**.  
  
2. En la lista de plantillas, expanda **Visual C#** o **Visual Basic**, elija el nodo **extensibilidad** y, a continuación, elija la plantilla de **Proyecto VSIX** .  
  
3. En el cuadro **nombre** , especifique **SimpleMathVSIX**y elija el botón **Aceptar** .  
  
4. En **Explorador de soluciones**, elija el elemento **source. Extension. vsixmanifest** .  
  
5. En la barra de menús, elija **Ver**, **Código**.  
  
6. Reemplace el XML existente por el siguiente código XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7. En **Explorador de soluciones**, elija el proyecto **SimpleMathVSIX** .  
  
8. En la barra de menús, elija **proyecto**, **Agregar nuevo elemento**.  
  
9. En la lista de **elementos comunes**, expanda **datos**y, a continuación, elija **archivo XML**.  
  
10. En el cuadro **nombre** , especifique `SDKManifest.xml` y, a continuación, elija el botón **Agregar** .  
  
11. En **Explorador de soluciones**, abra el menú contextual de `SDKManifest.xml` , elija **propiedades**y, a continuación, cambie el valor de la propiedad **incluir en VSIX** a **true**.  
  
12. Sustituye el contenido del archivo por el siguiente código XML:  
  
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrt/cs/winrtmathvsix/sdkmanifest.xml#1)]
     [!code-xml[CreatingAnSDKUsingWinRT#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrt/vb/winrtmathvsix/sdkmanifest.xml#1)]  
  
13. En **Explorador de soluciones**, abra el menú contextual del proyecto **SimpleMathVSIX** , elija **Agregar**y, a continuación, elija **nueva carpeta**.  
  
14. Cambie el nombre de la carpeta a `references` .  
  
15. Abra el menú contextual de la carpeta **referencias** , elija **Agregar**y, a continuación, elija **nueva carpeta**.  
  
16. Cambie el nombre de la subcarpeta a `commonconfiguration` , cree una subcarpeta en ella y asigne un nombre a la subcarpeta `neutral` .  
  
17. Repita los cuatro pasos anteriores, esta vez cambiando el nombre de la primera carpeta a `redist` .  
  
     El proyecto contiene ahora la siguiente estructura de carpetas:  
  
    ```  
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. En **Explorador de soluciones**, abra el menú contextual del proyecto **SimpleMath** y, a continuación, elija **Abrir carpeta en el explorador de archivos**.  
  
19. En el **Explorador de archivos**, vaya a la carpeta bin\Release, abra el menú contextual del archivo SimpleMath. winmd y, a continuación, elija **copiar**.  
  
20. En **Explorador de soluciones**, pegue el archivo en la carpeta references\commonconfiguration\neutral del proyecto **SimpleMathVSIX** .  
  
21. Repita el paso anterior, pegando el archivo SimpleMath. PRI en la carpeta redist\commonconfiguration\neutral del proyecto **SimpleMathVSIX** .  
  
22. En **Explorador de soluciones**, elija **SimpleMath. winmd**.  
  
23. En la barra de menús, elija **Ver**, **propiedades** (teclado: elija la tecla F4).  
  
24. En la ventana **propiedades** , cambie la propiedad **acción de compilación** a **contenido**y, a continuación, cambie la propiedad **incluir en VSIX** a **true**.  
  
25. En **Explorador de soluciones**, repita este proceso para **SimpleMath. PRI**.  
  
26. En **Explorador de soluciones**, elija el proyecto **SimpleMathVSIX** .  
  
27. En la barra de menús, elija **compilar**, **compilar SimpleMathVSIX**.  
  
28. En **Explorador de soluciones**, abra el menú contextual del proyecto **SimpleMathVSIX** y, a continuación, elija **Abrir carpeta en el explorador de archivos**.  
  
29. En el **Explorador de archivos**, vaya a la carpeta \bin\Release y, a continuación, ejecute SimpleMathVSIX. VSIX para instalarlo.  
  
30. Elija el botón **instalar** , espere a que finalice la instalación y, a continuación, reinicie Visual Studio.  
  
## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Para crear una aplicación de ejemplo que usa la biblioteca de clases  
  
1. En la barra de menús, elija **archivo**, **nuevo**, **nuevo proyecto**.  
  
2. En la lista de plantillas, expanda **Visual C#** o **Visual Basic**y, a continuación, elija el nodo de la **tienda Windows** .  
  
3. Elija la plantilla **aplicación vacía** , asigne al proyecto el nombre **ArithmeticUI**y, a continuación, elija el botón **Aceptar** .  
  
4. En **Explorador de soluciones**, abra el menú contextual del proyecto **ArithmeticUI** y, a continuación, elija **Agregar**, **referencia**.  
  
5. En la lista de tipos de referencia, expanda **Windows**y, a continuación, elija **extensiones**.  
  
6. En el panel de detalles, elija la extensión **simple del SDK de matemáticas** .  
  
    Aparece información adicional sobre el SDK. Puede elegir el vínculo **más información** para abrir https://docs.microsoft.com , como especificó en el archivo SDKManifest.xml anteriormente en este tutorial.  
  
7. En el cuadro de diálogo **Administrador de referencias** , active la casilla **SDK de matemáticas simple** y, a continuación, elija el botón **Aceptar** .  
  
8. En la barra de menús, elija **Ver**, **Examinador de objetos**.  
  
9. En la lista **examinar** , elija **matemáticas simples**.  
  
     Ahora puede explorar lo que hay en el SDK.  
  
10. En **Explorador de soluciones**, abra mainpage. XAML y reemplace su contenido por el código XAML siguiente:  
  
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml#1)]
     [!code-xml[CreatingAnSDKUsingWinRTDemoApp#1](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml#1)]  
  
11. Actualice MainPage.xaml.cs para que coincida con el código siguiente:  
  
     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/csharp/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/cs/winrtmathtest/mainpage.xaml.cs#2)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../snippets/visualbasic/VS_Snippets_VSSDK/creatingansdkusingwinrtdemoapp/vb/winrtmathtest/mainpage.xaml.vb#2)]  
  
12. Elija la tecla F5 para ejecutar la aplicación.  
  
13. En la aplicación, escriba dos números cualesquiera, elija una operación y, a continuación, elija el **=** botón.  
  
     Aparece el resultado correcto.  
  
    Ha creado y usado correctamente un SDK de extensión.  
  
## <a name="see-also"></a>Consulte también  
 [Tutorial: crear un SDK con C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Tutorial: crear un SDK mediante JavaScript](walkthrough-creating-an-sdk-using-javascript.md)   
 [Creación de un kit de desarrollo de software](../extensibility/creating-a-software-development-kit.md)
