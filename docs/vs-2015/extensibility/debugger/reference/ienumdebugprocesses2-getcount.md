---
title: IEnumDebugProcesses2::GetCount | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugProcesses2::GetCount
helpviewer_keywords:
- IEnumDebugProcesses2::GetCount
ms.assetid: 5dc3e36c-46e5-4556-bf41-1870aa67d2a0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2c74042510f589f3cf4ceca4bf3aab04a4b43fd2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807665"
---
# <a name="ienumdebugprocesses2getcount"></a>IEnumDebugProcesses2::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Devuelve el número de elementos de la enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pcelt`  
 [out] Devuelve el número de elementos de la enumeración.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método no forma parte de la interfaz de enumeración COM habitual que especifica que solamente el `Next`, `Clone`, `Skip`, y `Reset` métodos deben implementarse.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)

