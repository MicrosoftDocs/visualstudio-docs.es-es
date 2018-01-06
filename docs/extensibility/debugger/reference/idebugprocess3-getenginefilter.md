---
title: IDebugProcess3::GetEngineFilter | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetEngineFilter
- IDebugProcess3::GetEngineFilter
ms.assetid: ccb7ecb0-f189-4e80-b5b2-221a095e01f5
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 57a57341ba9df9333439c4acef2216821bc627a6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess3getenginefilter"></a>IDebugProcess3::GetEngineFilter
Recupera una matriz de identificadores únicos para los motores de depuración disponible.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetEngineFilter(  
   GUID_ARRAY *pEngineArray  
);  
```  
  
```csharp  
public int GetEngineFilter(  
   out GUID_ARRAY[] pEngineArray  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pEngineArray`  
 [out] Referencia a una estructura que contiene identificadores únicos para los motores de depuración.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)