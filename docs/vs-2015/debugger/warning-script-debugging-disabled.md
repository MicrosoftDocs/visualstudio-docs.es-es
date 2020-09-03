---
title: 'Advertencia: Depuración de scripts deshabilitada | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.scriptdisabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 36065120dc636f0004f0e00d8b17a0059a680723
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161382"
---
# <a name="warning-script-debugging-disabled"></a>Advertencia: Depuración de scripts deshabilitada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La depuración de script está deshabilitada actualmente en Internet Explorer  
  
 Esta advertencia se produce al intentar depurar script sin habilitar la depuración en Internet Explorer. Por razones de seguridad, Internet Explorer deshabilita de forma predeterminada la depuración de script.  
  
### <a name="to-enable-script-debugging-in-internet-explorer"></a>Para habilitar la depuración de script en Internet Explorer  
  
1. En el menú **Herramientas** de Internet Explorer, elija **Opciones de Internet**.  
  
2. En el cuadro de diálogo **Opciones de Internet**, haga clic en la pestaña **Opciones avanzadas**.  
  
3. En la pestaña **Opciones avanzadas**, observe la categoría **Examinar** en el cuadro **Configuración**.  
  
4. Desactive **Deshabilitar la depuración de scripts (Internet Explorer)** .  
  
5. Haga clic en **Aceptar**.  
  
6. Salga y reinicie Internet Explorer.  
  
     La nueva configuración estará ahora en vigor.  
  
## <a name="see-also"></a>Consulte también  
 [Cómo: Asociación a script](../debugger/how-to-attach-to-script.md)
