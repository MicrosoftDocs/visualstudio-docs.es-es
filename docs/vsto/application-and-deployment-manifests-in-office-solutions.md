---
title: Manifiestos de aplicación e implementación de soluciones de Office | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- manifests [Office development in Visual Studio]
- deployment manifests [Office development in Visual Studio]
- application manifests [Office development in Visual Studio]
- assemblies [Office development in Visual Studio], updating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9885f08db94cdbda7a0f8b531a6328ca2024466f
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Manifiestos de implementación y aplicación en soluciones de Office
  Un manifiesto de aplicación es un archivo XML que proporciona información que utiliza una solución de Office para buscar y actualizar sus ensamblados. Un manifiesto de aplicación puede utilizarse con un manifiesto de implementación, que es un archivo XML almacenado en el servidor que proporciona la información necesaria para encontrar la versión más reciente del manifiesto de aplicación y de los ensamblados.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="manifest-structure-for-office-solutions"></a>Estructura de manifiesto para soluciones de Office  
 Para las soluciones de Microsoft Office creadas con las herramientas de desarrollo de Office en Visual Studio, todos los manifiestos se basan en el esquema estándar de ClickOnce. Al implementar sus soluciones de Office, los manifiestos de aplicación de nivel de documento y de proyectos de complementos VSTO se encuentran en la caché de ClickOnce. Los manifiestos de implementación no se copian en el equipo cliente.  
  
 Para obtener información sobre el contenido de los manifiestos de aplicación e implementación de los proyectos de Office, consulte [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md) y [Deployment Manifests for Office Solutions](../vsto/deployment-manifests-for-office-solutions.md).  
  
## <a name="creating-application-and-deployment-manifests"></a>Crear manifiestos de aplicación e implementación  
 Los manifiestos de aplicación se crean automáticamente como parte del proceso de compilación. Cada vez que compila un proyecto de nivel de documento, la ubicación del manifiesto de implementación se incrusta en el documento como una propiedad de documento personalizada. Para los complementos VSTO, la ubicación del manifiesto de implementación se almacena en el registro.  
  
 Para obtener más información sobre la **Asistente para publicación de**, consulte [implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
 Para obtener más información acerca de cómo funcionan los manifiestos con las soluciones de Office, consulte [implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Vea también  
 [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md)   
 [Arquitectura de complementos VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Manifiesto de la implementación ClickOnce](/visualstudio/deployment/clickonce-deployment-manifest)  
  
  