---
title: Administrar referencias en un proyecto
description: Aprenda a administrar referencias a componentes externos y servicios conectados en un proyecto.
ms.custom: SEO-VS-2020
ms.date: 08/02/2019
ms.topic: conceptual
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fdf737d26ec14c2a108125425a3b66cdf4a0e519
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2020
ms.locfileid: "95870955"
---
# <a name="manage-references-in-a-project"></a>Administrar referencias en un proyecto

Antes de escribir código en un componente externo o en un servicio conectado, el proyecto debe contener primero una referencia a él. Una referencia es básicamente una entrada de un archivo de proyecto que contiene la información que Visual Studio necesita para localizar el componente o el servicio.

Para agregar una referencia, haga clic con el botón derecho en el nodo **Referencias** o **Dependencias** del **Explorador de soluciones** y elija **Agregar referencia**. También puede hacer clic con el botón derecho en el nodo del proyecto y seleccionar **Agregar** > **Referencia**. Para obtener más información, vea [Cómo: Agregar o quitar referencias](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md).

![Agregar una referencia en Visual C&#43;&#43;](../ide/media/vs2015_cpp_add_reference.png)

Puede agregar una referencia a los siguientes tipos de componentes y servicios:

- Bibliotecas de clases o ensamblados de .NET

- Aplicaciones para UWP

- componentes COM

- Otros ensamblados o bibliotecas de clases de proyectos de la misma solución

- Proyectos compartidos

- servicios Web XML

## <a name="uwp-app-references"></a>Referencias de aplicaciones para UWP

### <a name="project-references"></a>Referencias de proyecto

Los proyectos de la Plataforma universal de Windows (UWP) pueden crear referencias a otros proyectos UWP de la solución o a archivos binarios o proyectos de Windows 8.1, siempre que estos proyectos no usen las API que han quedado obsoletas en Windows 10. Para más información, vea [Migración Windows Runtime 8 a UWP](/windows/uwp/porting/w8x-to-uwp-root).

Si decide redirigir los proyectos de Windows 8.1 a Windows 10, vea [Portar, migrar y actualizar proyectos de Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

### <a name="extension-sdk-references"></a>Referencias del SDK de extensiones

Las aplicaciones para UWP en Visual Basic, C#, C++ y JavaScript pueden hacer referencia a los SDK de extensiones que tienen como destino Windows 8.1, siempre que estos SDK de extensiones no usen las API que han quedado obsoletas en Windows 10. Compruebe el sitio del proveedor del SDK de extensiones para averiguar si se puede hacer referencia a él con aplicaciones para UWP.

Si determina que el SDK de extensión al que la aplicación hace referencia no es compatible, debe realizar los pasos siguientes:

1. Consulte el nombre del proyecto que está provocando el error. La plataforma de destino del proyecto se indica entre paréntesis junto al nombre del mismo. Por ejemplo, **MyProjectName (Windows 8.1)** significa que el proyecto **MyProjectName** está destinado a la versión de la plataforma Windows 8.1.

1. Vaya al sitio del proveedor propietario del SDK de extensiones no compatible e instale la versión del SDK de extensiones con dependencias que son compatibles con la versión de la plataforma a la que está destinado el proyecto.

    > [!NOTE]
    > Una manera de averiguar si un SDK de extensiones tiene dependencias de otros es consultar en el **Administrador de referencias**. Reinicie Visual Studio, cree un proyecto de aplicación para UWP en C# y, después, haga clic con el botón derecho en el proyecto y seleccione **Agregar referencia**. Vaya a la pestaña **Windows**, después a la subpestaña **Extensiones** y seleccione el SDK de extensiones. Fíjese en el panel de la derecha del **Administrador de referencias**. Si tiene dependencias, se mostrarán allí.

    > [!IMPORTANT]
    > Si el proyecto tiene como destino Windows 10 y el SDK de extensiones instalado en el paso anterior tiene una dependencia del paquete Tiempo de ejecución de Microsoft Visual C++, la versión de ese paquete que es compatible con Windows 10 es v14.0 y se instala con Visual Studio.

1. Si el SDK de extensiones que se instaló en el paso anterior tiene dependencias de otros SDK de extensiones, vaya a los sitios web de los proveedores de las dependencias e instale las versiones de estas dependencias que sean compatibles con la versión de la plataforma a la que está destinado el proyecto.

1. Reinicie Visual Studio y abra la aplicación.

1. Haga clic con el botón derecho en el nodo **Referencias** o **Dependencias** en el proyecto que produjo el error y elija **Agregar referencia**.

1. Haga clic en la pestaña **Windows**, luego en la subpestaña **Extensiones** y, después, desactive las casillas de los SDK de extensiones antiguos y active las casillas de los nuevos. Haga clic en **Aceptar**.

## <a name="add-a-reference-at-design-time"></a>Agregar una referencia en tiempo de diseño

Cuando se hace referencia a un ensamblado del proyecto, Visual Studio busca el ensamblado en las ubicaciones siguientes:

- Directorio del proyecto actual. (Puede buscar estos ensamblados utilizando la ficha **Examinar** .)

- Otros directorios del proyecto de la misma solución. (Puede encontrar estos ensamblados en la pestaña **Proyectos** ).

> [!NOTE]
> - Todos los proyectos contienen una referencia implícita a **mscorlib**.
> - Todos los proyectos contienen una referencia implícita a `System.Core`, incluso si se quita `System.Core` de la lista de referencias.
> - Los proyectos de Visual Basic contienen una referencia implícita a <xref:Microsoft.VisualBasic>.

## <a name="references-to-shared-components-at-run-time"></a>Referencias a componentes compartidos en tiempo de ejecución

En tiempo de ejecución, los componentes deben estar en la ruta de acceso de salida del proyecto o en la caché global de ensamblados (GAC). Si el proyecto contiene una referencia a un objeto que no está en una de estas ubicaciones, debe copiar la referencia a la ruta de acceso de salida del proyecto al compilar el proyecto. La propiedad <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> indica si es necesario realizar esta copia. Si el valor es **True**, la referencia se copia al directorio del proyecto al compilar el proyecto. Si el valor es **False**, la referencia no se copia.

Si implementa una aplicación que contiene una referencia a un componente personalizado registrado en la GAC, el componente no se implementará con la aplicación, independientemente de la configuración de <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> . En versiones anteriores de Visual Studio, se podía establecer la propiedad <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> en una referencia para asegurarse de que se implementase el ensamblado. Ahora se debe agregar manualmente el ensamblado en la carpeta \Bin. Esto somete todo el código personalizado a escrutinio, reduciendo el riesgo de que se publique código personalizado con el que no esté familiarizado.

De forma predeterminada, la propiedad <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> está establecida en **False** si el ensamblado o el componente está en la caché global de ensamblados o es un componente del marco de trabajo. De lo contrario, el valor se establece en **True**. Las referencias de proyecto a proyecto siempre se establecen en **True**.

## <a name="reference-a-project-or-assembly-that-targets-a-different-version-of-net"></a>Hacer referencia a un proyecto o ensamblado que tiene como destino otra versión de .NET

Puede crear aplicaciones que hagan referencia a proyectos o ensamblados que tengan como destino otra versión de .NET. Por ejemplo, se podría crear una aplicación destinada a .NET Framework 4.6 que haga referencia a un ensamblado destinado a .NET Framework 4.5. Si crea un proyecto destinado a una versión anterior de .NET, no puede establecer una referencia en ese proyecto a un proyecto o ensamblado destinado a una versión más reciente.

Para obtener más información, vea [Información general sobre destinos de Framework](../ide/visual-studio-multi-targeting-overview.md).

## <a name="project-to-project-references"></a>Referencias entre proyectos

Las referencias de proyecto a proyecto son referencias a proyectos que contienen ensamblados. Para crear referencias de proyecto, use la pestaña **Proyectos** del cuadro de diálogo Administrador de referencias. Visual Studio puede encontrar un ensamblado cuando se le proporciona una ruta de acceso al proyecto.

Si tiene un proyecto que genera un ensamblado, debe hacer referencia al proyecto y no usar una referencia de archivo (ver abajo). La ventaja de una referencia de proyecto a proyecto es que crea una dependencia entre los proyectos en el sistema de compilación. El proyecto dependiente se compilará si ha cambiado desde la última vez que se compiló el proyecto que hace referencia. Una referencia a un archivo no crea una dependencia de compilación, por lo que es posible compilar el proyecto que hace referencia sin compilar el proyecto dependiente y la referencia puede quedar obsoleta. (Es decir, el proyecto puede hacer referencia a una versión previamente compilada del proyecto). Esto puede dar lugar a varias versiones de un solo archivo DLL que se requiere en el directorio *bin*, lo cual no es posible. Si se produce este conflicto, verá un mensaje como "Advertencia: la dependencia 'archivo' del proyecto 'proyecto' no se puede copiar en el directorio de ejecución porque sobrescribiría la referencia 'archivo'". Para obtener más información, vea [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md) y [Cómo: Creación y eliminación de dependencias del proyecto](../ide/how-to-create-and-remove-project-dependencies.md).

> [!NOTE]
> Se crea una referencia de archivo en lugar de una referencia entre proyectos si la versión de destino de .NET Framework de un proyecto es la versión 4.5, y la del otro proyecto es la versión 2, 3, 3.5 o 4.0.

## <a name="shared-project-references"></a>Referencias de proyectos compartidos

A diferencia de la mayoría de los demás tipos de proyecto, un *proyecto compartido* no tiene ninguna salida binaria. En su lugar, el código se compila en cada proyecto que hace referencia a él. Los [Proyectos compartidos](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) le permiten escribir código común al que distintos proyectos de aplicaciones hacen referencia. El código se compila como parte de cada proyecto de referencia y puede incluir directivas de compilador para ayudar a incorporar una funcionalidad específica de la plataforma en el código base compartido. Agregue una referencia a un proyecto compartido en la pestaña **Proyectos compartidos** del cuadro de diálogo Administrador de referencias.

## <a name="file-references"></a>Referencias de archivo

Las referencias a archivos son referencias directas a ensamblados fuera del contexto de un proyecto de Visual Studio. Se crean mediante la pestaña **Examinar** del cuadro de diálogo Administrador de referencias. Use una referencia de archivo cuando solo tenga un ensamblado o un componente, y no el proyecto que lo crea como salida.

## <a name="see-also"></a>Vea también

- [Solucionar problemas de referencias rotas](../ide/troubleshooting-broken-references.md)
- [Cómo: Agregar o quitar referencias](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
