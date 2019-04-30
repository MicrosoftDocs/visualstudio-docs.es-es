---
title: 'Advertencia: Depuración de scripts deshabilitada | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.scriptdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50fe457e2b66a4c1ddafc9fc24658f58f6f753d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901028"
---
# <a name="warning-script-debugging-disabled"></a>Advertencia: Depuración de scripts deshabilitada
La depuración de script está deshabilitada actualmente en Internet Explorer

 Esta advertencia se produce al intentar depurar script sin habilitar la depuración en Internet Explorer. Por razones de seguridad, Internet Explorer deshabilita de forma predeterminada la depuración de script.

### <a name="to-enable-script-debugging-in-internet-explorer"></a>Para habilitar la depuración de script en Internet Explorer

1. En el menú **Herramientas** de Internet Explorer, elija **Opciones de Internet**.

2. En el cuadro de diálogo **Opciones de Internet**, haga clic en la pestaña **Opciones avanzadas**.

3. En la pestaña **Opciones avanzadas**, observe la categoría **Examinar** en el cuadro **Configuración**.

4. Desactive **Deshabilitar la depuración de scripts (Internet Explorer)**.

5. Haga clic en **Aceptar**.

6. Salga y reinicie Internet Explorer.

     La nueva configuración estará ahora en vigor.

## <a name="see-also"></a>Vea también
- [Cómo: Asociación a script](../debugger/how-to-attach-to-script.md)