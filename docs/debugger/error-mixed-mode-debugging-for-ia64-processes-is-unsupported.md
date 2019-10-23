---
title: 'Error: no se admite la depuración en modo mixto para procesos IA64 | Microsoft Docs'
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
ms.openlocfilehash: 0bddbb1572bd0258eae2052eb34dfa3d0d67a134
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737625"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Error: No se admite la depuración en modo mixto para procesos IA64
El depurador [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no permite depurar código nativo y administrado mixto en un proceso basado en Itanium.

### <a name="to-correct-this-error"></a>Para corregir este error

- Compile una versión de 32 bits de su aplicación para la depuración.

## <a name="see-also"></a>Vea también
- [Remote Debugging](../debugger/remote-debugging.md)