---
title: Administrar referencias en un proyecto | Microsoft Docs
ms.custom: 
ms.date: 10/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- Visual C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
ms.assetid: 05d1c51b-44f3-4973-8a11-6c919b08ad62
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4145dda187e726096e2137d2a5fdc0455b6131e2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="managing-references-in-a-project"></a>Administrar referencias en un proyecto
Antes de escribir código en un componente externo o en un servicio conectado, el proyecto debe contener primero una referencia a él. Una referencia es básicamente una entrada de un archivo de proyecto que contiene la información que Visual Studio necesita para localizar el componente o el servicio.  

 Para agregar una referencia, haga clic con el botón derecho en el nodo Referencias del Explorador de soluciones y elija **Agregar referencia**. Para obtener más información, consulte [Cómo: Agregar o quitar referencias usando el Administrador de referencias](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).  

 ![Agregar una referencia en Visual C&#43;&#43;](../ide/media/vs2015_cpp_add_reference.png "vs2015_cpp_add_reference")  

 Puede hacer referencia a los siguientes tipos de componentes y servicios:    

-   Bibliotecas de clases o ensamblados de .NET Framework  

-   Aplicaciones para UWP

-   componentes COM  

-   Otros ensamblados o bibliotecas de clases de proyectos de la misma solución  

-   servicios Web XML  

## <a name="uwp-app-references"></a>Referencias de aplicaciones para UWP  

### <a name="project-references"></a>Referencias del proyecto  
 Los proyectos de la Plataforma universal de Windows (UWP) pueden crear referencias a otros proyectos UWP de la solución o a archivos binarios o proyectos de Windows 8.1, siempre que estos proyectos no usen las API que han quedado obsoletas en Windows 10. Para más información, vea [Migración Windows Runtime 8 a UWP](https://docs.microsoft.com/en-us/windows/uwp/porting/w8x-to-uwp-root).  

 Si decide redirigir los proyectos de Windows 8.1 a Windows 10, vea [Portar, migrar y actualizar proyectos de Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md).  

### <a name="extension-sdk-references"></a>Referencias del SDK de extensión  
 Las aplicaciones para UWP en Visual Basic, C#, C++ y JavaScript pueden hacer referencia a los SDK de extensiones que tienen como destino [!INCLUDE[win81](../debugger/includes/win81_md.md)], siempre que estos SDK de extensiones no usen las API que han quedado obsoletas en Windows 10. Consulte el sitio del proveedor del SDK de extensión para determinar si se puede hacer referencia a él en proyectos de Microsoft Store que tengan como destino UWP.  

 Si determina que el SDK de extensión al que la aplicación hace referencia no es compatible, debe realizar los pasos siguientes:  

1.  Consulte el nombre del proyecto que está provocando el error. La plataforma de destino del proyecto se indica entre paréntesis junto al nombre del mismo. Por ejemplo, **MyProjectName (Windows 8.1)** significa que el proyecto **MyProjectName** está destinado a la versión de la plataforma [!INCLUDE[win81](../debugger/includes/win81_md.md)].  

2.  Vaya al sitio del proveedor del SDK de extensión no compatible e instale la versión del SDK de extensión con dependencias que son compatibles con la versión de la plataforma a la que está destinada su proyecto.  

    > [!NOTE]
    >  Una forma de averiguar si un SDK de extensión tiene dependencias de otros SDK de extensión consiste en realizar los siguientes pasos: reinicie Visual Studio, cree un nuevo proyecto de aplicación para UWP en C#, haga clic con el botón derecho en el proyecto y elija **Agregar referencia**, vaya a la pestaña **Windows** y luego a la subpestaña **Extensiones**, seleccione el SDK de extensión y fíjese en el panel derecho del **Administrador de referencias**. Si tiene dependencias, se mostrarán allí.  

    > [!IMPORTANT]
    >  Si el proyecto tiene como destino Windows 10 y el SDK de extensión instalado anteriormente tiene una dependencia del paquete en tiempo de ejecución de Microsoft Visual C++, la versión de ese paquete que es compatible con Windows 10 es v14.0 y se instala con Visual Studio.  

3.  Si el SDK de extensión que instaló en el paso anterior tiene dependencias de otros SDK de extensión, vaya a los sitios web de los proveedores de las dependencias e instale las versiones de estas dependencias que sean compatibles con la versión de la plataforma a la que está destinada su proyecto.  

4.  Reinicie Visual Studio y abra la aplicación.  

5.  Haga clic con el botón derecho en el nodo **Referencias** en el proyecto que produjo el error y elija **Agregar referencia**.  

6.  Haga clic en la pestaña **Windows** y, a continuación, en la subpestaña **Extensiones** y, a continuación, desactive las casillas de los antiguos SDK de extensión y active las casillas de los nuevos SDK de extensión. Haga clic en **Aceptar**.  

## <a name="adding-a-reference-at-design-time"></a>Agregar una referencia en tiempo de diseño  
 Cuando hace una referencia a un ensamblado de su proyecto, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] busca el ensamblado en las siguientes ubicaciones:  

-   Directorio del proyecto actual. (Puede buscar estos ensamblados utilizando la ficha **Examinar** .)  

-   Otros directorios del proyecto de la misma solución. (Puede encontrar estos ensamblados en la pestaña **Proyectos** ).  

> [!NOTE]
>  Todos los proyectos contienen una referencia implícita a mscorlib. Los proyectos de Visual Basic contienen una referencia implícita a `Microsoft.VisualBasic`.  
>   
>  Todos los proyectos de Visual Studio contienen una referencia implícita a `System.Core`, aun cuando `System.Core` se quite de la lista de referencias.  

## <a name="references-to-shared-components-at-run-time"></a>Referencias a componentes compartidos en tiempo de ejecución  
 En tiempo de ejecución, los componentes deben estar en la ruta de acceso de salida del proyecto o en la caché global de ensamblados (GAC). Si el proyecto contiene una referencia a un objeto que no está en una de estas ubicaciones, debe copiar la referencia a la ruta de acceso de salida del proyecto al compilar el proyecto. La propiedad <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> indica si es necesario realizar esta copia. Si el valor es **True**, la referencia se copia al directorio del proyecto al compilar el proyecto. Si el valor es **False**, la referencia no se copia.  

 Si implementa una aplicación que contiene una referencia a un componente personalizado registrado en la GAC, el componente no se implementará con la aplicación, independientemente de la configuración de <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> . En versiones anteriores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], se podía establecer la propiedad <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> en una referencia para asegurarse de que se implementase el ensamblado. Ahora se debe agregar manualmente el ensamblado en la carpeta \Bin. Esto somete todo el código personalizado a escrutinio, reduciendo el riesgo de que se publique código personalizado con el que no esté familiarizado.  

 De forma predeterminada, la propiedad <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> está establecida en **False** si el ensamblado o el componente está en la caché global de ensamblados o es un componente del marco de trabajo. De lo contrario, el valor se establece en **True**. Las referencias de proyecto a proyecto siempre se establecen en **True**.  

## <a name="referencing-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Hacer referencia a un proyecto o ensamblado que tenga como destino una versión diferente de .NET Framework  
 Puede crear aplicaciones que hagan referencia a proyectos o ensamblados destinados a otra versión de .NET Framework. Por ejemplo, podría crear una aplicación destinada a [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] que haga referencia a un ensamblado destinado a [!INCLUDE[dnprdnext](../ide/includes/dnprdnext_md.md)]. Si crea un proyecto destinado a una versión anterior de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], no puede establecer una referencia en ese proyecto a un proyecto o ensamblado destinado a [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] o .NET Framework 4.  

 Para obtener más información, consulte [Elegir una versión específica de .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).  

## <a name="project-to-project-references"></a>Referencias entre proyectos  
 Las referencias entre proyectos son referencias a proyectos que contienen ensamblados. Puede crearlas en la pestaña **Proyecto** . Visual Studio puede encontrar un ensamblado cuando se le proporciona una ruta de acceso al proyecto.  

 Si tiene un proyecto que genera un ensamblado, debe hacer referencia al proyecto y no usar una referencia de archivo (ver abajo). La ventaja de una referencia de proyecto a proyecto es que crea una dependencia entre los proyectos en el sistema de compilación. El proyecto dependiente se compilará si ha cambiado desde la última vez que se compiló el proyecto que hace referencia. Una referencia a un archivo no crea una dependencia de compilación, por lo que es posible compilar el proyecto que hace referencia sin compilar el proyecto dependiente y la referencia puede quedar obsoleta. (Es decir, el proyecto puede hacer referencia a una versión previamente compilada del proyecto). Esto puede dar lugar a varias versiones de un solo archivo DLL que se requiere en el directorio bin, lo cual no es posible. Si se produce este conflicto, verá un mensaje como "Advertencia: la dependencia 'archivo' del proyecto 'proyecto' no se puede copiar en el directorio de ejecución porque sobrescribiría la referencia 'archivo'". Para obtener más información, consulte [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md) y [Cómo: Crear y quitar dependencias del proyecto](../ide/how-to-create-and-remove-project-dependencies.md).  

> [!NOTE]
>  Se crea una referencia de archivo en lugar de una referencia entre proyectos si la versión de destino de .NET Framework de un proyecto es la versión 4.5, y la del otro proyecto es la versión 2, 3, 3.5 o 4.0.  

## <a name="file-references"></a>Referencias de archivo  
 Las referencias de archivo son referencias directas a ensamblados fuera del contexto de un proyecto de Visual Studio. Puede crearlas en la pestaña **Examinar** del **Administrador de referencias**. Use una referencia de archivo cuando solo tenga un ensamblado o un componente, y no disponga del proyecto que lo crea como salida.  

## <a name="see-also"></a>Vea también  
 [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md)   
 [Cómo: Agregar o quitar referencias mediante el Administrador de referencias](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
