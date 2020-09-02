---
title: 'IDebugEngineProgram2:: Stop | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb74cb2940a91bbc64fa4a06f28d07a828357fc6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431490"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Detiene todos los subprocesos que se ejecutan en este programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Stop(   
   void   
);  
```  
  
```csharp  
int Stop();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Se llama a este método cuando este programa se está depurando en un entorno de varios programas. Cuando se recibe un evento de detención de algún otro programa, se llama a este método en este programa. La implementación de este método debe ser asincrónica; es decir, no es necesario detener todos los subprocesos antes de que este método devuelva. La implementación de este método puede ser tan simple como llamar al método [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) en este programa.  
  
 No se envía ningún evento de depuración como respuesta a este método.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)
