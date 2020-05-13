---
title: IDebugDocumentChecksum2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03cfb29cc54a2f0ab18bce3ec0761cfab62e20df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731898"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Representa una suma de comprobación para un documento de depuración y permite pasar la suma de comprobación entre componentes.

## <a name="syntax"></a>Sintaxis

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para los implementadores
 Esta interfaz se puede implementar por cualquier componente que expone el [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaz. Sin embargo, los motores de depuración lo implementan principalmente para que la suma de comprobación incrustada en un archivo de símbolos (*.pdb) se pueda devolver al IDE y se use al buscar un origen.

## <a name="methods"></a>Métodos
 En la tabla siguiente `IDebugDocumentChecksum2`se muestran los métodos de .

|Método|Descripción|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Recupera la suma de comprobación del documento y el identificador del algoritmo dado el número máximo de bytes que se van a utilizar.|

## <a name="requirements"></a>Requisitos
 Encabezado: Msdbg.h

 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll
