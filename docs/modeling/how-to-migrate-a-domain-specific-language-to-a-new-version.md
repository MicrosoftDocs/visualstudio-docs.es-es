---
title: 'Cómo: migrar un lenguaje específico de dominio a una nueva versión | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: d65739aa02f5e5a36f317bd113dd4dc349bde957
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Cómo: Migrar lenguajes específicos de dominio a una nueva versión
Puede migrar proyectos de definen y utilizar los lenguajes específicos de dominio a [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] de la versión de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] que se distribuyó con [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)].  
  
 Una herramienta de migración se proporciona como parte de [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]. La herramienta convierte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyectos y soluciones que usan o definen herramientas ADSL.  
  
 Debe ejecutar la herramienta de migración de forma explícita: no se inicia automáticamente al abrir una solución en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. La herramienta y el documento de instrucciones detalladas se pueden encontrar en esta ruta de acceso:  
  
 **% Programa Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
## <a name="before-you-migrate-your-dsl-projects"></a>Antes de migrar los proyectos de DSL  
 La herramienta de migración modifica [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] archivos de proyecto (**.csproj**) y archivos de solución (**.sln**).  
  
#### <a name="to-prepare-projects-for-migration"></a>Para preparar los proyectos para la migración.  
  
-   Asegúrese de que el **.csproj** y **.sln** se pueden escribir archivos. Si ya están bajo control de código fuente, asegúrese de que se desprotegen.  
  
-   Realizar una copia de las carpetas que desea migrar.  
  
## <a name="migrating-a-collection-of-projects"></a>Migrar una colección de proyectos  
  
#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Para migrar DSL proyectos y soluciones a Visual Studio 2010  
  
1.  Inicie la herramienta de migración de DSL.  
  
    -   Puede haga doble clic en la herramienta en el Explorador de Windows (o explorador de archivos) o iniciar la herramienta desde un símbolo del sistema. La herramienta está en esta ubicación:  
  
         **%ProgramFiles%\Microsoft visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
2.  Elija la carpeta que contiene las soluciones y proyectos que se va a convertir.  
  
    -   Escriba la ruta de acceso en el cuadro en la parte superior de la herramienta o haga clic en **examinar**.  
  
     La herramienta de migración muestra un árbol de proyectos que definen o usar DSL. El árbol incluye todos los proyectos que utiliza el **Microsoft.VisualStudio.Modeling.Sdk** o **TextTemplating** ensamblados.  
  
3.  Revise el árbol de proyectos y desactive los proyectos que no va a convertir.  
  
    -   Seleccione un proyecto o solución para ver una lista de cambios que harán que la herramienta.  
  
        > [!NOTE]
        >  Las casillas que aparecen junto a los nombres de carpetas no tienen ningún efecto. Debe expandir las carpetas para inspeccionar los proyectos y soluciones.  
  
4.  Convertir los proyectos.  
  
    1.  Haga clic en **convertir**.  
  
         Antes de cada archivo de proyecto se convierta, una copia de *proyecto *** .csproj** se guarda como *proyecto ***.vs2008.csproj**  
  
         Una copia de cada *solución *** .sln** se guarda como *solución ***.vs2008.sln**  
  
    2.  Investigar cualquier error en conversiones que se notifica.  
  
         Errores se notifican en la ventana de texto. Además, la vista de árbol muestra un indicador rojo en cada nodo que no se pudo convertir. Puede hacer clic en el nodo para obtener más información acerca de dicho error.  
  
5.  **Transformar todas las plantillas** en las soluciones que contienen correctamente al convertir proyectos.  
  
    1.  Abra la solución.  
  
    2.  Haga clic en el **Transformar todas las plantillas** botón en el encabezado del explorador de soluciones.  
  
        > [!NOTE]
        >  Puede realizar este paso innecesario. Para obtener más información, consulte [cómo automatizar Transformar todas las plantillas](http://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).  
  
6.  Actualice el código personalizado en los proyectos convertidos.  
  
    -   Intente compilar los proyectos e investigue los errores.  
  
    -   Probar el diseñador.  
  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vea también  
 [Blogs relacionados](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)

