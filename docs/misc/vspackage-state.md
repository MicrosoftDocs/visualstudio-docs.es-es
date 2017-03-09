---
title: "Estado de VSPackage | Microsoft Docs"
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
  - "estado, paquetes VSPackage"
  - "paquetes VSPackage, administrar estado de la aplicación"
  - "persistencia de estado"
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
caps.handback.revision: 25
manager: "douge"
---
# Estado de VSPackage
Muchos factores determinan el conjunto de valores persistentes, o de estado, una aplicación de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
-   los proyectos tienen proyecto y propiedades de configuración.  
  
-   las Soluciones tienen propiedades.  
  
-   Los valores de usuario determinan el tamaño y la posición de ventanas de documento, de ventanas de herramientas, el estado de acoplamiento, y métodos abreviados de teclado.  
  
-   Las aplicaciones pueden tener valores que los conjuntos de usuarios.  
  
-   Los objetos que una aplicación realiza pueden tener propiedades específicas.  
  
 Algunas de las maneras que un estado de la aplicación de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] puede ser administrada:  
  
-   A través de las páginas de propiedades del proyecto y de solución.  
  
-   Con **Importar y exportar el asistente de configuración**, que permite a un usuario para mover valores de un equipo a otro.  
  
-   En el cuadro de diálogo de **Opciones** , que incluye las opciones relacionadas con las aplicaciones.  
  
-   En la ventana de **Propiedades** , que expone propiedades de objetos.  
  
-   Con automatización.  Una aplicación puede tener acceso a VSPackage y a propiedades de objetos que se han expuesto a la automatización.  
  
 Debajo del estado de la aplicación sea los distintos mecanismos de persistencia que habiliten el estado de la aplicación que se guardará y restaurada.  
  
## En esta sección  
 [Compatibilidad con la persistencia de estado](../misc/support-for-state-persistence.md)  
 Muestra las estrategias comunes para guardar, restaurar, y restaurar el estado de un Paquete.  
  
 [Opciones y páginas de opciones](../extensibility/internals/options-and-options-pages.md)  
 Presenta las páginas opciones generales y personalizadas y explica cómo implementarlos.  
  
 [Creación de una página de opciones](../extensibility/creating-an-options-page.md)  
 explica cómo crear dos páginas opciones, una página simple y una página personalizada.  
  
 [Compatibilidad con categorías de configuración](../misc/support-for-settings-categories.md)  
 Describe la configuración del usuario y cómo se crean y se conservan.  
  
 [Creación de una categoría de configuración](../extensibility/creating-a-settings-category.md)  
 Explica cómo crear una categoría de configuración de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y utilizarla para guardar la configuración y restablecer la configuración de un archivo de configuración.  
  
 [Extender propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md)  
 Explica cómo mostrar y cambie el valor de un objeto en la ventana de **Propiedades** .  
  
 [Expone las propiedades en la ventana Propiedades](../extensibility/exposing-properties-to-the-properties-window.md)  
 Explica cómo exponer las propiedades públicas de un objeto en la ventana de **Propiedades** .  
  
 [Soporte técnico para el proyecto y propiedades de configuración](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 Explica cómo mostrar y cambiar proyecto y propiedades de configuración.  
  
 [Obtener propiedades del proyecto](../extensibility/getting-project-properties.md)  
 Le conduce a través de los pasos de crear un VSPackage administrado que muestra las propiedades del proyecto en una ventana de herramientas.  
  
 [Utilizar el almacén de configuración](../extensibility/using-the-settings-store.md)  
 Explica el mecanismo de persistencia del almacén de configuración y cómo utilizarlo.  
  
## Secciones relacionadas  
 [VSPackages](../extensibility/internals/vspackages.md)  
 Proporciona una orientación general a temas que explican cómo crear y utilizar VSPackages.