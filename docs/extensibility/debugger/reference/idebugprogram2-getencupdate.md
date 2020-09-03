---
title: 'IDebugProgram2:: GetENCUpdate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e90ff9f8a7a80913aec72b9fe2bb6fe470013d51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722833"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
Este método obtiene la actualización de editar y continuar (ENC) para este programa. Un motor de depuración siempre devuelve `E_NOTIMPL`.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetENCUpdate( 
   IUnknown** ppUpdate
);
```

```csharp
int GetENCUpdate(
   out object ppUpdate
);
```

## <a name="parameters"></a>Parámetros
`ppUpdate`\
enuncia Devuelve una interfaz interna que se puede usar para actualizar este programa.

## <a name="return-value"></a>Valor devuelto
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

> [!NOTE]
> Un motor de depuración personalizado siempre debe devolver `E_NOTIMPL` .

## <a name="see-also"></a>Vea también
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
