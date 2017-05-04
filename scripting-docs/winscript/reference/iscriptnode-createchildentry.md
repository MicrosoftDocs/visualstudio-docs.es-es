---
title: "IScriptNode:: CreateChildEntry | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode. CreateChildEntry
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::CreateChildEntry"
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# IScriptNode:: CreateChildEntry
Agrega una instancia secundaria de `IScriptEntry`.  
  
## Sintaxis  
  
```  
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### Parámetros  
 `isn`  
 \[in\] índice del elemento secundario del elemento primario.  
  
 `dwCookie`  
 \[in\] valor definido por la aplicación se utiliza para asociar la entrada secundaria con el objeto host.  
  
 `pszDelimiter`  
 \[in\] dirección del delimitador de FIN\-de\-script\- bloque.  Para analizar, el host normalmente utiliza un delimitador \(como dos comillas simples\), para detectar el final del bloque de script.  
  
 El delimitador permite al motor de creación de script para proporcionar el preprocesamiento.  Por ejemplo, el motor puede reemplazar una comilla simple con dos comillas sencillas para el uso como delimitador.  El motor determina cómo se utiliza el delimitador.  
  
 Establezca en NULL si un delimitador no marca el final del bloque de script.  
  
 `ppse`  
 \[out\] dirección de una variable que recibe un puntero a la interfaz de `IScriptEntry` de instancia secundaria.  
  
 Para los objetos de `IScriptNode` que representan una página Web, retornos de este parámetro una instancia de `IScriptEntry` que especifica un bloque de script.  
  
 Para los objetos de `IScriptEntry` que representan un bloque script, retornos de este parámetro una instancia de `IScriptEntry` que especifica un objeto de función.  
  
 Para los objetos de `IScriptEntry` que representan un objeto de función, error en este método.  
  
 Para los objetos de `IScriptScriptlet` , este método devuelve un error.  
  
## Valor devuelto  
 Interfaz `HRESULT`.  Los valores posibles son, pero no se limitan a, los de la tabla siguiente.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## Comentarios  
 La interfaz de `IScriptNode` representa una página Web o sus elementos.  La interfaz de `IScriptEntry` \(que se deriva de `IScriptNode`\) representa un bloque de script o un objeto de función.  La interfaz de `IScriptScriptlet` \(que se deriva de `IScriptEntry`\) representa un controlador de eventos.  
  
## Vea también  
 [IScriptNode \(Interfaz\)](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry \(Interfaz\)](../../winscript/reference/iscriptentry-interface.md)