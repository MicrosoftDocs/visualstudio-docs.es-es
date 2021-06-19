---
title: Migración de un proyecto Domain-Specific Language
description: Proporciona información sobre cómo migrar un proyecto de lenguaje específico de dominio a una versión más reciente de Visual Studio.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 8119f465e32d3754dc446524286e0a2c12dedc40
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387195"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Cómo: Migrar lenguajes específicos de dominio a una nueva versión
Puede migrar proyectos que definen y usan un lenguaje específico de dominio a [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] desde la versión de que se [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] distribuyó con [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] .

 Se proporciona una herramienta de migración como parte de [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] . La herramienta convierte Visual Studio y soluciones que usan o definen herramientas DSL.

 Debe ejecutar la herramienta de migración explícitamente: no se inicia automáticamente al abrir una solución en Visual Studio. La herramienta y el documento de instrucciones detallados se pueden encontrar en esta ruta de acceso:

 **%Archivos de programa%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Antes de migrar los proyectos DSL
 La herramienta de migración modifica Visual Studio archivos de proyecto (**.csproj**) y archivos de solución (**.sln**).

#### <a name="to-prepare-projects-for-migration"></a>Para preparar los proyectos para la migración.

- Asegúrese de que se pueden escribir los archivos **.csproj** y **.sln.** Si están bajo control de código fuente, asegúrese de que se han comprobado.

- Realice una copia de las carpetas que desea migrar.

## <a name="migrating-a-collection-of-projects"></a>Migración de una colección de proyectos

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Para migrar proyectos y soluciones dsl a Visual Studio 2010

1. Inicie la herramienta de migración de DSL.

   - Puede hacer doble clic en la herramienta en Explorador de Windows (o Explorador de archivos) o iniciar la herramienta desde un símbolo del sistema. La herramienta se encuentra en esta ubicación:

        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. Elija una carpeta que contenga soluciones y proyectos que quiera convertir.

   - Escriba la ruta de acceso en el cuadro de la parte superior de la herramienta o haga clic **en Examinar.**

     La herramienta de migración muestra un árbol de proyectos que definen o usan DSL. El árbol incluye todos los proyectos que usan los **ensamblados Microsoft.VisualStudio.Modeling.Sdk** o **TextTemplating.**

3. Revise el árbol de proyectos y desactive los proyectos que no desea convertir.

   - Seleccione un proyecto o una solución para ver una lista de los cambios que realizará la herramienta.

       > [!NOTE]
       > Las casillas que aparecen junto a los nombres de carpeta no tienen ningún efecto. Debe expandir las carpetas para inspeccionar los proyectos y soluciones.

4. Convierta los proyectos.

   1. Haga clic **en Convertir**.

        Antes de convertir cada archivo de proyecto, se guarda una copia del **proyecto .csproj** como **proyecto .vs2008.csproj**

        Se guarda una _copia_ de cada **.sln de** la solución como _solución_**.vs2008.sln.**

   2. Investigue las conversiones con errores que se notifican.

        Los errores se notifican en la ventana de texto. Además, la vista de árbol muestra una marca roja en cada nodo que no se pudo convertir. Puede hacer clic en el nodo para obtener más información sobre ese error.

5. **Transformar todas las plantillas** en soluciones que contengan proyectos convertidos correctamente.

   1. Abra la solución.

   2. Haga clic **en el botón Transformar** todas las plantillas en el encabezado de Explorador de soluciones.

       > [!NOTE]
       > Puede hacer que este paso sea innecesario. Para obtener más información, [vea How to Automate Transform All Templates](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

6. Actualice el código personalizado en los proyectos convertidos.

   - Intente compilar los proyectos e investigue los errores.

   - Pruebe el diseñador.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vea también

- [Entradas blogs relacionadas](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)