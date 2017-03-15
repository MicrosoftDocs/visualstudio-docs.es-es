---
title: "EncUnavailableReason | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EncUnavailableReason"
helpviewer_keywords: 
  - "EncUnavailableReason (enumeración)"
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# EncUnavailableReason
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

`This is for internal use only!` Representa las razones que **Editar y continuar** no está disponible.  
  
## Sintaxis  
  
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
  
```c#  
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
  
#### Parámetros  
 ENCUN\_NONE  
 Ninguna razón concreta por la que editar y continuar no está disponible.  
  
 ENCUN\_INTEROP  
 Editar y continuar no está disponible durante una llamada de Interoperabilidad.  
  
 ENCUN\_SQLCLR  
 Editar y continuar no está disponible durante una llamada a procedimiento de SQL que utiliza Common Language Runtime \(CLR\).  
  
 ENCUN\_MINIDUMP  
 Editar y continuar no está disponible al procesar un mini\-volcado.  
  
 ENCUN\_EMBEDDED  
 Editar y continuar no está disponible al procesar código incrustado.  
  
 ENCUN\_ATTACH  
 Editar y continuar no está disponible porque adjuntaron a la sesión, no iniciará por, el depurador.  
  
 ENCUN\_WIN64  
 Editar y continuar no está disponible mientras procesa el código de 64 bits de Windows.  
  
## Comentarios  
 Esta enumeración es sólo para uso interno por [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  Los métodos de [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) y de [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) implementados por un proveedor de puerto siempre deben devolver `E_NOTIMPL`.  
  
## Requisitos  
 encabezado: msdbg.idl  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)