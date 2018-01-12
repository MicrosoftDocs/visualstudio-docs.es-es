---
title: 'Tutorial: Importar un flujo de trabajo reutilizable de SharePoint Designer en Visual Studio | Documentos de Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.WSPImport.ImportWF
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
manager: ghogen
ms.workload: office
ms.openlocfilehash: 05428f2e702643b88415663249e9f29a9f7d46bc
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>Tutorial: Importar un flujo de trabajo reutilizable de SharePoint Designer en Visual Studio
  Este tutorial muestra cómo importar un flujo de trabajo reutilizable creado en SharePoint Designer 2010 en un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] proyecto de flujo de trabajo de SharePoint.  
  
 Flujos de trabajo creados en SharePoint Designer, o *flujos de trabajo declarativos*, constan de [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instrucciones en lugar de código. SharePoint Designer 2010 presenta *flujos de trabajo reutilizables*, que son flujos de trabajo portátiles y declarativos que pueden utilizarse por listas diferentes en sitios de SharePoint.  
  
 Flujos de trabajo creados en [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], como flujos de trabajo de máquina de estado y los no secuenciales, se denominan *flujos de trabajo de código*. Los flujos de trabajo de código están compuestos de archivos XML y módulos de código en el que los usuarios pueden personalizar el comportamiento del flujo de trabajo.  
  
 Visual Studio permite importar flujos de trabajo reutilizables creados en SharePoint Designer 2010 y convertirlos en flujos de trabajo de código para su uso en los sitios de SharePoint.  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Crear un flujo de trabajo simple y reutilizable en SharePoint Designer.  
  
-   Exportar el flujo de trabajo reutilizable de SharePoint Designer a un archivo .wsp y en SharePoint.  
  
-   Importar el archivo .wsp en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mediante el proyecto Importar flujo de trabajo reutilizable.  
  
-   Modificar el flujo de trabajo mediante la adición de código.  
  
-   Usar el flujo de trabajo importado en un sitio de SharePoint.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesita los componentes siguientes para completar este tutorial:  
  
-   Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] y SharePoint. Para obtener más información, consulte [requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.  
  
## <a name="create-target-sharepoint-subsites"></a>Crear subsitios de SharePoint de destino  
 Primero debe crear dos nuevos subsitios de SharePoint: uno para hospedar los flujos de trabajo reutilizables de SharePoint Designer, otro para hospedar los flujos de trabajo convertidos.  
  
#### <a name="to-create-sharepoint-subsites"></a>Para crear subsitios de SharePoint  
  
1.  En SharePoint Designer 2010, en la barra de menús, elija **archivo**, **nuevo sitio Web en blanco**.  
  
2.  En el **nuevo sitio Web en blanco** cuadro de diálogo, vaya a un sitio de SharePoint donde desea crear el flujo de trabajo, o utilice el valor de http://*SystemName*/ y, a continuación, elija la **Aceptar** botón.  
  
     Aparece la página principal.  
  
3.  En el **subsitios** sección, elija el **New** botón.  
  
4.  En el **New** diálogo cuadro, elija **plantillas de SharePoint** en la lista en el panel izquierdo y elija **sitio del equipo** en la lista en el panel derecho.  
  
5.  En el **especificar la ubicación del sitio Web** cuadro, reemplace la palabra **subsitio** en la dirección URL con **SPD1**y, a continuación, elija la **Aceptar** botón.  
  
     Se abrirá el nuevo subsitio en SharePoint Designer. Cierre esta instancia de SharePoint Designer y volver a la primera instancia (el sitio de nivel superior).  
  
6.  Repita los pasos 3 a 5 para crear el segundo subsitio, pero esta vez reemplace la palabra **subsitio** en el [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] con **SPD2**.  
  
## <a name="create-a-sharepoint-designer-reusable-workflow"></a>Crear un flujo de trabajo reutilizable de SharePoint Designer  
 Dado que SharePoint no incluye los flujos de trabajo reutilizables que puede usar para este ejemplo, se creará una. En este flujo de trabajo simple, cuando un usuario introduce una nueva tarea en la lista de tareas que tiene un título específico, la tarea se asigna a ese usuario.  
  
#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>Para crear un flujo de trabajo reutilizable de SharePoint Designer  
  
1.  En el **subsitios** sección, elija el **SPD1** sitio para modificarlo.  
  
2.  En la cinta de opciones, elija la **flujo de trabajo reutilizable** botón.  
  
     Aparece el Asistente para crear flujos de trabajo reutilizables.  
  
3.  En el **nombre** cuadro, escriba **flujo de trabajo de tarea SPD**.  
  
4.  En el **tipo de contenido** elija **tarea**y, a continuación, elija la **Aceptar** botón.  
  
     El flujo de trabajo se abre en el Diseñador de flujo de trabajo de SharePoint Designer.  
  
5.  En el Diseñador de flujo de trabajo, elija el paso 1 y, a continuación, en la cinta de opciones, elija la **condición** botón.  
  
6.  En la lista de condiciones, elija **si campo del elemento actual es igual al valor**.  
  
     Este paso agrega una condición que se denomina **si campo es igual al valor**.  
  
7.  En el **si campo es igual al valor** condición, elija la **campo** vínculo.  
  
8.  En la lista de valores, elija **título**.  
  
9. En el **si campo es igual al valor** condición, elija la **valor** vínculo.  
  
10. En el cuadro, escriba **nueva tarea**.  
  
     Lee la instrucción de condición ahora **si actual: título del elemento es igual a la nueva tarea**.  
  
11. Seleccione la línea en la instrucción de condición y, a continuación, en la cinta de opciones, elija la **acción** botón.  
  
12. En la lista de acciones, elija **campo de conjunto en el elemento actual**.  
  
13. En el **campo de conjunto para el valor** acción, elija la **campo** vincular y, a continuación, en la lista, elija **asignado a**.  
  
14. En el **campo de conjunto para el valor** acción, elija la **valor** vincular y, a continuación, en la lista de usuarios y grupos existentes, elija **usuario que creó el elemento**.  
  
15. Elija la **agregar** botón y, a continuación, elija la **Aceptar** botón.  
  
     Lee la instrucción de acción ahora **establecer asignado a en elemento actual: CreatedBy**.  
  
## <a name="save-and-deploy-the-reusable-workflow"></a>Guardar e implementar el flujo de trabajo reutilizable  
 Dado que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] puede importar sólo archivos .wsp, debe guardar el flujo de trabajo reutilizable como un archivo .wsp e implementarlo en SharePoint antes de importarla en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
> [!IMPORTANT]  
>  Si recibe un error en tiempo de ejecución lleva a cabo el procedimiento siguiente, tendrá que llevar a cabo el procedimiento en un sistema que tiene acceso al sitio de SharePoint.  
  
#### <a name="to-save-and-deploy-the-reusable-workflow"></a>Para guardar e implementar el flujo de trabajo reutilizable  
  
1.  En la parte superior de SharePoint Designer, elija la **guardar** botón para guardar el progreso y, a continuación, elija la **publicar** botón para implementar el flujo de trabajo para el **SPD1** sitio de SharePoint .  
  
2.  En el panel de navegación, elija la **flujos de trabajo** objeto.  
  
3.  En **flujo de trabajo reutilizable**, elija **flujo de trabajo de tarea SPD**.  
  
4.  En la cinta de opciones, elija la **Guardar como plantilla** botón para guardar el flujo de trabajo como un archivo .wsp.  
  
5.  Abra la **SPD1** sitio de SharePoint en un explorador para ver el archivo .wsp en SharePoint.  
  
6.  En la barra Inicio rápido, elija la **bibliotecas** vínculo.  
  
7.  En el **las bibliotecas de documentos** sección, elija el **activos del sitio** vínculo.  
  
     El **flujo de trabajo de tarea SPD** archivo aparece con otros activos del sitio.  
  
8.  En la lista de archivos, elija el nombre del archivo  
  
9. En el **descarga de archivos** diálogo cuadro, elija la **guardar** botón para guardar el archivo .wsp en el sistema local.  
  
## <a name="import-the-wsp-file-into-visual-studio"></a>Importar el archivo .wsp en Visual Studio  
 Importar el archivo .wsp en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utilizando un proyecto Importar flujo de trabajo reutilizable. Este proyecto convierte el flujo de trabajo de un flujo de trabajo reutilizable y declarativo en un flujo de trabajo de código. Una vez convertido el flujo de trabajo, se usará el código para modificar su comportamiento.  
  
#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>Para importar un flujo de trabajo de un archivo .wsp y modificarlo  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], en la barra de menús, elija **archivo**, **New**, **proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, expanda el **SharePoint** nodo bajo **Visual C#** o **Visual Basic**y, a continuación, elija la **2010** nodo.  
  
3.  En el **plantillas** panel, elija la **flujo de trabajo de importación reutilizable SharePoint 2010** plantilla, deje el nombre del proyecto como **WorkflowImportProject1**y, a continuación, elija la **Aceptar** botón.  
  
     Aparece el Asistente de personalización de SharePoint.  
  
4.  En el **especificar el nivel de sitio y la seguridad para la depuración** página, especifique la [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] para el segundo subsitio de SharePoint que creó previamente: http://*nombre del sistema*  /SPD2.  
  
5.  En el **¿qué es el nivel de confianza para esta solución de SharePoint?** sección, elija el **implementar como solución de granja de servidores** botón de opción y, a continuación, elija la **siguiente** botón.  
  
     Para obtener más información acerca de en un espacio aislado frente a las soluciones de granja de servidores, consulte [consideraciones sobre la solución en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  En el **especifique el nuevo origen de proyecto** página, vaya a la ubicación en el sistema donde guardó el archivo .wsp previamente, abra el archivo y, a continuación, elija la **siguiente** botón.  
  
    > [!NOTE]  
    >  Elija la **finalizar** botón para importar todos los elementos disponibles en el archivo .wsp.  
  
     Esto muestra una lista de flujos de trabajo reutilizables para la importación.  
  
7.  En el **seleccionar elementos para importar** cuadro, elija la **flujo de trabajo de tarea SPD** flujo de trabajo y, a continuación, elija la **finalizar** botón.  
  
     Una vez finalizada la operación de importación, un proyecto denominado **WorkflowImportProject1** se crea con un flujo de trabajo denominado **SPD_Workflow_TestFT**. En esta carpeta es el archivo de definición Elements.xml del flujo de trabajo y el archivo del Diseñador de flujo de trabajo (.xoml). El diseñador contiene dos archivos: el archivo de reglas (. Rules) y el archivo de código subyacente (.cs o .vb, según el lenguaje de programación del proyecto).  
  
8.  En **el Explorador de soluciones**, eliminar el **otros archivos importados** carpeta.  
  
9. En el archivo Elements.xml, elimine `InstantiationURL="_layouts/IniErkflIP.sspx"`.  
  
10. En **el Explorador de soluciones**, elija **WorkflowImportProject1**y, a continuación, en la barra de menús, elija **proyecto**, **establecer como proyecto de inicio** a establecer **WorkflowImportProject1** como el elemento de inicio.  
  
     Esto muestra la lista inmediatamente cuando se depura el proyecto.  
  
11. Dado que la **importar del flujo de trabajo de reutilizable SharePoint 2010** plantilla no importa los valores de propiedad de asociación del flujo de trabajo importado, debe escribirlos. Para hacerlo:  
  
    1.  En **el Explorador de soluciones**, elija la **SPD_Workflow_TestFT** nodo.  
  
    2.  Elija el botón de puntos suspensivos (![elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "elipse del Diseñador de ASP.NET Mobile")) botón situado junto a una de las propiedades de la lista, como el **lista de destinos de** propiedad.  
  
    3.  Rellene los valores que faltan en el Asistente para la personalización de SharePoint y, a continuación, elija la **finalizar** botón.  
  
12. Elija el archivo .xoml y, a continuación, en la barra de menús, elija **vista**, **diseñador** para ver el flujo de trabajo importado en el Diseñador de flujo de trabajo.  
  
13. En el **Windows Workflow v3.0** nodo de la **cuadro de herramientas**, realice uno de los siguientes pasos:  
  
    -   Abra el menú contextual para el **código** actividad y, a continuación, elija **copia**. En el Diseñador de flujo de trabajo, abra el menú contextual de la línea en la **SequenceActivity1** actividad y, a continuación, elija **pegar**.  
  
    -   Arrastre el **código** actividad desde la **cuadro de herramientas** hasta el Diseñador de flujo de trabajo y conectarlo a la línea en la **SequenceActivity1** actividad.  
  
     Esto agrega una actividad en el Diseñador de flujo de trabajo denominado **Actividadcódigo1**. En esta actividad, agregará una acción de código que crea un anuncio en la lista de anuncios cuando el usuario inicia el flujo de trabajo.  
  
14. Siga una de estas series de procedimientos:  
  
    -   Haga doble clic en **Actividadcódigo1** para generar un controlador de eventos y ver el código.  
  
    -   En el **propiedades** ventana para **Actividadcódigo1**, establezca el valor de la **ExecuteCode** propiedad **codeActivity_ExecuteCode**.  
  
15. Agregue lo siguiente bajo las existentes **con** o **importaciones** instrucciones:  
  
     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]  
  
16. Reemplace `codeActivity1_ExecuteCode` con lo siguiente:  
  
     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]  
  
## <a name="deploy-the-project-and-associate-the-workflow"></a>Implementar el proyecto y asociar el flujo de trabajo  
 A continuación, ejecute WorkflowImportProject1 implementarlo en un sitio de SharePoint y, a continuación, asociar el flujo de trabajo a la lista de tareas para ver y comprobar la modificación, convertir flujo de trabajo.  
  
#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>Para implementar el proyecto y asociar el flujo de trabajo  
  
1.  En [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], presione la tecla F5 para ejecutar e implementar el proyecto de flujo de trabajo convertido.  
  
2.  En la barra Inicio rápido, elija la **tareas** vínculo para mostrar la lista de tareas.  
  
3.  En el **herramientas de lista** ficha, elija la **elementos** botón y, a continuación, elija la **nuevo elemento** botón.  
  
     El **tareas - nuevo elemento** abre el cuadro de diálogo.  
  
4.  En el **título** cuadro, escriba **nueva tarea**y, a continuación, elija la **guardar** botón.  
  
5.  En el **herramientas de lista** ficha, elija la **lista** botón y, a continuación, elija la **configuración de la lista** botón.  
  
     El **configuración de la lista** aparecerá la página.  
  
6.  En el **permisos y administración** sección, elija el **configuración de flujo de trabajo** vínculo.  
  
     El **configuración de flujo de trabajo** aparecerá la página.  
  
7.  Elija la **agregar un flujo de trabajo** vínculo.  
  
8.  En el **flujo de trabajo** elija **WorkflowImportProject1 - prueba de flujo de trabajo SPD**.  
  
9. En el **nombre** cuadro, escriba **prueba de flujo de trabajo SPD**y, a continuación, elija la **Aceptar** botón.  
  
10. En la barra Inicio rápido, elija la **tareas** lista.  
  
11. Elija la flecha situada junto a **nueva tarea**y, a continuación, en la lista, elija **flujos de trabajo**.  
  
12. En el **iniciar un nuevo flujo de trabajo** sección, elija el vínculo para **prueba de flujo de trabajo SPD**y, a continuación, elija la **iniciar** botón para iniciar el flujo de trabajo.  
  
    > [!NOTE]  
    >  Como alternativa, se puede asociar automáticamente un flujo de trabajo con una lista, ejecute al Asistente para configuración de flujo de trabajo y establecer el flujo de trabajo para asociar automáticamente.  
  
     Tenga en cuenta que el flujo de trabajo realiza dos acciones: su nombre aparece en la tarea **asignado a** columna y un anuncio aparece en la **anuncios** lista.  
  
## <a name="see-also"></a>Vea también  
 [Importar elementos de un sitio de SharePoint existente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Desarrollar soluciones de SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  