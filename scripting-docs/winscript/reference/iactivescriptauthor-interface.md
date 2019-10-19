---
title: Interfaz Iactivescriptauthor (| Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptAuthor interface
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed0734fa48d58a5eae779c75c838c09215ed60a0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576155"
---
# <a name="iactivescriptauthor-interface"></a>IActiveScriptAuthor (Interfaz)
Representa servicios de creación, incluidos IntelliSense e intercalación de información.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz de `IActiveScriptAuthor` expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|Agrega el nombre de un elemento de nivel de raíz al espacio de nombres del motor de creación de scripts. Un *elemento de nivel de raíz* es un objeto que puede contener propiedades y métodos, y que también puede contener un origen de eventos.|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|Agrega un Scriptlet de código como elemento secundario del nivel de raíz `IScriptNode` objeto. En el host, el nombre completo del Scriptlet solo puede tener dos niveles.|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|Agrega una biblioteca de tipos al espacio de nombres para el script.|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|Devuelve el conjunto de caracteres de finalización para un contexto de finalización solicitado.|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|Devuelve el Scriptlet que tiene los atributos especificados.|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|Devuelve la información de tipo y las posiciones de delimitador de un carácter determinado en un bloque de código. Esto proporciona información para IntelliSense de miembros, listas globales y sugerencias de parámetros.|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|Devuelve información de idioma.|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|Devuelve el `IScriptNode` raíz del árbol de script del autor.|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|Devuelve los atributos de texto de un Scriptlet.|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|Devuelve los atributos de texto de un bloque de script.|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|Devuelve un valor que indica si un carácter determinado debe confirmar una finalización de instrucciones por parte de la aplicación.|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|Analiza el texto del script, agrega el texto al motor de creación de scripts de creación y crea un objeto `IScriptEntry` que corresponde al bloque de script.|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|Quita un objeto `NamedItem` del espacio de nombres del motor de creación de scripts.|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|Quita una biblioteca de tipos del espacio de nombres del motor de creación de scripts.|  
  
## <a name="see-also"></a>Vea también  
 [Active Script Authoring (Interfaces)](../../winscript/reference/active-script-authoring-interfaces.md)