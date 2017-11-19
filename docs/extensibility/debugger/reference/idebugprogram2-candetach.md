---
title: IDebugProgram2::CanDetach | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::CanDetach
helpviewer_keywords: IDebugProgram2::CanDetach
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8995bcd2d620289e9f52322b62810bc66cdc1c86
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2candetach"></a>IDebugProgram2::CanDetach
Determina si puede separar un motor de depuración (Alemania) desde el programa.  
  
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
 Si puede separar, devuelve `S_OK`; en caso contrario, devuelve un código de error. Devuelve `S_FALSE` si no se puede separar la Alemania desde el programa.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)