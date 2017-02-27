---
title: "Dise&#241;o de comando | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comandos"
  - "comandos, implementación"
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 34
---
# Dise&#241;o de comando
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Al agregar un comando a un Paquete, debe especificar donde aparezca, cuando está disponible, y cómo debe administrar.  
  
## definición de comandos  
 Para definir nuevos comandos, incluya un archivo de la tabla de comandos de Visual Studio \(.vsct\) en el proyecto de VSPackage.  Si ha creado un VSPackage utilizando la plantilla de paquete de Visual Studio, el proyecto incluye uno de estos archivos.  Para obtener más información, vea [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio combina todos los archivos de .vsct que encuentra para poder mostrar los comandos.  Dado que estos archivos son distintos binarios de VSPackage, Visual Studio no tiene que cargar el paquete para buscar los comandos.  Para obtener más información, vea [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio utiliza el atributo del registro de <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> para definir recursos y comandos de menú.  Para obtener más información, vea [Implementación](../../extensibility/internals/command-implementation.md).  
  
 Los comandos pueden cambiar en tiempo de ejecución de varias maneras diferentes.  Se pueden mostrar u ocultar, habilitar o deshabilitar.  Pueden mostrar el diferentes texto o iconos, o contiene valores diferentes.  Muchos personalización puede realizar antes de que Visual Studio cargue el paquete VSPackage.  Para obtener más información, vea [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## Controladores de comandos  
 Cuando se crea un comando, debe proporcionar un controlador de eventos para ejecutar el comando.  Si el usuario selecciona el comando, debe distribuir correctamente.  Distribuir un comando significa el envío de ella a VSPackage correcto para habilitar o deshabilitar la, la ocultar o para mostrarla, y lo ejecuta si el usuario decide hacerlo.  Para obtener más información, vea [Algoritmo de enrutamiento](../../extensibility/internals/command-routing-algorithm.md).  
  
## El entorno de comandos de Visual Studio  
 El host de la puede Visual Studio cualquier número de VSPackages, y cada uno pueden contribuir a su propio conjunto de comando.  El entorno sólo muestra los comandos apropiados para la tarea actual.  Para obtener más información, vea [Disponibilidad](../../extensibility/internals/command-availability.md) y [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md).  
  
 Un Paquete que define nuevos comandos, menús, barras de herramientas, o menús contextuales proporciona la información del comando a Visual Studio en tiempo de instalación a través de entradas de Registro que los recursos de referencia en código nativo o ensamblados administrados.  Cada recurso hace referencia a un archivo de recursos de datos binarios \(.cto\), que se muestra cuando se compila un archivo de la tabla de comandos de Visual Studio \(.vsct\).  Esto permite a Visual Studio para proporcionar conjuntos combinados de comando, menús, barras de herramientas y sin tener que cargar cada VSPackage instalado.  
  
### Organización de comando  
 Los comandos de entorno por grupo, prioridad, y el menú.  
  
-   Los grupos son colecciones lógicas de comandos relacionados, comando por ejemplo, de grupo de **Cortar**, de **Copiar**, y de **Pegar** .  los grupos son los comandos que aparecen en menús.  
  
-   Prioridad determina el orden en que los comandos individuales en un grupo aparecen en el menú.  
  
-   Menús actúan como contenedores para los grupos.  
  
 el entorno predefine algunos comandos, grupos, y menús.  Para obtener más información, vea [Comando predeterminado, el grupo y la ubicación de la barra de herramientas](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
 Un comando puede asignarse a un grupo primario.  El grupo primario controla la posición del comando en la estructura del menú principal y en el cuadro de diálogo **Personalizar** .  Un comando puede aparecer en varios grupos; por ejemplo, un comando puede estar en el menú principal, en un menú contextual y, en una barra de herramientas.  Para obtener más información, vea [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### Enrutamiento de comandos  
 El proceso de invocar y de distribuir los comandos para VSPackages difiere del proceso de los métodos de llamada en instancias de objeto.  
  
 El entorno enruta comandos secuencialmente de contexto \(local\) más interno del comando, que se basa en la selección actual, el contexto \(global\) fuera.  el primer contexto que puede ejecutar el comando es el que lo administra.  Para obtener más información, vea [Algoritmo de enrutamiento](../../extensibility/internals/command-routing-algorithm.md).  
  
 En la mayoría de las instancias, el entorno controla comandos con la interfaz de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  Porque el esquema de enrutamiento de comandos habilita varios objetos a los comandos de identificador, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> se puede implementar cualquier número de objetos; se trata de controles de Microsoft ActiveX, las implementaciones de la ventana de, los objetos document, las jerarquías del proyecto, y los propios objetos de VSPackage \(para los comandos globales\).  En algunos casos específicos, por ejemplo, mediante comandos en una jerarquía, la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> debe implementar.  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Implementación](../../extensibility/internals/command-implementation.md)|describe cómo implementar comandos en un VSPackage.|  
|[Disponibilidad](../../extensibility/internals/command-availability.md)|Describe cómo el contexto de Visual Studio determina los comandos que están disponibles.|  
|[Algoritmo de enrutamiento](../../extensibility/internals/command-routing-algorithm.md)|Describe cómo la arquitectura de enrutamiento de comandos de Visual Studio habilita comandos de administrar por diferente VSPackages.|  
|[Instrucciones de selección de ubicación](../../extensibility/internals/command-placement-guidelines.md)|sugiere cómo colocar comandos en el entorno de Visual Studio.|  
|[Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Describe cómo VSPackages mejor utilizar la arquitectura de comando de Visual Studio.|  
|[Comando predeterminado, el grupo y la ubicación de la barra de herramientas](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Describe cómo puede VSPackages mejor uso los comandos incluidos en Visual Studio.|  
|[Administración de VSPackages](../../extensibility/managing-vspackages.md)|describe cómo Visual Studio carga VSPackages.|  
|[Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Proporciona información sobre los archivos basados en XML de .vsct, que se utilizan para describir el diseño y la apariencia de comandos en VSPackages.|