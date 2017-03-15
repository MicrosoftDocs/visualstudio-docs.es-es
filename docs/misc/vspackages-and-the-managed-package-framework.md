---
title: "VSPackages y marco de trabajo de paquetes administrados | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "marco de trabajo de paquetes administrados"
  - "VSPackages, marco de trabajo de paquetes administrados"
  - "VSPackages administrados, marco de trabajo de paquetes"
ms.assetid: e8d80e0f-6b5b-4baf-a7df-59fd808c60cd
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# VSPackages y marco de trabajo de paquetes administrados
Puede reducir el tiempo de desarrollo creando un VSPackage con clases de managed package en \(MPF\) lugar de usar clases de interoperabilidad COM.  
  
 hay dos maneras de crear un VSPackage administrado:  
  
-   Utilice la plantilla de proyecto paquete de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
     Para obtener más información, vea [Tutorial: Crear un comando de menú mediante la plantilla de paquete de Visual Studio](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
-   Compile el Paquete sin la plantilla de proyecto paquete de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
     Por ejemplo, puede copiar un ejemplo VSPackage y cambiar el GUID y los nombres.  Puede encontrar ejemplos en la sección VSX de [Galería de código](http://code.msdn.microsoft.com/vsx/).  
  
## En esta sección  
 [Clases de Managed Package Framework](../misc/managed-package-framework-classes.md)  
 Describe y muestra los espacios de nombres de la clase de MPF y los archivos DLL.  
  
## Secciones relacionadas  
 [Tutorial: Crear un comando de menú mediante la plantilla de paquete de Visual Studio](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md)  
 explica cómo crear un VSPackage administrado.  
  
 [VSPackages administrado](../misc/managed-vspackages.md)  
 Presenta aspectos de VSPackages que se aplican a código administrado.