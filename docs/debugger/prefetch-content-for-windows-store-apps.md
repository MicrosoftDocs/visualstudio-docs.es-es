---
title: Depuración con contenido precargado en aplicaciones para UWP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 65b889452a23bb970cbee4c65455679a3473abab
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348072"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Depuración de aplicaciones para UWP con contenido precargado en Visual Studio

 Para mejorar la capacidad de respuesta de la aplicación para UWP, se puede solicitar a Windows que precargue algún contenido web, como páginas web o imágenes, en la memoria caché de [WinINet](/windows/desktop/WinInet/about-wininet) de la aplicación. Esta funcionalidad se denomina precarga. Es eficaz en particular para contenido que se use en el inicio, pero también se puede precargar otro contenido de uso frecuente. Los métodos de la clase [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) permiten especificar los URI del contenido que se desea precargar. En el [ejemplo de precarga de contenido](https://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) de Windows SDK dispones de ejemplos para agregar la funcionalidad ContentPrefetcher a una aplicación.

 Windows utiliza la heurística para determinar cuándo debe producirse la precarga, en caso de que deba producirse, y qué recursos se descargarán. La heurística tiene en cuenta las condiciones de energía y red del sistema, el historial de uso de la aplicación del usuario y los resultados de intentos de precarga anteriores. En Visual Studio, puedes usar el comando **Desencadenar precarga de aplicaciones de la Tienda Windows** para hacer que Windows ignore la heurística de ContentPrefetcher y precargue todo el contenido web especificado. Es algo que puede resultar útil si deseas probar el comportamiento o rendimiento de la aplicación con el contenido que se precarga en un estado conocido (cargado o no).

## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Para forzar la precarga de los recursos especificados de ContentPrefetcher
 En este procedimiento se asume que ya has configurado la funcionalidad ContentPrefetcher y que has especificado los URI de contenido para precargar en el proyecto de aplicación. Para forzar la precarga de contenido cuando los recursos especificados son nuevos o se han modificado, tienes que iniciar y detener la aplicación antes de elegir el comando **Desencadenar precarga de aplicaciones de la Tienda Windows**. Primero se ejecuta la aplicación para registrar los URI. Después, el comando **Desencadenar precarga de aplicaciones de la Tienda Windows** hace que ContentPrefetcher descargue el contenido y lo agregue a la memoria caché. En las siguientes ocasiones en que se ejecute la aplicación, se puede asumir que el contenido está precargado.

1. Inicia la aplicación para registrar los URI de contenido precargado con la aplicación. En el menú **Depurar**, seleccione **Iniciar depuración** (método abreviado de teclado: F5).

2. En el menú **Depurar**, seleccione **Detener depuración** (método abreviado de teclado: Mayús + F5).

3. En el menú **Depurar**, elija **Otros destinos de depuración** y después **Desencadenar precarga de aplicaciones de la Tienda Windows**.

   Ahora ya puedes depurar, probar o analizar tu aplicación con los recursos web precargados.

> [!NOTE]
> Repite estos pasos siempre que agregues o modifiques el contenido web especificado.

## <a name="see-also"></a>Vea también
- [Entrada de blog: Desencadenar la precarga de aplicaciones de Microsoft Store en Visual Studio 2013 Update 2](https://devblogs.microsoft.com/devops/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)