---
title: VSPackages y el marco de trabajo de paquetes administrados | Microsoft Docs
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
ms.openlocfilehash: 84fb41bfc80415535ca41d6b1a8c9dcf47124c7a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298229"
---
# <a name="vspackages-and-the-managed-package-framework"></a>VSPackages y marco de trabajo de paquetes administrados
Puede reducir el tiempo de desarrollo creando un VSPackage con las clases de Managed Package Framework (MPF) en lugar de mediante clases de interoperabilidad COM.  
  
 Hay dos maneras de crear un VSPackage administrado:  
  
- Usar la plantilla de proyecto de paquete de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
     Para obtener más información, vea [Tutorial: crear un comando de menú mediante la plantilla de paquete de Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
- Compilar el VSPackage sin la plantilla de proyecto de paquete de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
     Por ejemplo, puede copiar un VSPackage de ejemplo y cambiar los GUID y los nombres. 
  
## <a name="in-this-section"></a>Esta sección  
 [Clases de Managed Package Framework](../misc/managed-package-framework-classes.md)  
 Describe y enumera los espacios de nombres de la clase MPF y los archivos DLL.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tutorial: crear un comando de menú mediante la plantilla de paquete de Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)  
 Explica cómo crear un VSPackage administrado.  
  
 [VSPackages administrado](../misc/managed-vspackages.md)  
 Presenta aspectos de los VSPackages que se aplican a código administrado.