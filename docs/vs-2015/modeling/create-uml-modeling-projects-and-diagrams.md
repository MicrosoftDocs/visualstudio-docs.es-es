---
title: Create UML modeling projects and diagrams | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.addnewdiagramdialog
- vs.teamarch.createnewmodelingprojectdialog
helpviewer_keywords:
- projects [Visual Studio ALM], modeling
- diagrams - modeling, modeling
- modeling diagrams
- projects, UML
- UML, deleting diagrams
- UML
- UML diagrams, adding
- UML, projects
- Visual Studio ALM, modeling projects
- modeling projects
- UML diagrams
- projects, modeling
ms.assetid: c178b04b-4fd2-4bed-97e3-d793dae8649c
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5884dcd3f9e3cb8f1910d2e23ec80f910ed2fc9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301002"
---
# <a name="create-uml-modeling-projects-and-diagrams"></a>Crear proyectos y diagramas de modelado UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los modelos UML ayudan a entender, analizar y diseñar sistemas de software. Visual Studio proporciona plantillas para cinco de los diagramas UML más frecuentes: actividades, clases, componentes, secuencia y casos de uso. Además, se pueden crear diagramas de capas, que ayudan a definir la estructura del sistema.

 Los diagramas de modelado UML y los diagramas de capas únicamente pueden existir dentro de un proyecto de modelado. Cada proyecto de modelado contiene un modelo UML compartido y varios diagramas UML. Cada diagrama es una vista parcial del modelo. El modelo UML contiene todos los elementos de los diagramas UML y puede verse mediante el explorador de modelos UML. For information about models and their relationship to diagrams, see [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md). For information about modeling projects under version control, see [Manage models and diagrams under version control](../modeling/manage-models-and-diagrams-under-version-control.md) and [Structure your modeling solution](../modeling/structure-your-modeling-solution.md)

> [!NOTE]
> Hay otro tipo de diagrama, el diagrama de clases de .NET, que se utiliza para visualizar el código de programa. For more information, see [Designing and Viewing Classes and Types](https://go.microsoft.com/fwlink/?LinkId=142231).

## <a name="CreatingModelingDiagrams"></a> Create a Diagram in a Modeling Project
 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

#### <a name="to-create-a-diagram-and-add-it-to-a-project"></a>Para crear un diagrama y agregarlo a un proyecto

1. On the **Architecture** menu, choose **New UML or Layer Diagram**.

2. In the **Add New Diagram** dialog box, click the type of modeling diagram that you want.

    ![Add New Diagram dialog](../modeling/media/uml-adddiagram.png "UML_AddDiagram")

3. Escriba un nombre para el nuevo diagrama.

4. In the **Add to modeling project** box:

   - Select a modeling project that already exists in your solution, and then click **OK**.

     \- o -

   1. Select **Create a new modeling project**, and then click **OK**.

   2. In the **Create New Modeling Project** dialog box, type a name and location for the new project, and then click **OK**.

        ![Create New Modeling Project dialog](../modeling/media/uml-createmodel.png "UML_CreateModel")

        Si la solución está abierta, el nuevo proyecto se agrega a la solución. Si no tiene ninguna solución abierta, puede escribir un nombre para una nueva solución.

   Si ya tiene un proyecto de modelado, también puede utilizar el procedimiento siguiente.

#### <a name="to-add-a-diagram-to-an-existing-modeling-project"></a>Para agregar un diagrama a un proyecto de modelado existente

1. In **Solution Explorer**, click the modeling project node.

    > [!NOTE]
    > The modeling project contains a model definition folder named **ModelDefinition**.

2. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

3. In the **Add New Item -** *\<project name>* dialog box, under **Templates**, click the modeling diagram type, for example, **UML Component Diagram**.

4. Type a name for the diagram, and then click **Add**.

     El diagrama de modelado se abre y aparece en el proyecto de modelado.

    > [!CAUTION]
    > No agregue, copie ni arrastre archivos existentes de diagrama a otros proyectos de modelado o a otras ubicaciones de la solución. Esto provocaría la desaparición de los elementos de los diagramas copiados o se producirían errores al abrir los diagramas. Abra el archivo de diagrama desde el proyecto de modelado en el que se creó. Esto se debe a que un diagrama UML es una vista del modelo que es propiedad de su proyecto de modelado. Para copiar un archivo de diagrama, cree un diagrama nuevo y, a continuación, copie los elementos del diagrama de origen en el nuevo diagrama. For more information, see [Troubleshooting Modeling Projects and Diagrams](#TroubleshootingModelingProjects).

#### <a name="to-create-a-blank-modeling-project"></a>Para crear un proyecto de modelado en blanco

1. En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.

2. In the **New Project** dialog box, under **Installed Templates**, click **Modeling Projects**.

3. In the middle window, click **Modeling Project**.

4. Name the project and specify a location in the **Name** and **Location** boxes.

5. In the **Solution** box, select **Add to Solution** to add the new project to a solution you already have open; or **Create new Solution** to close any open solution and add the project to a new solution.

## <a name="RemovingModelingDiagrams"></a> Removing Modeling Diagrams from a Project
 Los diagramas se pueden eliminar de manera permanente o se pueden excluir temporalmente de un proyecto y, más adelante, restaurarlos.

#### <a name="to-permanently-delete-a-diagram-from-a-project"></a>Para eliminar permanentemente un diagrama de un proyecto

- In **Solution Explorer**, right-click the main file that represents the diagram, and then click **Delete**.

     El diagrama se quita del proyecto y del sistema de archivos. The elements shown on the diagram are not removed from **UML Model Explorer**.

    > [!NOTE]
    > Cada diagrama tiene dos archivos, uno dependiente del otro. Por ejemplo, si tiene un diagrama de componentes con el nombre `CD1`, debe eliminar el archivo denominado `CD1.componentdiagram`. Su archivo dependiente `CD1.componentdiagram.layout` se eliminará automáticamente.

#### <a name="to-temporarily-exclude-a-diagram-from-a-project"></a>Para excluir temporalmente un diagrama de un proyecto

- In **Solution Explorer**, right-click the diagram file, and then click **Exclude from Project**.

     El diagrama se quita del proyecto, pero no del sistema de archivos.

    > [!NOTE]
    > The elements shown on the diagram are not removed from **UML Model Explorer**.

#### <a name="to-restore-a-temporarily-excluded-diagram-to-a-project"></a>Para restaurar un diagrama excluido temporalmente en un proyecto

1. In **Solution Explorer**, click the modeling project node.

    > [!NOTE]
    > The modeling project contains a model definition folder named **ModelDefinition**.

2. On the **Project** menu, click **Add Existing Item**.

3. In the **Add Existing Item** dialog box, locate the diagram file, select the file, and then click **Add**.

     El diagrama de modelado se abre y aparece en el proyecto de modelado.

    > [!NOTE]
    > Cada diagrama tiene un par de archivos en el sistema de archivos. No seleccione un archivo con la extensión `.layout`. Además, Visual Studio no permite agregar diagramas UML existentes a varios proyectos de modelado. Cada archivo de diagrama debe abrirse dentro del proyecto de modelado en el que se creó. Esto se debe a que un diagrama UML muestra una vista de un modelo que es propiedad de su proyecto de modelado.

## <a name="NonModelDiagrams"></a> Diagrams that Do Not Require Modeling Projects
 Los tipos de diagramas siguientes no forman parte de un proyecto de modelado:

- Diagramas de clases que se crean como vistas del código fuente. Estos no están relacionados con diagramas de clases UML. For more information, see [Designing and Viewing Classes and Types](../ide/designing-and-viewing-classes-and-types.md).

- Mapas de código. Vea [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).

- Diagramas que no son diagramas UML o diagramas de capas, como los lenguajes específicos de dominio.

## <a name="TroubleshootingModelingProjects"></a> Troubleshooting Modeling Projects and Diagrams
 En la tabla siguiente se describen los problemas que pueden producirse con proyectos de modelado o diagramas y cómo resolverlos:

|**Problema**|**Causes**|**Resolución**|
|---------------|----------------|--------------------|
|El proyecto de modelado no se puede abrir o cargar en la solución.<br /><br /> Se mostrará el mensaje siguiente:<br /><br /> "Uno o varios proyectos de la solución no se cargaron correctamente. Consulte la ventana de salida para obtener más información".<br /><br /> La ventana de salida muestra el siguiente mensaje:<br /><br /> "*ModelingProjectFilenameAndPath*.modelproj: error: Unrecognized Guid format."|Un proyecto de modelado contiene referencias a proyectos que tienen el mismo nombre y están en la misma solución.<br /><br /> Por ejemplo, una capa está vinculada a proyectos que tienen el mismo nombre y están en la misma solución.|Utilice un editor de texto para abrir el archivo del proyecto de modelado, quite las referencias y, a continuación, intente abrir de nuevo el proyecto de modelado.<br /><br /> Para evitar este problema, no agregue referencias a proyectos que tengan el mismo nombre. Asegúrese de que los proyectos tienen nombres únicos.|
|Faltan elementos en los diagramas que se agregan, copian o arrastran a otros proyectos de modelado o a otras ubicaciones de la solución.<br /><br /> O bien<br /><br /> Cuando intenta abrir un diagrama, se muestran los mensajes siguientes:<br /><br /> -   "Some shapes or connectors on the diagram are missing because their definitions do not exist in this project. Puede que las definiciones se eliminaran del modelo mientras se cerraba el diagrama o que se copiara el diagrama en un proyecto que no contiene esas definiciones".<br /><br /> O bien<br /><br /> -   "This document is opened by another project."|El archivo de diagrama se agregó, arrastró o copió desde un proyecto de modelado a otro proyecto de modelado o a otra ubicación de la solución.|Para copiar un archivo de diagrama, cree un diagrama nuevo y, a continuación, copie los elementos del diagrama de origen en el nuevo diagrama.|

## <a name="see-also"></a>Vea también
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [Structure your modeling solution](../modeling/structure-your-modeling-solution.md)
