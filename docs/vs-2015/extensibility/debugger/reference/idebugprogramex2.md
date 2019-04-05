---
title: IDebugProgramEx2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9858b205f3bf581f2595ea645dcea700a382a6b1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998015"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz permite que la sesión de depuración manager (SDM) asociar a un programa y obtener el nodo de programa asociado con un programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProgramEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Un proveedor de puerto personalizado implementa esta interfaz en el mismo objeto que el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz para permitir que el SDM asociar a un programa mientras al mismo tiempo, lo que permite el proveedor del puerto realizar el seguimiento de todas las sesiones conectado a la programa. El proveedor del puerto personalizado puede implementar esta interfaz si así lo decide.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Las llamadas SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) en un `IDebugProgram2` interfaz para obtener esta interfaz para realizar un seguimiento de las sesiones que se han asociado a programas.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugProgramEx2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Asociar](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|Un programa se asocia a una sesión.|  
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|Obtiene el nodo de programa asociado con un programa.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz es privada entre el SDM y el programa.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Portpriv.h  
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
