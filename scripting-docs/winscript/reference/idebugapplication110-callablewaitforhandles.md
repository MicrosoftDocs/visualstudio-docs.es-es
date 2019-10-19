---
title: 'Idebugapplication110 (:: CallableWaitForHandles | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::CallableWaitForHandles
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22af0e9dcf548bbd2f0f8c179b4889d5294eb284
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575086"
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
Espera a que se señalice cualquiera de los identificadores especificados mientras se permite que las llamadas entre subprocesos se publiquen en este subproceso. Se debe llamar a este método desde el subproceso del depurador.  
  
> [!IMPORTANT]
> La [interfaz idebugapplication110 (](../../winscript/reference/idebugapplication110-interface.md) se implementa mediante PDM v 11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `handleCount`  
 Número de identificadores que se van a esperar.  
  
 `pHandles`  
 Conjunto de identificadores que se va a esperar.  
  
 `pIndex`  
 Cuando el valor HRESULT es S_OK, el índice en `pHandles` para el identificador que se señaló.  
  
## <a name="see-also"></a>Vea también  
 [IDebugApplication110 (Interfaz)](../../winscript/reference/idebugapplication110-interface.md)