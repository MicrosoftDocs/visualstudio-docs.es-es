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
ms.openlocfilehash: 306c2477e6e5f731ed6dbf20b2cf4d03d4556467
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509918"
---
# <a name="portability-and-interoperability-warnings"></a>Advertencias de interoperabilidad y portabilidad

Las advertencias de portabilidad admiten la portabilidad en diferentes plataformas. Las advertencias de interoperabilidad admiten la interacción con clientes COM.

## <a name="in-this-section"></a>En esta sección

| Regla | Descripción |
| - | - |
| [CA1401: P/Invoke no debe estar visible](../code-quality/ca1401.md) | Un método público o protegido en un tipo público tiene el System.Runtime.InteropServices.Dllatributo ImportAttribute (también se implementa mediante la palabra clave declare en Visual Basic). No se deberían exponer estos métodos. |
| [CA1417: no se usa `OutAttribute` en parámetros de cadena para P/Invoke](../code-quality/ca1417.md) | Los parámetros de cadena pasados por valor con el `OutAttribute` pueden desestabilizar el tiempo de ejecución si la cadena es una cadena interna. |