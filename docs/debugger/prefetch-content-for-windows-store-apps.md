---
title: Depurar con captura previa del contenido en las aplicaciones UWP | Documentos de Microsoft
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
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: f98867a5420755ca2eb4e2fb5e75070759a1a91b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Depurar aplicaciones UWP con contenido precargado en Visual Studio
![Solo se aplica a Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Para hacer que su aplicación UWP sean más receptivos, se puede solicitar a Windows que precargue algún contenido web, como páginas web o imágenes, en la aplicación [WinINet](http://msdn.microsoft.com/en-us/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](http://msdn.microsoft.com/library/aa383630.aspx)memoria caché. Esta funcionalidad se denomina precarga. Es especialmente eficaz para el contenido que se usa en el inicio, pero también puede precargar otro contenido de uso frecuente, demasiado. Los métodos de la [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) clase le permite especificar el URI del contenido que quieres precargar. Consulte el SDK de Windows [ejemplo de precarga de contenido](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) para obtener ejemplos de cómo agregar la funcionalidad ContentPrefetcher a la aplicación.  
  
 Windows utiliza la heurística para determinar cuándo debe producirse la precarga, en caso de que deba producirse, y qué recursos se descargarán. La heurística tiene en cuenta las condiciones de energía y red del sistema, el historial de uso de la aplicación del usuario y los resultados de intentos de precarga anteriores. En Visual Studio, puede usar el **desencadenar precarga de aplicaciones de la tienda de Windows** comando para hacer que Windows ignore la heurística de ContentPrefetcher y precargue todo el contenido web especificado. Es algo que puede resultar útil si deseas probar el comportamiento o rendimiento de la aplicación con el contenido que se precarga en un estado conocido (cargado o no).  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Para forzar la precarga de los recursos especificados de ContentPrefetcher  
 En este procedimiento se asume que ya has configurado la funcionalidad ContentPrefetcher y que has especificado los URI de contenido para precargar en el proyecto de aplicación. Para forzar la precarga de contenido cuando los recursos especificados son nuevos o modificados, tendrá que iniciar y detener la aplicación antes de elegir la **desencadenar precarga de aplicaciones de la tienda de Windows** comando. Primero se ejecuta la aplicación para registrar los URI. **Desencadenar precarga de aplicaciones de Windows Store** comando, a continuación, hace que ContentPrefetcher Descargue el contenido y agregar la memoria caché. En las siguientes ocasiones en que se ejecute la aplicación, se puede asumir que el contenido está precargado.  
  
1.  Inicia la aplicación para registrar los URI de contenido precargado con la aplicación. En el **depurar** menú, elija **Iniciar depuración** (método abreviado de teclado: F5).  
  
2.  En el **depurar** menú, elija **Detener depuración** (método abreviado de teclado: Mayús + F5).  
  
3.  En el **depurar** menú, elija **otros destinos de depuración** y, a continuación, elija **desencadenar precarga de aplicaciones de la tienda de Windows**.  
  
 Ahora ya puedes depurar, probar o analizar tu aplicación con los recursos web precargados.  
  
> [!NOTE]
>  Repite estos pasos siempre que agregues o modifiques el contenido web especificado.  
  
## <a name="see-also"></a>Vea también  
 [Entrada de blog: desencadenar precarga de almacén de las aplicaciones de Windows en Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)