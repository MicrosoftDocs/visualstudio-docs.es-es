---
title: VSPackages y Managed Package Framework | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed package framework
- VSPackages, managed package framework
- managed VSPackages, managed package framework
ms.assetid: e8d80e0f-6b5b-4baf-a7df-59fd808c60cd
caps.latest.revision: 16
manager: douge
ms.openlocfilehash: 2e265a342ec32abea40ab9b352b5735079462a46
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227986"
---
# <a name="vspackages-and-the-managed-package-framework"></a>VSPackages y marco de trabajo de paquetes administrados
Puede reducir el tiempo de desarrollo mediante la creación de un paquete VSPackage con el paquete administrado de clases de framework (MPF) en lugar de mediante el uso de las clases de interoperabilidad COM.  
  
 Hay dos maneras de crear un VSPackage administrado:  
  
-   Use el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] plantilla de proyecto de paquete  
  
     Para obtener más información, consulte [Tutorial: crear un comando al menú mediante la plantilla de paquete de Visual Studio](http://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
-   Crear el VSPackage sin el [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] plantilla de proyecto de paquete  
  
     Por ejemplo, puede copiar un paquete de VS de ejemplo y cambiar los GUID y los nombres. Puede encontrar ejemplos en la sección VSX de [Galería de código](http://code.msdn.microsoft.com/vsx/).  
  
## <a name="in-this-section"></a>En esta sección  
 [Clases de Managed Package Framework](../misc/managed-package-framework-classes.md)  
 Describe y se enumeran los espacios de nombres de clase MPF y archivos DLL.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tutorial: Crear un comando de menú mediante la plantilla de paquete de Visual Studio](http://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)  
 Explica cómo crear un VSPackage administrado.  
  
 [VSPackages administrado](../misc/managed-vspackages.md)  
 Presenta los aspectos de los paquetes VSPackage que se aplican a código administrado.