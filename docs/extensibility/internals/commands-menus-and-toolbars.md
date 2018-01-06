---
title: "Barras de herramientas, menús y comandos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: "60"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fa1513bcd61ac63fb9d2a59f69a8b2ce22cf5114
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="commands-menus-and-toolbars"></a>Comandos, menús y barras de herramientas
Menús y barras de herramientas son la forma, los usuarios tener acceso a comandos del VSPackage. Los comandos son funciones que realizan tareas, como la impresión de un documento, la actualización de una vista o la creación de un archivo nuevo. Los menús y las barras de herramientas son maneras gráficas y cómodas de presentar los comandos a los usuarios. Normalmente, los comandos relacionados se agrupan en clústeres en el mismo menú o en la misma barra de herramientas.  
  
-   Los menús suelen mostrarse como cadenas de una palabra agrupadas en clúster en una fila de la parte superior del entorno de desarrollo integrado (IDE) o una ventana de herramientas. Los menús también se pueden mostrar como resultado de un evento de botón derecho y se conocen como menús contextuales en ese contexto. Al hacer clic en ellos, los menús se expanden para mostrar uno o varios comandos. Cuando se hace clic en los comandos, pueden llevar a cabo tareas o iniciar submenús que contengan comandos adicionales. Algunos nombres de menú conocidos son Archivo, Edición, Vista y Ventana. Para obtener más información, consulte [extender menús y comandos de](../../extensibility/extending-menus-and-commands.md).  
  
-   Las barras de herramientas normalmente son filas de botones y otros controles, como cuadros combinados, cuadros de lista, cuadros de texto y controladores de menús. Todos los controles de barra de herramientas están asociados a comandos. Cuando se hace clic en un botón de barra de herramientas, se activa su comando asociado. Los botones de barra de herramientas suelen tener iconos que sugieren los comandos subyacentes, como una impresora para un comando Imprimir. En un control de lista desplegable, cada elemento de la lista está asociado a un comando distinto. Un controlador de menú es un híbrido en el que un lado del control es un botón de barra de herramientas y el otro lado es una flecha hacia abajo que muestra comandos adicionales cuando se hace clic en ella. Para obtener más información, consulte [agregando un controlador de menú a una barra de herramientas](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
-   Cuando se crea un comando, también debe crear un controlador de eventos para él. El controlador de eventos determina si el comando es visible o está activado, permite modificar su texto y garantiza que el comando responde correctamente ("enruta") cuando se activa. En la mayoría de los casos, el IDE controla los comandos mediante el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. Comandos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ruta de forma jerárquica, empezando por el contexto de los comandos más interno, según la selección local y continuando hasta el contexto más externo, según la selección global. Los comandos agregados al menú principal están disponibles inmediatamente para los scripts. Para obtener más información, vea [MenuCommands frente a. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md) y [objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md).  
  
 Para definir nuevos menús y barras de herramientas, debe describirlos en un archivo de tabla de comandos de Visual Studio (.vsct). La plantilla de paquete de Visual Studio se ocupa de crear este archivo, junto con los elementos necesarios para admitir los comandos, barras de herramientas y editores seleccionados en la plantilla. Como alternativa, puede escribir su propio archivo .vsct, mediante el esquema xml se describe aquí: [referencia de esquemas XML de VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
 Para obtener más información sobre cómo trabajar con archivos de vsct, consulte [tabla de comandos de Visual Studio (. Archivos Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Los temas de esta sección explican cómo funcionan los comandos, menús y barras de herramientas en los paquetes VSPackage.  
  
## <a name="in-this-section"></a>En esta sección  
 [Adición de elementos de la interfaz de usuario por VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Una descripción detallada de la especificación de formato de tabla de comandos.  
  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Describe un compilador para las tablas de comando y la sintaxis basada en XML.  
  
 [Ubicación predeterminada de comando, grupo y barra de herramientas](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 Describe las barras de herramientas, grupos, los menús y comandos predefinidos.  
  
 [Grupos, menús y comandos definidos por el IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 Especifica los menús predefinidos, los comandos y los grupos de comandos disponibles para su uso por el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Diseño de comandos](../../extensibility/internals/command-design.md)  
 Explica cómo diseñar los comandos.  
  
 [Optimización de comandos de menú y barra de herramientas](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Proporciona instrucciones para los comandos.  
  
 [Puesta a disposición de comandos](../../extensibility/internals/making-commands-available.md)  
 Explica cómo hacer que los comandos disponibles para Visual Studio.  
  
 [Comandos y menús que utilizan ensamblados de interoperabilidad](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Explica cómo implementar comandos que utilizan los ensamblados de interoperabilidad.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Enrutamiento de comandos en VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Explica el enrutamiento de comandos en los paquetes VSPackage.