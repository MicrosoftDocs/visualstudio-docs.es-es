---
description: Representa una suma de comprobación para un documento de depuración y permite pasar la suma de comprobación entre componentes.
title: IDebugDocumentChecksum2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c5b39f381817cd98fd94b1c746cbdccde31e0b1f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102165571"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Representa una suma de comprobación para un documento de depuración y permite pasar la suma de comprobación entre componentes.

## <a name="syntax"></a>Syntax

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Cualquier componente que exponga la interfaz [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) puede implementar esta interfaz. Sin embargo, se implementa principalmente mediante motores de depuración, de modo que la suma de comprobación insertada en un archivo de símbolos (*. pdb) se puede devolver al IDE y usarse al buscar un origen.

## <a name="methods"></a>Métodos
 En la tabla siguiente se muestran los métodos de `IDebugDocumentChecksum2` .

|Método|Descripción|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Recupera la suma de comprobación del documento y el identificador del algoritmo según el número máximo de bytes que se van a utilizar.|

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg. h

 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
