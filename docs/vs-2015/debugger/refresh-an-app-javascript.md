---
title: Actualizar una aplicación (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [Windows Store apps]
- debugging, refreshing pages [Windows Store apps]
- DOM Explorer, Refresh [Windows Store apps]
- Refresh [Windows Store apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca647572eac68dcf70d21b7ed687212a0229568f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575102"
---
# <a name="refresh-an-app-javascript"></a>Actualizar una aplicación (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [actualizar una aplicación (JavaScript)](https://docs.microsoft.com/visualstudio/debugger/refresh-an-app-javascript).  
  
Se aplica a Windows y Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Puede realizar cambios en el código mientras está depurando y, a continuación, actualice una aplicación de Store con JavaScript eligiendo el **actualizar Windows app** situado en la **depurar** barra de herramientas. Al elegir este botón, se recarga la aplicación sin detener y reiniciar el depurador. La característica Actualizar te permite modificar código de HTML, CSS y JavaScript, y ver el resultado rápidamente. Esta característica es compatible para las aplicaciones de la Tienda Windows y de la Tienda de Windows Phone.  
  
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
  
     Puede ser una aplicación de la Tienda Windows o de la Tienda de Windows Phone, o bien una aplicación universal.  
  
2.  Seleccione un dispositivo de depuración con la plantilla abierta en Visual Studio.  
  
     Si el proyecto de inicio actual es un proyecto de Windows Phone, seleccione un emulador de Windows Phone para el dispositivo de depuración. En caso contrario, seleccione **simulador** o **máquina Local**.  
  
     ![Lista de destinos de depuración seleccione](../debugger/media/js-select-target.png "JS_Select_Target")  
  
3.  Presiona F5 para ejecutar la aplicación en modo de depuración.  
  
4.  Cambia a Visual Studio. (Presiona F12).  
  
5.  En **el Explorador de soluciones**, en el **páginas** > **principal** carpeta y abra home.html.  
  
6.  Cambia el texto del título de la página de  
  
    ```html  
    Welcome to yourAppName!  
    ```  
  
     por otra cosa, así:  
  
    ```html  
    Hello!  
    ```  
  
7.  Haga clic en el **actualizar Windows app** button, que tiene el siguiente aspecto: ![botón de actualización de Windows app](../debugger/media/js-refresh.png "JS_Refresh"). (O bien, presiona F4).  
  
8.  Cambia a la aplicación. La aplicación se recarga sin que se reinicie el depurador y aparece el nuevo título de página.  
  
## <a name="see-also"></a>Vea también  
 [Inicio rápido: Depurar HTML y CSS](../debugger/quickstart-debug-html-and-css.md)



