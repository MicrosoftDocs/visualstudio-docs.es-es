---
title: 'Error: La depuración en modo mixto para los procesos IA64 no se admite | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f80cc0d38335679df413f104deadc8f9135ab765
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715757"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Error: No se admite la depuración en modo mixto para procesos IA64
El depurador [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no permite depurar código nativo y administrado mixto en un proceso basado en Itanium.

### <a name="to-correct-this-error"></a>Para corregir este error

-   Compile una versión de 32 bits de su aplicación para la depuración.

## <a name="see-also"></a>Vea también
- [Remote Debugging](../debugger/remote-debugging.md)