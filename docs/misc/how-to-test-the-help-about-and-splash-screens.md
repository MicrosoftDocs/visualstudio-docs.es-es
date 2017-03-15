---
title: "C&#243;mo: probar la pantalla Ayuda - Acerca de y la pantalla de presentaci&#243;n | Microsoft Docs"
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
  - "Cuadro de diálogo Acerca de"
  - "paquetes VSPackage, pantallas de presentación"
  - "paquetes VSPackage, personalización de marca"
ms.assetid: 2b959fa4-56d3-44f4-8c2d-9ea2e6fb269d
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# C&#243;mo: probar la pantalla Ayuda - Acerca de y la pantalla de presentaci&#243;n
Después de implementar **Ayuda de Acerca de** y compatibilidad de la pantalla de presentación, puede probar la implementación en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### Para probar el cuadro de diálogo acerca de Ayuda  
  
1.  Símbolo del sistema de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , ejecute devenv.exe con el modificador **\/setup** .  Para ejecutar en el entorno experimental, escriba:  
  
     **devenv \/rootsuffix Exp \/setup**  
  
     **La nota** Se tiene que repetir este paso solo cuando se cambia la información de presentación de **Ayuda de Acerca de** .  
  
2.  Ejecute [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en la misma raíz del registro considerado mencionados anteriormente, pero sin el modificador **\/setup** :  
  
     **devenv \/rootsuffix Exp**  
  
3.  En el menú de **Ayuda** , haga clic **Acerca de Microsoft Visual Studio**.  
  
     el nombre de VSPackage aparece en la lista de **Productos instalados** .  
  
4.  Seleccione el Paquete de la lista.  
  
     la información de producto de VSPackage aparece en el cuadro de texto de **Detalles del producto** .  
  
### Para probar la pantalla de presentación  
  
1.  Ejecute devenv.exe con el modificador **\/setup** .  Para ejecutar en el entorno experimental, escriba:  
  
     **devenv \/rootsuffix Exp \/setup**  
  
     **La nota** Se tiene que repetir este paso solo cuando se cambia la información de la pantalla de presentación.  
  
2.  Ejecute [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en la misma raíz del registro considerado mencionados anteriormente, pero con el modificador **\/splash** en lugar del modificador de **\/setup** .  
  
     **devenv \/rootsuffix Exp \/splash**  
  
     la información y el logotipo de producto de VSPackage aparecen en la pantalla de presentación.  
  
## Vea también  
 [Personalización de marca de VSPackage](../misc/vspackage-branding.md)