---
title: IDebugEngine3::SetSymbolPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a307f0ad2493db88c94f3578afa171db3e47a5ae
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882447"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Establece la ruta de acceso o rutas de acceso que se buscan los símbolos de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```csharp  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`szSymbolSearchPath`|[in] Cadena que contiene la ruta de acceso de búsqueda de símbolos o rutas de acceso. Para obtener más información, vea "Comentarios". No puede ser NULL.|  
|`szSymbolCachePath`|[in] Cadena que contiene la ruta de acceso local donde se pueden almacenar en caché los símbolos. No puede ser NULL.|  
|`Flags`|[in] No se usa; siempre se establece en 0.|  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La cadena `szSymbolSearchPath` es una lista de una o varias rutas separadas por punto y coma, buscar símbolos. Estas rutas de acceso pueden ser una ruta de acceso local, una ruta de acceso de estilo UNC o una dirección URL. Estas rutas de acceso también pueden ser una combinación de distintos tipos. Si la ruta de acceso UNC (por ejemplo, \\\Symserver\Symbols), a continuación, el motor de depuración debe determinar si la ruta de acceso es un servidor de símbolos y debe ser capaz de cargar símbolos desde ese servidor, almacenarlos en memoria caché en la ruta de acceso especificada por `szSymbolCachePath`.  
  
 La ruta de acceso de símbolos también puede contener una o varias ubicaciones de memoria caché. Las memorias caché se enumeran en orden de prioridad, con la caché de prioridad más alta en primer lugar y separadas por * símbolos. Por ejemplo:  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 El [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) método realiza la carga real de los símbolos.  
  
## <a name="see-also"></a>Vea también  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)