---
title: "Informaci&#243;n general sobre la compatibilidad con m&#250;ltiples versiones (multi-targeting) en Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "destinos múltiples [Visual Studio]"
  - "destinos múltiples [Visual Studio]"
  - "especificar versión de .NET Framework [Visual Studio]"
  - "versiones [Visual Studio], especificar versión de .NET Framework"
ms.assetid: b1702c33-0672-4ebc-b779-2b324d6ea880
caps.latest.revision: 36
caps.handback.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Informaci&#243;n general sobre la compatibilidad con m&#250;ltiples versiones (multi-targeting) en Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En esta versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], puede especificar la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] necesaria para la aplicación.  Por tanto, si desea usar esta versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para continuar desarrollando un proyecto que empezó en una versión anterior, no tiene que cambiar el destino del marco.  También podría crear una solución que contenga proyectos destinados a versiones diferentes del framework.  El marco de trabajo que tiene como destino también ayuda garantiza que la aplicación utilice solo la funcionalidad disponible en la versión especificada del marco de trabajo.  
  
> [!TIP]
>  También puede tener como destino aplicaciones para distintas plataformas.  Para obtener más información, vea [Compatibilidad con múltiples versiones \(multi\-targeting\)](../msbuild/msbuild-multitargeting-overview.md)  
  
## Características de establecimiento de destino de marco de trabajo  
 El establecimiento de destinos de marco de trabajo incluye las siguientes características:  
  
-   Al abrir un proyecto destinado a una versión anterior de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] puede actualizarlo automáticamente o dejar el destino como está.  
  
-   Al crear un proyecto, puede especificar la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] a la que desea destinarlo.  
  
-   Puede cambiar la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] a la que está destinado un proyecto existente.  
  
-   Puede establecer como destino una versión distinta de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] en cada proyecto de la misma solución.  
  
-   Cuando se cambia la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que un proyecto usa como destino, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] realiza los cambios necesarios en las referencias y los archivos de configuración.  
  
 Cuando trabaje en un proyecto destinado a una versión anterior de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio realiza dinámicamente modificaciones en el entorno de desarrollo, como se indica a continuación:  
  
-   Filtrará los elementos de los cuadros de diálogo **Nuevo proyecto**, **Agregar nuevo elemento**, **Agregar nueva referencia** y **Agregar referencia de servicio** para omitir las opciones que no están disponibles en la versión de destino.  
  
-   Filtrará los controles personalizados del **Cuadro de herramientas** para quitar aquellos que no están disponibles en la versión de destino y para mostrar solo los controles más actualizados cuando hay varios controles disponibles.  
  
-   Filtra IntelliSense para omitir características de lenguaje que no están disponibles en la versión de destino.  
  
-   Filtrará las propiedades de la ventana **Propiedades** para omitir las que no están disponibles en la versión de destino.  
  
-   Filtrará las opciones de menú para omitir las que no están disponibles en la versión de destino.  
  
-   Para compilaciones, utiliza la versión del compilador y las opciones del compilador adecuadas para la versión de destino.  
  
> [!NOTE]
>  El establecimiento de destino de marco de trabajo no garantiza que la aplicación se ejecutará correctamente.  Debe probar la aplicación para asegurarse de que se ejecuta correctamente en la versión de destino.  No puede especificar versiones de .NET Framework de destino anteriores a .NET Framework 2.0.  
  
## Seleccionar una versión de .NET Framework de destino  
 Al crear un proyecto, seleccione la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de destino en el cuadro de diálogo **Nuevo proyecto**.  La lista de plantillas de proyecto disponibles se filtra en función de lo que se seleccione.  En un proyecto existente, puede cambiar la versión o perfil de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de destino en el cuadro de diálogo de propiedades del proyecto.  Para obtener más información, vea [Cómo: Usar como destino una versión de .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
> [!NOTE]
>  En las ediciones Express de Visual Studio, no puede establecer el marco de destino en el cuadro **Nuevo proyecto**.  
  
## Resolver las referencias de los ensamblados del sistema y de usuarios  
 Para establecer como destino una versión de .NET Framework, debe instalar primero las referencias de ensamblado adecuadas.  Las referencias de ensamblado para las versiones 2.0, 3.0, y 3.5 de .NET Framework se incluyen en .NET Framework 3.5 SP1. Podrá descargar dichas referencias desde el sitio web [Centro de descarga de Microsoft, Microsoft Visual Studio](http://go.microsoft.com/fwlink/?LinkId=227602).  Las referencias de ensamblado para .NET Framework Client Profile 3.5, .NET Framework 4, .NET Framework Client Profile 4 y Silverlight también están disponibles en el sitio web [Descargas de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=179687).  
  
> [!NOTE]
>  Un perfil de cliente de .NET Framework es un subconjunto de .NET Framework que proporciona un conjunto limitado de bibliotecas y características.  Para obtener más información acerca de los perfiles de cliente, vea [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
 El cuadro de diálogo **Agregar referencia** deshabilita los ensamblados de sistema que no pertenecen a la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de destino de modo que no se puedan agregar a un proyecto accidentalmente. \(Los ensamblados del sistema son archivos .dll que se incluyen en una versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\). Las referencias que pertenecen a una versión de.NET Framework posterior a la versión de destino no se resolverán y los controles que dependan de este tipo de referencia no puede agregarse.  Si desea habilitar este tipo de referencia, restaure el destino de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] del proyecto en uno que incluya la referencia. Para obtener más información, vea [Introduction to the Project Designer](http://msdn.microsoft.com/es-es/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
 Para obtener más información sobre referencias de ensamblados, consulte [Resolver ensamblados en tiempo de diseño](../msbuild/resolving-assemblies-at-design-time.md).  
  
## Habilitar LINQ  
 Cuando el destino es .NET Framework 3.5 o versiones posteriores, automáticamente se agrega una referencia a System.Core y una importación de nivel de proyecto para System.Linq \(solo en Visual Basic\).  Si desea utilizar características de LINQ, también debe activar Option Infer \(solo en Visual Basic\).  La referencia y la importación se quitan automáticamente si cambia la versión de destino a una versión anterior de .NET Framework.  Para obtener más información, vea [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Vea también  
 [Compatibilidad con múltiples versiones \(multi\-targeting\)](../msbuild/msbuild-multitargeting-overview.md)   
 [.NET Framework Multi\-Targeting for ASP.NET Web Projects](../Topic/.NET%20Framework%20Multi-Targeting%20for%20ASP.NET%20Web%20Projects.md)   
 [Compatibilidad de la plataforma y requisitos del sistema](http://www.microsoft.com/visualstudio/eng/products/compatibility)