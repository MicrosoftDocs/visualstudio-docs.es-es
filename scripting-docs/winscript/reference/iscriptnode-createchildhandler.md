---
title: "IScriptNode::CreateChildHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.CreateChildHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::CreateChildHandler"
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IScriptNode::CreateChildHandler
Agrega un scriptlet como instancia secundaria de `IScriptNode`.  
  
## Sintaxis  
  
```  
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### Parámetros  
 `pszDefaultName`  
 \[in\] dirección del nombre predeterminado para asociar al scriptlet.  
  
 `prgpszNames`  
 \[in, size\_is \(`cpszNames`\)\] Una lista de identificadores de nombre completo en el host.  
  
 `cpszNames`  
 \[in\] número de identificadores del parámetro de `prgpszNames` .  
  
 `pszEvent`  
 \[in\] la dirección del búfer a El que identifica el nombre de evento asociado al scriptlet.  
  
 `pszDelimiter`  
 \[in\] dirección del delimitador de FIN\-de\-script\- bloque.  Para analizar, el host normalmente utiliza un delimitador \(como dos comillas simples\), para detectar el final del bloque de script.  
  
 El delimitador habilita el preprocesamiento por el motor de creación de script.  Por ejemplo, el motor puede reemplazar una comilla simple con dos comillas sencillas para el uso como delimitador.  El motor determina cómo se utiliza el delimitador.  
  
 Establezca en NULL si no se usa ningún delimitador para identificar el final del bloque de script.  
  
 `ptiSignature`  
 \[in\] información de tipo para obtener un objeto de función.  
  
 `iMethodSignature`  
 \[in\] índice de la función en el parámetro de `ITypeInfo``ptiSignature` .  
  
 `isn`  
 \[in\] índice del elemento secundario del elemento primario.  
  
 `dwCookie`  
 \[in\] valor definido por la aplicación que se usa para asociar la entrada al objeto host.  
  
 `ppse`  
 \[out\] dirección de una variable que recibe un puntero a la interfaz de `IScriptEntry` de instancia secundaria.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 Un scriptlet especifica un controlador de eventos.  Este método crea un scriptlet si lo llama un objeto de `IScriptNode` que representa una página Web.  Este método no tiene éxito si llama otras interfaces.  
  
## Vea también  
 [IScriptNode \(Interfaz\)](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry \(Interfaz\)](../../winscript/reference/iscriptentry-interface.md)