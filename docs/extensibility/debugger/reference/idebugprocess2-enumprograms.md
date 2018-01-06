---
title: IDebugProcess2::EnumPrograms | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::EnumPrograms
helpviewer_keywords: IDebugProcess2::EnumPrograms
ms.assetid: f5b7295d-487d-464f-a4c6-d54175b07705
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fd0f240e22636286a23d6c5772e54de4a5c087e0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess2enumprograms"></a>IDebugProcess2::EnumPrograms
Recupera una lista de todos los programas incluidos en este proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT EnumPrograms(   
   IEnumDebugPrograms2** ppEnum  
);  
```  
  
```csharp  
int EnumPrograms(   
   out IEnumDebugPrograms2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppEnum`  
 [out] Devuelve un [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md) objeto que contiene una lista de todos los programas en el proceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)