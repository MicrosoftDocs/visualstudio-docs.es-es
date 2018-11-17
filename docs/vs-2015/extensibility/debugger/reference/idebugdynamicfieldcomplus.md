---
title: IDebugDynamicFieldCOMPlus | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus interface
ms.assetid: c3a25f27-327a-4bdb-b026-27d436ddcd0c
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 39e9e456c19c228e39b1b7bffbf5298784ec96c0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817768"
---
# <a name="idebugdynamicfieldcomplus"></a>IDebugDynamicFieldCOMPlus
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Representa un campo dinámico para un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugDynamicFieldCOMPlus : IDebugDynamicField  
```  
  
## <a name="methods"></a>Métodos  
 Además de los métodos en el [IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md) interfaz, esta interfaz implementa los métodos siguientes:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetTypeFromPrimitive](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromprimitive.md)|Recupera un tipo dado su tipo primitivo.|  
|[GetTypeFromTypeDef](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus-gettypefromtypedef.md)|Recupera un tipo dado su token.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

