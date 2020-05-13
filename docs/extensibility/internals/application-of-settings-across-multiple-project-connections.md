---
title: Aplicación de la configuración a través de múltiples conexiones de proyecto ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bcaed0f7f2380dd36bcbffd776839025fe9efa16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710060"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Aplicación de la configuración en varias conexiones de proyecto
Un complemento de control de código fuente creado con la versión 1.2 de la API de complemento de Control de código fuente, puede usar una operación por lotes para ejecutar la misma operación de control de código fuente en varios proyectos o varios contextos de conexión. Los lotes se pueden usar para eliminar cuadros de diálogo redundantes por proyecto de la experiencia del usuario.

 Si un usuario selecciona varios elementos que pertenecen a más de una conexión en un complemento de control de código fuente creado mediante la versión 1.1 de la API de complemento de Control de código fuente (por ejemplo, dos proyectos web en equipos de recurso compartido de archivos diferentes) y los desprotege, el usuario ve el mismo cuadro de diálogo repetidamente. Este escenario se produce incluso si el usuario hace clic en la casilla de verificación **Aplicar a todos** en el cuadro de diálogo, porque el IDE restablece su estado para cada contexto de conexión.

## <a name="new-capability-flag"></a>Nueva bandera de capacidad
 La `SccBeginBatch` función `SCC_CAP_BATCH` establece el indicador para indicar que una operación por lotes está en curso.

## <a name="new-functions"></a>Nuevas funciones
Las siguientes funciones nuevas admiten la operación por lotes:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

La `SCCBeginBatch` función inicia un grupo de operaciones de control de código fuente. La `SccEndBatch` función cierra el grupo. Es posible que los grupos no estén anidados.

## <a name="see-also"></a>Vea también
- [Novedades de la API de complemento de Control de código fuente versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
