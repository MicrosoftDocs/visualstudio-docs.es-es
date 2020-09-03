---
title: Enumeradores | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711854"
---
# <a name="enumerators"></a>Enumerators
En esta sección se enumeran los tipos de datos de enumerador de la API del complemento de control de código fuente que debe conocer el complemento de control de código fuente.

## <a name="in-this-section"></a>En esta sección
- [Código de comando](../extensibility/command-code-enumerator.md) Enumera las opciones de las funciones [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) y [SccPopulateList](../extensibility/sccpopulatelist-function.md) .

- [Mensaje](../extensibility/message-enumerator.md) de Enumera las marcas usadas para la devolución de llamada de impresión, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

- [Código de estado del archivo](../extensibility/file-status-code-enumerator.md) Contiene valores constantes con nombre que especifican el estado de un archivo bajo control de código fuente.

- [Código de estado del directorio](../extensibility/directory-status-code-enumerator.md) Contiene valores constantes con nombre que especifican el estado de un directorio bajo control de código fuente.

## <a name="related-sections"></a>Secciones relacionadas
- [Crear un complemento de control de código fuente](../extensibility/internals/creating-a-source-control-plug-in.md) Define el SDK del complemento de control de código fuente y describe los recursos incluidos.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) Solicita al usuario opciones avanzadas para el comando especificado.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Examina la lista de archivos en busca de su estado actual. Además, utiliza la `pfnPopulate` función para notificar al llamador cuando un archivo no coincide con los criterios de `nCommand` .

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Describe la función de devolución de llamada que usa [SccOpenProject](../extensibility/sccopenproject-function.md) para mostrar mensajes desde el complemento de control de código fuente a través del IDE.

- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md) Proporciona una lista completa de todos los elementos de la API del complemento de control de código fuente.
