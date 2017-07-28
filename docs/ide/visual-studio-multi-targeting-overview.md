---
title: "Información general sobre la compatibilidad con múltiples versiones (multi-targeting) en Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
ms.assetid: b1702c33-0672-4ebc-b779-2b324d6ea880
caps.latest.revision: 36
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 8bf0b097be929b30627e0f1139c6e0b145933ab4
ms.openlocfilehash: 93e0c6676d48a0164dcf3b184bcb886934372787
ms.contentlocale: es-es
ms.lasthandoff: 05/26/2017

---
# <a name="visual-studio-multi-targeting-overview"></a>Información general sobre la compatibilidad con múltiples versiones (multi-targeting) en Visual Studio
En esta versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], puede especificar la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que se requiere para la aplicación. Por tanto, si quiere usar esta versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para seguir desarrollando un proyecto que ha iniciado en una versión anterior, no tiene que cambiar el marco de destino. También podría crear una solución que contenga proyectos destinados a versiones diferentes del marco. La elección del marco de destino ayuda también a garantizar que la aplicación use solo la funcionalidad que está disponible en la versión especificada del marco.  
  
> [!TIP]
>  También puede dirigir aplicaciones a distintas plataformas. Para obtener más información, consulte [Multitargeting](../msbuild/msbuild-multitargeting-overview.md) [Compatibilidad con múltiples versiones (multi-targeting)]  
  
## <a name="framework-targeting-features"></a>Características de la elección del marco de destino  
 La elección del marco de destino incluye las siguientes características:  
  
-   Si abre un proyecto que tiene como destino una versión anterior de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] puede actualizarlo de forma automática o mantener el destino tal cual.  
  
-   Al crear un proyecto, puede especificar la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que quiere usar como destino.  
  
-   Puede cambiar la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que tiene como destino un proyecto existente.  
  
-   Puede elegir como destino una versión diferente de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] en varios proyectos en la misma solución.  
  
-   Si cambia la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de destino de un proyecto, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] realiza los cambios necesarios en las referencias y archivos de configuración.  
  
 Si trabaja en un proyecto que tiene como destino una versión anterior de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio cambia de forma dinámica el entorno de desarrollo, de la siguiente forma:  
  
-   Filtra los elementos de los cuadros de diálogo **Nuevo proyecto**, **Agregar nuevo elemento**, **Agregar nueva referencia** y **Agregar referencia de servicio** para omitir las opciones que no están disponibles en la versión de destino.  
  
-   Filtra los controles personalizados del **Cuadro de herramientas** para quitar los que no están disponibles en la versión de destino y para mostrar solo los controles más actualizados cuando hay varios disponibles.  
  
-   Filtra IntelliSense para omitir características de lenguaje que no están disponibles en la versión de destino.  
  
-   Filtra las propiedades de la ventana **Propiedades** para omitir las que no están disponibles en la versión de destino.  
  
-   Filtra las opciones del menú para omitir aquellas que no están disponibles en la versión de destino.  
  
-   Para las compilaciones, usa la versión y las opciones del compilador que son adecuadas para la versión de destino.  
  
> [!NOTE]
>  La elección del marco de destino no garantiza que la aplicación se ejecute correctamente. Debe probar la aplicación para asegurarse de que se ejecuta en la versión de destino. No puede elegir como destino versiones de .NET Framework anteriores a la versión 2.0.  
  
## <a name="selecting-a-target-framework-version"></a>Seleccionar una versión de .NET Framework de destino  
 Al crear un proyecto, seleccione la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de destino en el cuadro de diálogo **Nuevo proyecto**. La lista de plantillas de proyecto disponibles se filtra según la selección. En un proyecto existente, puede cambiar la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de destino en el cuadro de diálogo de propiedades del proyecto. Para obtener más información, consulte [Cómo: Usar como destino una versión de .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
> [!NOTE]
>  En las ediciones Express de Visual Studio, no se puede establecer el marco de destino en el cuadro de diálogo **Nuevo proyecto**.  
  
## <a name="resolving-system-and-user-assembly-references"></a>Resolver referencias de ensamblado de usuario y sistema  
 Para elegir como destino una versión de .NET Framework, primero debe instalar las referencias de ensamblado adecuadas. Las referencias de ensamblado de las versiones de .NET Framework 2.0, 3.0 y 3.5 se incluyen en .NET Framework 3.5 SP1, que puede descargar desde el [Centro de descarga de Microsoft, en el sitio web de Microsoft Visual Studio](http://go.microsoft.com/fwlink/?LinkId=227602). Las referencias de ensamblado de .NET Framework 3.5 Client Profile, .NET Framework 4, .NET Framework 4 Client Profile y Silverlight también están disponibles en el sitio web [Descargas de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=179687).  
  
> [!NOTE]
>  Un perfil de cliente de .NET Framework es un subconjunto de .NET Framework que proporciona un conjunto limitado de bibliotecas y características. Para obtener más información sobre perfiles de cliente, consulte [.NET Framework Client Profile](/dotnet/framework/deployment/client-profile).  
  
 El cuadro de diálogo **Agregar referencia** deshabilita los ensamblados del sistema que no pertenecen a la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de destino para evitar que se agreguen a un proyecto de forma involuntaria. (Los ensamblados del sistema son archivos .dll que se incluyen en una versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]). No se resolverán las referencias que pertenezcan a una versión del marco posterior a la versión de destino y no se pueden agregar controles que dependan de este tipo de referencia. Si quiere habilitar este tipo de referencia, restablezca el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de destino del proyecto a otro que incluya la referencia.  Para obtener más información, consulte [Cómo: Usar como destino una versión de .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
 Para obtener más información sobre las referencias de ensamblado, consulte [Resolver ensamblados en tiempo de diseño](../msbuild/resolving-assemblies-at-design-time.md).  
  
## <a name="enabling-linq"></a>Habilitar LINQ  
 Si elige como destino .NET Framework 3.5 o una versión posterior, se agregan de forma automática una referencia a System.Core y una importación de nivel de proyecto para System.Linq (solo en Visual Basic). Si quiere usar características de LINQ, también debe activar Option Infer (solo en Visual Basic). La referencia y la importación se quitan de forma automática si cambia el destino a una versión anterior de .NET Framework. Para obtener más información, vea [Trabajar con LINQ](/dotnet/csharp/tutorials/working-with-linq).  
  
## <a name="see-also"></a>Vea también  
 [Multitargeting](../msbuild/msbuild-multitargeting-overview.md)  [Compatibilidad con múltiples versiones (multi-targeting)]  
 [Platform compatibility and system requirements](http://www.microsoft.com/visualstudio/eng/products/compatibility) (Compatibilidad de plataformas y requisitos del sistema)
