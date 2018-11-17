---
title: EncUnavailableReason | Documentos de Microsoft
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
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5ec7c652fd2a35aa927cb5c634fea3cdf9b19ee3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784018"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

`This is for internal use only!` Representa los motivos que **editar y continuar** no está disponible.  
  
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
 No hay motivo específico por editar y continuar no está disponible.  
  
 ENCUN_INTEROP  
 Editar y continuar no está disponible durante una llamada de interoperabilidad.  
  
 ENCUN_SQLCLR  
 Editar y continuar no está disponible durante una llamada de procedimiento SQL que utiliza Common Language Runtime (CLR).  
  
 ENCUN_MINIDUMP  
 Editar y continuar no está disponible mientras se procesaba un minivolcado.  
  
 ENCUN_EMBEDDED  
 Editar y continuar no está disponible cuando se procesa código incrustado.  
  
 ENCUN_ATTACH  
 Editar y continuar no está disponible porque se ha adjuntado a la sesión, no se inicia mediante el depurador.  
  
 ENCUN_WIN64  
 Editar y continuar no está disponible durante el procesamiento de código de Windows de 64 bits.  
  
## <a name="remarks"></a>Comentarios  
 Esta enumeración es para uso interno únicamente por [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. El [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) y [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) siempre deben devolver métodos tal como está implementado por un proveedor de puerto personalizado `E_NOTIMPL`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.idl  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)

