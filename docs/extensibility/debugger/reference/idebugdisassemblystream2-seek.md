---
title: IDebugDisassemblyStream2::Seek | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 375ff5c08c481061d217fbb0b3a4fac38d1e74c5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896645"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Mueve el puntero de lectura en la secuencia de desensamblado de un determinado número de instrucciones respecto a la posición especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```csharp  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwSeekStart`  
 [in] Un valor de la [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) enumeración que especifica la posición relativa para comenzar el proceso de búsqueda.  
  
 `pCodeContext`  
 [in] El [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que representa el contexto de código que es relativa la operación de búsqueda. Este parámetro se usa únicamente si `dwSeekStart`  =  `SEEK_START_CODECONTEXT`; en caso contrario, se omite este parámetro y puede ser un valor null.  
  
 `uCodeLocationId`  
 [in] El identificador de ubicación del código que es relativa la operación de búsqueda. Este parámetro se usa si `dwSeekStart`  =  `SEEK_START_CODELOCID`; de lo contrario, este parámetro se omite y se puede establecer en 0. Consulte la sección Comentarios para el [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) método para obtener una descripción de un identificador de ubicación del código.  
  
 `iInstructions`  
 [in] El número de instrucciones para mover en relación con la posición especificada en `dwSeekStart`. Este valor puede ser negativo para moverse hacia atrás.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`. Devuelve `S_FALSE` si fue la posición de búsqueda a un punto más allá de la lista de instrucciones disponibles. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si la búsqueda se realizó a una posición antes del comienzo de la lista, se establece la posición de lectura a la primera instrucción en la lista. Si la consulte consistía en una posición después del final de la lista, la posición de lectura se establece a la última instrucción en la lista.  
  
## <a name="see-also"></a>Vea también  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)