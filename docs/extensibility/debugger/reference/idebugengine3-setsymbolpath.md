---
title: IDebugEngine3::SetSymbolPath ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fbe5128900fa10147c747cbcba4129e96d4c4ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730665"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Establece la ruta de acceso o las rutas de acceso que se buscan para los símbolos de depuración.

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

## <a name="parameters"></a>Parámetros

`szSymbolSearchPath`\
[en] Cadena que contiene la ruta de búsqueda de símbolos o rutas de acceso. Consulte "Comentarios" para obtener más información. No puede ser null.

`szSymbolCachePath`\
[en] Cadena que contiene la ruta de acceso local donde se pueden almacenar en caché los símbolos. No puede ser null.

`Flags`\
[en] No utilizado; siempre establecido en 0.

## <a name="return-value"></a>Valor devuelto
 Si se realiza correctamente, devuelve S_OK; de lo contrario devuelve un código de error.

## <a name="remarks"></a>Observaciones
 La `szSymbolSearchPath` cadena es una lista de una o más rutas de acceso, separadas por punto y coma, para buscar símbolos. Estas rutas de acceso pueden ser una ruta de acceso local, una ruta de acceso de estilo UNC o una dirección URL. Estas rutas también pueden ser una mezcla de diferentes tipos. Si la ruta de acceso \\es UNC (por ejemplo, "Symserver" o "Símbolos") , el motor de depuración debe determinar si `szSymbolCachePath`la ruta de acceso es a un servidor de símbolos y debe poder cargar símbolos desde ese servidor, almacenarlos en caché en la ruta especificada por .

 La ruta de acceso del símbolo también puede contener una o varias ubicaciones de caché. Las cachés se enumeran en orden de prioridad, con la caché de prioridad más alta primero y separadas por * símbolos. Por ejemplo:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 El método [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) realiza la carga real de los símbolos.

## <a name="see-also"></a>Vea también
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
