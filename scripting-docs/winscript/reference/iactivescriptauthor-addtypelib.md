---
title: "IActiveScriptAuthor::AddTypeLib | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddTypeLib"
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptAuthor::AddTypeLib
Agrega una biblioteca de tipos al espacio de nombres para el script.  
  
## Sintaxis  
  
```  
HRESULT AddTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor,  
   DWORD     dwFlags  
);  
```  
  
#### Parámetros  
 `rguidTypeLib`  
 \[in\] CLSID \(identificador de clase\) de la biblioteca de tipos que se va a agregar.  
  
 `dwMajor`  
 \[in\] número de versión de principal de El.  
  
 `dwMinor`  
 \[in\] número de versión de lanzamiento de El.  
  
 `dwFlags`  
 \[in\] No se utiliza.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Este método llama a `LoadTypeLib` para cargar la biblioteca de tipos.  Sobre el correctamente, este método llama a `IActiveScriptAuthor::AddNamedItem` para agregar información de tipo.  
  
## Vea también  
 [IActiveScriptAuthor \(Interfaz\)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)   
 [LoadTypeLib](http://msdn.microsoft.com/es-es/155b48e5-5438-409e-9342-630a6a500f60)