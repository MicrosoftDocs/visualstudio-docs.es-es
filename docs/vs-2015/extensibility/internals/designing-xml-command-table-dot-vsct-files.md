---
title: Diseñar la tabla de comandos XML (. Archivos de Vsct) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 987536af051de4a66b3eccadb105fd98455ddf06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196850"
---
# <a name="designing-xml-command-table-vsct-files"></a>Diseño de archivos de tabla de comandos XML (.Vsct)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un archivo de tabla de comandos XML (. Vsct) describe el diseño y la apariencia de los elementos de comando de un VSPackage. Los elementos de comando incluyen botones, cuadros combinados, menús, barras de herramientas y grupos de elementos de comandos. En este tema se describen los archivos de tabla de comandos XML, cómo afectan a los elementos de comando y menús, y cómo se crean.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>Comandos, menús, grupos y el archivo. Vsct  
 los archivos. Vsct se organizan en torno a comandos, menús y grupos de comandos. Las etiquetas XML del archivo. Vsct representan cada uno de estos elementos, junto con otros elementos asociados, como botones de comando, colocación de comandos y mapas de bits.  
  
 Cuando se crea un VSPackage nuevo mediante la ejecución de la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] plantilla de paquete, la plantilla genera un archivo. Vsct con los elementos necesarios para un comando de menú, una ventana de herramientas o un editor personalizado, en función de las selecciones. A continuación, este archivo. Vsct se puede modificar para cumplir los requisitos de un VSPackage específico. Para obtener ejemplos de cómo modificar un archivo. Vsct, vea los ejemplos de [extensión de menús y comandos](../../extensibility/extending-menus-and-commands.md).  
  
 Para crear un nuevo archivo. Vsct en blanco, consulte [Cómo: crear un. Archivo Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Una vez creado, se agregan elementos, atributos y valores XML al archivo para describir el diseño del elemento de comando. Para obtener un esquema XML detallado, vea la [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>Diferencias entre los archivos. CTC y. Vsct  
 Aunque el significado de las etiquetas XML en un archivo. Vsct es el mismo que en el formato de archivo. CTC que ahora está en desuso, su implementación es un poco diferente.  
  
- La nueva **\<extern>** etiqueta es donde se hace referencia a otros archivos. h que se van a compilar, como los de la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] barra de herramientas.  
  
- Aunque los archivos. Vsct admiten la instrucción **/include** , como lo hacen los archivos. CTC, también incluye un nuevo \<**import> elemento * *. La diferencia es que **/include** aporta **toda** la información, pero \<**import> * * solo proporciona los nombres.  
  
- Aunque los archivos. CTC requieren un archivo de encabezado en el que se definen las directivas de preprocesador, no se requiere uno para los archivos. Vsct. En su lugar, coloque las directivas en la tabla de símbolos, que se encuentra en los **\<Symbol>** elementos, que se encuentra en la parte inferior del archivo. Vsct.  
  
- los archivos. Vsct incluyen una **\<Annotation>** etiqueta, que le permite insertar cualquier información que desee, como notas o incluso imágenes.  
  
- Los valores se almacenan como atributos en el elemento.  
  
- Las marcas de comandos se pueden almacenar individualmente o apiladas.  Sin embargo, IntelliSense no funciona en las marcas de comandos apiladas. Para obtener más información sobre las marcas de comandos, vea el elemento de la [marca de comandos](../../extensibility/command-flag-element.md).  
  
- Puede especificar varios tipos, como listas desplegables de división, combinados, etc.  
  
- Los GUID no se validan.  
  
- Cada elemento de la interfaz de usuario tiene una cadena que representa el texto que se muestra con él.  
  
- Parent es opcional. Si se omite, se usa el valor "grupo desconocido".  
  
- El argumento Icon es opcional.  
  
- La sección de mapa de bits (igual que un archivo. CTC), excepto que ahora se puede especificar un nombre de archivo a través de href que el compilador vsct.exe va a extraer en tiempo de compilación.  
  
- ResID: el identificador de recurso de mapa de bits antiguo se puede usar y sigue funcionando igual que en los archivos. CTC.  
  
- HRef: un nuevo método que le permite especificar un nombre de archivo para el recurso de mapa de bits. Se supone que se usan todos, por lo que puede omitir la sección utilizada. El compilador buscará primero los recursos locales para el archivo, luego en los recursos compartidos de red y en los recursos definidos por el modificador/I.  
  
- KeyBinding: ya no tiene que especificar un emulador. Si especifica uno, el compilador supondrá que el editor y el emulador son los mismos.  
  
- KeyChord--se ha quitado. El nuevo formato es Key1, Mod1, Key2, Mod2.  Puede especificar una constante de carácter, hexadecimal o VK.  
  
  El nuevo compilador, vsct.exe, compila los archivos. CTC y. Vsct. Sin embargo, el compilador de ctc.exe anterior no reconocerá ni compilará los archivos. Vsct.  
  
  Puede usar el compilador vsct.exe para convertir un archivo. CTO existente en un archivo. Vsct. Para obtener más información, consulte [Cómo: crear un. Archivo Vsct de un existente. Archivo CTO](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
## <a name="the-vsct-file-elements"></a>Los elementos de archivo. Vsct  
 La tabla de comandos tiene los siguientes elementos y jerarquías:  
  
 [Elemento CommandTable](../../extensibility/commandtable-element.md) : representa todos los comandos, grupos de menús y menús asociados con el VSPackage.  
  
 [Extern (elemento](../../extensibility/extern-element.md) ): hace referencia a los archivos. h externos que desee fusionar mediante combinación con el archivo. Vsct.  
  
 [Include (elemento](../../extensibility/include-element.md) ): hace referencia a los archivos de encabezado (. h) adicionales que desea compilar junto con el archivo. Vsct. Un archivo. Vsct puede incluir archivos. h que contienen constantes que definen comandos, grupos de menús y menús que proporciona el IDE u otro VSPackage.  
  
 [Elemento Commands](../../extensibility/commands-element.md) : representa todos los comandos individuales que se pueden ejecutar. Cada comando tiene los cuatro elementos secundarios siguientes:  
  
 [Elemento menus](../../extensibility/menus-element.md) : representa todos los menús y las barras de herramientas del VSPackage. Los menús son contenedores para grupos de comandos.  
  
 [Elemento Groups](../../extensibility/groups-element.md) : representa todos los grupos del VSPackage. Los grupos son colecciones de comandos individuales.  
  
 [Elemento Buttons](../../extensibility/buttons-element.md) : representa todos los botones de comando y los elementos de menú del VSPackage. Los botones son controles visuales que se pueden asociar a comandos.  
  
 [Bitmaps (elemento](../../extensibility/bitmaps-element.md) ): representa todos los mapas de bits de todos los botones del VSPackage. Los mapas de bits son imágenes que se muestran junto a o en los botones de comando, dependiendo del contexto.  
  
 [Elemento CommandPlacements](../../extensibility/commandplacements-element.md) : indica ubicaciones adicionales donde se deben colocar los comandos individuales en los menús del VSPackage.  
  
 [Elemento VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) : especifica si un comando se muestra en todo momento o solo en determinados contextos, como cuando se muestra un cuadro de diálogo o una ventana concretos. Los menús y comandos que tienen un valor para este elemento solo se mostrarán cuando el contexto especificado esté activo. El comportamiento predeterminado es mostrar el comando en todo momento.  
  
 [Elemento KeyBindings](../../extensibility/keybindings-element.md) : especifica cualquier enlace de teclado para los comandos. Es decir, una o varias combinaciones de teclas que se deben presionar para ejecutar el comando, como **Ctrl + S**.  
  
 [Elemento UsedCommands](../../extensibility/usedcommands-element.md) : informa al entorno de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que, aunque el comando especificado está implementado por otro código, cuando el VSPackage actual está activo, proporciona la implementación del comando.  
  
 `Symbols Element` : Contiene los nombres de símbolo y los identificadores GUID de todos los comandos del paquete.  
  
## <a name="vsct-file-design-guidelines"></a>. Instrucciones para el diseño de archivos Vsct  
 Para diseñar correctamente un archivo. Vsct, siga estas instrucciones.  
  
- Los comandos solo se pueden colocar en grupos, los grupos solo se pueden colocar en los menús y los menús solo se pueden colocar en grupos. En realidad, solo los menús se muestran en el IDE, los grupos y los comandos no.  
  
- Los submenús no se pueden asignar directamente a un menú, sino que deben asignarse a un grupo que, a su vez, se asigna a un menú.  
  
- Los comandos, submenús y grupos pueden asignarse a un solo grupo o menú de protección mediante el campo primario de su Directiva de definición.  
  
- La organización de una tabla de comandos únicamente a través de los campos primarios de las directivas tiene una limitación significativa. Las directivas que definen objetos solo pueden tomar un argumento primario.  
  
- La reutilización de comandos, grupos o submenús requiere el uso de una nueva Directiva para crear una nueva instancia del objeto con su propio `GUID:ID` par.  
  
- Cada `GUID:ID` par debe ser único. La interfaz controla la reutilización de un comando que tiene, por ejemplo, colocado en un menú, una barra de herramientas o un menú contextual <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
- Los comandos y submenús también se pueden asignar a varios grupos, y los grupos pueden asignarse a varios menús mediante el [elemento Commands](../../extensibility/commands-element.md).  
  
## <a name="vsct-file-notes"></a>. Notas del archivo Vsct  
 Si realiza cambios en un archivo. Vsct después de compilarlo y colocarlo en un archivo DLL satélite nativo, debe ejecutar **devenv.exe/Setup/nosetupvstemplates**. Esto obliga a que se vuelvan a leer los recursos de VSPackage especificados en el registro experimental y la base de datos interna que describe la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] recompilación.  
  
 Durante el desarrollo, es posible crear y registrar varios proyectos de VSPackage en el subárbol del registro experimental, lo que puede dar lugar a confusión en el IDE. Para solucionarlo, puede restablecer la configuración predeterminada del subárbol experimental para quitar todos los VSPackages registrados y cualquier cambio que haya realizado en el IDE. Para restablecer el subárbol experimental, use la herramienta de CreateExpInstance.exe que se incluye con el SDK de Visual Studio. Puede encontrarlo en  
  
 **% PROGRAMFILES (x86)% \ Visual Studio \<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Ejecute la herramienta mediante la línea de comandos **CreateExpInstance/RESET**. Recuerde que esta herramienta quita del Hive experimental todos los VSPackages registrados que no se instalan normalmente con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>Consulte también  
 [Ampliación de menús y comandos](../../extensibility/extending-menus-and-commands.md)
