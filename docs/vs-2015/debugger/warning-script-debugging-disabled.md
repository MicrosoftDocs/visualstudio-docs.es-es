---
title: 'Advertencia: Depuración de scripts deshabilitada | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.scriptdisabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91b54b3e9a70284dc1efb03be7adfaa5d1421920
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573810"
---
# <a name="warning-script-debugging-disabled"></a>Advertencia: Depuración de script deshabilitada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [advertencia: depuración de scripts deshabilitada](https://docs.microsoft.com/visualstudio/debugger/warning-script-debugging-disabled).  
  
La depuración de script está deshabilitada actualmente en Internet Explorer  
  
 Esta advertencia se produce al intentar depurar script sin habilitar la depuración en Internet Explorer. Por razones de seguridad, Internet Explorer deshabilita de forma predeterminada la depuración de script.  
  
### <a name="to-enable-script-debugging-in-internet-explorer"></a>Para habilitar la depuración de script en Internet Explorer  
  
1.  En el Explorador de Internet **herramientas** menú, elija **opciones de Internet**.  
  
2.  En el **opciones de Internet** cuadro de diálogo, haga clic en el **avanzadas** ficha.  
  
3.  En el **avanzadas** pestaña, observe el **configuración** cuadro, **exploración** categoría.  
  
4.  Borrar **Deshabilitar depuración de scripts (Internet Explorer)**.  
  
5.  Haga clic en **Aceptar**.  
  
6.  Salga y reinicie Internet Explorer.  
  
     La nueva configuración estará ahora en vigor.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Adjuntar a script](../debugger/how-to-attach-to-script.md)



