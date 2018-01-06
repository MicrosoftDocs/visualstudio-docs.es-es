---
title: "Introducción a los complementos de Control de código fuente | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 197cc0f0997e80d6cae277c4b19c5bbc82dce805
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-source-control-plug-ins"></a>Introducción a los complementos de Control de código fuente
Para crear un control de código fuente complemento, debe crear un archivo DLL que implementa las funciones definidas en la API de complemento de Control de origen, y, a continuación, registrar la DLL con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para que esté disponible para su uso en el control de versiones de código de origen.  
  
 Tres versiones de la API de complemento de Control de origen (versiones 1.1, 1.2 y 1.3) están disponibles para los complementos de control de código fuente. La API de complementos de Control de código fuente mostradas aquí es la versión 1.3. Se diseñó para ser totalmente compatibles con los complementos de control de código fuente admite las versiones 1.1 y 1.2. El [What's New en la API de complemento de origen Control versión 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) sección detallan las nuevas características que se admiten en la versión más reciente de la API de complemento de Control de origen.  
  
## <a name="in-this-section"></a>En esta sección  
 [Instalación de un complemento de control de código fuente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Describe cómo hacer que las entradas del registro necesarias para conectar un archivo DLL del control de código fuente.  
  
 [Novedades de la API del complemento de control de código fuente, versión 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Proporciona una breve descripción de los cambios realizados en la API de complementos de Control de código fuente en la versión 1.3.  
  
 [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Proporciona una breve descripción de los cambios realizados en la API de complementos de Control de código fuente en la versión 1.2.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Complementos de control de código fuente](../../extensibility/source-control-plug-ins.md)  
 Proporciona una lista completa de todos los elementos de la API de complementos de Control de código fuente.  
  
 [Creación de un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Define el SDK de complemento de Control de origen y se describen los recursos incluidos.