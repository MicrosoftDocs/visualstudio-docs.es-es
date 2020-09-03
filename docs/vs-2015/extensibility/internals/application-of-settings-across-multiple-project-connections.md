---
title: Aplicación de la configuración en varias conexiones de proyecto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bca17fdc440fc373d0d4811ed57cd5d27a6c201a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203850"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Aplicación de configuración en varias conexiones de proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un complemento de control de código fuente creado mediante la API de complemento de control de código fuente 1,2, puede usar una operación por lotes para ejecutar la misma operación de control de código fuente en varios proyectos o contextos de conexión múltiples. Los lotes se pueden usar para eliminar los cuadros de diálogo redundantes por proyecto de la experiencia del usuario.  
  
 Si un usuario selecciona varios elementos que pertenecen a más de una conexión en un complemento de control de código fuente creado mediante la API de complemento de control de código fuente 1,1 (por ejemplo, dos proyectos web en diferentes máquinas de recursos compartidos de archivos) y los protege, el usuario verá el mismo cuadro de diálogo varias veces. Esto sucede incluso si el usuario hace clic en la casilla de verificación **aplicar a todo** del cuadro de diálogo, ya que el IDE restablece su estado para cada contexto de conexión.  
  
## <a name="new-capability-flag"></a>Nueva marca de capacidad  
 `SccBeginBatch` La función establece la `SCC_CAP_BATCH` marca para indicar que una operación por lotes está en curso.  
  
## <a name="new-functions"></a>Funciones nuevas  
 Las siguientes funciones nuevas admiten la operación por lotes:  
  
- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
- [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
  La `SCCBeginBatch` función inicia un grupo de operaciones de control de código fuente. `SccEndBatch` cierra el grupo. Los grupos no pueden estar anidados.  
  
## <a name="see-also"></a>Consulte también  
 [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
