---
title: Aplicación de la configuración en varias conexiones de proyecto | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710060"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Aplicación de la configuración en varias conexiones de proyecto
Un complemento de control de código fuente creado mediante la API de complemento de control de código fuente versión 1,2, puede usar una operación por lotes para ejecutar la misma operación de control de código fuente en varios proyectos o contextos de conexión múltiples. Los lotes se pueden usar para eliminar los cuadros de diálogo redundantes por proyecto de la experiencia del usuario.

 Si un usuario selecciona varios elementos que pertenecen a más de una conexión en un complemento de control de código fuente creado mediante la API del complemento de control de código fuente, versión 1,1 (por ejemplo, dos proyectos web en diferentes máquinas de recursos compartidos de archivos) y los protege, el usuario verá el mismo cuadro de diálogo varias veces. Este escenario se produce incluso si el usuario hace clic en la casilla de verificación **aplicar a todo** del cuadro de diálogo, ya que el IDE restablece su estado para cada contexto de conexión.

## <a name="new-capability-flag"></a>Nueva marca de capacidad
 La `SccBeginBatch` función establece la `SCC_CAP_BATCH` marca para indicar que una operación por lotes está en curso.

## <a name="new-functions"></a>Nuevas funciones
Las siguientes funciones nuevas admiten la operación por lotes:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

La `SCCBeginBatch` función inicia un grupo de operaciones de control de código fuente. La `SccEndBatch` función cierra el grupo. Los grupos no pueden estar anidados.

## <a name="see-also"></a>Vea también
- [Novedades de la API del complemento de control de código fuente versión 1,2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
