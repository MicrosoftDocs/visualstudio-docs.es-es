---
title: IDebugProgramDestroyEventFlags2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 86f7e211c742e4d95f3459d058139854874e7d85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182216"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Permite que un motor de depuración invalide el comportamiento predeterminado de la [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] interfaz de usuario al finalizar una sesión de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugProgramDestroyEventFlags2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz la implementan los motores de depuración. Resulta útil para los hosts que pueden crear y destruir varios programas a lo largo de la duración de un proceso.  
  
## <a name="methods"></a>Métodos  
 En la tabla siguiente se muestran los métodos de `IDebugProgramDestroyEventFlags2` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Recupera las marcas de destrucción del programa.|  
  
## <a name="remarks"></a>Observaciones  
 El comportamiento predeterminado de la [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] interfaz de usuario es volver al modo de diseño después de que todos los programas hayan enviado un evento de destrucción de programas. Esta interfaz permite a un motor de depuración cambiar ese comportamiento.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
