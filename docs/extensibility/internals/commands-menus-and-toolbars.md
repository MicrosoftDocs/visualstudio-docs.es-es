---
title: "Barras de herramientas, men&#250;s y comandos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "menús [Visual Studio SDK], comandos"
  - "comandos [Visual Studio]"
  - "barras de herramientas [Visual Studio], comandos"
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: 60
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 60
---
# Barras de herramientas, men&#250;s y comandos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Menús y barras de herramientas son la forma, los usuarios tener acceso a comandos en su VSPackage. Comandos son funciones que realizar tareas, como la impresión de un documento, al actualizar una vista o crear un nuevo archivo. Menús y barras de herramientas son de manera gráfica cómoda para presentar los comandos a los usuarios. Normalmente, los comandos relacionados se agrupan en el mismo menú o barra de herramientas.  
  
-   Normalmente, los menús se muestran como cadenas de una palabra en clúster en una fila en la parte superior del entorno de desarrollo integrado \(IDE\) o una ventana de herramientas. Los menús también se pueden mostrar como resultado de un evento con el botón secundario y se conocen como menús contextuales en ese contexto. Al hacer clic, los menús se expanden para mostrar uno o más comandos. Comandos, al hacer clic, pueden llevar a cabo tareas o iniciar submenús que contienen comandos adicionales. Algunos nombres de menú conocidos son el archivo, edición, vista y ventana. Para obtener más información, consulta [Comandos y menús de extensión](../../extensibility/extending-menus-and-commands.md).  
  
-   Barras de herramientas normalmente son las filas de botones y otros controles, como controladores de menús, cuadros de lista, cuadros de texto y cuadros combinados. Todos los controles de barra de herramientas están asociados con los comandos. Al hacer clic en un botón de barra de herramientas, se activa su comando asociado. Botones de barra de herramientas suelen tengan iconos que sugiera los comandos subyacentes, como una impresora para un comando de impresión. En un control de lista desplegable, cada elemento de la lista está asociado con un comando distinto. Un controlador de menú es un híbrido en el que un lado del control es un botón de barra de herramientas y el otro lado es una flecha hacia abajo que se muestra al hacer clic en los comandos adicionales. Para obtener más información, consulta [Agregar un controlador de menú a una barra de herramientas](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
-   Cuando se crea un comando, también debe crear un controlador de eventos para él. El controlador de eventos determina si el comando es visible o activado, le permite modificar su texto y se asegura de que el comando responde correctamente \("rutas"\) cuando se activa. En la mayoría de los casos, el IDE controla los comandos usando el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. Comandos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ruta de forma jerárquica, empezando por el contexto de comandos más interno, según la selección local y continuar con el contexto más externo, según la selección global. Los comandos agregados al menú principal están disponibles inmediatamente para secuencias de comandos. Para obtener más información, consulte [MenuCommands frente a OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md) y [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md).  
  
 Para definir nuevos menús y barras de herramientas, debe describir en un archivo de la tabla de comandos de Visual Studio \(.vsct\). La plantilla de paquete de Visual Studio crea este archivo, junto con los elementos necesarios para admitir los comandos, barras de herramientas y editores seleccionados en la plantilla. Como alternativa, puede escribir su propio archivo vsct, mediante el esquema xml se describe aquí: [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
 Para obtener más información sobre cómo trabajar con los archivos .vsct, vea [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Los temas de esta sección explican cómo funcionan las barras de herramientas, menús y comandos de VSPackages.  
  
## En esta sección  
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Una descripción detallada de la especificación de formato de tabla de comandos.  
  
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Describe una sintaxis basada en XML y el compilador para las tablas de comando.  
  
 [Comando predeterminado, el grupo y la ubicación de la barra de herramientas](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 Describe las barras de herramientas, grupos, menús y comandos predefinidos.  
  
 [Grupos, menús y comandos definidos por el IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 Especifica los menús predefinidos, los comandos y los grupos de comandos disponibles para su uso por el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Diseño de comando](../../extensibility/internals/command-design.md)  
 Explica cómo diseñar los comandos.  
  
 [Optimización de menús y comandos de barra de herramientas](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Proporciona instrucciones para los comandos.  
  
 [Disponibilidad de los comandos](../../extensibility/internals/making-commands-available.md)  
 Explica cómo hacer que los comandos disponibles en Visual Studio.  
  
 [Comandos y menús que utilizan ensamblados de interoperabilidad](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Explica cómo implementar los comandos que utilizan ensamblados de interoperabilidad.  
  
## Secciones relacionadas  
 [Enrutamiento de comandos en VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Explica el enrutamiento de comandos en VSPackages.