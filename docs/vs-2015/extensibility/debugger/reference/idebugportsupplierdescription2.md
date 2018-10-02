---
title: IDebugPortSupplierDescription2 | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 042cb2090f87a3b1453f31a833c584f7d30e5a13
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47565880"
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugPortSupplierDescription2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportsupplierdescription2).  
  
Habilita la [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] la interfaz de usuario para mostrar el texto dentro de la **información de transporte** sección de la **asociar al proceso** cuadro de diálogo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se implementa mediante proveedores de puertos.  
  
## <a name="methods"></a>Métodos  
 La tabla siguiente muestran los métodos de `IDebugPortSupplierDescription2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Recupera la descripción y los metadatos de descripción para el proveedor del puerto.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

