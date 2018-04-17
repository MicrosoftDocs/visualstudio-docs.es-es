---
title: IDebugProcess2::CanDetach | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c49cc87352c3869fd8a954457ad14ec1486b4198
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
Determina si el Administrador de sesión de depuración (SDM) puede separar el proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CanDetach(  
   void  
);  
```  
  
```csharp  
int CanDetach();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK.` devuelve `S_FALSE` si el depurador no se puede desasociar del proceso. De lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)