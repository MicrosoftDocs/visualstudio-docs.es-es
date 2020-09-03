---
title: 'IDebugObject2:: IsEncOutdated | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a90ff97b87ec2abaab87dfece5b2a2ac1cabb28c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726101"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
Este método determina si el estado de editar y continuar de este objeto o del contenedor primario no está actualizado. Un evaluador de expresiones personalizado no implementa este método y siempre devuelve `E_NOTIMPL` .

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT IsEncOutdated(
   BOOL* pfEncOutdated
);
```

```csharp
int IsEncOutdated(
   out int pfEncOutdated
);
```

## <a name="parameters"></a>Parámetros
`pfEncOutdated`\
enuncia Distinto de cero ( `TRUE` ) si el estado de editar y continuar no está actualizado, cero ( `FALSE` ) si no lo está.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

> [!NOTE]
> Un evaluador de expresiones personalizadas siempre debe devolver `E_NOTIMPL` .

## <a name="see-also"></a>Vea también
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
