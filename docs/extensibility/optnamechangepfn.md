---
title: OPTNAMECHANGEPFN | Microsoft Docs
description: Obtenga información sobre la función de devolución de llamada OPTNAMECHANGEPFN, que comunica los cambios de nombre del complemento de control de código fuente con el IDE de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4e6cb58aebbe76eff5c66dc29ecfad8c77c8717c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090374"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Se trata de una función de devolución de llamada especificada en una llamada a [SccSetOption](../extensibility/sccsetoption-function.md) (mediante la opción `SCC_OPT_NAMECHANGEPFN` ) y se utiliza para comunicar los cambios de nombre realizados por el complemento de control de código fuente al IDE.

## <a name="signature"></a>Firma

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>Parámetros
 pvCallerData

de Valor de usuario especificado en una llamada anterior a [SccSetOption](../extensibility/sccsetoption-function.md) (con la opción `SCC_OPT_USERDATA` ).

 pszOldName

de Nombre original del archivo.

 pszNewName

de Nombre al que se ha cambiado el nombre del archivo.

## <a name="return-value"></a>Valor devuelto
 Ninguno.

## <a name="remarks"></a>Observaciones
 Si se cambia el nombre de un archivo durante una operación de control de código fuente, el complemento de control de código fuente puede notificar al IDE sobre el cambio de nombre a través de esta devolución de llamada.

 Si el IDE no admite esta devolución de llamada, no llamará a [SccSetOption](../extensibility/sccsetoption-function.md) para especificarla. Si el complemento no admite esta devolución de llamada, se devolverá `SCC_E_OPNOTSUPPORTED` de la `SccSetOption` función cuando el IDE intente establecer la devolución de llamada.

## <a name="see-also"></a>Consulte también
- [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
