---
title: Crear soluciones y proyectos | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], deleting
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
ms.assetid: 836f8ca0-3fc9-4f4b-9090-45f2e4d2e9c8
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 336fb41ee6a4c90e7065187b2805aefe9e6e6df7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893707"
---
# <a name="creating-solutions-and-projects"></a>Creating Solutions and Projects
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los proyectos son los contenedores lógicos de todo lo necesario para compilar la aplicación. Cuando se crea un proyecto eligiendo **Archivo &#124; Nuevo &#124; Proyecto** desde el menú principal, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] crea una solución que lo contiene. Después puede agregar otros proyectos nuevos o existentes a la solución si fuese necesario. Puede crear proyectos a partir de archivos de código existentes, así como proyectos temporales (solo .NET) que se eliminarán cuando ya no los necesite.  
  
> [!NOTE]
>  Las descripciones de este tema se basan en Visual Studio Community. Los cuadros de diálogo y los comandos de menú que se ven pueden diferir de los aquí descritos, en función de la configuración o la edición de Visual Studio. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-project-from-an-installed-project-template"></a>Crear un proyecto a partir de una plantilla de proyecto instalada  
 **Archivo &#124; Nuevo &#124; Proyecto** en el menú principal para que aparezca el cuadro de diálogo Nuevo proyecto. En el panel izquierdo en **Instalado &#124; Plantillas**, elija el lenguaje de programación y la plataforma o la tecnología y, después, elija una de las plantillas disponibles en el panel central.  
  
 En el diálogo **Nuevo proyecto** , el menú desplegable **Solución** le ofrece la opción de crear el nuevo proyecto en una solución nueva o existente, o en una nueva instancia de Visual Studio.  
  
## <a name="create-a-project-from-existing-code-files"></a>Crear un proyecto a partir de archivos de código existentes  
 Si tiene una colección de archivos de origen separados, puede crear fácilmente un proyecto que los contenga. Elija **Archivo &#124; Nuevo &#124; Proyecto a partir de código existente** para iniciar el **Asistente para crear proyectos a partir de archivos de código existentes** y siga las indicaciones.  
  
> [!TIP]
>  Esta opción funciona mejor con recopilaciones de archivos relativamente simples.  
  
## <a name="create-a-temporary-project-c-and-visual-basic"></a>Crear un proyecto temporal (C# y Visual Basic)  
 Cuando se trabaja con proyectos temporales, puede crear y experimentar con un proyecto .NET sin especificar una ubicación de disco. Al crear un proyecto, basta con seleccionar un tipo de proyecto y una plantilla y especificar un nombre en el cuadro de diálogo **Nuevo proyecto** . Cuando trabaje con el proyecto temporal, podrá guardarlo o descartarlo en cualquier momento.  
  
## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>Crear un proyecto .NET que tenga como destino una versión concreta de .NET Framework  
 Puede crear un proyecto que tenga como destino versiones anteriores de .NET Framework mediante el menú desplegable de versión **.NET Framework** que se encuentra en la parte superior del cuadro de diálogo **Nuevo proyecto** . Establezca este valor antes de seleccionar una plantilla de proyecto, dado que en la lista solo aparecerán plantillas compatibles con esa versión de .NET Framework.  
  
 Para obtener acceso a versiones anteriores a la 4, debe tener instalado .NET Framework 3.5 en su sistema.  
  
## <a name="downloading-sample-solutions"></a>Descargar soluciones de ejemplo  
 Puede usar Visual para descargar e instalar soluciones de ejemplo desde la [Galería de código de MSDN](http://go.microsoft.com/fwlink/?LinkId=254185).  
  
 Puede descargar los ejemplos individualmente o puede descargar un Sample Pack, que contiene ejemplos relacionados que comparten una tecnología o un tema. Recibirá una notificación cuando se publiquen cambios en el código fuente de cualquier ejemplo que descargue.  
  
 Para obtener más información, vea [Ejemplos de Visual Studio](../ide/visual-studio-samples.md).  
  
## <a name="adding-single-files-at-the-solution-level"></a>Agregar archivos individuales al nivel de solución  
 A veces, puede tener un archivo al que hagan referencia varios proyectos, o que contenga texto o datos varios que, lógicamente, pertenezcan al nivel de solución en lugar de a un proyecto determinado.  Para agregar un solo elemento a una solución:  
  
1.  Haga clic con el botón derecho en el nodo de solución en **Explorador de soluciones** y pulse **Agregar &#124; Nuevo elemento** o **Agregar &#124; Elemento existente**.  
  
## <a name="creating-empty-solutions"></a>Crear soluciones vacías  
 Aunque un proyecto debe residir en una solución, puede crear una solución que no tenga proyectos.  
  
#### <a name="to-create-an-empty-solution"></a>Para crear una solución vacía  
  
1. En el menú **Archivo** , haga clic en **Nuevo** y, a continuación, en **Nuevo proyecto**.  
  
2. En el panel de la izquierda, seleccione **Instalado**, seleccione **Otros tipos de proyectos**y, a continuación, seleccione **Soluciones de Visual Studio** en la lista expandida.  
  
3. En el panel central, seleccione **Solución en blanco**.  
  
4. Establezca los valores **Nombre** y **Ubicación** de su solución y haga clic en **Aceptar**.  
  
   Después de crear una solución vacía, puede agregarle elementos o proyectos nuevos o existentes al hacer clic en **Agregar nuevo elemento** o **Agregar elemento existente** en el menú **Proyecto** .  
  
### <a name="deleting-solutions"></a>Eliminar soluciones  
 Es posible eliminar una solución de forma permanente, pero sin usar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Antes de eliminar una solución, mueva cualquier proyecto que podría desear utilizar de nuevo en otra solución. A continuación, use el Explorador de archivos para eliminar el directorio que contiene los archivos de solución .sln y .suo.  
  
> [!NOTE]
>  El archivo .suo es un archivo oculto que no aparece en la configuración predeterminada del Explorador de archivos.  
  
##### <a name="to-delete-a-solution"></a>Para eliminar una solución  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario en la solución que desea eliminar y seleccione **Abrir carpeta en el Explorador de archivos**.  
  
2.  Suba un nivel en el Explorador de archivos.  
  
3.  Seleccione el directorio que contiene la solución y presione Supr.  
  
## <a name="see-also"></a>Vea también  
 [Soluciones y proyectos](../ide/solutions-and-projects-in-visual-studio.md)   
 [Cómo: Crear soluciones de varios proyectos](http://msdn.microsoft.com/en-us/02ecd6dd-0114-46fe-b335-ba9c5e3020d6)



