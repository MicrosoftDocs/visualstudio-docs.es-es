---
title: Selección de .NET Framework como destino
ms.date: 02/06/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
- framework targeting [Visual Studio]
- .NET framework targeting [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 763e02dbd491e132dc91ec7a79717fab1e645d86
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53955206"
---
# <a name="visual-studio-multi-targeting-overview"></a>Información general sobre la compatibilidad con múltiples versiones de Visual Studio

En Visual Studio, puede especificar la versión o perfil de .NET Framework que desee como destino del proyecto. Para ejecutar una aplicación en otro equipo, la versión de Framework de destino de la aplicación debe ser compatible con la versión de Framework que está instalada en el equipo.

También puede crear una solución que contenga proyectos destinados a versiones diferentes de la plataforma. La elección de la plataforma de destino ayuda a garantizar que la aplicación use solo la funcionalidad que está disponible en la versión especificada de la plataforma.

> [!TIP]
> También puede dirigir aplicaciones a distintas plataformas. Para obtener más información, consulte [Compatibilidad con múltiples versiones (multi-targeting)](../msbuild/msbuild-multitargeting-overview.md).

## <a name="framework-targeting-features"></a>Características de la elección de la plataforma de destino

La elección del marco de destino incluye las siguientes características:

- Si abre un proyecto que tiene como destino una versión anterior de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio puede actualizarlo de forma automática o mantener el destino tal cual.

- Al crear un proyecto, puede especificar la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que quiere usar como destino.

- Puede cambiar la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que tiene como destino un proyecto existente.

- Puede elegir como destino una versión diferente de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] en varios proyectos en la misma solución.

- Si cambia la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de destino de un proyecto, [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] realiza los cambios necesarios en las referencias y archivos de configuración.

Si trabaja en un proyecto que tiene como destino una versión anterior de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Visual Studio cambia de forma dinámica el entorno de desarrollo, de la siguiente forma:

- Filtra los elementos de los cuadros de diálogo **Agregar nuevo elemento**, **Agregar nueva referencia** y **Agregar referencia de servicio** para omitir las opciones que no están disponibles en la versión de destino.

- Filtra los controles personalizados del **Cuadro de herramientas** para quitar los que no están disponibles en la versión de destino y para mostrar solo los controles más actualizados cuando hay varios disponibles.

- Filtra **IntelliSense** para omitir características de lenguaje que no están disponibles en la versión de destino.

- Filtra las propiedades de la ventana **Propiedades** para omitir las que no están disponibles en la versión de destino.

- Filtra las opciones del menú para omitir aquellas que no están disponibles en la versión de destino.

- Para las compilaciones, usa la versión y las opciones del compilador que son adecuadas para la versión de destino.

> [!NOTE]
> La elección del marco de destino no garantiza que la aplicación se ejecute correctamente. Debe probar la aplicación para asegurarse de que se ejecuta en la versión de destino. No puede elegir como destino versiones de .NET Framework anteriores a la versión 2.0.

## <a name="select-a-target-framework-version"></a>Seleccionar una versión de la plataforma de destino

Al crear un proyecto, seleccione la versión de destino de .NET Framework en el cuadro de diálogo **Nuevo proyecto**. La lista de las plataformas disponibles incluye las versiones de las plataformas instaladas que son aplicables al tipo de plantilla seleccionada. Para los tipos de plantilla que no requieren .NET Framework, como las plantillas de .NET Core, la lista desplegable **Plataforma** permanece oculta.

![Desplegable Plataforma en el cuadro de diálogo Nuevo proyecto](media/vside-newproject-framework.png)

En un proyecto existente, puede cambiar la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de destino en el cuadro de diálogo de propiedades del proyecto. Para obtener más información, vea [Cómo: Usar una versión de .NET Framework como destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

## <a name="resolve-system-and-user-assembly-references"></a>Resolver referencias de ensamblado de usuario y sistema

Para elegir como destino una versión de .NET Framework, primero debe instalar las referencias de ensamblado adecuadas. Puede descargar los paquetes de desarrollador para distintas versiones de .NET Framework en la página [Descargas de .NET](https://www.microsoft.com/net/download/windows).

El cuadro de diálogo **Agregar referencia** deshabilita los ensamblados del sistema que no pertenecen a la versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de destino para evitar que se agreguen a un proyecto de forma involuntaria. (Los ensamblados del sistema son archivos *.dll* que se incluyen en una versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]). No se resolverán las referencias que pertenezcan a una versión del marco posterior a la versión de destino y no se pueden agregar controles que dependan de este tipo de referencia. Si quiere habilitar este tipo de referencia, restablezca el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] de destino del proyecto a otro que incluya la referencia.  Para obtener más información, vea [Cómo: Usar una versión de .NET Framework como destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

Para obtener más información sobre las referencias de ensamblado, consulte [Resolver ensamblados en tiempo de diseño](../msbuild/resolving-assemblies-at-design-time.md).

## <a name="enable-linq"></a>Habilitar LINQ

Si elige como destino .NET Framework 3.5 o una versión posterior, se agregan de forma automática una referencia a **System.Core** y una importación de nivel de proyecto para <xref:System.Linq> (solo en Visual Basic). Si quiere usar características de LINQ, también debe activar `Option Infer` (solo en Visual Basic). La referencia y la importación se quitan de forma automática si cambia el destino a una versión anterior de .NET Framework. Para obtener más información, vea [Trabajar con LINQ](/dotnet/csharp/tutorials/working-with-linq).

## <a name="see-also"></a>Vea también

- [Compatibilidad con múltiples versiones (MSBuild)](../msbuild/msbuild-multitargeting-overview.md)
- [Cómo: Modificar la plataforma de destino y el conjunto de herramientas de la plataforma (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)