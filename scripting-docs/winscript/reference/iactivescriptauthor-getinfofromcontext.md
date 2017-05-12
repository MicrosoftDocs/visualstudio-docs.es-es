---
title: "IActiveScriptAuthor::GetInfoFromContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetInfoFromContext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetInfoFromContext"
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor::GetInfoFromContext
Especificado información de tipo y posiciones de delimitación por un carácter concreto en un bloque de código.  Esto proporciona información para el miembro IntelliSense, listas globales, y sugerencias de parámetro.  
  
## Sintaxis  
  
```  
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### Parámetros  
 `pszCode`  
 \[in\] la dirección de la cadena del bloque de código utilizada para generar información de resultados.  
  
 `cchCode`  
 \[in\] longitud del bloque de código.  
  
 `ichCurrentPosition`  
 \[in\] la posición de carácter de relación con el inicio del bloque.  
  
 `dwListTypesRequested`  
 \[in\] tipos de lista se solicitados.  Puede ser una combinación de los siguientes valores:  
  
|Constante|Valor|Descripción|  
|---------------|-----------|-----------------|  
|SCRIPT\_CMPL\_NOLIST|0x0000|Ninguna lista.|  
|SCRIPT\_CMPL\_MEMBERLIST|0x0001|Lista de miembros.|  
|SCRIPT\_CMPL\_ENUMLIST|0x0002|Lista de Enumeración.|  
|SCRIPT\_CMPL\_PARAMLIST|0x0004|Lista de parámetros de método de llamada.|  
|SCRIPT\_CMPL\_GLOBALLIST|0x0008|Lista global.|  
  
 Tratan el tipo de SCRIPT\_CMPL\_GLOBALLIST como elemento predeterminado de finalización que se puede combinar mediante el operador OR con otros elementos de finalización.  Los intentos del motor de creación de script primero para rellenar la información de tipo para otros elementos de lista de finalización.  Si se produce un error, el motor rellenan para SCRIPT\_CMPL\_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 \[out\] tipo de lista proporcionado.  
  
 `pichListAnchorPosition`  
 \[out\] índice inicial del contexto que contiene la posición actual.  Índice inicial es relativa al inicio del bloque.  
  
 Se rellena esto sólo cuando `dwListTypesRequested` incluye SCRIPT\_CMPL\_MEMBERLIST, SCRIPT\_CMPL\_ENUMLIST, o SCRIPT\_CMPL\_GLOBALLIST.  Para los otros tipos solicitados de la lista, el resultado son indefinidos.  
  
 `pichFuncAnchorPosition`  
 \[out\] índice inicial de la llamada de función que contiene la posición actual.  Índice inicial es relativa al inicio del bloque.  
  
 Se rellena esto sólo cuando el contexto que contiene la posición actual es una llamada de función, y cuando `dwListTypesRequested` incluye SCRIPT\_CMPL\_PARAMLIST.  Si no, el resultado es indefinido.  
  
 `pmemid`  
 \[out\] El MEMBERID de la función, definido por un tipo del parámetro de `IProvideMultipleClassInfo``ppunk` out.  
  
 Se rellena esto sólo cuando `dwListTypesRequested` incluye SCRIPT\_CMPL\_PARAMLIST.  
  
 `piCurrentParameter`  
 \[out\] índice del parámetro que contiene la posición actual.  Si la posición actual es en el nombre de la función, se devuelve \-1.  
  
 Se rellena el valor de `piCurrentParameter` cuando `dwListTypesRequested` incluye SCRIPT\_CMPL\_PARAMLIST.  
  
 `ppunk`  
 La información de tipo, que se proporciona en forma de objeto de `IProvideMultipleClassInfo` .  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
  
## Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideMultipleClassInfo>   
 [IActiveScriptAuthor \(Interfaz\)](../../winscript/reference/iactivescriptauthor-interface.md)