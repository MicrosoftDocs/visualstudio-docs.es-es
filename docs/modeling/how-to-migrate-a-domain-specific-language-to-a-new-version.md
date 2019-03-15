---
title: Filtrar Migrar un lenguaje específico de dominio a una nueva versión
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dae9c7728de35c92c973c9fca097595b56aabaf5
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57869249"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Filtrar Migrar un lenguaje específico de dominio a una nueva versión
Puede migrar los proyectos que definen y usar los lenguajes específicos de dominio a [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] desde la versión de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] que se distribuyó con [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].

 Se proporciona una herramienta de migración como parte de [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]. La herramienta convierte los proyectos de Visual Studio y las soluciones que usan o definen herramientas de DSL.

 Debe ejecutar la herramienta de migración de forma explícita: no se inicia automáticamente al abrir una solución en Visual Studio. La herramienta y el documento de orientación detallada pueden encontrarse en esta ruta de acceso:

 **%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Antes de migrar los proyectos DSL
 La herramienta de migración modifica los archivos de proyecto de Visual Studio (**.csproj**) y archivos de solución (**.sln**).

#### <a name="to-prepare-projects-for-migration"></a>Para preparar los proyectos de migración.

-   Asegúrese de que el **.csproj** y **.sln** se pueden escribir archivos. Si ya están bajo control de código fuente, asegúrese de que están desprotegidos.

-   Realice una copia de las carpetas que se va a migrar.

## <a name="migrating-a-collection-of-projects"></a>Migrar una colección de proyectos

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Para migrar DSL proyectos y soluciones de Visual Studio 2010

1. Inicie la herramienta de migración de DSL.

   -   Puede haga doble clic en la herramienta en el Explorador de Windows (o explorador de archivos), o iniciar la herramienta desde un símbolo del sistema. La herramienta está en esta ubicación:

        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. Elija una carpeta que contiene las soluciones y proyectos que se va a convertir.

   - Escriba la ruta de acceso en el cuadro en la parte superior de la herramienta o haga clic en **examinar**.

     La herramienta de migración muestra un árbol de proyectos que definir o usar lenguajes DSL. El árbol incluye todos los proyectos que utilizan el **Microsoft.VisualStudio.Modeling.Sdk** o **TextTemplating** ensamblados.

3. Revise el árbol de proyectos y desactive los proyectos que no desea convertir.

   -   Seleccione un proyecto o solución para ver una lista de cambios que hará que la herramienta.

       > [!NOTE]
       >  Las casillas que aparecen junto a los nombres de carpeta no tienen ningún efecto. Debe expandir las carpetas para inspeccionar los proyectos y soluciones.

4. Convertir los proyectos.

   1.  Haga clic en **convertir**.

        Antes de cada archivo de proyecto se convierta, una copia de _proyecto_**.csproj** se guarda como _proyecto_**. vs2008.csproj**

        Una copia de cada _solución_**.sln** se guarda como _solución_**. vs2008.sln**

   2.  Investigue cualquier error en conversiones que se notifica.

        Errores se notifican en la ventana de texto. Además, la vista de árbol muestra un indicador rojo en cada nodo que no se pudo convertir. Puede hacer clic en el nodo para obtener más información sobre ese error.

5. **Transformar todas las plantillas** en soluciones que contengan correctamente convierte los proyectos.

   1.  Abra la solución.

   2.  Haga clic en el **Transformar todas las plantillas** botón en el encabezado del explorador de soluciones.

       > [!NOTE]
       >  Puede realizar este paso innecesario. Para obtener más información, consulte [cómo automatizar Transformar todas las plantillas](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

6. Actualice el código personalizado en los proyectos convertidos.

   -   Intentar compilar los proyectos e investigue los errores.

   -   Pruebe su diseñador.


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vea también

- [Blogs relacionados](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)