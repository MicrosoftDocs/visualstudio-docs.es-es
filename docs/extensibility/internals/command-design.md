---
title: Diseño de comandos (Command Design) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aa58813623dc8150cafb4fbfee6496d09f889ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709655"
---
# <a name="command-design"></a>Diseño de comandos
Al agregar un comando a un VSPackage, debe especificar dónde va a aparecer, cuándo está disponible y cómo se debe controlar.

## <a name="define-commands"></a>Definir comandos
 Para definir nuevos comandos, incluya un archivo de tabla de comandos de Visual Studio (*.vsct*) en el proyecto de VSPackage. Si ha creado un VSPackage mediante la plantilla de paquete de Visual Studio, el proyecto incluye uno de estos archivos. Para obtener más información, vea Archivos de tabla de [comandos de Visual Studio (.vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Visual Studio combina todos los archivos *.vsct* que encuentra para que pueda mostrar los comandos. Dado que estos archivos son distintos del binario de VSPackage, Visual Studio no tiene que cargar el paquete para buscar los comandos. Para obtener más información, vea [Cómo VSPackages agregan elementos](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)de interfaz de usuario .

 Visual Studio <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> usa el atributo registration para definir comandos y recursos de menú. Para obtener más información, consulte [Implementación de comandos](../../extensibility/internals/command-implementation.md).

 Los comandos se pueden cambiar en tiempo de ejecución de varias maneras diferentes. Se pueden mostrar u ocultar, habilitar o deshabilitar. Pueden mostrar texto o iconos diferentes, o contener valores diferentes. Se puede realizar una gran cantidad de personalización antes de que Visual Studio cargue el VSPackage. Para obtener más información, vea [Cómo VSPackages agregan elementos](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)de interfaz de usuario .

## <a name="command-handlers"></a>Controladores de comandos
 Al crear un comando, debe proporcionar un controlador de eventos para ejecutar el comando. Si el usuario selecciona el comando, debe enrutarse adecuadamente. Enrutar un comando significa enviarlo al VSPackage correcto para habilitarlo o deshabilitarlo, ocultarlo o mostrarlo y ejecutarlo si el usuario decide hacerlo. Para obtener más información, consulte [Algoritmo de enrutamiento de](../../extensibility/internals/command-routing-algorithm.md)comandos .

## <a name="visual-studio-command-environment"></a>Entorno de comandos de Visual Studio
 Visual Studio puede hospedar cualquier número de VSPackages y cada uno puede contribuir con su propio conjunto de comandos. El entorno muestra solo los comandos que son adecuados para la tarea actual. Para obtener más información, consulte [Objetos](../../extensibility/internals/command-availability.md) de contexto Disponibilidad de [comandos](../../extensibility/internals/selection-context-objects.md)y Selección .

 Un VSPackage que define nuevos comandos, menús, barras de herramientas o menús contextuales proporciona su información de comandos a Visual Studio en tiempo de instalación a través de entradas del Registro que hacen referencia a recursos en ensamblados nativos o administrados. A continuación, cada recurso hace referencia a un archivo de recursos de datos binarios (*.cto*), que se genera al compilar un archivo de tabla de comandos de Visual Studio (*.vsct*). Esto permite a Visual Studio proporcionar conjuntos de comandos combinados, menús y barras de herramientas sin tener que cargar todos los VSPackage instalados.

### <a name="command-organization"></a>Organización de comandos
 El entorno posiciona los comandos por grupo, prioridad y menú.

- Los grupos son colecciones lógicas de comandos relacionados, por ejemplo, el grupo de comandos **Cortar**, **Copiar**y **Pegar.** Los grupos son los comandos que aparecen en los menús.

- La prioridad determina el orden en el que aparecen los comandos individuales de un grupo en el menú.

- Los menús actúan como contenedores para grupos.

  El entorno predefine algunos comandos, grupos y menús. Para obtener más información, consulte Colocación predeterminada de [comandos, grupos y barras](../../extensibility/internals/default-command-group-and-toolbar-placement.md)de herramientas .

  Se puede asignar un comando a un grupo principal. El grupo principal controla la posición del comando en la estructura del menú principal y en el cuadro de diálogo **Personalizar.** Un comando puede aparecer en varios grupos; por ejemplo, un comando puede estar en el menú principal, en un menú contextual y en una barra de herramientas. Para obtener más información, vea [Cómo VSPackages agregan elementos](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)de interfaz de usuario .

### <a name="command-routing"></a>Enrutamiento de comandos
 El proceso de invocar y enrutar comandos para VSPackages difiere del proceso de llamar a métodos en instancias de objeto.

 El entorno enruta los comandos secuencialmente desde el contexto de comando más interno (local), que se basa en la selección actual, al contexto más externo (global). El primer contexto que es capaz de ejecutar el comando es el que lo controla. Para obtener más información, consulte [Algoritmo de enrutamiento de](../../extensibility/internals/command-routing-algorithm.md)comandos .

 En la mayoría de los casos, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> el entorno controla los comandos mediante la interfaz. Dado que el esquema de enrutamiento de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> comandos permite que muchos objetos diferentes controlen comandos, se pueden implementar mediante cualquier número de objetos; estos incluyen controles ActiveX de Microsoft, implementaciones de vista de ventana, objetos de documento, jerarquías de proyecto y objetos VSPackage (para comandos globales). En algunos casos especializados, por ejemplo, los <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> comandos de ruteo en una jerarquía, la interfaz se debe implementar.

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Implementación del comando](../../extensibility/internals/command-implementation.md)|Describe cómo implementar comandos en un VSPackage.|
|[Disponibilidad de comandos](../../extensibility/internals/command-availability.md)|Describe cómo el contexto de Visual Studio determina qué comandos están disponibles.|
|[Algoritmo de enrutamiento de comandos](../../extensibility/internals/command-routing-algorithm.md)|Describe cómo la arquitectura de enrutamiento de comandos de Visual Studio permite que los comandos se controlen mediante diferentes VSPackages.|
|[Directrices de colocación de comandos](../../extensibility/internals/command-placement-guidelines.md)|Sugiere cómo colocar comandos en el entorno de Visual Studio.|
|[Cómo VSPackages agregan elementos de interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Describe cómo VSPackages puede utilizar mejor la arquitectura de comandos de Visual Studio.|
|[Colocación predeterminada de comandos, grupos y barras de herramientas](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Describe cómo VSPackages puede usar mejor los comandos que se incluyen en Visual Studio.|
|[Administración de VSPackages](../../extensibility/managing-vspackages.md)|Describe cómo Visual Studio carga VSPackages.|
|[Archivos de tabla de comandos de Visual Studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Proporciona información acerca de los archivos *.vsct* basados en XML, que se usan para describir el diseño y la apariencia de los comandos en VSPackages.|
