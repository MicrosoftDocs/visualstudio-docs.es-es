---
title: "Informaci&#243;n general de la barra de herramientas, el men&#250; y los comandos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "conceptos básicos del menú [SDK de Visual Studio]"
  - "conceptos básicos de la barra de herramientas [SDK de Visual Studio]"
ms.assetid: cbdaceaa-7dd3-4a56-aea6-b759e48d83d6
caps.latest.revision: 19
caps.handback.revision: 19
manager: "douge"
---
# Informaci&#243;n general de la barra de herramientas, el men&#250; y los comandos
Los menús y las barras de herramientas ofrecen a los usuarios una manera gráfica y cómoda de acceder a comandos del VSPackage. Los comandos son funciones que realizan tareas, como la impresión de un documento, la actualización de una vista o la creación de un archivo nuevo. Los menús y las barras de herramientas son maneras gráficas y cómodas de presentar los comandos a los usuarios. Normalmente, los comandos relacionados se agrupan en clústeres en el mismo menú o en la misma barra de herramientas.  
  
-   Los menús suelen mostrarse como cadenas de una palabra agrupadas en clúster en una fila de la parte superior del entorno de desarrollo integrado \(IDE\) o una ventana de herramientas. Los menús también se pueden mostrar como resultado de un evento de botón derecho y se conocen como menús contextuales en ese contexto. Al hacer clic en ellos, los menús se expanden para mostrar uno o varios comandos. Cuando se hace clic en los comandos, pueden llevar a cabo tareas o iniciar submenús que contengan comandos adicionales. Algunos nombres de menú conocidos son Archivo, Edición, Vista y Ventana. Para obtener más información, consulta [Comandos y menús de extensión](../extensibility/extending-menus-and-commands.md).  
  
-   Las barras de herramientas normalmente son filas de botones y otros controles, como cuadros combinados, cuadros de lista, cuadros de texto y controladores de menús. Todos los controles de barra de herramientas están asociados a comandos. Cuando se hace clic en un botón de barra de herramientas, se activa su comando asociado. Los botones de barra de herramientas suelen tener iconos que sugieren los comandos subyacentes, como una impresora para un comando Imprimir. En un control de lista desplegable, cada elemento de la lista está asociado a un comando distinto. Un controlador de menú es un híbrido en el que un lado del control es un botón de barra de herramientas y el otro lado es una flecha hacia abajo que muestra comandos adicionales cuando se hace clic en ella. Para obtener más información, vea [Cómo: Crear barras de herramientas para las ventanas de herramientas](../misc/how-to-create-toolbars-for-tool-windows.md) y [Agregar iconos a los comandos de menú](../extensibility/adding-icons-to-menu-commands.md).  
  
-   Cuando se crea un comando, también debe crear un controlador de eventos para él. El controlador de eventos determina si el comando es visible o está activado, permite modificar su texto y garantiza que el comando responde correctamente \("enruta"\) cuando se activa. En la mayoría de los casos, el IDE controla los comandos mediante la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>. Los comandos de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] enrutan de forma jerárquica, empezando por el contexto de comandos más interno, según la selección local, y continuando hasta el contexto más externo, según la selección global. Los comandos agregados al menú principal están disponibles inmediatamente para los scripts. Para obtener más información, vea [MenuCommands frente a OleMenuCommands](../misc/menucommands-vs-olemenucommands.md) y [Objetos de contexto de selección](../extensibility/internals/selection-context-objects.md).  
  
 Para definir nuevos menús y barras de herramientas, debe describirlos en un archivo de tabla de comandos de Visual Studio \(.vsct\). La plantilla de paquete de Visual Studio se ocupa de crear este archivo, junto con los elementos necesarios para admitir los comandos, barras de herramientas y editores seleccionados en la plantilla. Como alternativa, puede escribir su propio archivo .vsct, mediante el esquema xml se describe aquí: [Referencia del esquema XML de VSCT](../extensibility/vsct-xml-schema-reference.md).  
  
 Para más información sobre cómo trabajar con los archivos .vsct, vea [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) o pruebe alguno de los elementos que se muestran en [Tutoriales para elementos de la interfaz de usuario](../misc/walkthroughs-for-user-interface-elements.md).  
  
 Para obtener una descripción más detallada de los menús y barras de herramientas, consulte [Diseño de comando](../extensibility/internals/command-design.md).  
  
## Vea también  
 [Comandos y menús de extensión](../extensibility/extending-menus-and-commands.md)   
 [Barras de herramientas, menús y comandos](../extensibility/internals/commands-menus-and-toolbars.md)   
 [VSPackages](../extensibility/internals/vspackages.md)