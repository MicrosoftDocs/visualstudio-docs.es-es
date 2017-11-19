---
title: IDebugProgramEngines2::SetEngine | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramEngines2::SetEngine
helpviewer_keywords: IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: af62aec85afd39ee617b9b700e14168395269532
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramengines2setengine"></a>IDebugProgramEngines2::SetEngine
Indica el nodo de programa o un programa qué motor de depuración (Alemania) a utilizar para depurar este programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetEngine(   
   REFGUID guidEngine  
);  
```  
  
```csharp  
int SetEngine(   
   ref Guid guidEngine  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guidEngine`  
 [in] El GUID de la DE.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)