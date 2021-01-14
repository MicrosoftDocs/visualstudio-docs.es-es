---
title: 'Advertencia: Depuración de scripts deshabilitada | Microsoft Docs'
description: La advertencia "Depuración de scripts deshabilitada" aparece al intentar depurar un script sin habilitar la depuración de scripts en Internet Explorer. Consulte los pasos para habilitarla.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 7cc2e03a4efcf9a88675fd3c80f374ff78ba35bb
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149565"
---
# <a name="warning-script-debugging-disabled"></a>Advertencia: Depuración de scripts deshabilitada
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

## <a name="see-also"></a>Vea también
- [Cómo: Asociación a script](attach-to-running-processes-with-the-visual-studio-debugger.md)