---
title: GETNAME_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 648f84b106dab7aa6e38cc3e45e59162a216a875
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160135"
---
# <a name="getname_type"></a>GETNAME_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica el tipo de nombre de los archivos que se van a recuperar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 Especifica un nombre descriptivo del documento o contexto.  
  
 GN_FILENAME  
 Especifica la ruta de acceso completa del documento o contexto.  
  
 GN_BASENAME  
 Especifica un nombre de archivo base en lugar de una ruta de acceso completa del documento o contexto.  
  
 GN_MONIKERNAME  
 Especifica un nombre único del documento o contexto en forma de moniker.  
  
 GN_URL  
 Especifica un nombre de dirección URL del documento o contexto.  
  
 GN_TITLE  
 Especifica el título del documento, si existe.  
  
 GN_STARTPAGEURL  
 Obtiene la dirección URL de la página de inicio de los procesos.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se pasan como parámetros a los métodos [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)y [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) para especificar el tipo de nombre que se va a devolver.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName (](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName (](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)
