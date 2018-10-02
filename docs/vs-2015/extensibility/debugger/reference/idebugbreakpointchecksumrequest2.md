---
title: IDebugBreakpointChecksumRequest2 | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugBreakpointChecksumRequest2 interface
ms.assetid: 9cfdbca5-052c-48e9-8411-e2e9e4065d00
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bfccf1afeb521f5557ff20256dfede221ded687a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582175"
---
# <a name="idebugbreakpointchecksumrequest2"></a>IDebugBreakpointChecksumRequest2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugBreakpointChecksumRequest2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbreakpointchecksumrequest2).  
  
Representa una suma de comprobación de documento para una solicitud de punto de interrupción.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugBreakpointChecksumRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Implementada por el [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] depurar paquete y utilizado por los motores de depuración.  
  
## <a name="methods"></a>Métodos  
 La tabla siguiente muestran los métodos de `IDebugBreakpointChecksumRequest2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetChecksum](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-getchecksum.md)|Recupera la suma de comprobación de documento para una solicitud de punto de interrupción según el identificador único del algoritmo de suma de comprobación para usar.|  
|[IsChecksumEnabled](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2-ischecksumenabled.md)|Determina si la suma de comprobación está habilitada para este documento.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

