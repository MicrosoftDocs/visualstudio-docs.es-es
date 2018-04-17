---
title: IDebugWindowsComputerPort2::GetComputerInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetComputerInfo
- IDebugWindowsComputerPort2::GetComputerInfo
ms.assetid: 654910b2-c239-44c8-92fc-317680a5672f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e9dff1b64cafa6a212600cd467b86f8ddca83337
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugwindowscomputerport2getcomputerinfo"></a>IDebugWindowsComputerPort2::GetComputerInfo
Recupera información sobre el equipo en el que el depurador en ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetComputerInfo(  
   COMPUTER_INFO * pInfo  
);  
```  
  
```csharp  
public int GetComputerInfo(  
   out COMPUTER_INFO[] pInfo  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pInfo`  
 [out] Referencia a una estructura que contiene la información del equipo.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)   
 [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)