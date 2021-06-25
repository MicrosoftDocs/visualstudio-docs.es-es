---
title: OptNAMECHANGEPFN | Microsoft Docs
description: Obtenga información sobre la función de devolución de llamada OPTNAMECHANGEPFN, que comunica los cambios de nombre del complemento de control de código fuente al IDE Visual Studio código fuente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 340012663ad7d21c0b5c2ef81283f5d780d6011c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901531"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Se trata de una función de devolución de llamada especificada en una llamada a [SccSetOption](../extensibility/sccsetoption-function.md) (mediante la opción ) y se usa para comunicar los cambios de nombre realizados por el complemento de control de código fuente al `SCC_OPT_NAMECHANGEPFN` IDE.

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

[in] Valor de usuario especificado en una llamada anterior a [SccSetOption](../extensibility/sccsetoption-function.md) (mediante la opción `SCC_OPT_USERDATA` ).

 pszOldName

[in] Nombre original del archivo.

 pszNewName

[in] Nombre al que se ha cambiado el nombre del archivo.

## <a name="return-value"></a>Valor devuelto
 Ninguno.

## <a name="remarks"></a>Observaciones
 Si se cambia el nombre de un archivo durante una operación de control de código fuente, el complemento de control de código fuente puede notificar al IDE el cambio de nombre a través de esta devolución de llamada.

 Si el IDE no admite esta devolución de llamada, no llamará a [SccSetOption](../extensibility/sccsetoption-function.md) para especificarla. Si el complemento no admite esta devolución de llamada, devolverá de la función cuando el `SCC_E_OPNOTSUPPORTED` IDE intente establecer la `SccSetOption` devolución de llamada.

## <a name="see-also"></a>Consulta también
- [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)
