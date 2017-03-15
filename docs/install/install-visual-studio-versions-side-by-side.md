---
title: "Instalar distintas versiones de Visual Studio en paralelo | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "instalación simultánea [Visual Studio]"
  - "Ayuda [Visual Studio], instalación"
  - "Express Edition [Visual Studio]"
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
caps.handback.revision: 47
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# Instalar distintas versiones de Visual Studio en paralelo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede instalar esta versión de Visual Studio en un equipo que ya tiene una versión anterior instalada. Si se produce un error de instalación, puede usar la [herramienta de recopilación de registros](http://go.microsoft.com/fwlink/?LinkId=262077) para recopilar información sobre los errores de forma que pueda depurar los problemas usted mismo.  
  
> [!NOTE]
>  Se recomienda instalar las versiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en el orden en que se publicaron. Por ejemplo, instale Visual Studio 2013 antes de instalar Visual Studio 2015.  
  
 Antes de instalar versiones en paralelo, debe tener en cuenta los siguientes puntos:  
  
-   Si usa Visual Studio 2015 para abrir una solución creada en [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)], puede volver a abrir y modificar después la solución en la versión anterior siempre y cuando no haya implementado ninguna de las características que son específicas de Visual Studio 2015.  
  
-   Si intenta usar Visual Studio 2015 para abrir una solución creada en [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] o en una versión anterior, es posible que necesite modificar los proyectos y los archivos para que sean compatibles con Visual Studio 2015. Para más información, vea [Portar, migrar y actualizar proyectos de Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md).  
  
-   Si se desinstala una versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en un equipo que tiene más de una versión instalada, se quitan las asociaciones de archivo de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para todas las versiones. Estas asociaciones de archivo se pueden volver a asignar mediante el botón **Restaurar asociaciones de archivo** que está disponible en la página **Entorno**, **General** del cuadro de diálogo [Opciones](../ide/reference/general-environment-options-dialog-box.md).  
  
-   Visual Studio no actualiza automáticamente las extensiones porque no todas las extensiones son compatibles. Debe reinstalar las extensiones desde la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=178891) o el editor de software.  
  
## Versiones de .NET Framework e instalaciones en paralelo  
  
-   Los proyectos de Visual Basic, Visual C\# y Visual F\# utilizan la opción **Versión de .NET Framework de destino** del **Diseñador de proyectos** para especificar la versión de .NET Framework que utiliza un proyecto. En un proyecto de C\+\+, se puede cambiar manualmente la versión de .NET Framework de destino si se modifica el archivo .vcxproj. Para obtener más información, consulta [Compatibilidad de versiones](../Topic/Version%20Compatibility%20in%20the%20.NET%20Framework.md).  
  
     Cuando se crea un proyecto, se puede especificar la versión de .NET Framework a la que se dirige el proyecto en la lista **.NET Framework** del cuadro de diálogo **Nuevo proyecto**.  
  
     Para obtener información específica del lenguaje, vea el tema correspondiente en la tabla siguiente.  
  
    |Lenguaje|Tema|  
    |--------------|----------|  
    |[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]|[Aplicación \(Página, Diseñador de proyectos\) \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)|  
    |Visual C\#|[Página de aplicación, Diseñador de proyectos \(C\#\)](../ide/reference/application-page-project-designer-csharp.md)|  
    |Visual F\#|[Configurar proyectos](../Topic/Configuring%20Projects%20\(F%23\).md)|  
    |C\+\+|[Cómo: Modificar versión de .NET Framework de destino y el conjunto de herramientas de la plataforma](../Topic/How%20to:%20Modify%20the%20Target%20Framework%20and%20Platform%20Toolset.md)|  
    |[!INCLUDE[jsprjscript](../debugger/debug-interface-access/includes/jsprjscript_md.md)]|[Ejecutar una aplicación de JScript en una versión anterior de Common Language Runtime](http://msdn.microsoft.com/es-es/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|  
  
## Vea también  
 [Instalar Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)   
 [Portar, migrar y actualizar proyectos de Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)   
 [Compatibilidad de versiones](../Topic/Version%20Compatibility%20in%20the%20.NET%20Framework.md)   
 [Instalar varias versiones de idioma de Visual Studio](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)   
 [Compilar aplicaciones aisladas y ensamblados simultáneos de C\/C\+\+](/visual-cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies)   
 [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3)