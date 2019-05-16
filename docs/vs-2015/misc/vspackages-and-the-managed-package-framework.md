---
title: VSPackages y Managed Package Framework | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework
- VSPackages, managed package framework
- managed VSPackages, managed package framework
ms.assetid: e8d80e0f-6b5b-4baf-a7df-59fd808c60cd
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: 5b72b2c3bd6b03d1d3f3e50135c2ddf4758a4bd9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683047"
---
# <a name="vspackages-and-the-managed-package-framework"></a>VSPackages y marco de trabajo de paquetes administrados
Puede reducir el tiempo de desarrollo mediante la creación de un paquete VSPackage con el paquete administrado de clases de framework (MPF) en lugar de mediante el uso de las clases de interoperabilidad COM.  
  
 Hay dos maneras de crear un VSPackage administrado:  
  
- Use el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] plantilla de proyecto de paquete  
  
     Para obtener más información, vea [Tutorial: Creación de un comando de menú mediante la plantilla de paquete de Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
- Crear el VSPackage sin el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] plantilla de proyecto de paquete  
  
     Por ejemplo, puede copiar un paquete de VS de ejemplo y cambiar los GUID y los nombres. Puede encontrar ejemplos en la sección VSX de [Galería de código](http://code.msdn.microsoft.com/vsx/).  
  
## <a name="in-this-section"></a>En esta sección  
 [Clases de Managed Package Framework](../misc/managed-package-framework-classes.md)  
 Describe y se enumeran los espacios de nombres de clase MPF y archivos DLL.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tutorial: Creación de un comando de menú mediante la plantilla de paquete de Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)  
 Explica cómo crear un VSPackage administrado.  
  
 [VSPackages administrado](../misc/managed-vspackages.md)  
 Presenta los aspectos de los paquetes VSPackage que se aplican a código administrado.