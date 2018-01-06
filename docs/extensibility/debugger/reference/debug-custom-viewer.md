---
title: DEBUG_CUSTOM_VIEWER | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEBUG_CUSTOM_VIEWER
helpviewer_keywords: DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5890e3942a9c571671784e5d7342bbb8530838ee
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="debugcustomviewer"></a>DEBUG_CUSTOM_VIEWER
Una estructura que identifica un visor personalizado o escriba el visualizador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct tagDEBUG_CUSTOM_VIEWER {  
   DWORD dwID;  
   BSTR  bstrMenuName;  
   BSTR  bstrDescription;  
   GUID  guidLang;  
   GUID  guidVendor;  
   BSTR  bstrMetric;  
} DEBUG_CUSTOM_VIEWER;  
```  
  
```csharp  
public struct DEBUG_CUSTOM_VIEWER {  
   public uint   dwID;  
   public string bstrMenuName;  
   public string bstrDescription;  
   public Guid   guidLang;  
   public Guid   guidVendor;  
   public string bstrMetric;  
};  
```  
  
## <a name="members"></a>Miembros  
 dwID  
 Un identificador para distinguir varios visores o visualizadores implementados por una `GUID`.  
  
 bstrMenuName  
 El texto que aparecerá en el menú desplegable.  
  
 bstrDescription  
 Descripción del visor personalizado o visualizador de tipo (debe ser un valor null si no usa).  
  
 guidLang  
 Idioma del evaluador de expresiones que proporcionan.  
  
 guidVendor  
 Proveedor del evaluador de expresiones que proporcionan.  
  
 bstrMetric  
 Métrica en la que el visor personalizado o el visualizador de tipo `CLSID` se almacena.  
  
## <a name="remarks"></a>Comentarios  
 Una lista de esta estructura es devuelto por una llamada a la [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) método (y, por extensión, el [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) método).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)