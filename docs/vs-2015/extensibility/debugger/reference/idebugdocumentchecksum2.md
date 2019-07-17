---
title: IDebugDocumentChecksum2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ba1510745b4781d56655fe83fffbb18f4ca65254
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156479"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Representa una suma de comprobación para un documento de depuración y permite pasar la suma de comprobación entre los componentes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugDocumentChecksum2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 Esta interfaz se puede implementar cualquier componente que expone el [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaz. Sin embargo, principalmente se implementa mediante motores de depuración para que la suma de comprobación incrustado en un archivo de símbolos (*.pdb) puede pasar hasta el IDE y usado al buscar un origen.  
  
## <a name="methods"></a>Métodos  
 La tabla siguiente muestran los métodos de `IDebugDocumentChecksum2`.  
  
|Método|DESCRIPCIÓN|  
|------------|-----------------|  
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Recupera el identificador de suma de comprobación y el algoritmo de documento dado el número máximo de bytes que se utilizará.|  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Msdbg.h  
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
