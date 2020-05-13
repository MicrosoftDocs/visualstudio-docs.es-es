---
title: OPTNAMECHANGEPFN ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 603bd08c1ec3832bf732e0b33101076738d009e3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702245"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Se trata de una función de devolución de llamada `SCC_OPT_NAMECHANGEPFN`especificada en una llamada a la [SccSetOption](../extensibility/sccsetoption-function.md) (mediante la opción ) y se utiliza para comunicar los cambios de nombre realizados por el complemento de control de código fuente al IDE.

## <a name="signature"></a>Signature

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>Parámetros
 pvCallerData

[en] Valor de usuario especificado en una llamada anterior a `SCC_OPT_USERDATA` [SccSetOption](../extensibility/sccsetoption-function.md) (mediante la opción ).

 pszOldName

[en] El nombre original del archivo.

 pszNewName

[en] El nombre al que se ha cambiado el nombre del archivo.

## <a name="return-value"></a>Valor devuelto
 Ninguno.

## <a name="remarks"></a>Observaciones
 Si se cambia el nombre de un archivo durante una operación de control de código fuente, el complemento de control de código fuente puede notificar al IDE sobre el cambio de nombre a través de esta devolución de llamada.

 Si el IDE no admite esta devolución de llamada, no llamará a [la SccSetOption](../extensibility/sccsetoption-function.md) para especificarlo. Si el complemento no admite esta devolución `SCC_E_OPNOTSUPPORTED` de `SccSetOption` llamada, se devolverá de la función cuando el IDE intente establecer la devolución de llamada.

## <a name="see-also"></a>Vea también
- [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
