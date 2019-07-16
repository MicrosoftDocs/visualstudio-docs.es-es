---
title: Aplicación de configuración en varias conexiones de proyecto | Microsoft Docs
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203850"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Aplicación de configuración en varias conexiones de proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un complemento de control de origen creados con el complemento de API de origen Control 1.2, puede usar una operación por lotes para ejecutar la misma operación de control de código fuente a través de varios proyectos o varios contextos de conexión. Los lotes pueden utilizarse para eliminar redundantes, cuadros de diálogo de la experiencia del usuario por proyecto.  
  
 Si un usuario selecciona varios elementos que pertenecen a más de una conexión en un complemento de control de código fuente creada con código fuente Control complemento API 1.1, (por ejemplo, dos proyectos Web en el recurso compartido de archivos diferentes máquinas) y comprobaciones de ellas, el usuario ve el mismo cuadro de diálogo de forma repetida. Esto ocurre incluso si el usuario hace clic en el **aplicar a todo** casilla de verificación en el cuadro de diálogo, dado que el IDE restablece su estado para cada contexto de conexión.  
  
## <a name="new-capability-flag"></a>Nueva marca de capacidad  
 `SccBeginBatch` Función establece el `SCC_CAP_BATCH` marca para indicar que una operación por lotes está en curso  
  
## <a name="new-functions"></a>Nuevas funciones  
 Las siguientes funciones nuevas admiten la operación por lotes:  
  
- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
- [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
  El `SCCBeginBatch` función inicia un grupo de operaciones de control de código fuente. `SccEndBatch` cierra el grupo. No se pueden anidar los grupos.  
  
## <a name="see-also"></a>Vea también  
 [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
