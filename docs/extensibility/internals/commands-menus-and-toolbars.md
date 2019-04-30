---
title: Los comandos, menús y barras de herramientas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0634105b9b071ac4155adb3248abd2b4be19b29
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62862000"
---
# <a name="commands-menus-and-toolbars"></a>Los comandos, menús y barras de herramientas
Los menús y barras de herramientas son la forma que los usuarios tener acceso a comandos del VSPackage. Los comandos son funciones que realizan tareas, como la impresión de un documento, la actualización de una vista o la creación de un archivo nuevo. Los menús y las barras de herramientas son maneras gráficas y cómodas de presentar los comandos a los usuarios. Normalmente, los comandos relacionados se agrupan en clústeres en el mismo menú o en la misma barra de herramientas.

- Los menús suelen mostrarse como cadenas de una palabra agrupadas en clúster en una fila de la parte superior del entorno de desarrollo integrado (IDE) o una ventana de herramientas. Los menús también se pueden mostrar como resultado de un evento de botón derecho y se conocen como menús contextuales en ese contexto. Al hacer clic en ellos, los menús se expanden para mostrar uno o varios comandos. Cuando se hace clic en los comandos, pueden llevar a cabo tareas o iniciar submenús que contengan comandos adicionales. Algunos nombres de menú conocidos son **archivo**, **editar**, **vista**, y **ventana**. Para obtener más información, consulte [amplían los menús y comandos](../../extensibility/extending-menus-and-commands.md).

- Las barras de herramientas normalmente son filas de botones y otros controles, como cuadros combinados, cuadros de lista, cuadros de texto y controladores de menús. Todos los controles de barra de herramientas están asociados a comandos. Cuando se hace clic en un botón de barra de herramientas, se activa su comando asociado. Los botones de barra de herramientas suelen tener iconos que sugieren los comandos subyacentes, como una impresora para un comando Imprimir. En un control de lista desplegable, cada elemento de la lista está asociado a un comando distinto. Un controlador de menú es un híbrido en el que un lado del control es un botón de barra de herramientas y el otro lado es una flecha hacia abajo que muestra comandos adicionales cuando se hace clic en ella. Para obtener más información, consulte [agregar un controlador de menú a una barra de herramientas](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).

- Cuando se crea un comando, también debe crear un controlador de eventos para él. El controlador de eventos determina si el comando es visible o está activado, permite modificar su texto y garantiza que el comando responde correctamente ("enruta") cuando se activa. En la mayoría de los casos, el IDE controla los comandos mediante la interfaz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>. Los comandos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] enrutan de forma jerárquica, empezando por el contexto de comandos más interno, según la selección local, y continuando hasta el contexto más externo, según la selección global. Los comandos agregados al menú principal están disponibles inmediatamente para los scripts. Para obtener más información, consulte [MenuCommands frente a. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md) y [objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md).

  Para definir nuevos menús y barras de herramientas, debe describirlos en una tabla de comandos de Visual Studio (*.vsct*) archivo. La plantilla de paquete de Visual Studio crea este archivo, junto con los elementos necesarios para admitir los comandos, barras de herramientas y editores seleccionados en la plantilla. Como alternativa, puede escribir su propio *.vsct* de archivos, mediante el esquema XML se describe aquí: [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md).

  Para obtener más información sobre cómo trabajar con *.vsct* archivos, consulte [archivos de tabla (.vsct) de comandos de Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

  Los temas de esta sección explican cómo funcionan las barras de herramientas, menús y comandos en VSPackages.

## <a name="in-this-section"></a>En esta sección
- [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Una descripción detallada de la especificación de formato de tabla de comandos.

- [Archivos visuales Studio comando table (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Describe una sintaxis basada en XML y el compilador para las tablas de comando.

- [Posición predeterminada de comando, grupo y barra de herramientas](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

 Describe las barras de herramientas, grupos, menús y comandos predefinidos.

- [Grupos, menús y comandos definidos por el IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Especifica los menús predefinidos, comandos y grupos de comandos disponibles para su uso por el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Diseño de comandos](../../extensibility/internals/command-design.md)

 Explica cómo diseñar los comandos.

- [Optimizar los comandos de menú y barra de herramientas](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)

 Proporciona instrucciones para los comandos.

- [Hacer que los comandos disponibles](../../extensibility/internals/making-commands-available.md)

 Explica cómo hacer que los comandos disponibles para Visual Studio.

- [Los comandos y menús que utilizan ensamblados de interoperabilidad](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Explica cómo implementar los comandos que utilizan ensamblados de interoperabilidad.

## <a name="related-sections"></a>Secciones relacionadas
- [Enrutamiento de comandos en VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 Explica el enrutamiento de comandos en VSPackages.