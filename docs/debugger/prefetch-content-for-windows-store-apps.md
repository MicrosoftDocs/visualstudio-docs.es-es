---
title: Depuración con contenido previamente capturado en aplicaciones para UWP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 28a73974a71df7fa652e4b246043e901df76e94c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72730569"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Depuración de aplicaciones para UWP con contenido capturado previamente en Visual Studio

 Para que la aplicación para UWP tenga mayor capacidad de respuesta, puede solicitar que Windows cargue previamente algún contenido Web, como páginas web o imágenes, en la caché de [WinInet](/windows/desktop/WinInet/about-wininet) de la aplicación. Esta funcionalidad se denomina precarga. Es eficaz en particular para contenido que se use en el inicio, pero también se puede precargar otro contenido de uso frecuente. Los métodos de la clase [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) permiten especificar los URI del contenido que se desea precargar. En el [ejemplo de precarga de contenido](https://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) de Windows SDK dispones de ejemplos para agregar la funcionalidad ContentPrefetcher a una aplicación.

 Windows utiliza la heurística para determinar cuándo debe producirse la precarga, en caso de que deba producirse, y qué recursos se descargarán. La heurística tiene en cuenta las condiciones de energía y red del sistema, el historial de uso de la aplicación del usuario y los resultados de intentos de precarga anteriores. En Visual Studio, puedes usar el comando **Desencadenar precarga de aplicaciones de la Tienda Windows** para hacer que Windows ignore la heurística de ContentPrefetcher y precargue todo el contenido web especificado. Es algo que puede resultar útil si deseas probar el comportamiento o rendimiento de la aplicación con el contenido que se precarga en un estado conocido (cargado o no).

## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Para forzar la precarga de los recursos especificados de ContentPrefetcher
 En este procedimiento se asume que ya has configurado la funcionalidad ContentPrefetcher y que has especificado los URI de contenido para precargar en el proyecto de aplicación. Para forzar la precarga de contenido cuando los recursos especificados son nuevos o se han modificado, tienes que iniciar y detener la aplicación antes de elegir el comando **Desencadenar precarga de aplicaciones de la Tienda Windows**. Primero se ejecuta la aplicación para registrar los URI. Después, el comando **Desencadenar precarga de aplicaciones de la Tienda Windows** hace que ContentPrefetcher descargue el contenido y lo agregue a la memoria caché. En las siguientes ocasiones en que se ejecute la aplicación, se puede asumir que el contenido está precargado.

1. Inicia la aplicación para registrar los URI de contenido precargado con la aplicación. En el menú **Depurar**, seleccione **Iniciar depuración** (método abreviado de teclado: F5).

2. En el menú **Depurar**, seleccione **Detener depuración** (método abreviado de teclado: mayús + F5).

3. En el menú **Depurar**, elija **Otros destinos de depuración** y después **Desencadenar precarga de aplicaciones de la Tienda Windows**.

   Ahora ya puedes depurar, probar o analizar tu aplicación con los recursos web precargados.

> [!NOTE]
> Repite estos pasos siempre que agregues o modifiques el contenido web especificado.

## <a name="see-also"></a>Vea también
- [Entrada de blog: desencadenar la captura previa de aplicaciones de la tienda Windows en Visual Studio 2013 Update 2](https://devblogs.microsoft.com/devops/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)