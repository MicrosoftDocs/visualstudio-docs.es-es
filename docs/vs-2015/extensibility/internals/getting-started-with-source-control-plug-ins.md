---
title: Introducción a los complementos de Control de código fuente | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 56b38a1727d0ae859d12b1547e90705cdd6716e7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578462"
---
# <a name="getting-started-with-source-control-plug-ins"></a>Introducción a los complementos de control de código fuente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Introducción a los complementos de Control de código fuente](https://docs.microsoft.com/visualstudio/extensibility/internals/getting-started-with-source-control-plug-ins).  
  
Para crear un control de código fuente complemento, debe crear un archivo DLL que implementa las funciones definidas en la API de complemento de Control de código fuente, y, a continuación, registrar la DLL con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para que esté disponible para su uso en el control de versión de código fuente.  
  
 Las tres versiones de la API de complemento de Control de código fuente (versiones 1.1, 1.2 y 1.3) están disponibles para los complementos de control de código fuente. La API de complemento de Control de código fuente documentados aquí es la versión 1.3. Se ha diseñado para ser totalmente compatible con los complementos de control de código fuente que se admiten las versiones 1.1 y 1.2. El [Novedades en el Control de origen complemento API versión 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) sección describen las nuevas características admitidas en la versión más reciente de la API de complemento de Control de código fuente.  
  
## <a name="in-this-section"></a>En esta sección  
 [Instalación de un complemento de control de código fuente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Describe cómo hacer que las entradas del registro necesarias para conectar un archivo DLL de control de código fuente.  
  
 [Novedades de la API del complemento de control de código fuente, versión 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Proporciona una breve descripción de los cambios realizados en la API de complemento de Control de código fuente en la versión 1.3.  
  
 [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Proporciona una breve descripción de los cambios realizados en la API de complemento de Control de código fuente en la versión 1.2.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Complementos de control de código fuente](../../extensibility/source-control-plug-ins.md)  
 Proporciona una lista completa de todos los elementos de la API de complemento de Control de código fuente.  
  
 [Creación de un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Define el SDK de complemento de Control de origen y se describen los recursos incluidos.

