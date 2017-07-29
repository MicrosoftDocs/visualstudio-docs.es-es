---
title: "Proyectos y soluciones, Cuadro de diálogo Opciones | Microsoft Docs"
ms.custom: 
ms.date: 7/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
- VS.ToolsOptionsPages.Projects.Locations
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
caps.latest.revision: 12
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: dc7a0c10390de67b56a83d2824224bed24125db0
ms.openlocfilehash: 9e34dc6bd0a876be15dccaff519d67a566022008
ms.contentlocale: es-es
ms.lasthandoff: 07/17/2017

---
# <a name="projects-and-solutions-options-dialog-box"></a>Proyectos y soluciones, Cuadro de diálogo Opciones

Establece el comportamiento [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] relacionado con proyectos y soluciones. Para acceder a estas opciones, seleccione **Herramientas > Opciones**, expanda **Proyectos y soluciones** y haga clic en **General**.

Las rutas de acceso predeterminadas para las carpetas de proyectos y plantillas se establecen a través de la pestaña **Ubicaciones** en el mismo cuadro de diálogo.
  
> [!NOTE]
>  Las opciones disponibles en los cuadros de diálogo, así como los nombres y las ubicaciones de los comandos de menú que se ven, podrían diferir de lo que se describe en la Ayuda, en función de los valores de configuración o de edición activos. Esta página de la Ayuda se ha redactado teniendo en cuenta la **Configuración general de desarrollo**. Para ver o cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**. Para más información, vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="general-tab-options"></a>Opciones de la pestaña General  
 
**Carga de solución ligera**: reduce la cantidad de tiempo y memoria necesarios para cargar soluciones grandes en el IDE. Las soluciones grandes que contienen muchos proyectos de C#, Visual Basic o C++ probablemente experimentarán una ventaja de rendimiento considerable al usar la carga de solución ligera.

- **Permitir que Visual Studio elija lo mejor para mi solución**: permite que Visual Studio determine automáticamente si se debe aplicar la carga de solución ligera según las características de la solución.
- **Habilitado**: siempre se aplica la carga de solución ligera al cargar las soluciones.
- **Deshabilitado**: nunca se aplica la carga de solución ligera.

Para obtener más información, vea [Optimize Visual Studio Startup Time](../optimize-visual-studio-startup-time.md#speed-up-solution-load) (Optimizar el tiempo de inicio de Visual Studio).

**Mostrar lista de errores si la compilación termina con errores**  
Abre la ventana **Lista de errores** al terminar la compilación solo si no se ha podido compilar un proyecto. Se muestran los errores que se producen durante el proceso de compilación. Cuando esta opción está desactivada, se siguen produciendo errores, pero no se abre la ventana una vez finalizada la compilación. Esta opción está habilitada de forma predeterminada.  

**Realizar seguimiento del elemento activo en el Explorador de soluciones**  
Si esta opción está activada, el **Explorador de soluciones** se abre automáticamente y se selecciona el elemento activo. El elemento seleccionado cambia conforme trabaja con distintos archivos de un proyecto o solución o con distintos componentes de un diseñador. Si esta opción está desactivada, la selección del **Explorador de soluciones** no cambia automáticamente. Esta opción está habilitada de forma predeterminada.  

**Mostrar configuraciones de compilación avanzadas**  
Si está activada, las opciones de configuración de compilación aparecen en los cuadros de diálogo **Páginas de propiedades del proyecto** y **Páginas de propiedades de la solución**. Si está desactivada, las opciones de configuración de compilación no aparecen en los cuadros de diálogo **Páginas de propiedades del proyecto** y **Páginas de propiedades de la solución** de los proyectos de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] y [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] que contienen una o las dos configuraciones de depuración y publicación. Si un proyecto tiene una configuración definida por el usuario, se muestran las opciones de configuración de compilación.  

Si no está activada, los comandos del menú **Compilar**, como **Compilar solución**, **Recompilar solución** y **Limpiar solución**, se ejecutan en la configuración de publicación, mientras que los comandos del menú **Depurar**, como **Iniciar depuración** e **Iniciar sin depurar**, se ejecutan en la configuración de depuración.  

**Mostrar solución siempre**  
Cuando se selecciona, la solución y todos los comandos que se aplican a soluciones siempre se muestran en el IDE. Cuando está desactivada, todos los proyectos se crean como proyectos independientes y no ve la solución en el Explorador de soluciones ni en los comandos que se aplican a las soluciones en el IDE si la solución solo contiene un proyecto.  

**Guardar nuevos proyectos al crearlos**  
Si está activada, puede especificar una ubicación para el proyecto en el cuadro de diálogo **Nuevo proyecto**. Cuando está desactivada, todos los proyectos nuevos se crean como proyectos temporales. Cuando se trabaja con proyectos temporales, puede crear y experimentar con un proyecto sin tener que especificar una ubicación de disco.  

**Advertir al usuario cuando la ubicación del proyecto no sea de confianza**  
Si intenta crear un nuevo proyecto o abrir un proyecto existente en una ubicación que no sea de plena confianza (por ejemplo, en una ruta de acceso UNC o HTTP), se muestra un mensaje. Use esta opción para especificar si el mensaje se muestra cada vez que intente crear o abrir un proyecto en una ubicación que no sea de plena confianza.  

**Mostrar ventana de salida cuando empiece la compilación**  
Muestra automáticamente la ventana de salida en el IDE al empezar la compilación de la solución. Para más información, vea [Cómo: Controlar la ventana Resultados](http://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858).

**Solicitar cambio de nombre simbólico al cambiar el nombre de los archivos**  
Cuando se selecciona, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] muestra un cuadro de mensaje que pregunta si también debe cambiar o no el nombre de todas las referencias del proyecto al elemento de código.  

**Preguntar antes de mover los archivos a una nueva ubicación**  
Cuando se selecciona, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] muestra un cuadro de mensaje de confirmación antes de que las ubicaciones de archivos se cambien por las acciones en el Explorador de soluciones. 

## <a name="locations-tab-options"></a>Opciones de la pestaña Ubicaciones

**Ubicación de proyectos**  
Especifica la ubicación predeterminada donde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] crea las nuevas carpetas de proyectos y soluciones. Varios cuadros de diálogo también usan la ubicación establecida en esta opción para los puntos iniciales de las carpetas. Por ejemplo, el cuadro de diálogo Abrir proyecto usa esta ubicación para el acceso directo Mis proyectos.  

**Ubicación de plantillas de proyecto de usuario**  
Especifica la ubicación predeterminada que usa el cuadro de diálogo **Nuevo proyecto** para crear la lista de **Mis plantillas**. Para más información, vea [Cómo: Localizar y organizar plantillas](../../ide/how-to-locate-and-organize-project-and-item-templates.md).  

**Ubicación de plantillas de elemento de usuario**  
Especifica la ubicación predeterminada que usa el cuadro de diálogo **Agregar nuevo elemento** para crear la lista de **Mis plantillas**. Para más información, vea [Cómo: Localizar y organizar plantillas](../../ide/how-to-locate-and-organize-project-and-item-templates.md). 

## <a name="see-also"></a>Vea también  
- [Cuadro de diálogo Opciones, Proyectos y soluciones, Compilar y ejecutar](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- - [Cuadro de diálogo Opciones, Proyectos y soluciones, Proyectos web](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
