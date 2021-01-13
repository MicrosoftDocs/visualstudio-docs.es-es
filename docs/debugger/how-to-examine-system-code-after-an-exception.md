---
title: Examen del código del sistema después de una excepción | Microsoft Docs
description: Obtenga información sobre cómo examinar el código en una llamada del sistema para determinar la causa de la excepción. El procedimiento se aplica incluso si no se han cargado los símbolos para el código del sistema.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eceb9f898b4329940408e4063dc73d81e2a604a4
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903460"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Procedimiento Examinar el código del sistema después de una excepción
Cuando se produce una excepción, es posible que tenga que examinar el código de una llamada al sistema para determinar su causa. El procedimiento siguiente explica cómo hacerlo si no se tienen símbolos cargados para el código del sistema o si Sólo mi código está habilitado.

### <a name="to-examine-system-code-following-an-exception"></a>Para examinar el código del sistema tras una excepción

1. En la ventana **Pila de llamadas**, haga clic con el botón derecho y, a continuación, haga clic en **Mostrar código externo**.

     Si Sólo mi código no está habilitado, esta opción no está disponible en el menú contextual y de forma predeterminada se muestra el código del sistema.

2. Haga clic con el botón derecho en los marcos del código externos que ahora aparecen en la ventana **Pila de llamadas**.

3. Elija **Cargar símbolos desde** y, a continuación, haga clic en **Servidores de símbolos de Microsoft**.

    1. Si Sólo mi código está habilitado, aparecerá un cuadro de diálogo. Indica que Sólo mi código se ha deshabilitado. Esto es necesario para entrar en las llamadas del sistema.

    2. Aparece el cuadro de diálogo **Descargar símbolos públicos**. Desaparecerá cuando finalice la descarga.

4. Ahora puede examinar el código del sistema en la ventana **Pila de llamadas** y otras ventanas. Por ejemplo, puede hacer doble clic en un marco de pila de llamadas para ver el código en una ventana de origen de datos o **Desensamblado**.

## <a name="see-also"></a>Vea también
- [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md)