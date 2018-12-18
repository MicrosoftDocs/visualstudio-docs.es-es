---
title: IDebugDisassemblyStream2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ef0720d0faf3286580142525e499c9e0009a36d2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786631"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz representa una secuencia de instrucciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un motor de depuración implementa esta interfaz para admitir el desensamblado del código de un programa.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Una llamada a la [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) método devuelve esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugDisassemblyStream2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Lee las instrucciones a partir de la posición actual en la secuencia de desensamblado.|  
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Mueve el puntero de lectura en la secuencia de desensamblado de un determinado número de instrucciones respecto a la posición especificada.|  
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Devuelve un identificador de ubicación de código para un contexto de código determinado.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Devuelve un objeto de contexto de código correspondiente a un identificador de ubicación de código especificado.|  
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Devuelve un identificador de ubicación del código que representa la ubicación actual del código.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Obtiene el documento de origen asociado a esta secuencia de desensamblado.|  
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Obtiene el ámbito de esta secuencia de desensamblado.|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Obtiene el tamaño de esta secuencia de desensamblado.|  
  
## <a name="remarks"></a>Comentarios  
 La secuencia de desensamblado se puede crear para representar el espacio de direcciones completa o solo una función o módulo en el espacio. Cada instrucción se representa mediante un [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estructura devuelta por una llamada a la [lectura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)

