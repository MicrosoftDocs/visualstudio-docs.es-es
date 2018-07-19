---
title: 'Tutorial: Importar un flujo de trabajo reutilizable de SharePoint Designer en Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2269beef06f7ca43556c2c00493ac8d7cb1c4ad5
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119539"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>Tutorial: Importar un flujo de trabajo reutilizable de SharePoint Designer en Visual Studio
  Este tutorial muestra cómo importar un flujo de trabajo reutilizable creado en SharePoint Designer 2010 en un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proyecto de flujo de trabajo de SharePoint.  
  
 Flujos de trabajo creados en SharePoint Designer, o *flujos de trabajo declarativos*, constan de [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instrucciones en lugar de código. SharePoint Designer 2010 presenta *flujos de trabajo reutilizables*, que son flujos de trabajo declarativos y portátiles que pueden usar distintas listas de sitios de SharePoint.  
  
 Flujos de trabajo creados en [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], como flujos de trabajo secuenciales y de estado de máquina, se denominan *flujos de trabajo de código*. Los flujos de trabajo de código constan de archivos XML y módulos de código en el que los usuarios pueden personalizar el comportamiento del flujo de trabajo.  
  
 Visual Studio permite importar flujos de trabajo reutilizables creados en SharePoint Designer 2010 y convertirlas en flujos de trabajo de código para su uso en los sitios de SharePoint.  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Creación de un flujo de trabajo sencilla y reutilizable en SharePoint Designer.  
  
-   Exportar el flujo de trabajo reutilizable de SharePoint Designer para un *.wsp* archivo y en SharePoint.  
  
-   Importar el *.wsp* archivo [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usando el proyecto Importar flujo de trabajo reutilizable.  
  
-   Modificar el flujo de trabajo mediante la adición de código.  
  
-   Mediante el flujo de trabajo importado en un sitio de SharePoint.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint. Para obtener más información, consulte [requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.  
  
## <a name="create-target-sharepoint-subsites"></a>Crear subsitios de SharePoint de destino
 En primer lugar cree dos nuevos subsitios de SharePoint: uno para hospedar los flujos de trabajo reutilizables de SharePoint Designer, otro para hospedar los flujos de trabajo convertidos.  
  
#### <a name="to-create-sharepoint-subsites"></a>Para crear subsitios de SharePoint  
  
1.  En SharePoint Designer 2010, en la barra de menús, elija **archivo** > **nuevo sitio Web en blanco**.  
  
2.  En el **nuevo sitio Web en blanco** cuadro de diálogo, vaya a un sitio de SharePoint donde desea crear el flujo de trabajo o usar el valor http://*SystemName*/ y, a continuación, elija el **Aceptar** botón.  
  
     Aparece la página principal.  
  
3.  En el **subsitios** sección, elija el **New** botón.  
  
4.  En el **New** cuadro de diálogo, seleccione **plantillas de SharePoint** en la lista en el panel izquierdo y elija **Team Site** en la lista en el panel derecho.  
  
5.  En el **especificar la ubicación del sitio Web** cuadro, reemplace la palabra **subsitio** en la dirección URL con **SPD1**y, a continuación, elija el **Aceptar** botón.  
  
     Se abrirá el nuevo subsitio en SharePoint Designer. Cierre esta instancia de SharePoint Designer y vuelva a la primera instancia (el sitio de nivel superior).  
  
6.  Repita los pasos 3 a 5 para crear el segundo subsitio, pero esta vez reemplace la palabra **subsitio** en el [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] con **SPD2**.  
  
## <a name="create-a-sharepoint-designer-reusable-workflow"></a>Crear un flujo de trabajo reutilizable de SharePoint Designer
 Dado que SharePoint no incluye los flujos de trabajo reutilizables que puede usar para este ejemplo, se creará una. En este flujo de trabajo simple, cuando un usuario escribe una nueva tarea en la lista de tareas que tiene un título específico, la tarea se asigna a ese usuario.  
  
#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>Para crear un flujo de trabajo reutilizable de SharePoint Designer
  
1.  En el **subsitios** sección, elija el **SPD1** sitio para modificarlo.  
  
2.  En la cinta de opciones, elija la **flujo de trabajo reutilizable** botón.  
  
     Aparece el Asistente de creación de flujo de trabajo reutilizable.  
  
3.  En el **nombre** , escriba **flujo de trabajo de tarea SPD**.  
  
4.  En el **tipo de contenido** elija **tarea**y, a continuación, elija el **Aceptar** botón.  
  
     El flujo de trabajo se abre en el Diseñador de flujo de trabajo de SharePoint Designer.  
  
5.  En el Diseñador de flujo de trabajo, elija el paso 1 y, a continuación, en la cinta de opciones, elija la **condición** botón.  
  
6.  En la lista de condiciones, elija **si el campo de elemento actual es igual al valor**.  
  
     Este paso agrega una condición que se denomina **si campo es igual al valor**.  
  
7.  En el **si campo es igual al valor** de condición, elija el **campo** vínculo.  
  
8.  En la lista de valores, elija **título**.  
  
9. En el **si campo es igual al valor** de condición, elija el **valor** vínculo.  
  
10. En el cuadro, escriba **nueva tarea**.  
  
     Lee la instrucción de condición ahora **si Current Item: Title es igual a la nueva tarea**.  
  
11. Seleccione la línea en la instrucción de condición y, a continuación, en la cinta de opciones, elija la **acción** botón.  
  
12. En la lista de acciones, elija **campo de conjunto en el elemento actual**.  
  
13. En el **campo de conjunto con valor** acción, elija la **campo** vincular y, a continuación, en la lista, elija **asignado a**.  
  
14. En el **campo de conjunto con valor** acción, elija la **valor** vincular y, a continuación, en la lista de usuarios y grupos existentes, elija **usuario que creó el elemento**.  
  
15. Elija la **agregar** botón y, a continuación, elija el **Aceptar** botón.  
  
     Lee la instrucción de acción ahora **establecer asignado al elemento actual: CreatedBy**.  
  
## <a name="save-and-deploy-the-reusable-workflow"></a>Guardar e implementar el flujo de trabajo reutilizable
 Dado que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] puede importar sólo *.wsp* archivos, debe guardar el flujo de trabajo reutilizable, como un *.wsp* archivo e implementarla en SharePoint antes de importarla en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
> [!IMPORTANT]  
>  Si recibe un error en tiempo de ejecución realizar el procedimiento siguiente, deberá llevar a cabo el procedimiento en un sistema que tiene acceso al sitio de SharePoint.  
  
#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Para guardar e implementar el flujo de trabajo reutilizable  
  
1.  En la parte superior de SharePoint Designer, elija el **guardar** botón para guardar el progreso y, a continuación, elija el **publicar** botón para implementar el flujo de trabajo la **SPD1** sitio de SharePoint .  
  
2.  En el panel de navegación, elija el **flujos de trabajo** objeto.  
  
3.  En **flujo de trabajo reutilizable**, elija **flujo de trabajo de tarea SPD**.  
  
4.  En la cinta de opciones, elija la **Guardar como plantilla** botón para guardar el flujo de trabajo como un *.wsp* archivo.  
  
5.  Abra el **SPD1** sitio de SharePoint en un explorador para ver el *.wsp* archivo en SharePoint.  
  
6.  En la barra Inicio rápido, elija el **bibliotecas** vínculo.  
  
7.  En el **las bibliotecas de documentos** sección, elija el **activos del sitio** vínculo.  
  
     El **flujo de trabajo de tarea SPD** archivo aparece con otros recursos del sitio.  
  
8.  En la lista de archivos, elija el nombre de archivo  
  
9. En el **descarga de archivos** diálogo cuadro, elija el **guardar** botón para guardar la *.wsp* archivo en el sistema local.  
  
## <a name="import-the-wsp-file-into-visual-studio"></a>Importar el archivo .wsp en Visual Studio
 Importar el *.wsp* archivo [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilizando un proyecto Importar flujo de trabajo reutilizable. Este proyecto convierte el flujo de trabajo de un flujo de trabajo reutilizable y declarativo en un flujo de trabajo de código. Una vez convertido el flujo de trabajo, se usará el código para modificar su comportamiento.  
  
#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Para importar un flujo de trabajo desde un archivo .wsp y modifíquelo  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], en la barra de menús, elija **archivo** > **New** > **proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, expanda el **SharePoint** nodo bajo **Visual C#** o **Visual Basic**y, a continuación, elija el **2010** nodo.  
  
3.  En el **plantillas** panel, elija el **el flujo de trabajo de importación reutilizable de SharePoint 2010** plantilla, deje el nombre del proyecto como **WorkflowImportProject1**y, a continuación, elija el **Aceptar** botón.  
  
     Aparece el Asistente de personalización de SharePoint.  
  
4.  En el **especificar el nivel de sitio y de seguridad para la depuración** , escriba el [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] para el segundo subsitio de SharePoint que creó anteriormente: http://*nombre del sistema*  /SPD2.  
  
5.  En el **¿qué es el nivel de confianza para esta solución de SharePoint?** sección, elija el **implementar como solución de granja de servidores** botón de opción y, a continuación, elija el **siguiente** botón.  
  
     Para obtener más información acerca de espacio aislado frente a soluciones de granja de servidores, consulte [consideraciones sobre la solución en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  En el **especificar el origen del nuevo proyecto** página, vaya a la ubicación en el sistema donde se guardó anteriormente el *.wsp* de archivos, abra el archivo y, a continuación, elija el **siguiente** botón.  
  
    > [!NOTE]  
    >  Elija la **finalizar** botón para importar todos los elementos disponibles en el *.wsp* archivo.  
  
     Esto muestra una lista de flujos de trabajo reutilizables para la importación.  
  
7.  En el **seleccionar elementos para importar** , seleccione el **flujo de trabajo de tarea SPD** flujo de trabajo y, a continuación, elija el **finalizar** botón.  
  
     Una vez finalizada la operación de importación, un proyecto denominado **WorkflowImportProject1** se crea que contiene un flujo de trabajo denominado **SPD_Workflow_TestFT**. En esta carpeta es el archivo de definición del flujo de trabajo *Elements.xml* y el archivo del Diseñador de flujo de trabajo (*.xoml*). El diseñador contiene dos archivos: el archivo de reglas (Rules) y el archivo de código subyacente (ya sea *.cs* o *.vb*, en función de lenguaje de programación del proyecto).  
  
8.  En **el Explorador de soluciones**, elimine el **otros archivos importados** carpeta.  
  
9. En el *Elements.xml* de archivos, eliminar `InstantiationURL="_layouts/IniErkflIP.sspx"`.  
  
10. En **el Explorador de soluciones**, elija **WorkflowImportProject1**y, a continuación, en la barra de menús, elija **proyecto** > **establecer como proyecto de inicio**  establecer **WorkflowImportProject1** como elemento de inicio.  
  
     Esto muestra la lista inmediatamente cuando se depura el proyecto.  
  
11. Dado que el **flujo de trabajo de importación reutilizable de SharePoint 2010** plantilla no importa los valores de propiedad de asociación del flujo de trabajo importado, debe escribirlos. Para hacerlo:  
  
    1.  En **el Explorador de soluciones**, elija el **SPD_Workflow_TestFT** nodo.  
  
    2.  Elija el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")) situado junto a una de las propiedades de la lista, como el **lista destino** propiedad.  
  
    3.  Rellene los valores que faltan en el Asistente de personalización de SharePoint y, a continuación, elija el **finalizar** botón.  
  
12. Elija el archivo .xoml y, a continuación, en la barra de menús, elija **vista** > **diseñador** para ver el flujo de trabajo importado en el Diseñador de flujo de trabajo.  
  
13. En el **Windows Workflow v3.0** nodo de la **cuadro de herramientas**, realice uno de los pasos siguientes:  
  
    -   Abra el menú contextual para el **código** actividad y, a continuación, elija **copia**. En el Diseñador de flujo de trabajo, abra el menú contextual de la línea bajo el **SequenceActivity1** actividad y, a continuación, elija **pegar**.  
  
    -   Arrastre el **código** actividad desde la **cuadro de herramientas** hasta el Diseñador de flujo de trabajo y conéctelo a la línea bajo el **SequenceActivity1** actividad.  
  
     Esto agrega una actividad en el Diseñador de flujo de trabajo denominado **CodeActivity1**. En esta actividad, agregará una acción de código que crea un anuncio en la lista de anuncios cuando el usuario inicia el flujo de trabajo.  
  
14. Siga una de estas series de procedimientos:  
  
    -   Haga doble clic en **CodeActivity1** para generar un controlador de eventos y ver el código.  
  
    -   En el **propiedades** ventana para **CodeActivity1**, establezca el valor de la **ExecuteCode** propiedad **codeActivity_ExecuteCode**.  
  
15. Agregue lo siguiente bajo existente **mediante** o **importaciones** instrucciones:  
  
     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. Reemplace `codeActivity1_ExecuteCode` con lo siguiente:  
  
     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## <a name="deploy-the-project-and-associate-the-workflow"></a>Implementar el proyecto y asociar el flujo de trabajo
 A continuación, ejecute WorkflowImportProject1 implementarlo en un sitio de SharePoint y, a continuación, asociar el flujo de trabajo a la lista de tareas para ver y probar modificada, convertir flujo de trabajo.  
  
#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Para implementar el proyecto y asociar el flujo de trabajo  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], elija el **F5** clave ejecutar e implementar el proyecto de flujo de trabajo convertido.  
  
2.  En la barra Inicio rápido, elija el **tareas** vínculo para mostrar la lista de tareas.  
  
3.  En el **herramientas de lista** ficha, elija la **elementos** botón y, a continuación, elija el **nuevo elemento** botón.  
  
     El **tareas - nuevo elemento** abre el cuadro de diálogo.  
  
4.  En el **título** , escriba **nueva tarea**y, a continuación, elija el **guardar** botón.  
  
5.  En el **herramientas de lista** ficha, elija la **lista** botón y, a continuación, elija el **configuración de la lista** botón.  
  
     El **configuración de la lista** aparece la página.  
  
6.  En el **permisos y administración** sección, elija el **Workflow Settings** vínculo.  
  
     El **Workflow Settings** aparece la página.  
  
7.  Elija la **agregar un flujo de trabajo** vínculo.  
  
8.  En el **flujo de trabajo** elija **WorkflowImportProject1 - prueba de flujo de trabajo SPD**.  
  
9. En el **nombre** , escriba **prueba de flujo de trabajo SPD**y, a continuación, elija el **Aceptar** botón.  
  
10. En la barra Inicio rápido, elija el **tareas** lista.  
  
11. Elija la flecha situada junto a **nueva tarea**y, a continuación, en la lista, elija **flujos de trabajo**.  
  
12. En el **iniciar un nuevo flujo de trabajo** sección, elija el vínculo para **prueba de flujo de trabajo SPD**y, a continuación, elija el **iniciar** botón para iniciar el flujo de trabajo.  
  
    > [!NOTE]  
    >  Como alternativa, se puede asociar automáticamente un flujo de trabajo con una lista de ejecutar al Asistente para configuración de flujo de trabajo y estableciendo el flujo de trabajo para asociar automáticamente.  
  
     Tenga en cuenta que el flujo de trabajo realiza dos acciones: su nombre aparece en la tarea **asignado a** columna y un anuncio aparecerá en la **anuncios** lista.  
  
## <a name="see-also"></a>Vea también
 [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
