---
title: IDebugProcess2::Detach | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::Detach
helpviewer_keywords: IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c308dae9b324871f8604b6bedecf3d297f3eacd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
Desasocia al depurador de este proceso separando todos los programas en el proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Detach(   
   void   
);  
```  
  
```csharp  
int Detach();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Todos los programas y el proceso continúan ejecutándose, pero ya no forman parte de la sesión de depuración. Después de la operación de separación es depuración completa, no se enviarán eventos para este proceso (y sus programas).  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)