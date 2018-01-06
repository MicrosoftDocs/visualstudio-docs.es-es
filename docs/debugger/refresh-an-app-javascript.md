---
title: "Actualizar una aplicación de Windows 8.1 o UWP | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 636f88313d53625e5bb778ffe7bebc8f891ed4bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="refresh-a-uwp-or-windows-81-app"></a>Actualizar una aplicación de Windows 8.1 o UWP
![Se aplica a Windows y Windows Phone](../debugger/media/windows_and_phone_content.png "windows_and_phone_content")  
  
 Puede realizar cambios en el código durante la depuración y, a continuación, actualizar una aplicación de UWP con JavaScript eligiendo el **actualizar aplicación de Windows** situado en la **depurar** barra de herramientas. Al elegir este botón, se recarga la aplicación sin detener y reiniciar el depurador. La característica Actualizar te permite modificar código de HTML, CSS y JavaScript, y ver el resultado rápidamente. Esta característica se admite para las aplicaciones UWP y Windows 8.1.  
  
 La actualización no conserva el estado de la aplicación ni refleja los siguientes cambios en la aplicación:  
  
-   Cambios en el archivo de manifiesto del paquete, incluidos los cambios de imágenes especificadas en el manifiesto del paquete.  
  
-   Cambios de referencias, como agregar o quitar una referencia de SDK, o cambios a los componentes de Windows Runtime (archivos .winmd).  
  
-   Cambios de recursos, como los aplicados a cadenas de archivos .resjson.  
  
-   Cambios del archivo de proyecto que dan lugar a cambios del nombre de la ruta de acceso, nuevos archivos de proyecto o archivos eliminados.  
  
-   Cambios de propiedades del proyecto y de elementos, como cambios en el dispositivo de depuración seleccionado, o en la acción de empaquetado de un archivo (en la ventana Propiedades).  
  
> [!IMPORTANT]
>  Cuando cambias las referencias, cambias el manifiesto del paquete o realizas otros cambios especificados en la lista anterior, debes detener y reiniciar el depurador para actualizar los archivos de código fuente HTML, CSS y JavaScript.  
  
### <a name="to-refresh-an-app"></a>Para actualizar una aplicación  
  
1.  En Visual Studio, cree un nuevo proyecto con la plantilla de proyecto Aplicación de navegación.  
  
     Puede tratarse de aplicación de UWP o una aplicación de Windows 8.1.  
  
2.  Seleccione un dispositivo de depuración con la plantilla abierta en Visual Studio.  
  
     Si el proyecto de inicio actual es un proyecto de Windows Phone, seleccione un emulador de Windows Phone para el dispositivo de depuración. En caso contrario, seleccione **simulador** o **equipo Local**.  
  
     ![Lista de destinos de depuración seleccione](../debugger/media/js_select_target.png "JS_Select_Target")  
  
3.  Presiona F5 para ejecutar la aplicación en modo de depuración.  
  
4.  Cambia a Visual Studio. (Presiona F12).  
  
5.  En **el Explorador de soluciones**, en la **páginas** > **principal** carpeta y abra home.html.  
  
6.  Cambia el texto del título de la página de  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     por otra cosa, así:  
  
    ```html  
    Hello!  
    ```  
  
7.  Haga clic en el **actualizar aplicación de Windows** botón, que tiene el siguiente aspecto: ![botón de aplicación de Windows de actualización](../debugger/media/js_refresh.png "JS_Refresh"). (O bien, presiona F4).  
  
8.  Cambia a la aplicación. La aplicación se recarga sin que se reinicie el depurador y aparece el nuevo título de página.  
  
## <a name="see-also"></a>Vea también  
 [Inicio rápido: Depurar HTML y CSS](../debugger/quickstart-debug-html-and-css.md)