---
title: Diseño de comandos | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6fe22e67d97af7dc7b8c900dd10c301d02d8c5a7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582417"
---
# <a name="command-design"></a>Diseño de comandos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [comando diseño](https://docs.microsoft.com/visualstudio/extensibility/internals/command-design).  
  
Al agregar un comando a un VSPackage, debe especificar dónde va a aparecer, cuando está disponible y cómo resulta controlarse.  
  
## <a name="defining-commands"></a>Definición de comandos  
 Para definir nuevos comandos, incluir un archivo de Visual Studio Command Table (.vsct) en el proyecto de VSPackage. Si ha creado un paquete VSPackage mediante el uso de la plantilla de paquete de Visual Studio, el proyecto incluye alguno de estos archivos. Para obtener más información, consulte [Visual Studio Command Table (. Archivos Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio combina todos los archivos .vsct encuentra para que pueda mostrar los comandos. Ya que estos archivos son distintos del VSPackage binario, no tiene Visual Studio cargar el paquete para encontrar los comandos. Para obtener más información, consulte [cómo VSPackages agregar elementos de la interfaz](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio usa el <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> atributo de registro para definir los recursos de menús y comandos. Para obtener más información, consulte [implementación](../../extensibility/internals/command-implementation.md).  
  
 Los comandos pueden cambiarse en tiempo de ejecución de varias maneras diferentes. Puede mostrar u ocultados, habilitados o deshabilitados. Puede mostrar texto diferente o iconos o contienen valores distintos. Puede realizar una gran cantidad de personalización antes de Visual Studio carga el VSPackage. Para obtener más información, consulte [cómo VSPackages agregar elementos de la interfaz](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Controladores de comandos  
 Cuando se crea un comando, debe proporcionar un controlador de eventos para ejecutar el comando. Si el usuario selecciona el comando, se debe enrutar adecuadamente. Enrutamiento de un comando significa enviarlo a VSPackage correcto para habilitar o deshabilitarlo, ocultar o mostrarla y ejecutarlo de nuevo si el usuario decide hacerlo. Para obtener más información, consulte [algoritmo de enrutamiento](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="the-visual-studio-command-environment"></a>El entorno de comandos de Visual Studio  
 Visual Studio puede alojar cualquier número de paquetes VSPackage, y cada uno puede aportar su propio conjunto de comandos. El entorno muestra sólo los comandos que son adecuados para la tarea actual. Para obtener más información, consulte [disponibilidad](../../extensibility/internals/command-availability.md) y [objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md).  
  
 Un VSPackage que define los nuevos comandos, menús, barras de herramientas o los menús contextuales proporciona su información de comandos de Visual Studio en tiempo de instalación a través de entradas del registro que hacen referencia a recursos en ensamblados nativos o administrados. Cada recurso, a continuación, hace referencia a un archivo de recursos (.cto) de datos binarios, que se produce cuando se compila un archivo de Visual Studio Command Table (.vsct). Esto permite que Visual Studio proporcionar conjuntos de comandos combinados, menús y barras de herramientas sin tener que cargar cada VSPackage instalado.  
  
### <a name="command-organization"></a>Organización de comando  
 El entorno coloca comandos por grupo, prioridad y menú.  
  
-   Los grupos son recopilaciones lógicas de comandos relacionados, por ejemplo, el **cortar**, **copia**, y **pegar** del grupo de comandos. Los grupos son los comandos que aparecen en los menús.  
  
-   Prioridad determina el orden en que aparecen los comandos individuales en un grupo en el menú.  
  
-   Los menús actúan como contenedores para los grupos.  
  
 El entorno predefine algunos comandos, grupos y los menús. Para obtener más información, consulte [comando predeterminado, el grupo y ubicación de la barra de herramientas](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
 Un comando puede asignarse a un grupo primario. El grupo primario controla la posición del comando en la estructura de menú principal y en el **personalizar** cuadro de diálogo. Un comando puede aparecer en varios grupos; Por ejemplo, puede ser un comando en el menú principal, en un menú contextual y en una barra de herramientas. Para obtener más información, consulte [cómo VSPackages agregar elementos de la interfaz](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>enrutamiento de comandos  
 El proceso de invocación y enrutamiento de comandos para VSPackages difiere el proceso de llamar a métodos en instancias de objeto.  
  
 El entorno enruta los comandos secuencialmente desde el contexto de comandos (local) más interno, que se basa en la selección actual, en el contexto más externo (global). El primer contexto que es capaz de ejecutar el comando es lo que los controle. Para obtener más información, consulte [algoritmo de enrutamiento](../../extensibility/internals/command-routing-algorithm.md).  
  
 En la mayoría de los casos, el entorno controla los comandos mediante el uso de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. Dado que el esquema de enrutamiento de comandos permite muchos objetos diferentes controlar los comandos, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pueden implementarse por cualquier número de objetos; estos incluyen controles Microsoft ActiveX, las implementaciones de la vista de ventana, los objetos de documento, las jerarquías de proyecto y objetos de VSPackage a sí mismos (para los comandos globales). En algunos casos especializados, por ejemplo, comandos de enrutamiento en una jerarquía, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> debe implementar la interfaz.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Implementación](../../extensibility/internals/command-implementation.md)|Describe cómo implementar comandos en un VSPackage.|  
|[Disponibilidad](../../extensibility/internals/command-availability.md)|Describe cómo el contexto de Visual Studio determina qué comandos están disponibles.|  
|[Algoritmo de enrutamiento](../../extensibility/internals/command-routing-algorithm.md)|Describe cómo la arquitectura de enrutamiento de comandos de Visual Studio permite comandos controlando VSPackages diferentes.|  
|[Instrucciones sobre la selección de ubicación](../../extensibility/internals/command-placement-guidelines.md)|Sugiere cómo posicionar los comandos en el entorno de Visual Studio.|  
|[Adición de elementos de la interfaz de usuario por VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Describe cómo los paquetes VSPackage pueden usar mejor la arquitectura de comandos de Visual Studio.|  
|[Ubicación predeterminada de comando, grupo y barra de herramientas](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Describe cómo los VSPackages mejor puede utilizar los comandos que se incluyen en Visual Studio.|  
|[Administración de VSPackages](../../extensibility/managing-vspackages.md)|Describe cómo Visual Studio carga VSPackages.|  
|[Archivos de tabla de comandos de Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Proporciona información acerca de los archivos .vsct basado en XML, que se utilizan para describir el diseño y la apariencia de los comandos en VSPackages.|

