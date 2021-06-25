---
title: Funciones de devolución de llamada implementadas por el IDE | Microsoft Docs
description: Obtenga información sobre las funciones de devolución de llamada a las que el complemento puede llamar en el momento adecuado durante una operación de control de código fuente para pasar información al IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 78ce3a9cdd183cff0518ee3c6da9326c63297a85
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899152"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funciones de devolución de llamada implementadas por el IDE
Para que la integración con el entorno de desarrollo integrado (IDE) sea lo más fluida posible y para proporcionar una experiencia unificada del usuario final, el complemento de control de código fuente puede usar funciones de devolución de llamada implementadas por el IDE. El complemento puede llamar a estas funciones en el momento adecuado durante una operación de control de código fuente para pasar información al IDE. A continuación, el IDE puede mostrar esta información como elementos incrustados en su interfaz de usuario nativa. El usuario tiene una experiencia menos fragmentada en este escenario que si el complemento empleara su propia interfaz de usuario.

 El archivo de encabezado necesario *es scc.h*. La ubicación predeterminada es *\Archivos de programa\VSIP 8.0\EnvSDK\common\inc \\*. También se encuentra en la carpeta VSIP que tiene el ejemplo de complemento de control de código fuente en \Archivos de *programa\VSIP 8.0\MSSCCI \\*.

## <a name="in-this-section"></a>En esta sección
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Describe la función de devolución de llamada que [usa SccOpenProject para](../extensibility/sccopenproject-function.md) mostrar mensajes desde el complemento de control de código fuente a través del IDE.

- [POPLISTFUNC](../extensibility/poplistfunc.md) Describe la función de devolución de llamada que usa [SccPopulateList](../extensibility/sccpopulatelist-function.md) cuando el IDE no tiene acceso completo a la información que solo está disponible para el complemento de control de código fuente, como una lista completa de archivos bajo control de versiones.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Describe la función de devolución de llamada que usa la [operación SccQueryChanges.](../extensibility/sccquerychanges-function.md)

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Describe la función de devolución de llamada que usa la [operación SccPopulateDirList.](../extensibility/sccpopulatedirlist-function.md)

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Describe la función de devolución de llamada establecida por una llamada a [SccSetOption](../extensibility/sccsetoption-function.md) que permite al complemento de control de código fuente comunicar los cambios de nombre al IDE.

## <a name="related-sections"></a>Secciones relacionadas
- [SccOpenProject](../extensibility/sccopenproject-function.md) Abre un proyecto.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Examina la lista de archivos para ver su estado actual. Además, usa la función para notificar al autor de la llamada cuando un `pfnPopulate` archivo no coincide con los criterios de `nCommand` .

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Examina una lista de directorios y archivos de un proyecto o proyectos que están bajo control de código fuente. Cada nombre de directorio y archivo encontrado se pasa a una función de devolución de llamada.

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) Examina los cambios de nombre que se realizaron en una lista de archivos. Cada nombre de archivo se pasa a una función de devolución de llamada junto con su estado de cambio.

- [SccSetOption](../extensibility/sccsetoption-function.md) Establece una amplia variedad de opciones. Cada opción comienza por `SCC_OPT_xxx` y tiene su propio conjunto definido de valores.

- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md) Describe el contenido de la sección de referencia del SDK del complemento de control de código fuente.
