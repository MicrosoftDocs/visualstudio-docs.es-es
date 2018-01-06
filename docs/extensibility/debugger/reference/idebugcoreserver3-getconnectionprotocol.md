---
title: IDebugCoreServer3::GetConnectionProtocol | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer3::GetConnectionProtocol
helpviewer_keywords: IDebugCoreServer3::GetConnectionProtocol
ms.assetid: 368ced5b-c5d9-4090-a5b4-26ff400d1a55
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dfa1b8c335d871c83aaf27e3929dd70e981450da
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver3getconnectionprotocol"></a>IDebugCoreServer3::GetConnectionProtocol
Devuelve un valor que indica el protocolo que se usa para la comunicación entre el servidor y el paquete de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetConnectionProtocol(  
   CONNECTION_PROTOCOL* pProtocol  
);  
```  
  
```csharp  
int GetConnectionProtocol(  
   CONNECTION_PROTOCOL[] pProtocol  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pProtocol`  
 [out] Devuelve uno de los valores de la [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md) enumeración.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve el código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md)