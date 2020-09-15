---
title: Advertencias de interoperabilidad y portabilidad
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings, portability warnings
- portability warnings
- warnings, portability
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f09ccafb79a87dff5c18bb4af11a12e1b1729a4
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2020
ms.locfileid: "90100505"
---
# <a name="portability-and-interoperability-warnings"></a>Advertencias de interoperabilidad y portabilidad

Las advertencias de portabilidad admiten la portabilidad en diferentes plataformas. Las advertencias de interoperabilidad admiten la interacción con clientes COM.

## <a name="in-this-section"></a>En esta sección

| Regla | Descripción |
| - | - |
| [CA1401: P/Invoke no debe estar visible](../code-quality/ca1401.md) | Un método público o protegido en un tipo público tiene el System.Runtime.InteropServices.Dllatributo ImportAttribute (también se implementa mediante la palabra clave declare en Visual Basic). No se deberían exponer estos métodos. |
| [CA1416: validar la compatibilidad de la plataforma](../code-quality/ca1416.md) | El uso de API dependientes de la plataforma en un componente hace que el código deje de funcionar en todas las plataformas. |
| [CA1417: no se usa `OutAttribute` en parámetros de cadena para P/Invoke](../code-quality/ca1417.md) | Los parámetros de cadena pasados por valor con el `OutAttribute` pueden desestabilizar el tiempo de ejecución si la cadena es una cadena interna. |
