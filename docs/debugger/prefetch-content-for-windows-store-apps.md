---
title: Depurar con captura previa del contenido en las aplicaciones UWP | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 241937c8462577d6af375d2440efe828a738a8cc
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Depurar aplicaciones UWP con contenido precargado en Visual Studio
  
 Para hacer que su aplicación UWP sean más receptivos, se puede solicitar a Windows que precargue algún contenido web, como páginas web o imágenes, en la aplicación [WinINet](http://msdn.microsoft.com/library/0a06f2af-957a-4dff-a8cc-187370181b5c) memoria caché. Esta funcionalidad se denomina precarga. Es especialmente eficaz para el contenido que se usa en el inicio, pero también puede precargar otro contenido de uso frecuente, demasiado. Los métodos de la [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) clase le permite especificar el URI del contenido que quieres precargar. Consulte el SDK de Windows [ejemplo de precarga de contenido](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) para obtener ejemplos de cómo agregar la funcionalidad ContentPrefetcher a la aplicación.  
  
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