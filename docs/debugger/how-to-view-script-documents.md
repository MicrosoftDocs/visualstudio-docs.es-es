---
title: Procedimiento Ver documentos de Script | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 3592056fdde7756f3fbe63d0dc5d86782fdf9a8b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867736"
---
# <a name="how-to-view-script-documents"></a>Procedimiento Visualización de documentos de script
En versiones anteriores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], los archivos de script de cliente generados a partir de script de servidor aparecían en la ventana Explorador de scripts. Esta ventana solía estar oculta, por lo que la disponibilidad de archivos de script de cliente no siempre resultaba obvia.  
  
 En [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], los archivos de script de cliente generados a partir de script de servidor aparecen en el Explorador de soluciones, que está visible de manera predeterminada. Se ha eliminado la ventana Explorador de scripts.  
  
 Los archivos de script de cliente sólo están visibles en modo de depuración o en modo de interrupción. Aparecen en el nodo **Documentos de script**.  
  
 Los archivos de script de servidor siempre están visibles. Aparecen en el nodo **\<Nombre de ruta de acceso del sitio web>**. El nombre del nodo es similar a este ejemplo: `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>Para ver un documento de script de servidor  
  
1.  En el **Explorador de soluciones**, abra el nodo **\<Nombre de ruta de acceso del sitio web>**.  
  
2.  Haga doble clic en el archivo de script que desee ver.  
  
     El archivo de script de servidor se abre en una ventana de código fuente.  
  
### <a name="to-view-a-client-side-script-document"></a>Para ver un documento de script de cliente  
  
1.  En el **Explorador de soluciones**, abra el nodo **Documentos de script**.  
  
2.  Haga doble clic en el archivo de script que desee ver.  
  
     El archivo de script de cliente se abre en una ventana de código fuente.  
  
## <a name="see-also"></a>Vea también  
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)