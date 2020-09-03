---
title: 'IDebugEngine3:: SetSymbolPath | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d3ea3086931ab655209a5ca26d4d1527462fb205
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476800"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Establece la ruta de acceso o rutas de acceso en las que se buscan símbolos de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
|`szSymbolSearchPath`|de Cadena que contiene las rutas de acceso de búsqueda de símbolos. Consulte "Comentarios" para obtener más información. No puede ser NULL.|  
|`szSymbolCachePath`|de Cadena que contiene la ruta de acceso local donde se pueden almacenar en caché los símbolos. No puede ser NULL.|  
|`Flags`|de No se utiliza; siempre se establece en 0.|  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Observaciones  
 La cadena `szSymbolSearchPath` es una lista de una o más rutas de acceso, separadas por punto y coma, para buscar símbolos. Estas rutas de acceso pueden ser una ruta de acceso local, una ruta de acceso de estilo UNC o una dirección URL. Estas rutas de acceso también pueden ser una combinación de tipos diferentes. Si la ruta de acceso es UNC (por ejemplo, \\ \Symserver\Symbols), el motor de depuración debe determinar si la ruta de acceso es a un servidor de símbolos y debe ser capaz de cargar los símbolos desde ese servidor, Caching en la ruta de acceso especificada por `szSymbolCachePath` .  
  
 La ruta de acceso de símbolos también puede contener una o varias ubicaciones de caché. Las cachés se muestran en orden de prioridad, con la caché de prioridad más alta primero y separadas por * símbolos. Por ejemplo:  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com  
```  
  
 El método [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) realiza la carga real de los símbolos.  
  
## <a name="see-also"></a>Consulte también  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
