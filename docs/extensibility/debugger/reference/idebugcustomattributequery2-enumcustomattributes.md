---
description: Obtiene un enumerador para todos los atributos personalizados asociados a este campo.
title: 'IDebugCustomAttributeQuery2:: Enumcustomattributes (| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 348d5e753702e523f09bef8cbd5f374294c197e4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154449"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
Obtiene un enumerador para todos los atributos personalizados asociados a este campo.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumCustomAttributes( 
   IEnumDebugCustomAttributes** ppEnum
);
```

```csharp
int EnumCustomAttributes(
   out IEnumDebugCustomAttributes ppEnum
);
```

## <a name="parameters"></a>Parámetros
`ppEnum`\
enuncia Devuelve un objeto [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) que representa la lista de atributos personalizados; de lo contrario, devuelve un valor NULL si no hay ningún atributo personalizado.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, Devuelve S_OK o S_FALSE si no hay ningún atributo personalizado en este campo. De lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
 Un campo puede tener varios atributos personalizados.

## <a name="see-also"></a>Consulte también
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
