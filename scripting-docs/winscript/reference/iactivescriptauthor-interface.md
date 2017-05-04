---
title: "IActiveScriptAuthor (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptAuthor (interfaz)"
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor (Interfaz)
Representa servicios de creación, con IntelliSense y la intercalación de la información.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `IActiveScriptAuthor` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Agrega el nombre de un elemento de nivel raíz al espacio de nombres del script del motor de creación.  *Un elemento de nivel de raíz* es un objeto que pueden contener propiedades y métodos, y que puede contener también un origen de eventos.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Agrega un scriptlet de código como elemento secundario del objeto de `IScriptNode` de nivel raíz.  En el host, el nombre completo del scriptlet sólo puede tener dos niveles.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Agrega una biblioteca de tipos al espacio de nombres para el script.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Devuelve el conjunto de caracteres de finalizaciones para un contexto solicitado de finalización.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Devuelve el scriptlet que tiene los atributos especificados.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Especificado información de tipo y posiciones de delimitación por un carácter concreto en un bloque de código.  Esto proporciona información para el miembro IntelliSense, listas globales, y sugerencias de parámetro.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Devuelve información del lenguaje.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Devuelve la raíz de `IScriptNode` de árbol de script author.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Devuelve los atributos de texto de un scriptlet.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Devuelve los atributos de texto de un bloque de script.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Devuelve un valor que indica si un carácter especificado debe confirmar una realización de extraer por la aplicación.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|El texto del script de los análisis, se agrega texto al motor de creación del script de creación, y crea un objeto de `IScriptEntry` que corresponde al bloque de script.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Quita un objeto de `NamedItem` del motor de creación de script.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Quita una biblioteca de tipos del espacio de nombres del motor de creación de script.|  
  
## Vea también  
 [Active Script Authoring \(Interfaces\)](../../winscript/reference/active-script-authoring-interfaces.md)