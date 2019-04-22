---
title: Proyectos y soluciones, Cuadro de diálogo Opciones | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9c4876aedd12b2284982304b16049691ce6c9b0d
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59652896"
---
# <a name="projects-and-solutions-options-dialog-box"></a>Proyectos y soluciones, Cuadro de diálogo Opciones
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Establece la ruta de acceso predeterminada de las carpetas de proyecto de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] y determina el comportamiento predeterminado de la ventana **Salida**, **Lista de tareas** y el **Explorador de soluciones** mientras se desarrollan y compilan proyectos. Para acceder a este cuadro de diálogo, haga clic en **Herramientas/Opciones**, expanda **Proyectos y soluciones** y haga clic en **General**.  
  
> [!NOTE]
>  Las opciones disponibles en los cuadros de diálogo, así como los nombres y las ubicaciones de los comandos de menú que se ven, podrían diferir de lo que se describe en la Ayuda, en función de los valores de configuración o de edición activos. Esta página de la Ayuda se ha redactado teniendo en cuenta la **Configuración general de desarrollo**. Para ver o cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="settings"></a>Configuración  
 **Ubicación de proyectos**  
 Establece la ubicación predeterminada donde se crean las nuevas carpetas y directorios de proyectos y soluciones. Varios cuadros de diálogo también usan la ubicación establecida en esta opción para los puntos iniciales de las carpetas. Por ejemplo, el cuadro de diálogo Abrir proyecto usa esta ubicación para el acceso directo Mis proyectos.  
  
 **Ubicación de plantillas de proyecto de usuario**  
 Establece la ubicación predeterminada usada por el cuadro de diálogo **Nuevo proyecto** para crear la lista de **Mis plantillas**. Para obtener más información, vea [Cómo: Buscar y organizar plantillas](../../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
 **Ubicación de plantillas de elemento de usuario**  
 Establece la ubicación predeterminada usada por el cuadro de diálogo **Agregar nuevo elemento** para crear la lista de **Mis plantillas**. Para obtener más información, vea [Cómo: Buscar y organizar plantillas](../../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
 **Mostrar lista de errores si la compilación termina con errores**  
 Abre la ventana **Lista de errores** al terminar la compilación solo si no se ha podido compilar un proyecto. Se muestran los errores que se producen durante el proceso de compilación. Cuando esta opción está desactivada, se siguen produciendo errores, pero no se abre la ventana una vez finalizada la compilación. Esta opción está habilitada de forma predeterminada.  
  
 **Realizar seguimiento del elemento activo en el Explorador de soluciones**  
 Si esta opción está activada, el **Explorador de soluciones** se abre automáticamente y se selecciona el elemento activo. El elemento seleccionado cambia conforme trabaja con distintos archivos de un proyecto o solución o con distintos componentes de un diseñador. Si esta opción está desactivada, la selección del **Explorador de soluciones** no cambia automáticamente. Esta opción está habilitada de forma predeterminada.  
  
 **Mostrar configuraciones de compilación avanzadas**  
 Si está activada, las opciones de configuración de compilación aparecen en los cuadros de diálogo **Páginas de propiedades del proyecto** y **Páginas de propiedades de la solución**. Si está desactivada, las opciones de configuración de compilación no aparecen en los cuadros de diálogo **Páginas de propiedades del proyecto** y **Páginas de propiedades de la solución** de los proyectos de [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] y [!INCLUDE[csprcs](../../includes/csprcs-md.md)] que contienen una o las dos configuraciones de depuración y publicación. Si un proyecto tiene una configuración definida por el usuario, se muestran las opciones de configuración de compilación.  
  
 Si no está activada, los comandos del menú **Compilar**, como **Compilar solución**, **Recompilar solución** y **Limpiar solución**, se ejecutan en la configuración de publicación, mientras que los comandos del menú **Depurar**, como **Iniciar depuración** e **Iniciar sin depurar**, se ejecutan en la configuración de depuración.  
  
 **Mostrar solución siempre**  
 Cuando se selecciona, la solución y todos los comandos que se aplican a soluciones siempre se muestran en el IDE. Cuando está desactivada, todos los proyectos se crean como proyectos independientes y no ve la solución en el Explorador de soluciones ni en los comandos que se aplican a las soluciones en el IDE si la solución solo contiene un proyecto.  
  
 **Guardar nuevos proyectos al crearlos**  
 Si está activada, puede especificar una ubicación para el proyecto en el cuadro de diálogo **Nuevo proyecto**. Cuando está desactivada, todos los proyectos nuevos se crean como proyectos temporales. Cuando se trabaja con proyectos temporales, puede crear y experimentar con un proyecto sin tener que especificar una ubicación de disco.  
  
 **Advertir al usuario cuando la ubicación del proyecto no sea de confianza**  
 Si intenta crear un nuevo proyecto o abrir un proyecto existente en una ubicación que no sea de plena confianza (por ejemplo, en una ruta de acceso UNC o HTTP), se muestra un mensaje. Use esta opción para especificar si el mensaje se muestra cada vez que intente crear o abrir un proyecto en una ubicación que no sea de plena confianza.  
  
 **Mostrar ventana de salida cuando empiece la compilación**  
 Muestra automáticamente la ventana de salida en el IDE al empezar la compilación de la solución. Para obtener más información, vea [Cómo: Controlar la ventana de salida](http://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858). Esta opción está habilitada de forma predeterminada.  
  
 **Solicitar cambio de nombre simbólico al cambiar el nombre de los archivos**  
 Cuando se selecciona, muestra un cuadro de mensaje que pregunta si [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debe cambiar o no el nombre de todas las referencias del proyecto al elemento de código.  
  
## <a name="see-also"></a>Vea también  
 [Cuadro de diálogo Opciones, Proyectos y soluciones, Compilar y ejecutar](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
