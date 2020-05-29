---
title: Comandos, menús y barras de herramientas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65f5a43bee5a89492bc1ecc7bf7c1126b5a80456
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173595"
---
# <a name="commands-menus-and-toolbars"></a>Comandos, menús y barras de herramientas
Los menús y las barras de herramientas son la forma en que los usuarios acceden a los comandos del VSPackage. Los comandos son funciones que realizan tareas, como la impresión de un documento, la actualización de una vista o la creación de un archivo nuevo. Los menús y las barras de herramientas son maneras gráficas y cómodas de presentar los comandos a los usuarios. Normalmente, los comandos relacionados se agrupan en clústeres en el mismo menú o en la misma barra de herramientas.

- Los menús suelen mostrarse como cadenas de una palabra agrupadas en clúster en una fila de la parte superior del entorno de desarrollo integrado (IDE) o una ventana de herramientas. Los menús también se pueden mostrar como resultado de un evento de botón derecho y se conocen como menús contextuales en ese contexto. Al hacer clic en ellos, los menús se expanden para mostrar uno o varios comandos. Cuando se hace clic en los comandos, pueden llevar a cabo tareas o iniciar submenús que contengan comandos adicionales. Algunos nombres de menú conocidos son **archivo**, **edición**, **vista**y **ventana**. Para obtener más información, vea [extender menús y comandos](../../extensibility/extending-menus-and-commands.md).

- Las barras de herramientas normalmente son filas de botones y otros controles, como cuadros combinados, cuadros de lista, cuadros de texto y controladores de menús. Todos los controles de barra de herramientas están asociados a comandos. Cuando se hace clic en un botón de barra de herramientas, se activa su comando asociado. Los botones de barra de herramientas suelen tener iconos que sugieren los comandos subyacentes, como una impresora para un comando Imprimir. En un control de lista desplegable, cada elemento de la lista está asociado a un comando distinto. Un controlador de menú es un híbrido en el que un lado del control es un botón de barra de herramientas y el otro lado es una flecha hacia abajo que muestra comandos adicionales cuando se hace clic en ella. Para obtener más información, vea [Agregar un controlador de menú a una barra de herramientas](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).

- Cuando se crea un comando, también debe crear un controlador de eventos para él. El controlador de eventos determina si el comando es visible o está activado, permite modificar su texto y garantiza que el comando responde correctamente ("enruta") cuando se activa. En la mayoría de los casos, el IDE controla los comandos mediante la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>. Los comandos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] enrutan de forma jerárquica, empezando por el contexto de comandos más interno, según la selección local, y continuando hasta el contexto más externo, según la selección global. Los comandos agregados al menú principal están disponibles inmediatamente para los scripts. Para obtener más información, vea [MenuCommands frente a OleMenuCommands](/visualstudio/misc/menucommands-vs-olemenucommands?view=vs-2015) y [objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md).

  Para definir nuevos menús y barras de herramientas, debe describirlos en un archivo de tabla de comandos de Visual Studio (*. Vsct*). La plantilla de paquete de Visual Studio crea este archivo, junto con los elementos necesarios para admitir los comandos, barras de herramientas y editores seleccionados en la plantilla. Como alternativa, puede escribir su propio archivo *. Vsct* con el esquema XML que se describe aquí: [Referencia del esquema XML de Vsct](../../extensibility/vsct-xml-schema-reference.md).

  Para obtener más información sobre cómo trabajar con archivos *. Vsct* , consulte [archivos de tabla de comandos de Visual Studio (. Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

  En los temas de esta sección se explica cómo funcionan los comandos, menús y barras de herramientas en VSPackages.

## <a name="in-this-section"></a>En esta sección
- [Cómo agrega VSPackages los elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Una descripción detallada de la especificación de formato de tabla de comandos.

- [Archivos de tabla de comandos de Visual Studio (. Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Describe una sintaxis y un compilador basados en XML para las tablas de comandos.

- [Ubicación predeterminada del comando, el grupo y la barra de herramientas](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

 Describe los comandos, grupos, menús y barras de herramientas predefinidos.

- [Comandos, menús y grupos definidos por el IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Especifica los menús, comandos y grupos de comandos predefinidos disponibles para que los use el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Diseño de comandos](../../extensibility/internals/command-design.md)

 Explica cómo diseñar comandos.

- [Optimizar comandos de menús y barras de herramientas](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)

 Proporciona instrucciones para los comandos.

- [Crear comandos disponibles](../../extensibility/internals/making-commands-available.md)

 Explica cómo poner comandos a disposición de Visual Studio.

- [Comandos y menús que utilizan ensamblados de interoperabilidad](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Explica cómo implementar comandos que utilizan ensamblados de interoperabilidad.

## <a name="related-sections"></a>Secciones relacionadas
- [Enrutamiento de comandos en VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 Explica el enrutamiento de comandos en VSPackages.
