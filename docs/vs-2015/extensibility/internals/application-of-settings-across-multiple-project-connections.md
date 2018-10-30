---
title: Aplicación de configuración en varias conexiones de proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7f848c64072ebd77dfa3494b5dfc390c34855948
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940858"
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

