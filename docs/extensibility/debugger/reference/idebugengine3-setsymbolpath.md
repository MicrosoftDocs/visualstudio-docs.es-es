---
title: "IDebugEngine3::SetSymbolPath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::SetSymbolPath"
helpviewer_keywords: 
  - "IDebugEngine3::SetSymbolPath"
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugEngine3::SetSymbolPath
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Establece la ruta de acceso o rutas de acceso que se buscan símbolos de depuración.  
  
## Sintaxis  
  
```cpp#  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```c#  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`szSymbolSearchPath`|\[in\]  Cadena que contiene la ruta de búsqueda o rutas de acceso de símbolos.  Vea “notas” para obtener detalles.  No puede ser NULL.|  
|`szSymbolCachePath`|\[in\]  Cadena que contiene la ruta de acceso local donde los símbolos se pueden almacenar en caché.  No puede ser NULL.|  
|`Flags`|\[in\]  No se utiliza; establezca siempre a 0.|  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; si no devuelve un código de error.  
  
## Comentarios  
 La cadena`szSymbolSearchPath` es una lista de una o más rutas, separados por punto y coma, para buscar símbolos.  Estas rutas de acceso puede ser una ruta de acceso local, una ruta de UNC\-estilo, o una dirección URL.  Estas rutas también pueden ser una combinación de tipos diferentes.  Si la ruta de acceso es UNC \(por ejemplo, \\\\Symserver\\Symbols\), el motor de depuración debe determinar si la ruta de acceso a un servidor de símbolos y puede cargar símbolos de ese servidor, almacenándolos en caché en la ruta de acceso especificada por `szSymbolCachePath`.  
  
 La ruta de acceso de símbolos también puede contener una o más ubicaciones de memoria caché.  Cachés en orden de prioridad, con una caché de prioridad superior primero, y por independientes \* símbolos.  Por ejemplo:  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 El método de [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) realiza la carga real de los símbolos.  
  
## Vea también  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)