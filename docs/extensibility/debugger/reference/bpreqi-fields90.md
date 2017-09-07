---
title: BPREQI_FIELDS90 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 2de27fc0c3ea470e63c82c8116e34e450eb08bb2
ms.contentlocale: es-es
ms.lasthandoff: 09/06/2017

---
# <a name="bpreqifields90"></a>BPREQI_FIELDS90
Enumera los valores válidos que especifican la información que va a recuperar sobre una solicitud de punto de interrupción. Esta enumeración se extiende el [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_BPREQI_FIELDS90  
{  
   // VS 8.0 values  
   BPREQI90_BPLOCATION                = 0x0001,  
   BPREQI90_LANGUAGE                  = 0x0002,  
   BPREQI90_PROGRAM                   = 0x0004,  
   BPREQI90_PROGRAMNAME               = 0x0008,  
   BPREQI90_THREAD                    = 0x0010,  
   BPREQI90_THREADNAME                = 0x0020,  
   BPREQI90_PASSCOUNT                 = 0x0040,  
   BPREQI90_CONDITION                 = 0x0080,  
   BPREQI90_FLAGS                     = 0x0100,  
   BPREQI90_ALLOLDFIELDS              = 0x01ff,  
   BPREQI90_VENDOR                    = 0x0200,  
   BPREQI90_CONSTRAINT                = 0x0400,  
   BPREQI90_TRACEPOINT                = 0x0800,  
  
   // Values added in VS 9.0  
   BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
   BPREQI90_ALLFIELDS                 = 0xffff  
};  
typedef DWORD BPREQI_FIELDS90;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS90  
{  
    // VS 8.0 values  
    BPREQI90_BPLOCATION                = 0x0001,  
    BPREQI90_LANGUAGE                  = 0x0002,  
    BPREQI90_PROGRAM                   = 0x0004,  
    BPREQI90_PROGRAMNAME               = 0x0008,  
    BPREQI90_THREAD                    = 0x0010,  
    BPREQI90_THREADNAME                = 0x0020,  
    BPREQI90_PASSCOUNT                 = 0x0040,  
    BPREQI90_CONDITION                 = 0x0080,  
    BPREQI90_FLAGS                     = 0x0100,  
    BPREQI90_ALLOLDFIELDS              = 0x01ff,  
    BPREQI90_VENDOR                    = 0x0200,  
    BPREQI90_CONSTRAINT                = 0x0400,  
    BPREQI90_TRACEPOINT                = 0x0800,  
  
    // Values added in VS 9.0  
    BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
    BPREQI90_ALLFIELDS                 = 0xffff  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 BPREQI90_BPLOCATION  
 Inicializar o usar el `bpLocation` campo (ubicación de punto de interrupción) de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) o [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estructura.  
  
 BPREQI90_LANGUAGE  
 Inicializar o usar el `guidLanguage` campo de la `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` estructura.  
  
 BPREQI90_PROGRAM  
 Inicializar o usar el `pProgram` campo de la `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` estructura.  
  
 BPREQI90_PROGRAMNAME  
 Inicializar o usar el `bstrProgramName` campo de la `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` estructura.  
  
 BPREQI90_THREAD  
 Inicializar o usar el `pThread` campo de la `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` estructura.  
  
 BPREQI90_THREADNAME  
 Inicializar o usar el `bstrThreadName` campo de la `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` estructura.  
  
 BPREQI90_PASSCOUNT  
 Inicializar o usar el `bpPassCount` campo de la `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` estructura.  
  
 BPREQI90_CONDITION  
 Inicializar o usar el `bpCondition` campo (condición de punto de interrupción) de la `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` estructura.  
  
 BPREQI90_FLAGS  
 Inicializar o usar el `dwFlags` campo de la `BP_REQUEST_INFO` o `BP_REQUEST_INFO2` estructura.  
  
 BPREQI90_ALLOLDFIELDS  
 Inicializar o usar todos los campos de la de la `BP_REQUEST_INFO` estructura.  
  
 BPREQI90_VENDOR  
 Inicializar o usar el `guidVendor` campo `BP_REQUEST_INFO2` estructura.  
  
 BPREQI90_CONSTRAINT  
 Inicializar o usar el `bstrConstraint` campo `BP_REQUEST_INFO2` estructura.  
  
 BPREQI90_TRACEPOINT  
 Inicializar o usar el `bstrTracepoint` campo `BP_REQUEST_INFO2` estructura.  
  
 BPREQI90_MACROTRACEPOINT  
 Inicializar o usar el `bstrMacroTracepoint` campo `BP_REQUEST_INFO2` estructura. BPREQI_ALLFIELDS no incluye este campo.  
  
 BPREQI90_ALLFIELDS  
 Especifica todos los campos de la `BP_REQUEST_INFO2` estructura.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
