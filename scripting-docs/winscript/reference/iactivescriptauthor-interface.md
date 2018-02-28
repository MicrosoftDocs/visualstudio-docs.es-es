---
title: IActiveScriptAuthor (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptAuthor interface
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37abb356ab24d64a05a1f1209809d63e2f55e228
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthor-interface"></a>IActiveScriptAuthor (Interfaz)
Representa la creación de servicios, incluido IntelliSense y la intercalación de la información.  
  
 Además de los métodos heredados de `IUnknown`, el `IActiveScriptAuthor` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Agrega el nombre de un elemento de nivel de raíz para el espacio de nombres del motor de creación de script. A *elemento de nivel raíz* es un objeto que puede contener métodos y propiedades, y que también puede contener un origen de eventos.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Agrega un Subscript de código como un elemento secundario del nivel raíz `IScriptNode` objeto. En el host, el nombre completo de la scriptlet puede tener sólo dos niveles.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Agrega una biblioteca de tipos para el espacio de nombres para la secuencia de comandos.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Devuelve el conjunto de caracteres de finalización para un contexto de finalización solicitada.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Devuelve el scriptlet que tiene los atributos especificados.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Devuelve el tipo información y las posiciones de delimitación para un carácter determinado en un bloque de código. Esto proporciona información de miembro de IntelliSense, las listas globales y sugerencias sobre parámetros.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Devuelve información del idioma.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Devuelve el `IScriptNode` raíz del árbol de secuencia de comandos del autor.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Devuelve los atributos de texto de un Subscript.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Devuelve los atributos de texto de un bloque de script.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Devuelve un valor que indica si un carácter dado debe confirmar la finalización de instrucciones por la aplicación.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Analiza el texto de la secuencia de comandos, agrega el texto al motor de creación de secuencia de comandos de creación y crea un `IScriptEntry` objeto que se corresponde con el bloque de script.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Quita un `NamedItem` objetos del espacio de nombres del motor de creación de script.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Quita una biblioteca de tipos del espacio de nombres del motor de creación del script.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Authoring (Interfaces)](../../winscript/reference/active-script-authoring-interfaces.md)