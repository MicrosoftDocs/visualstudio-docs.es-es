---
description: La sección de referencia incluye información general conceptual de la API, una guía que muestra la sintaxis y el uso de todos los elementos de la API, así como una serie de ejemplos de código.
title: Referencia de API (depuración de Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 47c6697945c6c588a8b4e57ab03d573d45c4d4cf
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102144642"
---
# <a name="api-reference-visual-studio-debugging"></a>Referencia de API (depuración de Visual Studio)
La sección de referencia incluye información general conceptual de la API, una guía que muestra la sintaxis y el uso de todos los elementos de la API, así como una serie de ejemplos de código. Todas las referencias se enumeran alfabéticamente por categoría.

 En la tabla siguiente se muestran los `HRESULT` valores comunes devueltos por los métodos.

|Nombre|Descripción|Valor|
|----------|-----------------|-----------|
|S_OK|Correcto.|0x00000000|
|E_UNEXPECTED|Error inesperado.|0x8000FFFF|
|E_NOTIMPL|Sin implementar.|0x80004001|
|E_OUTOFMEMORY|Memoria insuficiente para completar la operación.|0x8007000E|
|E_INVALIDARG|Uno o varios argumentos no son válidos.|0x80070057|
|E_NOINTERFACE|No se admite esta interfaz.|0x80004002|
|E_POINTER|Puntero no válido.|0x80004003|
|E_HANDLE|Identificador no válido.|0x80070006|
|E_ABORT|La operación se anuló.|0x80004004|
|E_FAIL|Error inesperado.|0x80004005|
|E_ACCESSDENIED|Error general de acceso denegado.|0x80070005|

> [!NOTE]
> Cuando se [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] devuelve un método de depuración `S_OK` , se supone que todos los punteros de parámetro de salida son válidos; es decir, no se realiza ninguna validación en los punteros de parámetro out cuando `S_OK` se devuelve.
>
> [!NOTE]
> Los parámetros no válidos o `NULL` [out] pueden hacer que el IDE se bloquee.

## <a name="see-also"></a>Consulte también
- [Interfaces](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Asistentes de SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Extensibilidad del depurador de Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
