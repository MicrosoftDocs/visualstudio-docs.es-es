---
title: Funciones de devolución de llamada implementadas por el IDE Microsoft Docs
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
ms.openlocfilehash: 666486f5b800707a4467a129abeed7a13306f10a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739897"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funciones de devolución de llamada implementadas por el IDE
Para que la integración con el entorno de desarrollo integrado (IDE) sea lo más fluida posible y para proporcionar una experiencia de usuario final unificada, el complemento de control de código fuente puede usar funciones de devolución de llamada implementadas por el IDE. El complemento puede llamar a estas funciones en momentos adecuados durante una operación de control de código fuente para pasar información al IDE; el IDE puede mostrar esta información como elementos incrustados en su interfaz de usuario nativa. El usuario tiene una experiencia menos fragmentada en este escenario que si el complemento empleó su propia interfaz de usuario.

 El archivo de encabezado necesario es *scc.h*. La ubicación predeterminada es "Archivos de *programa", VSIP 8.0, EnvSDK, common, inc\\*. También se encuentra en la carpeta VSIP que tiene el ejemplo del complemento de control de código fuente en *.\\*

## <a name="in-this-section"></a>En esta sección
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Describe la función de devolución de llamada que usa [SccOpenProject](../extensibility/sccopenproject-function.md) para mostrar mensajes desde el complemento de control de código fuente a través del IDE.

- [POPLISTFUNC](../extensibility/poplistfunc.md) Describe la función de devolución de llamada que usa [SccPopulateList](../extensibility/sccpopulatelist-function.md) cuando el IDE no tiene acceso completo a la información que solo está disponible para el complemento de control de código fuente, como una lista completa de archivos bajo control de versiones.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Describe la función de devolución de llamada que usa la operación [SccQueryChanges.](../extensibility/sccquerychanges-function.md)

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Describe la función de devolución de llamada que utiliza la operación [SccPopulateDirList.](../extensibility/sccpopulatedirlist-function.md)

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Describe la función de devolución de llamada establecida por una llamada a la [SccSetOption](../extensibility/sccsetoption-function.md) que permite que el complemento de control de código fuente para comunicar los cambios de nombre al IDE.

## <a name="related-sections"></a>Secciones relacionadas
- [SccOpenProject](../extensibility/sccopenproject-function.md) Abre un proyecto.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Examina la lista de archivos para su estado actual. Además, `pfnPopulate` utiliza la función para notificar al autor `nCommand`de la llamada cuando un archivo no coincide con los criterios para el archivo .

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Examina una lista de directorios y archivos de un proyecto o proyectos que están bajo control de código fuente. Cada directorio y nombre de archivo encontrados se pasa a una función de devolución de llamada.

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) Examina los cambios de nombre realizados en una lista de archivos. Cada nombre de archivo se pasa a una función de devolución de llamada junto con su estado de cambio.

- [SccSetOption](../extensibility/sccsetoption-function.md) Establece una amplia variedad de opciones. Cada opción `SCC_OPT_xxx` comienza con y tiene su propio conjunto definido de valores.

- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md) Describe el contenido de la sección de referencia del SDK de complemento de Control de código fuente.
