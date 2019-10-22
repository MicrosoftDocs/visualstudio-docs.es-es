---
title: Procedimiento Ver documentos de Script | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 88f923ab0447f1ac7d57e84d94f0ab442d912d67
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189600"
---
# <a name="how-to-view-script-documents"></a>Procedimiento Visualización de documentos de script
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En versiones anteriores de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], los archivos de script de cliente generados a partir de script de servidor aparecían en la ventana Explorador de scripts. Esta ventana solía estar oculta, por lo que la disponibilidad de archivos de script de cliente no siempre resultaba obvia.  
  
 En [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], los archivos de script de cliente generados a partir de script de servidor aparecen en el Explorador de soluciones, que está visible de manera predeterminada. Se ha eliminado la ventana Explorador de scripts.  
  
 Los archivos de script de cliente sólo están visibles en modo de depuración o en modo de interrupción. Aparecen en el nodo **Documentos de script**.  
  
 Los archivos de script de servidor siempre están visibles. Aparecen en el nodo **\<Nombre de ruta de acceso del sitio web>** . El nombre del nodo es similar a este ejemplo: `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>Para ver un documento de script de servidor  
  
1. En el **Explorador de soluciones**, abra el nodo **\<Nombre de ruta de acceso del sitio web>** .  
  
2. Haga doble clic en el archivo de script que desee ver.  
  
     El archivo de script de servidor se abre en una ventana de código fuente.  
  
### <a name="to-view-a-client-side-script-document"></a>Para ver un documento de script de cliente  
  
1. En el **Explorador de soluciones**, abra el nodo **Documentos de script**.  
  
2. Haga doble clic en el archivo de script que desee ver.  
  
     El archivo de script de cliente se abre en una ventana de código fuente.  
  
## <a name="see-also"></a>Vea también  
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)
