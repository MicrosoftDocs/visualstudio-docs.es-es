---
title: IDebugPortSupplierDescription2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c15facb38037272dcf2cef4f06d84d835b874012
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
Habilita la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] interfaz de usuario para mostrar el texto dentro de la **información de transporte** sección de la **adjuntar al proceso** cuadro de diálogo.  
  
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
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Recupera la descripción y los metadatos de la descripción para el proveedor del puerto.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll