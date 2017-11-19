---
title: "Diseño de comandos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: "34"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf6d0d7a9aa556aab454f90e4dcfc5dc4f236c03
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="command-design"></a>Diseño de comando
Cuando se agrega un comando a un paquete VSPackage, debe especificar donde va a aparecer, cuando está disponible y cómo resulta controlarse.  
  
## <a name="defining-commands"></a>Definir comandos  
 Para definir nuevos comandos, incluir un archivo de tabla de comandos de Visual Studio (.vsct) en el proyecto de VSPackage. Si ha creado un paquete VSPackage mediante el uso de la plantilla de paquete de Visual Studio, el proyecto incluye alguno de estos archivos. Para obtener más información, vea [tabla de comandos de Visual Studio (. Archivos Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio combina todos los archivos de vsct encuentra para que pueden mostrar los comandos. Ya que estos archivos son distintos desde el VSPackage binario, no tiene Visual Studio cargar el paquete para buscar los comandos. Para obtener más información, consulte [cómo VSPackages agregar elementos de la interfaz](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio usa el <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> atributo de registro para definir recursos de menús y comandos. Para obtener más información, consulte [implementación](../../extensibility/internals/command-implementation.md).  
  
 Comandos pueden cambiarse en tiempo de ejecución en una de varias maneras diferentes. Pueden mostrar u ocultados, habilitados o deshabilitados. Puede mostrar texto diferente o iconos o contienen valores distintos. Se puede realizar una gran cantidad de personalización antes de que Visual Studio cargue el VSPackage. Para obtener más información, consulte [cómo VSPackages agregar elementos de la interfaz](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Controladores de comandos  
 Cuando se crea un comando, debe proporcionar un controlador de eventos para ejecutar el comando. Si el usuario selecciona el comando, debe enrutarse correctamente. Enrutamiento de un comando significa enviarlo al VSPackage correcto para habilitar o deshabilitar, ocultar o mostrarla y ejecutarlo si el usuario decide hacerlo. Para obtener más información, consulte [algoritmo de enrutamiento](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="the-visual-studio-command-environment"></a>El entorno de comandos de Visual Studio  
 Visual Studio puede alojar cualquier número de VSPackages, y cada uno puede aportar su propio conjunto de comandos. El entorno muestra únicamente los comandos que son adecuados para la tarea actual. Para obtener más información, consulte [disponibilidad](../../extensibility/internals/command-availability.md) y [selección de objetos en el contexto](../../extensibility/internals/selection-context-objects.md).  
  
 Un VSPackage que define los nuevos comandos, menús, barras de herramientas o los menús contextuales proporciona su información de comando a Visual Studio en tiempo de instalación a través de entradas del registro que hacen referencia a recursos de ensamblados nativos o administrados. Cada recurso, a continuación, hace referencia a un archivo de recursos (.cto) de datos binarios, que se produce cuando se compila un archivo de tabla de comandos de Visual Studio (.vsct). Esto permite que Visual Studio proporcionar conjuntos de comandos combinados, los menús y barras de herramientas sin tener que cargar cada VSPackage instalado.  
  
### <a name="command-organization"></a>Organización de comando  
 El entorno coloca comandos por grupo, la prioridad y el menú.  
  
-   Los grupos son recopilaciones lógicas de comandos relacionados, por ejemplo, el **cortar**, **copia**, y **pegar** del grupo de comandos. Los grupos son los comandos que aparecen en los menús.  
  
-   La prioridad determina el orden en que los comandos individuales en un grupo aparecen en el menú.  
  
-   Menús actúan como contenedores para los grupos.  
  
 El entorno predefine algunos comandos, los grupos y los menús. Para obtener más información, consulte [comando predeterminado, grupo y la ubicación de la barra de herramientas](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
 Un comando puede asignarse a un grupo primario. El grupo primario controla la posición del comando en la estructura de menú principal y en el **personalizar** cuadro de diálogo. Un comando puede aparecer en varios grupos; Por ejemplo, puede ser un comando en el menú principal, en un menú contextual y en una barra de herramientas. Para obtener más información, consulte [cómo VSPackages agregar elementos de la interfaz](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>enrutamiento de comandos  
 El proceso de invocación y el enrutamiento de comandos para VSPackages es diferente del proceso de llamadas a métodos en instancias de objeto.  
  
 El entorno enruta los comandos secuencialmente desde el contexto de comandos (local) más interno, que se basa en la selección actual, en el contexto más externo (global). El primer contexto que puede ejecutar el comando es el que los controle. Para obtener más información, consulte [algoritmo de enrutamiento](../../extensibility/internals/command-routing-algorithm.md).  
  
 En la mayoría de los casos, el entorno controla los comandos mediante el uso de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz. Dado que el esquema de enrutamiento de comandos permite muchos objetos diferentes controlar los comandos, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> puede ser implementada por cualquier número de objetos; estos incluyen controles Microsoft ActiveX, las implementaciones de la vista de ventana, objetos de documento, las jerarquías de proyecto, y objetos de VSPackage a sí mismos (para los comandos globales). En algunos casos especializados, por ejemplo, enrutamiento de comandos en una jerarquía, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> debe implementar la interfaz.  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Implementación](../../extensibility/internals/command-implementation.md)|Describe cómo implementar comandos en un paquete VSPackage.|  
|[Disponibilidad](../../extensibility/internals/command-availability.md)|Describe cómo el contexto de Visual Studio determina qué comandos están disponibles.|  
|[Algoritmo de enrutamiento](../../extensibility/internals/command-routing-algorithm.md)|Describe cómo la arquitectura de enrutamiento de comandos de Visual Studio permite comandos controlando VSPackages diferentes.|  
|[Instrucciones de selección de ubicación](../../extensibility/internals/command-placement-guidelines.md)|Sugiere cómo colocar los comandos en el entorno de Visual Studio.|  
|[Adición de elementos de la interfaz de usuario por VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Describe cómo VSPackages puede utilizar mejor la arquitectura de comandos de Visual Studio.|  
|[Ubicación predeterminada de comando, grupo y barra de herramientas](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Describe cómo VSPackages mejor puede utilizar los comandos que se incluyen en Visual Studio.|  
|[Administración de VSPackages](../../extensibility/managing-vspackages.md)|Describe la forma en que Visual Studio carga VSPackages.|  
|[Archivos de tabla de comandos de Visual Studio (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Proporciona información acerca de los archivos de vsct basado en XML, que se utilizan para describir el diseño y la apariencia de comandos de VSPackages.|