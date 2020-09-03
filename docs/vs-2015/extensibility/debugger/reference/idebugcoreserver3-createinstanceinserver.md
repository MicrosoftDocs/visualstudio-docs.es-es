---
title: 'IDebugCoreServer3:: CreateInstanceInServer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1d8964a79aaeb7b90dfbc809ec547d0282d79fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205266"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea una instancia de un motor de depuración en el servidor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 de Ruta de acceso al archivo DLL que implementa el CLSID especificado en el `clsidObject` parámetro. Si es `NULL` , se llama a la `CoCreateInstance` función de com.  
  
 `wLangId`  
 de Configuración regional del motor de depuración. Puede ser 0 si no se debe llamar al método [setlocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) .  
  
 `clsidObject`  
 de CLSID del motor de depuración que se va a crear.  
  
 `riid`  
 de IDENTIFICADOR de interfaz de la interfaz específica que se va a recuperar del objeto de clase.  
  
 `ppvObject`  
 [out] `IUnknown` interfaz del objeto con instancias. Convierta este objeto en la interfaz deseada.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
