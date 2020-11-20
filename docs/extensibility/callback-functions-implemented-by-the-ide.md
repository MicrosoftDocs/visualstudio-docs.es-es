---
title: Funciones de devolución de llamada implementadas por el IDE | Microsoft Docs
description: Obtenga información sobre las funciones de devolución de llamada a las que el complemento puede llamar en los momentos adecuados durante una operación de control de código fuente para pasar información al IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9dfb7e8b7e046c9587f591aec96a6a7fbd270865
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974456"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funciones de devolución de llamada implementadas por el IDE
Para que la integración con el entorno de desarrollo integrado (IDE) sea lo más fluida posible y proporcionar una experiencia de usuario final unificada, el complemento de control de código fuente puede usar funciones de devolución de llamada implementadas por el IDE. El complemento puede llamar a estas funciones en los momentos adecuados durante una operación de control de código fuente para pasar información al IDE; después, el IDE puede mostrar esta información como elementos incrustados en su interfaz de usuario nativa. El usuario tiene una experiencia menos fragmentada en este escenario que si el complemento empleó su propia interfaz de usuario.

 El archivo de encabezado necesario es *SCC. h*. La ubicación predeterminada es *\Archivos de Files\VSIP 8.0 \ \\ EnvSDK\common\inc*. También está en la carpeta VSIP que tiene el ejemplo de complemento de control de código fuente en *\Archivos de Files\VSIP 8.0 \\ \ MSSCCI*.

## <a name="in-this-section"></a>En esta sección
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Describe la función de devolución de llamada que usa [SccOpenProject](../extensibility/sccopenproject-function.md) para mostrar mensajes desde el complemento de control de código fuente a través del IDE.

- [POPLISTFUNC](../extensibility/poplistfunc.md) Describe la función de devolución de llamada que usa [SccPopulateList](../extensibility/sccpopulatelist-function.md) cuando el IDE no tiene acceso completo a la información que solo está disponible para el complemento de control de código fuente, como una lista completa de archivos bajo control de versiones.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Describe la función de devolución de llamada que usa la operación [SccQueryChanges](../extensibility/sccquerychanges-function.md) .

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Describe la función de devolución de llamada que usa la operación [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) .

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Describe la función de devolución de llamada establecida por una llamada a [SccSetOption](../extensibility/sccsetoption-function.md) que permite que el complemento de control de código fuente comunique los cambios de nombre al IDE.

## <a name="related-sections"></a>Secciones relacionadas
- [SccOpenProject](../extensibility/sccopenproject-function.md) Abre un proyecto.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Examina la lista de archivos en busca de su estado actual. Además, utiliza la `pfnPopulate` función para notificar al llamador cuando un archivo no coincide con los criterios de `nCommand` .

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Examina una lista de directorios y archivos de un proyecto o proyectos que están bajo control de código fuente. Cada nombre de archivo y directorio encontrado se pasa a una función de devolución de llamada.

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) Examina los cambios de nombre que se realizaron en una lista de archivos. Cada nombre de archivo se pasa a una función de devolución de llamada junto con su estado de cambio.

- [SccSetOption](../extensibility/sccsetoption-function.md) Establece una gran variedad de opciones. Cada opción comienza con `SCC_OPT_xxx` y tiene su propio conjunto de valores definido.

- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md) Describe el contenido de la sección de referencia del SDK del complemento de control de código fuente.
