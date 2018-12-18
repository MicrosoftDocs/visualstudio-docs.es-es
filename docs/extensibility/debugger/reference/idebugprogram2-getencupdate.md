---
title: IDebugProgram2::GetENCUpdate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c356154c5d77c01f84c5fe4446b8ac92235c10e4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867005"
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
  
#### <a name="parameters"></a>Parámetros  
 `ppUpdate`  
 [out] Devuelve una interfaz interna que puede usarse para actualizar este programa.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
> [!NOTE]
>  Siempre debe devolver un motor de depuración `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)