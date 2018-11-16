---
title: Crear proyectos de modelado UML y diagramas | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5d841c9fde677eb4a8fb17e952a817364dab277e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738397"
---
# <a name="create-uml-modeling-projects-and-diagrams"></a>Crear proyectos y diagramas de modelado UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los modelos UML ayudan a entender, analizar y diseñar sistemas de software. Visual Studio proporciona plantillas para cinco de los diagramas UML más frecuentes: actividades, clases, componentes, secuencia y casos de uso. Además, se pueden crear diagramas de capas, que ayudan a definir la estructura del sistema.  
  
 Los diagramas de modelado UML y los diagramas de capas únicamente pueden existir dentro de un proyecto de modelado. Cada proyecto de modelado contiene un modelo UML compartido y varios diagramas UML. Cada diagrama es una vista parcial del modelo. El modelo UML contiene todos los elementos de los diagramas UML y puede verse mediante el explorador de modelos UML. Para obtener información sobre los modelos y su relación con los diagramas, vea [modelos y diagramas UML editar](../modeling/edit-uml-models-and-diagrams.md). Para obtener información sobre proyectos de modelado bajo control de versiones, vea [administrar modelos y diagramas con control de versiones](../modeling/manage-models-and-diagrams-under-version-control.md) y [estructurar la solución de modelado](../modeling/structure-your-modeling-solution.md)  
  
> [!NOTE]
>  Hay otro tipo de diagrama, el diagrama de clases de .NET, que se utiliza para visualizar el código de programa. Para obtener más información, consulte [diseñar y ver clases y tipos](http://go.microsoft.com/fwlink/?LinkId=142231).  
  
##  <a name="CreatingModelingDiagrams"></a> Crear un diagrama en un proyecto de modelado  
 Para ver qué versiones de Visual Studio admiten esta característica, vea [Compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
#### <a name="to-create-a-diagram-and-add-it-to-a-project"></a>Para crear un diagrama y agregarlo a un proyecto  
  
1. En el **arquitectura** menú, elija **nuevo UML o diagrama de capas**.  
  
2. En el **Agregar nuevo diagrama** diálogo cuadro, haga clic en el tipo de diagrama de modelado que desee.  
  
    ![Agregar cuadro de diálogo nuevo diagrama](../modeling/media/uml-adddiagram.png "UML_AddDiagram")  
  
3. Escriba un nombre para el nuevo diagrama.  
  
4. En el **agregar a proyecto de modelado** cuadro:  
  
   - Seleccione un proyecto de modelado que ya existe en la solución y, a continuación, haga clic en **Aceptar**.  
  
     \- o -  
  
   1.  Seleccione **crear un nuevo proyecto de modelado**y, a continuación, haga clic en **Aceptar**.  
  
   2.  En el **crear nuevo proyecto de modelado** cuadro de diálogo, escriba un nombre y una ubicación para el nuevo proyecto y, a continuación, haga clic en **Aceptar**.  
  
        ![Cuadro de diálogo nuevo proyecto de modelado crear](../modeling/media/uml-createmodel.png "UML_CreateModel")  
  
        Si la solución está abierta, el nuevo proyecto se agrega a la solución. Si no tiene ninguna solución abierta, puede escribir un nombre para una nueva solución.  
  
   Si ya tiene un proyecto de modelado, también puede utilizar el procedimiento siguiente.  
  
#### <a name="to-add-a-diagram-to-an-existing-modeling-project"></a>Para agregar un diagrama a un proyecto de modelado existente  
  
1.  En **el Explorador de soluciones**, haga clic en el modelado del nodo del proyecto.  
  
    > [!NOTE]
    >  El proyecto de modelado contiene una carpeta de definición de modelo denominada **ModelDefinition**.  
  
2.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
3.  En el **Agregar nuevo elemento -**  *\<nombre del proyecto >* cuadro de diálogo **plantillas**, haga clic en el modelado del diagrama de tipo, por ejemplo, **UML Diagrama de componentes**.  
  
4.  Escriba un nombre para el diagrama y, a continuación, haga clic en **agregar**.  
  
     El diagrama de modelado se abre y aparece en el proyecto de modelado.  
  
    > [!CAUTION]
    >  No agregue, copie ni arrastre archivos existentes de diagrama a otros proyectos de modelado o a otras ubicaciones de la solución. Esto provocaría la desaparición de los elementos de los diagramas copiados o se producirían errores al abrir los diagramas. Abra el archivo de diagrama desde el proyecto de modelado en el que se creó. Esto se debe a que un diagrama UML es una vista del modelo que es propiedad de su proyecto de modelado. Para copiar un archivo de diagrama, cree un diagrama nuevo y, a continuación, copie los elementos del diagrama de origen en el nuevo diagrama. Para obtener más información, consulte [solución de problemas de proyectos de modelado y diagramas](#TroubleshootingModelingProjects).  
  
#### <a name="to-create-a-blank-modeling-project"></a>Para crear un proyecto de modelado en blanco  
  
1.  En el menú **Archivo** , elija **Nuevo**y haga clic en **Proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo **plantillas instaladas**, haga clic en **proyectos de modelado**.  
  
3.  En la ventana central, haga clic en **proyecto de modelado**.  
  
4.  Denomine el proyecto y especifique una ubicación en la **nombre** y **ubicación** cuadros.  
  
5.  En el **solución** cuadro, seleccione **agregar a solución** para agregar el nuevo proyecto a una solución que ya haya abierto; o **crear nueva solución** para cerrar cualquier solución abierta y agregar el proyecto para una nueva solución.  
  
##  <a name="RemovingModelingDiagrams"></a> Quitar diagramas de un proyecto de modelado  
 Los diagramas se pueden eliminar de manera permanente o se pueden excluir temporalmente de un proyecto y, más adelante, restaurarlos.  
  
#### <a name="to-permanently-delete-a-diagram-from-a-project"></a>Para eliminar permanentemente un diagrama de un proyecto  
  
-   En **el Explorador de soluciones**, haga clic en el archivo principal que representa el diagrama y, a continuación, haga clic en **eliminar**.  
  
     El diagrama se quita del proyecto y del sistema de archivos. No se quitan los elementos que aparecen en el diagrama de **Explorador de modelos UML**.  
  
    > [!NOTE]
    >  Cada diagrama tiene dos archivos, uno dependiente del otro. Por ejemplo, si tiene un diagrama de componentes con el nombre `CD1`, debe eliminar el archivo denominado `CD1.componentdiagram`. Su archivo dependiente `CD1.componentdiagram.layout` se eliminará automáticamente.  
  
#### <a name="to-temporarily-exclude-a-diagram-from-a-project"></a>Para excluir temporalmente un diagrama de un proyecto  
  
-   En **el Explorador de soluciones**, haga clic en el archivo de diagrama y, a continuación, haga clic en **excluir del proyecto**.  
  
     El diagrama se quita del proyecto, pero no del sistema de archivos.  
  
    > [!NOTE]
    >  No se quitan los elementos que aparecen en el diagrama de **Explorador de modelos UML**.  
  
#### <a name="to-restore-a-temporarily-excluded-diagram-to-a-project"></a>Para restaurar un diagrama excluido temporalmente en un proyecto  
  
1.  En **el Explorador de soluciones**, haga clic en el modelado del nodo del proyecto.  
  
    > [!NOTE]
    >  El proyecto de modelado contiene una carpeta de definición de modelo denominada **ModelDefinition**.  
  
2.  En el **proyecto** menú, haga clic en **Agregar elemento existente**.  
  
3.  En el **Agregar elemento existente** cuadro de diálogo, busque el archivo de diagrama, seleccione el archivo y, a continuación, haga clic en **agregar**.  
  
     El diagrama de modelado se abre y aparece en el proyecto de modelado.  
  
    > [!NOTE]
    >  Cada diagrama tiene un par de archivos en el sistema de archivos. No seleccione un archivo con la extensión `.layout`. Además, Visual Studio no permite agregar diagramas UML existentes a varios proyectos de modelado. Cada archivo de diagrama debe abrirse dentro del proyecto de modelado en el que se creó. Esto se debe a que un diagrama UML muestra una vista de un modelo que es propiedad de su proyecto de modelado.  
  
##  <a name="NonModelDiagrams"></a> Diagramas que no necesitan proyectos de modelado  
 Los tipos de diagramas siguientes no forman parte de un proyecto de modelado:  
  
-   Diagramas de clases que se crean como vistas del código fuente. Estos no están relacionados con diagramas de clases UML. Para obtener más información, consulte [diseñar y ver clases y tipos](../ide/designing-and-viewing-classes-and-types.md).  
  
-   Mapas de código. Vea [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).  
  
-   Diagramas que no son diagramas UML o diagramas de capas, como los lenguajes específicos de dominio.  
  
##  <a name="TroubleshootingModelingProjects"></a> Solución de problemas de proyectos de modelado y diagramas  
 En la tabla siguiente se describen los problemas que pueden producirse con proyectos de modelado o diagramas y cómo resolverlos:  
  
|**Problema**|**Causas**|**Resolución**|  
|---------------|----------------|--------------------|  
|El proyecto de modelado no se puede abrir o cargar en la solución.<br /><br /> Se mostrará el mensaje siguiente:<br /><br /> "Uno o varios proyectos de la solución no se cargaron correctamente. Consulte la ventana de salida para obtener más información".<br /><br /> La ventana de salida muestra el siguiente mensaje:<br /><br /> "*ModelingProjectFilenameAndPath*. modelproj: error: formato de Guid no reconocido."|Un proyecto de modelado contiene referencias a proyectos que tienen el mismo nombre y están en la misma solución.<br /><br /> Por ejemplo, una capa está vinculada a proyectos que tienen el mismo nombre y están en la misma solución.|Utilice un editor de texto para abrir el archivo del proyecto de modelado, quite las referencias y, a continuación, intente abrir de nuevo el proyecto de modelado.<br /><br /> Para evitar este problema, no agregue referencias a proyectos que tengan el mismo nombre. Asegúrese de que los proyectos tienen nombres únicos.|  
|Faltan elementos en los diagramas que se agregan, copian o arrastran a otros proyectos de modelado o a otras ubicaciones de la solución.<br /><br /> o bien<br /><br /> Cuando intenta abrir un diagrama, se muestran los mensajes siguientes:<br /><br /> -"Algunas formas o conectores en el diagrama faltan porque no existen sus definiciones en este proyecto. Puede que las definiciones se eliminaran del modelo mientras se cerraba el diagrama o que se copiara el diagrama en un proyecto que no contiene esas definiciones".<br /><br /> O bien<br /><br /> -"Este documento está abierto en otro proyecto".|El archivo de diagrama se agregó, arrastró o copió desde un proyecto de modelado a otro proyecto de modelado o a otra ubicación de la solución.|Para copiar un archivo de diagrama, cree un diagrama nuevo y, a continuación, copie los elementos del diagrama de origen en el nuevo diagrama.|  
  
## <a name="see-also"></a>Vea también  
 [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Estructurar la solución de modelado](../modeling/structure-your-modeling-solution.md)



