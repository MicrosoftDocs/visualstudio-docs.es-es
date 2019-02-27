---
title: Depurar con contenido precargado en aplicaciones para UWP | Microsoft Docs
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
ms.openlocfilehash: 7e59548ac46196f86813aa312e68bbe043edf701
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56701282"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Depurar aplicaciones para UWP con contenido precargado en Visual Studio

 Para que responda mejor su aplicación para UWP, puede solicitar Windows que precargue algún contenido web, como páginas web o imágenes, en la aplicación [WinINet](/windows/desktop/WinInet/about-wininet) memoria caché. Esta funcionalidad se denomina precarga. Es eficaz en particular para contenido que se use en el inicio, pero también se puede precargar otro contenido de uso frecuente. Los métodos de la clase [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) permiten especificar los URI del contenido que se desea precargar. En el [ejemplo de precarga de contenido](https://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) de Windows SDK dispones de ejemplos para agregar la funcionalidad ContentPrefetcher a una aplicación.

 Windows utiliza la heurística para determinar cuándo debe producirse la precarga, en caso de que deba producirse, y qué recursos se descargarán. La heurística tiene en cuenta las condiciones de energía y red del sistema, el historial de uso de la aplicación del usuario y los resultados de intentos de precarga anteriores. En Visual Studio, puedes usar el comando **Desencadenar precarga de aplicaciones de la Tienda Windows** para hacer que Windows ignore la heurística de ContentPrefetcher y precargue todo el contenido web especificado. Es algo que puede resultar útil si deseas probar el comportamiento o rendimiento de la aplicación con el contenido que se precarga en un estado conocido (cargado o no).

## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Para forzar la precarga de los recursos especificados de ContentPrefetcher
 En este procedimiento se asume que ya has configurado la funcionalidad ContentPrefetcher y que has especificado los URI de contenido para precargar en el proyecto de aplicación. Para forzar la precarga de contenido cuando los recursos especificados son nuevos o se han modificado, tienes que iniciar y detener la aplicación antes de elegir el comando **Desencadenar precarga de aplicaciones de la Tienda Windows**. Primero se ejecuta la aplicación para registrar los URI. Después, el comando **Desencadenar precarga de aplicaciones de la Tienda Windows** hace que ContentPrefetcher descargue el contenido y lo agregue a la memoria caché. En las siguientes ocasiones en que se ejecute la aplicación, se puede asumir que el contenido está precargado.

1. Inicia la aplicación para registrar los URI de contenido precargado con la aplicación. En el menú **Depurar**, seleccione **Iniciar depuración** (método abreviado de teclado: F5).

2. En el menú **Depurar**, seleccione **Detener depuración** (método abreviado de teclado: mayús + F5).

3. En el menú **Depurar**, elija **Otros destinos de depuración** y después **Desencadenar precarga de aplicaciones de la Tienda Windows**.

   Ahora ya puedes depurar, probar o analizar tu aplicación con los recursos web precargados.

> [!NOTE]
>  Repite estos pasos siempre que agregues o modifiques el contenido web especificado.

## <a name="see-also"></a>Vea también
- [Entrada de blog: desencadenar precarga para Windows Store Apps en Visual Studio 2013 Update 2](https://devblogs.microsoft.com/devops/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)