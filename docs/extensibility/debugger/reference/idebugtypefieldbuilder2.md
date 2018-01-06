---
title: IDebugTypeFieldBuilder2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0f671087c5d7a97340ff47cee2954426f35a7170
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
Extiende la **IDebugTypeFieldBuilder** para poder crear tipos de matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder  
```  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz puede obtenerse desde el proveedor de símbolos.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos en el [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) interfaz, esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Crea una matriz del tipo especificado y el tamaño.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll