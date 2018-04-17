---
title: 'Cómo: ver documentos de Script | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 62c62212e72561817b58cf1496fff20a05745277
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-view-script-documents"></a>Cómo: Ver documentos de script
En versiones anteriores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], los archivos de script de cliente generados a partir de script de servidor aparecían en la ventana Explorador de scripts. Esta ventana solía estar oculta, por lo que la disponibilidad de archivos de script de cliente no siempre resultaba obvia.  
  
 En [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], los archivos de script de cliente generados a partir de script de servidor aparecen en el Explorador de soluciones, que está visible de manera predeterminada. Se ha eliminado la ventana Explorador de scripts.  
  
 Los archivos de script de cliente sólo están visibles en modo de depuración o en modo de interrupción. Aparecen en la **documentos de Script** nodo.  
  
 Los archivos de script de servidor siempre están visibles. Aparecen en la  **\<ruta de acceso del sitio Web >** nodo. El nombre del nodo es similar a este ejemplo: `c:\...\Website2\`  
  
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