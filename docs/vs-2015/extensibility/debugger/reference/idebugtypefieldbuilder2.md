---
title: IDebugTypeFieldBuilder2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2 interface
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 96241026afff71c061abcfae3547d25cc2166902
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987390"
---
# <a name="idebugtypefieldbuilder2"></a>IDebugTypeFieldBuilder2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
