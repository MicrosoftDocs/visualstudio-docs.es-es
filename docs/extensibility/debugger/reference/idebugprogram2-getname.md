---
title: IDebugProgram2::GetName | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::GetName
helpviewer_keywords: IDebugProgram2::GetName
ms.assetid: a54cbf13-b3e3-4c9f-8b8d-13573232dfb0
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: def082b7485bc8487ff061a07c46b06824050f51
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2getname"></a>IDebugProgram2::GetName
Obtiene el nombre del programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName(   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrName`  
 [out] Devuelve el nombre del programa.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El nombre devuelto por este método siempre es un nombre descriptivo, que se puede mostrar el usuario que describe el programa.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)