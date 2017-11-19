---
title: "Cómo: ver documentos de Script | Documentos de Microsoft"
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
helpviewer_keywords: Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af4230a0d0bec680be1231f37e4e0bfbe51bc459
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-view-script-documents"></a>Cómo: Ver documentos de script
En versiones anteriores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], los archivos de script de cliente generados a partir de script de servidor aparecían en la ventana Explorador de scripts. Esta ventana solía estar oculta, por lo que la disponibilidad de archivos de script de cliente no siempre resultaba obvia.  
  
 En [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], los archivos de script de cliente generados a partir de script de servidor aparecen en el Explorador de soluciones, que está visible de manera predeterminada. Se ha eliminado la ventana Explorador de scripts.  
  
 Los archivos de script de cliente sólo están visibles en modo de depuración o en modo de interrupción. Aparecen en la **documentos de Script** nodo.  
  
 Los archivos de script de servidor siempre están visibles. Aparecen en la  **\<ruta de acceso del sitio Web >** nodo. El nombre del nodo es similar a este ejemplo:`c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>Para ver un documento de script de servidor  
  
1.  En **el Explorador de soluciones**, abra el  **\<ruta de acceso del sitio Web >** nodo.  
  
2.  Haga doble clic en el archivo de script que desee ver.  
  
     El archivo de script de servidor se abre en una ventana de código fuente.  
  
### <a name="to-view-a-client-side-script-document"></a>Para ver un documento de script de cliente  
  
1.  En **el Explorador de soluciones**, abra el **documentos de Script** nodo.  
  
2.  Haga doble clic en el archivo de script que desee ver.  
  
     El archivo de script de cliente se abre en una ventana de código fuente.  
  
## <a name="see-also"></a>Vea también  
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)