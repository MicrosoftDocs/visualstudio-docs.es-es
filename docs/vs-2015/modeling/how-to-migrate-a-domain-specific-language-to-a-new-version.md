---
title: 'Cómo: migrar lenguajes específicos de dominio a una nueva versión | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 45f7b38f7dbb6ea470b2d9e186dc8e6bf4b33b1e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657330"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Cómo: Migrar lenguajes específicos de dominio a una nueva versión
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede migrar proyectos que definan y usen lenguaje específico de dominio para [!INCLUDE[vs2010](../includes/vs2010-md.md)] de la versión de [!INCLUDE[dsl](../includes/dsl-md.md)] distribuida con [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)].

 Una herramienta de migración se proporciona como parte de [!INCLUDE[vssdk_current_long](../includes/vssdk-current-long-md.md)]. La herramienta convierte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proyectos y soluciones que usan o definen herramientas de DSL.

 Debe ejecutar la herramienta de migración explícitamente: no se inicia automáticamente cuando se abre una solución en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. La herramienta y el documento de instrucciones detalladas se pueden encontrar en esta ruta de acceso:

 **% Archivos de programa%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>Antes de migrar los proyectos DSL
 La herramienta de migración modifica [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] archivos de proyecto ( **. csproj**) y los archivos de solución ( **. sln**).

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

        Antes de que se convierta cada archivo de proyecto, se guarda una copia de _Project_ **. csproj** como _Project_ **. VS2008. csproj**

        Una copia de cada _solución_ **. sln** se guarda como _Solution_ **. VS2008. sln** .

   2. Investigue cualquier conversión con errores que se notifique.

        Los errores se muestran en la ventana de texto. Además, la vista de árbol muestra una marca roja en cada nodo que no se pudo convertir. Puede hacer clic en el nodo para obtener más información sobre ese error.

5. **Transformar todas las plantillas** en soluciones que contengan proyectos convertidos correctamente.

   1. Abra la solución.

   2. Haga clic en el botón **transformar todas las plantillas** en el encabezado de explorador de soluciones.

       > [!NOTE]
       > Puede hacer que este paso no sea necesario. Para obtener más información, consulte [cómo automatizar la transformación de todas las plantillas](https://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

6. Actualice el código personalizado en los proyectos convertidos.

   - Intente compilar los proyectos e investigue los errores.

   - Pruebe el diseñador.

## <a name="see-also"></a>Vea también
 [Novedades del SDK de modelado y virtualización](../misc/what-s-new-in-visualization-and-modeling-sdk.md)
