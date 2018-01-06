---
title: IDebugEngine3::LoadSymbols | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine3::LoadSymbols
helpviewer_keywords: IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 97509031e123babf5febfd51ebff3047e5d21ccf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Símbolos de carga (según sea necesario) para todos los módulos que se está depurados el motor de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```csharp  
int LoadSymbols();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Ninguno.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve el código de error.  
  
## <a name="remarks"></a>Comentarios  
 Esto carga de símbolos de depuración para todos los módulos al que hace referencia este motor de depuración. Los símbolos se cargan únicamente si no ya se han cargado. Símbolos se buscan en las rutas de acceso que se establece mediante una llamada a [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).  
  
## <a name="see-also"></a>Vea también  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)