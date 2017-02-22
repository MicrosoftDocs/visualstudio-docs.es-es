---
title: "POPDIRLISTFUNC | Microsoft Docs"
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
  - "POPLISTFUNC"
helpviewer_keywords: 
  - "Función de devolución de llamada POPDIRLISTFUNC"
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta es una función de devolución de llamada a la [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) función para actualizar un conjunto de directorios y \(opcionalmente\) los nombres de archivo para comprobar que están bajo control de código fuente.  
  
 El `POPDIRLISTFUNC` devolución de llamada debe llamarse únicamente para los nombres de archivos y directorios \(en la lista proporcionada para el `SccPopulateDirList` función\) que en realidad está bajo control de código fuente.  
  
## Signature  
  
```cpp#  
typedef BOOL (*POPDIRLISTFUNC)( LPVOID pvCallerData, BOOL bFolder, LPCSTR lpDirectoryOrFileName );  
```  
  
## Parámetros  
 pvCallerData  
 \[in\] Valor del usuario [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 bcarpeta  
 \[in\] `TRUE` Si el nombre de `lpDirectoryOrFileName` es un directorio; de lo contrario, el nombre es un nombre de archivo.  
  
 lpDirectoryOrFileName  
 \[in\] Ruta de acceso local completa de un nombre de directorio o archivo que está bajo control de código fuente.  
  
## Valor devuelto  
 El IDE devuelve un código de error adecuado:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC\_OK|Continuar el procesamiento.|  
|SCC\_I\_OPERATIONCANCELED|Detener el procesamiento.|  
|SCC\_E\_xxx|Cualquier error de control de código fuente adecuada debe detener el procesamiento.|  
  
## Comentarios  
 Si el `fOptions` parámetro de la `SccPopulateDirList` función contiene el `SCC_PDL_INCLUDEFILES` marca, la lista posiblemente contiene nombres de archivo, así como nombres de directorio.  
  
## Vea también  
 [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Códigos de error](../extensibility/error-codes.md)