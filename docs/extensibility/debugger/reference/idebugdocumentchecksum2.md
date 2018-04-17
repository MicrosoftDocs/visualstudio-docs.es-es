---
title: IDebugDocumentChecksum2 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 068447399a8cfd43cb5fe07ea82e7cf4400f460c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Representa una suma de comprobación para un documento de depuración y permite pasar la suma de comprobación entre los componentes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugDocumentChecksum2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se puede implementar cualquier componente que expone el [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaz. Sin embargo, principalmente se implementa mediante motores de depuración para que pueda ser pasa hacia el IDE y usado al buscar un origen de la suma de comprobación que se incrusta en un archivo de símbolos (*.pdb).  
  
## <a name="methods"></a>Métodos  
 La tabla siguiente muestran los métodos de `IDebugDocumentChecksum2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Recupera el identificador de suma de comprobación y el algoritmo de documento dado el número máximo de bytes que se va a usar.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll