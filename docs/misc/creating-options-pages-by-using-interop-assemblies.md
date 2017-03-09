---
title: "Crear p&#225;ginas de opciones mediante ensamblados de interoperabilidad | Microsoft Docs"
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
  - "páginas de opciones de herramientas [SDK de Visual Studio], crear con ensamblados de interoperabilidad"
  - "ensamblados de interoperabilidad, crear páginas de opciones de herramientas"
ms.assetid: 7a03f2f5-a53e-4a46-877f-5b10dd82dbc3
caps.latest.revision: 30
caps.handback.revision: 30
manager: "douge"
---
# Crear p&#225;ginas de opciones mediante ensamblados de interoperabilidad
Los paquetes VSPackage administrados pueden usar ensamblados de interoperabilidad basados en COM del [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] para ampliar el entorno de desarrollo integrado \(IDE\) de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] agregando las páginas **Opciones** al menú **Herramientas**.  
  
 Una página **Opciones de herramientas** es fundamentalmente un control de usuario y está codificada de la misma forma que cualquier otro control de usuario. Normalmente, usaría uno de los diseñadores del IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para crear el objeto y agregar controles de usuario.  
  
> [!NOTE]
>  Una página **Opciones de herramientas** implementada como un cuadro de diálogo, con una función DialogProc para controlar mensajes de Windows, debe ser un cuadro de diálogo no modal y no debe llamar a la función EndDialog.  
  
 Debe usar el objeto de automatización que el VSPackage proporciona al entorno para admitir las propiedades que muestra el control de usuario.  
  
 Un VSPackage que implemente una página **Opciones de herramientas** puede admitir el control mediante programación de sus propiedades directamente o a través del modelo de automatización del IDE. Para obtener más información sobre la compatibilidad de las páginas **Opciones de herramientas** con la automatización, consulte [Crear páginas de opciones mediante automatización](../misc/creating-options-pages-by-using-automation.md).  
  
## Disponibilidad de las páginas Opciones de herramientas en el IDE  
 Además de implementar un control de usuario, los paquetes VSPackage deben hacer que ese control esté disponible en el IDE.  
  
 Esto se realiza a través de la implementación del método <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>, que devuelve una estructura <xref:Microsoft.VisualStudio.Shell.Interop.VSPROPSHEETPAGE> basada en el GUID que se pasó.  
  
 El IDE usa la estructura <xref:Microsoft.VisualStudio.Shell.Interop.VSPROPSHEETPAGE> para establecer las características de una página **Propiedades**.  
  
 La configuración contenida en su miembro `dwFlags` determina la interpretación exacta de los otros miembros de <xref:Microsoft.VisualStudio.Shell.Interop.VSPROPSHEETPAGE>. Normalmente, la estructura proporciona:  
  
-   Un identificador para la instancia desde la que se va a cargar un recurso de icono o de cadena.  
  
-   El identificador de recursos de las plantillas de cuadro de diálogo de la página.  
  
-   Un puntero a la función DialogProc de la página.  
  
## Registro de una página Opciones de herramientas  
 Puede registrar una página **Opciones de herramientas** mediante la creación de una entrada en la siguiente ubicación del Registro: HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<versión\>*\\ToolsOptionsPages, donde *\<versión\>* es la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], como 8.0.  
  
 Para registrar la página, puede editar manualmente el Registro o usar un script del Registro \(archivo .rgs\). Para obtener más información, consulta [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts).  
  
## Vea también  
 [Ampliar el entorno de Visual Studio](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)   
 [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts)   
 [Compatibilidad de automatización para las páginas de opciones](../extensibility/internals/automation-support-for-options-pages.md)   
 [Usar páginas de opciones](../misc/using-options-pages.md)   
 [Crear páginas de opciones](../extensibility/internals/creating-options-pages.md)   
 [Crear páginas de opciones mediante automatización](../misc/creating-options-pages-by-using-automation.md)