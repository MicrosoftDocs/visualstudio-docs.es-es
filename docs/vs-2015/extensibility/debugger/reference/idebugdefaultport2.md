---
title: IDebugDefaultPort2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9367968f08116a21ea51fc1d0167fa57a5e3bd7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724495"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz proporciona varios métodos para acceder al servidor de un puerto y las facilidades de notificación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Visual Studio implementa esta interfaz para representar el puerto de depuración para tener acceso a programas. Un proveedor de puerto personalizado también puede implementar esta interfaz si controla la depuración remota.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Un argumento a los métodos en el [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interfaz proporciona esta interfaz. Una llamada a [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) en un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaz también puede obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 Además de los métodos definidos en [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), esta interfaz implementa los métodos siguientes:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Obtiene la interfaz de notificación de puerto de este puerto.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Obtiene la interfaz para el servidor que aloja este puerto.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Determina si este puerto se está ejecutando en el equipo local.|  
  
## <a name="remarks"></a>Comentarios  
 El nombre "`IDebugDefaultPort2`" es un poco de inapropiada, ya no representa un puerto predeterminado. Podría denominarse "IDebugPort3."  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)

