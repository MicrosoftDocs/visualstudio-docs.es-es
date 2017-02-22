---
title: "IDebugPortSupplierDescription2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaz IDebugPortSupplierDescription2"
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplierDescription2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Permite que la interfaz de usuario de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] para mostrar texto dentro de la sección de **Información de transporte** del cuadro de diálogo de **Adjuntar a procesar** .  
  
## Sintaxis  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## Notas para los implementadores  
 Esta interfaz se implementa con los proveedores de puerto.  
  
## Métodos  
 La tabla siguiente se muestran los métodos de `IDebugPortSupplierDescription2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|Recupera la descripción y los metadatos de la descripción del proveedor de puerto.|  
  
## Requisitos  
 encabezado: Msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll