---
title: OPTNAMECHANGEPFN | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6107f48f4680cef9cbb825f4d760f3f0bac1ec1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336238"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Se trata de una función de devolución de llamada especificada en una llamada a la [SccSetOption](../extensibility/sccsetoption-function.md) (mediante la opción `SCC_OPT_NAMECHANGEPFN`) y se usa para comunicar los cambios de nombre mediante el control de código fuente complemento vuelve a realizar el IDE.

## <a name="signature"></a>Signatura

```cpp
typedef void (*OPTNAMECHANGEPFN)(
   LPVOID pvCallerData,
   LPCSTR pszOldName,
   LPCSTR pszNewName
);
```

## <a name="parameters"></a>Parámetros
 pvCallerData

[in] Valor de usuario especificado en una llamada anterior a la [SccSetOption](../extensibility/sccsetoption-function.md) (mediante la opción `SCC_OPT_USERDATA`).

 pszOldName

[in] El nombre original del archivo.

 pszNewName

[in] Se ha cambiado el nombre del archivo a.

## <a name="return-value"></a>Valor devuelto
 Ninguno.

## <a name="remarks"></a>Comentarios
 Si se cambia el nombre de un archivo durante una operación de control de código fuente, el complemento de control de código fuente puede notificar el IDE sobre el cambio de nombre a través de esta devolución de llamada.

 Si el IDE no admite esta devolución de llamada, no llamará a la [SccSetOption](../extensibility/sccsetoption-function.md) para especificarla. Si el complemento no admite esta devolución de llamada, devolverá `SCC_E_OPNOTSUPPORTED` desde el `SccSetOption` funcionar cuando el IDE intenta establecer la devolución de llamada.

## <a name="see-also"></a>Vea también
- [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccSetOption](../extensibility/sccsetoption-function.md)