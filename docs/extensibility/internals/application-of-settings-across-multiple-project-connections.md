---
title: Aplicación de configuración en varias conexiones de proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6dbc2638fa23a1e0c7bf1301c3c978a1ef864c75
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074104"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Aplicación de configuración en varias conexiones de proyecto
Un complemento de control de origen creados con el origen de Control de complemento de API versión 1.2, puede usar una operación por lotes para ejecutar la misma operación de control de código fuente a través de varios proyectos o varios contextos de conexión. Los lotes pueden utilizarse para eliminar redundantes, cuadros de diálogo de la experiencia del usuario por proyecto.

 Si un usuario selecciona varios elementos que pertenecen a más de una conexión en un complemento de control de código fuente creada con código fuente Control complemento API versión 1.1 (por ejemplo, dos proyectos web en el recurso compartido de archivos diferentes máquinas) y comprobaciones de ellas, el usuario ve el mismo cuadro de diálogo varias veces. Este escenario se produce incluso si el usuario hace clic en el **aplicar a todo** casilla de verificación en el cuadro de diálogo, dado que el IDE restablece su estado para cada contexto de conexión.

## <a name="new-capability-flag"></a>Nueva marca de capacidad
 El `SccBeginBatch` función establece el `SCC_CAP_BATCH` marca para indicar que una operación por lotes está en curso.

## <a name="new-functions"></a>Nuevas funciones
Las siguientes funciones nuevas admiten la operación por lotes:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

El `SCCBeginBatch` función inicia un grupo de operaciones de control de código fuente. El `SccEndBatch` función cierra el grupo. No se pueden anidar los grupos.

## <a name="see-also"></a>Vea también
- [Novedades de la versión 1.2 de origen Control complemento de API](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)