---
title: 'IDebugProcess2:: GetAttachedSessionName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b70fd48adacdbbf936c6997fc373ad4a8d7e696b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724056"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
Obtiene el nombre de la sesión que está depurando este proceso. Un IDE puede mostrar esta información a un usuario que está depurando un proceso determinado en un equipo determinado.

> [!NOTE]
> Este método está en desuso y su implementación siempre debe devolver `E_NOTIMPL` .

## <a name="syntax"></a>Sintaxis

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

## <a name="parameters"></a>Parámetros
`pbstrSessionName`\

## <a name="return-value"></a>Valor devuelto
 Este método siempre debe devolver `E_NOTIMPL` .

## <a name="see-also"></a>Vea también
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
