---
title: Funciones de devolución de llamada implementadas por el IDE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dff6ee0a81472ea556aaca478a2ff33db93fe871
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321180"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funciones de devolución de llamada implementadas por el IDE
Para que la integración con el entorno de desarrollo integrado (IDE) como transparente como sea posible y para proporcionar una experiencia unificada para el usuario final, el complemento de control de origen puede usar las funciones de devolución de llamada que se implementan mediante el IDE. El complemento puede llamar a estas funciones en los momentos adecuados durante una operación de control de código fuente para pasar información a IDE; el IDE, a continuación, puede mostrar esta información como los elementos incrustados en su interfaz de usuario nativa. El usuario tiene una experiencia menos fragmentada en este escenario que si el complemento emplea su propia interfaz de usuario.

 El archivo de encabezado necesario es *scc.h*. La ubicación predeterminada es *\Program Files\VSIP 8.0\EnvSDK\common\inc\\* . También está en la carpeta VSIP que tiene el ejemplo de complemento de control de origen en *\Program Files\VSIP 8.0\MSSCCI\\* .

## <a name="in-this-section"></a>En esta sección
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) describe la función de devolución de llamada que se usa por [SccOpenProject](../extensibility/sccopenproject-function.md) para mostrar mensajes desde el complemento a través del IDE de control de origen.

- [POPLISTFUNC](../extensibility/poplistfunc.md) describe la función de devolución de llamada que se usa por [SccPopulateList](../extensibility/sccpopulatelist-function.md) cuando el IDE no tiene acceso completo a la información que solo está disponible para el complemento, por ejemplo, una lista completa de control de código fuente archivos bajo control de versiones.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) describe la función de devolución de llamada que usa el [SccQueryChanges](../extensibility/sccquerychanges-function.md) operación.

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) describe la función de devolución de llamada que usa el [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) operación.

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) describe la función de devolución de llamada definida por una llamada a la [SccSetOption](../extensibility/sccsetoption-function.md) que permite el control de código fuente complemento comunicarse realizar una copia de los cambios de nombre en el IDE.

## <a name="related-sections"></a>Secciones relacionadas
- [SccOpenProject](../extensibility/sccopenproject-function.md) abre un proyecto.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) examina la lista de archivos para su estado actual. Además, utiliza el `pfnPopulate` función para notificar al llamador cuando un archivo no coincide con los criterios para la `nCommand`.

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) examina una lista de directorios y archivos en un proyecto o proyectos que están bajo control de código fuente. Cada nombre de archivo y directorio que se encuentra se pasa a una función de devolución de llamada.

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) examina los cambios de nombre que se realizaron en una lista de archivos. Cada nombre de archivo se pasa a una función de devolución de llamada junto con su estado de cambio.

- [SccSetOption](../extensibility/sccsetoption-function.md) establece una amplia variedad de opciones. Cada opción se inicia con `SCC_OPT_xxx` y tiene su propio conjunto definido de valores.

- [Los complementos de Control de origen](../extensibility/source-control-plug-ins.md) describe el contenido de la sección de referencia del SDK de complemento de Control de origen.