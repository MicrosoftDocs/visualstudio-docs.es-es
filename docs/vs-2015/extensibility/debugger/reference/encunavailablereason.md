---
title: EncUnavailableReason | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ebdc5518579223a0081f30a0affd3a45e91604e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198776"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

`This is for internal use only!` Representa las razones por las que **Editar y continuar** no está disponible.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum tagEncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
typedef enum tagEncUnavailableReason EncUnavailableReason;  
```  
  
```csharp  
public enum EncUnavailableReason {  
   ENCUN_NONE,  
   ENCUN_INTEROP,  
   ENCUN_SQLCLR,  
   ENCUN_MINIDUMP,  
   ENCUN_EMBEDDED,  
   ENCUN_ATTACH,  
   ENCUN_WIN64  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 ENCUN_NONE  
 No hay ningún motivo específico por el que editar y continuar no esté disponible.  
  
 ENCUN_INTEROP  
 Editar y continuar no está disponible durante una llamada de interoperabilidad.  
  
 ENCUN_SQLCLR  
 Editar y continuar no está disponible durante una llamada a procedimiento SQL que usa Common Language Runtime (CLR).  
  
 ENCUN_MINIDUMP  
 Editar y continuar no está disponible mientras se procesa un minivolcado.  
  
 ENCUN_EMBEDDED  
 Editar y continuar no está disponible cuando se procesa código incrustado.  
  
 ENCUN_ATTACH  
 La función editar y continuar no está disponible porque el depurador ha adjuntado la sesión, pero no la ha iniciado.  
  
 ENCUN_WIN64  
 Editar y continuar no está disponible al procesar el código de Windows de 64 bits.  
  
## <a name="remarks"></a>Comentarios  
 Esta enumeración solo es para uso interno por parte de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] . Los métodos [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) y [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) implementados por un proveedor de Puerto personalizado siempre deben devolver `E_NOTIMPL` .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. idl  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
