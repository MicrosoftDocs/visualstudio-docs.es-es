---
title: 'Cómo: migrar un proyecto de lenguaje Domain-Specific'
description: Proporciona información sobre cómo migrar un proyecto de lenguaje específico de dominio a una versión más reciente de Visual Studio.
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: bbefb1cd5ae546c5454660b6782f9c76f35a63f4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922696"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Cómo: Migrar lenguajes específicos de dominio a una nueva versión
Puede migrar proyectos que definen y usan lenguajes específicos de dominio a [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] desde la versión de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] que se distribuyó con [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] .

 Una herramienta de migración se proporciona como parte de [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] . La herramienta convierte proyectos y soluciones de Visual Studio que usan o definen herramientas de DSL.

 Debe ejecutar la herramienta de migración explícitamente: no se inicia automáticamente cuando se abre una solución en Visual Studio. La herramienta y el documento de instrucciones detalladas se pueden encontrar en esta ruta de acceso:

 **% Archivos de programa%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Antes de migrar los proyectos DSL
 La herramienta de migración modifica los archivos de proyecto de Visual Studio (**. csproj**) y los archivos de solución (**. sln**).

#### <a name="to-prepare-projects-for-migration"></a>Para preparar los proyectos para la migración.

- Asegúrese de que se pueden escribir los archivos **. csproj** y **. sln** . Si están bajo control de código fuente, asegúrese de que están desprotegidos.

- Realice una copia de las carpetas que desea migrar.

## <a name="migrating-a-collection-of-projects"></a>Migración de una colección de proyectos

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Para migrar proyectos y soluciones DSL a Visual Studio 2010

1. Inicie la herramienta de migración de DSL.

   - Puede hacer doble clic en la herramienta en el explorador de Windows (o explorador de archivos) o iniciar la herramienta desde un símbolo del sistema. La herramienta está en esta ubicación:

        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. Elija una carpeta que contenga las soluciones y los proyectos que desea convertir.

   - Escriba la ruta de acceso en el cuadro de la parte superior de la herramienta o haga clic en **examinar**.

     La herramienta de migración muestra un árbol de proyectos que definen o usan DSL. El árbol incluye todos los proyectos que usan los ensamblados **Microsoft. VisualStudio. Modeling. SDK** o **TextTemplating** .

3. Revise el árbol de proyectos y desactive los proyectos que no desea convertir.

   - Seleccione un proyecto o una solución para ver una lista de los cambios que realizará la herramienta.

       > [!NOTE]
       > Las casillas que aparecen junto a los nombres de carpeta no tienen ningún efecto. Debe expandir las carpetas para inspeccionar los proyectos y las soluciones.

4. Convierta los proyectos.

   1. Haga clic en **convertir**.

        Antes de que se convierta cada archivo de proyecto, se guarda una copia de _Project_**. csproj** como _Project_**. VS2008. csproj**

        Una copia de cada _solución_**. sln** se guarda como _Solution_**. VS2008. sln** .

   2. Investigue cualquier conversión con errores que se notifique.

        Los errores se muestran en la ventana de texto. Además, la vista de árbol muestra una marca roja en cada nodo que no se pudo convertir. Puede hacer clic en el nodo para obtener más información sobre ese error.

5. **Transformar todas las plantillas** en soluciones que contengan proyectos convertidos correctamente.

   1. Abra la solución.

   2. Haga clic en el botón **transformar todas las plantillas** en el encabezado de explorador de soluciones.

       > [!NOTE]
       > Puede hacer que este paso no sea necesario. Para obtener más información, consulte [cómo automatizar la transformación de todas las plantillas](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

6. Actualice el código personalizado en los proyectos convertidos.

   - Intente compilar los proyectos e investigue los errores.

   - Pruebe el diseñador.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vea también

- [Entradas blogs relacionadas](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)