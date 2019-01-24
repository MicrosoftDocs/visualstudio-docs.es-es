---
title: Introducción a los complementos de Control de código fuente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 829bf676a407fd166eda252cb4e6e2fbdb93fa41
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854508"
---
# <a name="get-started-with-source-control-plug-ins"></a>Introducción a los complementos de control de código fuente
Para crear un control de código fuente complemento, debe crear un archivo DLL que implementa las funciones definidas en la API de complemento de Control de código fuente, y, a continuación, registrar la DLL con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para que esté disponible para su uso en el control de versión de código fuente.  
  
 Las tres versiones de la API de complemento de Control de código fuente (versiones 1.1, 1.2 y 1.3) están disponibles para los complementos de control de código fuente. La API de complemento de Control de código fuente documentados aquí es la versión 1.3. Se ha diseñado para ser totalmente compatible con los complementos de control de código fuente que se admiten las versiones 1.1 y 1.2. El [cuáles son las novedades en el Control de origen complemento API versión 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) sección describen las nuevas características admitidas en la versión más reciente de la API de complemento de Control de código fuente.  
  
## <a name="in-this-section"></a>En esta sección  
 [Cómo: Instalar un complemento de control de código fuente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Describe cómo hacer que las entradas del registro necesarias para conectar un archivo DLL de control de código fuente.  
  
 [Novedades de la API de complemento origen Control versión 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Proporciona una breve descripción de los cambios realizados en la API de complemento de Control de código fuente en la versión 1.3.  
  
 [Novedades de la versión 1.2 de origen Control complemento de API](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Proporciona una breve descripción de los cambios realizados en la API de complemento de Control de código fuente en la versión 1.2.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Complementos de control de código fuente](../../extensibility/source-control-plug-ins.md)  
 Proporciona una lista completa de todos los elementos de la API de complemento de Control de código fuente.  
  
 [Crear un control de código fuente complemento](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Define el SDK de complemento de Control de origen y se describen los recursos incluidos.