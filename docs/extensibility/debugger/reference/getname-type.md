---
title: "GETNAME_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GETNAME_TYPE"
helpviewer_keywords: 
  - "Enumeración GETNAME_TYPE"
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# GETNAME_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Especifica el tipo del nombre de archivos para recuperar.  
  
## Sintaxis  
  
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
  
```c#  
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
  
## Members  
 GN\_NAME  
 Especifica un nombre descriptivo del documento o del contexto.  
  
 GN\_FILENAME  
 Especifica la ruta de acceso completa del documento o del contexto.  
  
 GN\_BASENAME  
 Especifica un nombre de archivo base en lugar de una ruta de acceso completa del documento o del contexto.  
  
 GN\_MONIKERNAME  
 Especifica un nombre único del documento o del contexto en forma de moniker.  
  
 GN\_URL  
 Especifica el nombre de la dirección URL del documento o del contexto.  
  
 GN\_TITLE  
 Especifica un título del documento, si existe.  
  
 GN\_STARTPAGEURL  
 Obtiene la dirección URL de la página de inicio de los procesos.  
  
## Comentarios  
 Estos valores se pasan como parámetros a los métodos de [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), de [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md), y de [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) para especificar qué tipo de nombre a devolver.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)   
 [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)