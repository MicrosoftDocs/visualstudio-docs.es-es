---
title: 'IDebugCoreServer3:: GetServerFriendlyName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fa81daf7ab1d592e6a2cd460268e5d66925f61e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842510"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera un nombre descriptivo para el servidor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetServerFriendlyName(  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetServerFriendlyName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pbstrName`  
 enuncia Devuelve un nombre descriptivo para el servidor.  
  
> [!NOTE]
> El autor de la llamada es responsable de liberar la cadena.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve el código de error.  
  
## <a name="remarks"></a>Notas  
 En el caso de los servidores iniciados por el usuario, el nombre devuelto por este método es el nombre completo del servidor. En el caso de los servidores iniciados automáticamente, el nombre es el del equipo en el que se está ejecutando el servidor.  
  
 Para un nombre orientado al equipo, llame al método [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) .  
  
## <a name="see-also"></a>Consulte también  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)
