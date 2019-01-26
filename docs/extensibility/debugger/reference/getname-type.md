---
title: GETNAME_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6443c4c359562cc6b04ab413c31fb61441511ef4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916568"
---
# <a name="getnametype"></a>GETNAME_TYPE
Especifica el tipo de nombre de archivos que se va a recuperar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
typedef DWORD GETNAME_TYPE;  
```  
  
```csharp  
public enum enum_GETNAME_TYPE {   
   GN_NAME         = 0,  
   GN_FILENAME     = 1,  
   GN_BASENAME     = 2,  
   GN_MONIKERNAME  = 3,  
   GN_URL          = 4,  
   GN_TITLE        = 5,  
   GN_STARTPAGEURL = 6  
};  
```  
  
## <a name="members"></a>Miembros  
 GN_NAME  
 Especifica un nombre descriptivo del documento o del contexto.  
  
 GN_FILENAME  
 Especifica la ruta de acceso completa del documento o del contexto.  
  
 GN_BASENAME  
 Especifica un nombre de archivo base en lugar de una ruta de acceso completa del documento o del contexto.  
  
 GN_MONIKERNAME  
 Especifica un nombre único del documento o el contexto en el formulario de un moniker.  
  
 GN_URL  
 Especifica un nombre de la dirección URL del documento o del contexto.  
  
 GN_TITLE  
 Especifica un título del documento, si existe alguno.  
  
 GN_STARTPAGEURL  
 Obtiene la dirección URL de página inicial para los procesos.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se pasan como parámetros a la [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md), y [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) métodos para especificar qué tipo de nombre para devolver.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)