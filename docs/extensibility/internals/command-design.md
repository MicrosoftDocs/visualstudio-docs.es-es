---
title: Diseño de comandos | Microsoft Docs
description: Obtenga información sobre cómo diseñar un comando para un VSPackage en Visual Studio. Como, por ejemplo, cómo especificar dónde aparece, Cuándo está disponible y cómo debe controlarse.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0acef6dd38238ef58f1dd66f7d8de35318e4ffc6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078934"
---
# <a name="command-design"></a>Diseño de comandos
Cuando se agrega un comando a un VSPackage, debe especificar dónde va a aparecer, Cuándo está disponible y cómo debe controlarse.

## <a name="define-commands"></a>Definir comandos
 Para definir nuevos comandos, incluya un archivo de tabla de comandos de Visual Studio (*. Vsct*) en el proyecto de VSPackage. Si ha creado un VSPackage mediante la plantilla de paquete de Visual Studio, el proyecto incluye uno de estos archivos. Para obtener más información, vea [archivos de tabla de comandos de Visual Studio (. Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

 Visual Studio combina todos los archivos *. Vsct* que encuentra para que pueda mostrar los comandos. Dado que estos archivos son distintos del archivo binario de VSPackage, Visual Studio no tiene que cargar el paquete para encontrar los comandos. Para obtener más información, vea [Cómo agrega VSPackages los elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

 Visual Studio usa el <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> atributo de registro para definir los comandos y los recursos del menú. Para obtener más información, vea [implementación de comandos](../../extensibility/internals/command-implementation.md).

 Los comandos se pueden cambiar en tiempo de ejecución de varias maneras diferentes. Pueden mostrarse u ocultarse, habilitarse o deshabilitarse. Pueden mostrar texto o iconos distintos o contener valores distintos. Se puede realizar una gran cantidad de personalización antes de que Visual Studio cargue el VSPackage. Para obtener más información, vea [Cómo agrega VSPackages los elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

## <a name="command-handlers"></a>Controladores de comandos
 Al crear un comando, debe proporcionar un controlador de eventos para ejecutar el comando. Si el usuario selecciona el comando, se debe enrutar correctamente. El enrutamiento de un comando significa enviarlo al VSPackage correcto para habilitarlo o deshabilitarlo, ocultarlo o mostrarlo, y ejecutarlo si el usuario decide hacerlo. Para obtener más información, vea [algoritmo de enrutamiento de comandos](../../extensibility/internals/command-routing-algorithm.md).

## <a name="visual-studio-command-environment"></a>Entorno de comandos de Visual Studio
 Visual Studio puede hospedar cualquier número de VSPackages y cada uno puede contribuir con su propio conjunto de comandos. El entorno muestra solo los comandos que son adecuados para la tarea actual. Para obtener más información, vea objetos de [contexto de selección](../../extensibility/internals/selection-context-objects.md)y [disponibilidad de comandos](../../extensibility/internals/command-availability.md) .

 Un VSPackage que define nuevos comandos, menús, barras de herramientas o menús contextuales proporciona la información de comandos a Visual Studio en el momento de la instalación a través de las entradas del registro que hacen referencia a los recursos de los ensamblados nativos o administrados. Cada recurso hace referencia a un archivo de recursos de datos binarios (*. CTO*), que se genera al compilar un archivo de tabla de comandos de Visual Studio (*. Vsct*). Esto permite a Visual Studio proporcionar conjuntos de comandos, menús y barras de herramientas combinados sin tener que cargar cada VSPackage instalado.

### <a name="command-organization"></a>Organización de comandos
 El entorno coloca los comandos por grupo, prioridad y menú.

- Los grupos son colecciones lógicas de comandos relacionados, por ejemplo, el grupo de comandos **cortar**, **copiar** y **pegar** . Los grupos son los comandos que aparecen en los menús.

- Prioridad determina el orden en que aparecen los comandos individuales en un grupo en el menú.

- Los menús actúan como contenedores para los grupos.

  El entorno predefine algunos comandos, grupos y menús. Para obtener más información, vea selección de ubicación de la barra de herramientas, el [grupo y el comando predeterminado](../../extensibility/internals/default-command-group-and-toolbar-placement.md).

  Un comando se puede asignar a un grupo primario. El grupo primario controla la posición del comando en la estructura de menú principal y en el cuadro de diálogo **personalizar** . Un comando puede aparecer en varios grupos; por ejemplo, un comando puede estar en el menú principal, en un menú contextual y en una barra de herramientas. Para obtener más información, vea [Cómo agrega VSPackages los elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).

### <a name="command-routing"></a>Enrutamiento de comandos
 El proceso de invocar y enrutar comandos para VSPackages difiere del proceso de llamada a métodos en instancias de objeto.

 El entorno enruta los comandos secuencialmente desde el contexto de comandos más interno (local), que se basa en la selección actual, hasta el contexto más externo (global). El primer contexto que puede ejecutar el comando es el que lo controla. Para obtener más información, vea [algoritmo de enrutamiento de comandos](../../extensibility/internals/command-routing-algorithm.md).

 En la mayoría de los casos, el entorno controla los comandos mediante la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. Dado que el esquema de enrutamiento de comandos permite que muchos objetos diferentes controlen los comandos, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> se puede implementar mediante cualquier número de objetos; entre ellos, los controles ActiveX de Microsoft, las implementaciones de vistas de ventanas, los objetos de documento, las jerarquías de proyecto y los propios objetos VSPackage (para los comandos globales). En algunos casos especializados, por ejemplo, los comandos de enrutamiento en una jerarquía, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> se debe implementar la interfaz.

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Implementación de comandos](../../extensibility/internals/command-implementation.md)|Describe cómo implementar comandos en un VSPackage.|
|[Disponibilidad de comandos](../../extensibility/internals/command-availability.md)|Describe cómo el contexto de Visual Studio determina qué comandos están disponibles.|
|[Algoritmo de enrutamiento de comandos](../../extensibility/internals/command-routing-algorithm.md)|Describe cómo la arquitectura de enrutamiento de comandos de Visual Studio permite que los comandos se controlen mediante VSPackages diferentes.|
|[Instrucciones de selección de ubicación de comandos](../../extensibility/internals/command-placement-guidelines.md)|Sugiere cómo colocar comandos en el entorno de Visual Studio.|
|[Cómo agrega VSPackages los elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Describe cómo los paquetes VSPackage pueden aprovechar mejor la arquitectura de comandos de Visual Studio.|
|[Ubicación predeterminada del comando, el grupo y la barra de herramientas](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Describe cómo los paquetes VSPackage pueden usar mejor los comandos que se incluyen en Visual Studio.|
|[Administración de VSPackages](../../extensibility/managing-vspackages.md)|Describe cómo Visual Studio carga VSPackages.|
|[Archivos de tabla de comandos de Visual Studio (. Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Proporciona información sobre los archivos *. Vsct* basados en XML, que se utilizan para describir el diseño y la apariencia de los comandos en VSPackages.|
