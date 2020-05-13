---
title: Enumeradores de la casa de la página de la empresa Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee48d064612e5519d5ad7e5eaf04de6c5a697837
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711854"
---
# <a name="enumerators"></a>Enumerators
En esta sección se enumeran los tipos de datos del enumerador en la API de complemento de Control de código fuente que debe conocer el complemento de control de código fuente.

## <a name="in-this-section"></a>En esta sección
- [Código de comando](../extensibility/command-code-enumerator.md) Enumera las opciones para el [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) y [SccPopulateList](../extensibility/sccpopulatelist-function.md) funciones.

- [Mensaje](../extensibility/message-enumerator.md) Enumera los indicadores utilizados para la devolución de llamada de impresión, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

- [Código de estado del archivo](../extensibility/file-status-code-enumerator.md) Contiene valores constantes con nombre que especifican el estado de un archivo bajo control de código fuente.

- [Código de estado del directorio](../extensibility/directory-status-code-enumerator.md) Contiene valores constantes con nombre que especifican el estado de un directorio bajo control de código fuente.

## <a name="related-sections"></a>Secciones relacionadas
- [Crear un complemento de control de código fuente](../extensibility/internals/creating-a-source-control-plug-in.md) Define el SDK de complemento de Control de código fuente y describe los recursos incluidos.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) Solicita al usuario opciones avanzadas para el comando dado.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Examina la lista de archivos para su estado actual. Además, `pfnPopulate` utiliza la función para notificar al autor `nCommand`de la llamada cuando un archivo no coincide con los criterios para el archivo .

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Describe la función de devolución de llamada que usa [SccOpenProject](../extensibility/sccopenproject-function.md) para mostrar mensajes desde el complemento de control de código fuente a través del IDE.

- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md) Proporciona una lista completa de todos los elementos de la API de complemento de Control de código fuente.
