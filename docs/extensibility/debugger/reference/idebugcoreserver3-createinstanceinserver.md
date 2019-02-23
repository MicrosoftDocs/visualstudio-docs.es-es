---
title: IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c570c7afe8721c757bae9352f70361d5b6cf392a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698448"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
Crea una instancia de un motor de depuración en el servidor.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreateInstanceInServer(
   LPCWSTR  szDll,
   WORD     wLangId,
   REFCLSID clsidObject,
   REFIID   riid,
   void**   ppvObject
);
```

```csharp
int CreateInstanceInServer(
   string     szDll,
   ushort     wLangID,
   ref Guid   clsidObject,
   ref Guid   riid,
   out IntPtr ppvObject
);
```

#### <a name="parameters"></a>Parámetros
 `szDll`

 [in] Ruta de acceso a la dll que implementa el CLSID especificado en el `clsidObject` parámetro. Si se trata de `NULL`, a continuación, COM `CoCreateInstance` se llama a la función.

 `wLangId`

 [in] Configuración regional del motor de depuración. Esto puede ser 0 si la [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) no se debe llamar al método.

 `clsidObject`

 [in] CLSID del motor de depuración para crear.

 `riid`

 [in] Id. de interfaz de la interfaz específica para recuperar desde el objeto de clase.

 `ppvObject`

 [out] `IUnknown` interfaz desde el objeto con instancias. Convertir o calcular las referencias de este objeto en la interfaz deseada.

## <a name="return-value"></a>Valor devuelto
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="see-also"></a>Vea también
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)