---
title: IDebugApplication110::CallableWaitForHandles | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplication110::CallableWaitForHandles
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b259f5296f8e0b32def793a81e4c2e1069643306
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
Espera a que cualquiera de los identificadores especificados a que se señalice permitiendo que las llamadas entre subprocesos se registren en este subproceso. Este método se debe invocar desde el subproceso del depurador.  
  
> [!IMPORTANT]
>  [IDebugApplication110 (interfaz)](../../winscript/reference/idebugapplication110-interface.md) se implementa mediante PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `handleCount`  
 El número de identificadores de espera.  
  
 `pHandles`  
 El conjunto de identificadores de espera.  
  
 `pIndex`  
 Cuando el valor HRESULT es S_OK, el índice en `pHandles` para el identificador que se había señalado.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplication110 (Interfaz)](../../winscript/reference/idebugapplication110-interface.md)