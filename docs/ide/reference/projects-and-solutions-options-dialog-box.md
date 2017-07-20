---
title: "Proyectos y soluciones, Cuadro de diálogo Opciones | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
caps.latest.revision: 12
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: a41015624d9c64e053770707bf09b73d8606cb03
ms.contentlocale: es-es
ms.lasthandoff: 05/24/2017

---
# Proyectos y soluciones, Cuadro de diálogo Opciones
<a id="projects-and-solutions-options-dialog-box" class="xliff"></a>
Establece la ruta de acceso predeterminada de las carpetas de proyecto de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y determina el comportamiento predeterminado de la ventana **Salida**, **Lista de tareas** y el **Explorador de soluciones** mientras se desarrollan y compilan proyectos. Para acceder a este cuadro de diálogo, haga clic en **Herramientas/Opciones**, expanda **Proyectos y soluciones** y haga clic en **General**.  
  
> [!NOTE]
>  Las opciones disponibles en los cuadros de diálogo, así como los nombres y las ubicaciones de los comandos de menú que se ven, podrían diferir de lo que se describe en la Ayuda, en función de los valores de configuración o de edición activos. Esta página de la Ayuda se ha redactado teniendo en cuenta la **Configuración general de desarrollo**. Para ver o cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**. Para más información, vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## Configuración
<a id="settings" class="xliff"></a>  
 **Ubicación de proyectos**  
 Establece la ubicación predeterminada donde se crean las nuevas carpetas y directorios de proyectos y soluciones. Varios cuadros de diálogo también usan la ubicación establecida en esta opción para los puntos iniciales de las carpetas. Por ejemplo, el cuadro de diálogo Abrir proyecto usa esta ubicación para el acceso directo Mis proyectos.  
  
 **Ubicación de plantillas de proyecto de usuario**  
 Establece la ubicación predeterminada usada por el cuadro de diálogo **Nuevo proyecto** para crear la lista de **Mis plantillas**. Para más información, vea [Cómo: Localizar y organizar plantillas](../../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
 **Ubicación de plantillas de elemento de usuario**  
 Establece la ubicación predeterminada usada por el cuadro de diálogo **Agregar nuevo elemento** para crear la lista de **Mis plantillas**. Para más información, vea [Cómo: Localizar y organizar plantillas](../../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
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
 Muestra automáticamente la ventana de salida en el IDE al empezar la compilación de la solución. Para más información, vea [Cómo: Controlar la ventana Resultados](http://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858). Esta opción está habilitada de forma predeterminada.  
  
 **Solicitar cambio de nombre simbólico al cambiar el nombre de los archivos**  
 Cuando se selecciona, muestra un cuadro de mensaje que pregunta si [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe cambiar o no el nombre de todas las referencias del proyecto al elemento de código.  
  
## Vea también
<a id="see-also" class="xliff"></a>  
 [Cuadro de diálogo Opciones, Proyectos y soluciones, Compilar y ejecutar](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
