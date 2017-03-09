---
title: "Conservaci&#243;n de estado y el IDE de Visual Studio | Microsoft Docs"
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
  - "configuración de IDE, persistencia de estado"
  - "configuración de usuario [SDK de Visual Studio], conservar"
  - "páginas Opciones de herramientas [SDK de Visual Studio], conservar configuración"
  - "ID, conservación de estado"
  - "conservación, configuración de usuario"
ms.assetid: fdd49bb1-ed3b-4428-b685-de65c3215c1c
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# Conservaci&#243;n de estado y el IDE de Visual Studio
El comando de **Opciones para importar o exportar** en el menú de **Herramientas** del entorno de \(IDE\) desarrollo integrado importa y exporta las personalizaciones del entorno de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Los valores API de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] permiten a un VSPackage para definir una o más categorías de configuración \(grupos de variables de estado\) que se conservarán cuando un usuario elija el comando de **Opciones para importar o exportar** .  
  
 GUID identifica cada categoría de configuración y se define en su propia entrada del Registro, denominados como *punto de configuración personalizado*.  
  
> [!NOTE]
>  Las implementaciones estándar de las páginas de **HerramientasOpciones** , de **Cuadro de herramientas**, y de `Microsoft.VisualStudio.Shell.DialogPage` automáticamente proporcionan compatibilidad para la persistencia.  Los valores API pueden reemplazar el mecanismo predeterminado.  Para obtener más información, vea [Extensión del Cuadro de herramientas](../misc/extending-the-toolbox.md), [Páginas Opciones](../misc/options-pages.md) y <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
## En esta sección  
 [Compatibilidad con la configuración de usuario](../extensibility/internals/support-for-user-settings.md)  
 Describe los valores del registro \(punto de configuración personalizado\) y los atributos utilizados para especificar una implementación de los valores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilizada por un Paquete determinado.  
  
 [Cómo: Exportar configuración mediante ensamblados de interoperabilidad](../misc/how-to-export-settings-by-using-interop-assemblies.md)  
 Proporciona una descripción detallada de cómo implementar la compatibilidad para guardar datos de configuración utilizando el mecanismo de los valores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para la interoperabilidad VSPackages basado ensamblado.  
  
 [Cómo: Usar ensamblados de interoperabilidad para importar la configuración](../misc/how-to-use-interop-assemblies-to-import-settings.md)  
 Proporciona una descripción detallada de cómo implementar compatibilidad para recuperar datos de configuración utilizando el mecanismo de los valores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para la interoperabilidad VSPackages basado ensamblado.  
  
 [Exportación de configuración](../misc/exporting-settings.md)  
 Incluye una descripción detallada de cómo implementar la compatibilidad para guardar datos de configuración utilizando el mecanismo de los valores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para el paquete administrado VSPackages basado marco.  
  
 [Importación de la configuración](../misc/importing-settings.md)  
 Proporciona una descripción detallada de cómo implementar compatibilidad para recuperar datos de configuración utilizando el mecanismo de los valores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para el paquete administrado VSPackages basado marco.  
  
## Secciones relacionadas  
 [Working with Settings](http://msdn.microsoft.com/es-es/4c0a56ab-6091-4ebc-9dc7-52c40846bacb)  
 Describe cómo administrar las secciones de importación\/exportación del IDE.  
  
 [Páginas Opciones](../misc/options-pages.md)  
 Describe la compatibilidad que [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] proporciona automáticamente para administrar nuevas páginas existentes o que crean de **HerramientasOpciones** .  
  
 [Extensión del Cuadro de herramientas](../misc/extending-the-toolbox.md)  
 Explica la compatibilidad que [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] proporciona automáticamente para administrar o ampliar **Cuadro de herramientas**.  
  
 [Opciones y configuración de usuario de extensión](../extensibility/extending-user-settings-and-options.md)  
 Describe cómo programar el paquete VSPackage obtener y conservar las preferencias del usuario.