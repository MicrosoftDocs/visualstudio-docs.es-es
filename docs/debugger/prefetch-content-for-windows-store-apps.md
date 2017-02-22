---
title: "Precargar contenido para aplicaciones de la Tienda Windows | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Precargar contenido para aplicaciones de la Tienda Windows
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para que la aplicación de la Tienda Windows tenga más capacidad de respuesta, puede solicitar que Windows cargue previamente algún contenido web, como páginas web o imágenes, en la caché [WinINet](http://msdn.microsoft.com/es-es/0a06f2af-957a-4dff-a8cc-187370181b5c) [WinINet](http://msdn.microsoft.com/library/aa383630.aspx) de la aplicación. Esta funcionalidad se denomina precarga. Es eficaz en particular para contenido que se use en el inicio, pero también se puede precargar otro contenido de uso frecuente. Los métodos de la clase [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) permiten especificar los URI del contenido que quiera cargar previamente. Consulte [Ejemplo de precarga de contenido](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) del SDK de Windows para obtener ejemplos de cómo agregar la funcionalidad ContentPrefetcher a la aplicación.  
  
 Windows usa la heurística para determinar el momento, si se debe realizar la precarga y qué recursos se descargarán. La heurística tiene en cuenta las condiciones de energía y red del sistema, el historial de uso de la aplicación del usuario y los resultados de intentos de precarga anteriores. En Visual Studio, puedes usar el comando **Desencadenar precarga de aplicaciones de la Tienda Windows** para hacer que Windows ignore la heurística de ContentPrefetcher y precargue todo el contenido web especificado. Esto puede ser útil si quiere probar el comportamiento o el rendimiento de la aplicación con el contenido que se precarga en un estado conocido \(cargado o no cargado\).  
  
## Para forzar la precarga de los recursos especificados de ContentPrefetcher  
 Este procedimiento supone que ya ha configurado la funcionalidad ContentPrefetcher y ha especificado los URI de contenido para cargar previamente en el proyecto de la aplicación. Para forzar la precarga de contenido cuando los recursos especificados son nuevos o se han modificado, tienes que iniciar y detener la aplicación antes de elegir el comando **Desencadenar precarga de aplicaciones de la Tienda Windows**. Primero se ejecuta la aplicación para registrar los URI. Después, el comando **Desencadenar precarga de aplicaciones de la Tienda Windows** hace que ContentPrefetcher descargue el contenido y lo agregue a la memoria caché. En las ejecuciones posteriores de la aplicación, puede suponer que el contenido está cargado previamente.  
  
1.  Inicie la aplicación para registrar los URI de contenido de precarga con la aplicación. En el menú **Depurar**, seleccione **Iniciar depuración** \(método abreviado de teclado: F5\).  
  
2.  En el menú **Depurar**, seleccione **Detener depuración** \(método abreviado de teclado: Mayús \+ F5\).  
  
3.  En el menú **Depurar**, seleccione **Otros destinos de depuración** y seleccione **Desencadenar precarga de aplicaciones de la Tienda Windows**.  
  
 Ahora puede depurar, probar o analizar la aplicación con los recursos web precargados.  
  
> [!NOTE]
>  Repita estos pasos cada vez que agregue o modifique el contenido web especificado.  
  
## Vea también  
 [Entrada de Blog: Desencadenar la precarga de aplicaciones de la Tienda Windows en Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)