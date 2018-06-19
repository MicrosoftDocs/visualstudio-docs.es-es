---
title: Aplicación de la configuración en varias conexiones de proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0dff30ea80fb2de9bf4d90ffa48cd2f9b3d40756
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129211"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Aplicación de la configuración en varias conexiones de proyecto
Un complemento de control de origen creados con 1.2 de API de complemento de Control de origen, puede usar una operación por lotes para ejecutar la misma operación de control de código fuente en varios proyectos o varios contextos de conexión. Lotes pueden usarse para eliminar redundantes, cuadros de diálogo de la experiencia del usuario por proyecto.  
  
 Si un usuario selecciona varios elementos que pertenecen a más de una conexión en un complemento de control de código fuente creada con la API complemento origen Control 1.1, (por ejemplo, dos proyectos Web de recurso compartido de archivos diferentes máquinas) y comprueba su salida, el usuario ve el mismo cuadro de diálogo varias veces. Esto ocurre incluso si el usuario hace clic en el **aplicar a todos los** casilla de verificación en el cuadro de diálogo, porque el IDE restablece su estado para cada contexto de conexión.  
  
## <a name="new-capability-flag"></a>Nueva marca de capacidad  
 `SccBeginBatch` Función establece el `SCC_CAP_BATCH` marca para indicar que una operación por lotes está en curso  
  
## <a name="new-functions"></a>Nuevas funciones  
 Las nuevas funciones siguientes admiten la operación por lotes:  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 El `SCCBeginBatch` función inicia un grupo de operaciones de control de código fuente. `SccEndBatch` cierra el grupo. No se pueden anidar los grupos.  
  
## <a name="see-also"></a>Vea también  
 [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)