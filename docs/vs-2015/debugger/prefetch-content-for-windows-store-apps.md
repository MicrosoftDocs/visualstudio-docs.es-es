---
title: Precargar contenido para aplicaciones de Windows Store | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
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
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1da34d2baba519f9b8fa8cfde5756e8fccdfe7b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49868734"
---
# <a name="prefetch-content-for-windows-store-apps"></a>Precargar contenido para aplicaciones de la Tienda Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Solo se aplica a Windows] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Para hacer que la aplicación de Windows Store con más capacidad de respuesta, puede solicitar Windows que precargue algún contenido web, como páginas web o imágenes, en la aplicación [WinINet](http://msdn.microsoft.com/en-us/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](http://msdn.microsoft.com/library/aa383630.aspx)memoria caché. Esta funcionalidad se denomina precarga. Es eficaz en particular para contenido que se use en el inicio, pero también se puede precargar otro contenido de uso frecuente. Los métodos de la [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) clase le permite especificar el URI del contenido que desee cargar previamente. Consulte el SDK de Windows [ejemplo de precarga de contenido](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) para obtener ejemplos de cómo agregar la funcionalidad ContentPrefetcher a la aplicación.  
  
 Windows utiliza la heurística para determinar cuándo debe producirse la precarga, en caso de que deba producirse, y qué recursos se descargarán. La heurística tiene en cuenta las condiciones de energía y red del sistema, el historial de uso de la aplicación del usuario y los resultados de intentos de precarga anteriores. En Visual Studio, puede usar el **desencadenar precarga de aplicaciones de Windows Store** comando para forzar a Windows a ignore la heurística de ContentPrefetcher y precargue todo el contenido web especificado. Es algo que puede resultar útil si deseas probar el comportamiento o rendimiento de la aplicación con el contenido que se precarga en un estado conocido (cargado o no).  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>Para forzar la precarga de los recursos especificados de ContentPrefetcher  
 En este procedimiento se asume que ya has configurado la funcionalidad ContentPrefetcher y que has especificado los URI de contenido para precargar en el proyecto de aplicación. Para forzar la precarga de contenido cuando los recursos especificados son nuevos o modificados, tendrá que iniciar y detener la aplicación antes de elegir el **desencadenar precarga de aplicaciones de Windows Store** comando. Primero se ejecuta la aplicación para registrar los URI. **Desencadenar precarga de aplicaciones de Windows Store** comando, a continuación, hace que ContentPrefetcher Descargue el contenido y agregarlo de la memoria caché. En las siguientes ocasiones en que se ejecute la aplicación, se puede asumir que el contenido está precargado.  
  
1. Inicia la aplicación para registrar los URI de contenido precargado con la aplicación. En el **depurar** menú, elija **Iniciar depuración** (método abreviado de teclado: F5).  
  
2. En el **depurar** menú, elija **Detener depuración** (método abreviado de teclado: Mayús + F5).  
  
3. En el **depurar** menú, elija **otros destinos de depuración** y, a continuación, elija **desencadenar precarga de aplicaciones de Windows Store**.  
  
   Ahora ya puedes depurar, probar o analizar tu aplicación con los recursos web precargados.  
  
> [!NOTE]
>  Repite estos pasos siempre que agregues o modifiques el contenido web especificado.  
  
## <a name="see-also"></a>Vea también  
 [Entrada de blog: desencadenar precarga para Windows Store Apps en Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)



