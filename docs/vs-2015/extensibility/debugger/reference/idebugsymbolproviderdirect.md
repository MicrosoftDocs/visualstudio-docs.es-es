---
title: IDebugSymbolProviderDirect | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d0586966564b0159dc0dd6d17b3e8f09f948157
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751681"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Representa un proveedor de símbolos que se tiene acceso directo a las interfaces de símbolos de metadatos y core.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugSymbolProviderDirect: IUnknown  
```  
  
## <a name="methods"></a>Métodos  
 Esta interfaz implementa los métodos siguientes:  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Recupera el identificador de dominio de aplicación dado la dirección de depuración.|  
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Recupera información acerca de los módulos en el grupo de símbolos.|  
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Recupera información sobre el grupo de símbolos de los cuales el proveedor de símbolos es un miembro.|  
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Recupera la información de la importación de metadatos.|  
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Recupera información sobre el método en la dirección de depuración especificado.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Recupera un lector de símbolos de código no administrado.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz puede usarse en lugar de la mayoría de las otras interfaces de proveedor de símbolos. Proporciona acceso directo a los metadatos y `CorSym` interfaces.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

