---
title: Diseñar la tabla de comandos XML (. Archivos Vsct) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6c7a4e07c45c5d651af057e1eb33c23d37601cb3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762813"
---
# <a name="designing-xml-command-table-vsct-files"></a>Diseñar la tabla de comandos XML (. Archivos Vsct)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un archivo de tabla (.vsct) del comando XML describe el diseño y la apariencia de los elementos de comando para un paquete VSPackage. Elementos de comandos incluyen botones, cuadros combinados, los menús, barras de herramientas y grupos de elementos de comando. Este tema describe cómo crearlos, cómo afectan a los menús y elementos de comandos y archivos de la tabla de comandos XML.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>El archivo .vsct, grupos, menús y comandos  
 los archivos .vsct están organizados en torno a grupos de comandos, menús y comandos. Las etiquetas XML en el archivo .vsct representan cada uno de estos elementos, junto con otros elementos asociados, como botones de comando, la colocación de comandos y los mapas de bits.  
  
 Cuando crea un nuevo VSPackage mediante la ejecución de la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] plantilla de paquete, la plantilla genera un archivo .vsct con los elementos necesarios para un comando de menú, una ventana de herramientas o un editor personalizado, dependiendo de las selecciones. Este archivo .vsct, a continuación, se puede modificar para cumplir los requisitos de un VSPackage concreto. Para obtener ejemplos de cómo modificar un archivo .vsct, vea los ejemplos de [ampliación de menús y comandos](../../extensibility/extending-menus-and-commands.md).  
  
 Para crear un archivo .vsct en blanco, vea [Cómo: crear una. Archivo de Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Una vez creado, agregue elementos, atributos y valores XML al archivo para describir el diseño del elemento de comando. Para un esquema XML detallado, consulte el [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>Diferencias entre los archivos de CTC y .vsct  
 Aunque el significado de las etiquetas XML en un archivo .vsct es los mismos, como los de ahora en desuso de formato de archivo .ctc, su implementación es un poco diferente.  
  
- El nuevo  **\<extern >** etiqueta es donde hacen referencia a otros archivos .h se compile, como los relativos a la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] barra de herramientas.  
  
- Mientras la compatibilidad con archivos de vsct el **/ include** instrucción, como archivos de CTC, también incluye un nuevo \< **Importar >** elemento. La diferencia es que **/ include** pone **todas** de la información, pero \< **Importar >** aporta sólo los nombres.  
  
- Mientras que los archivos de CTC requieren un archivo de encabezado en el que define sus directivas de preprocesador, uno no es necesario para los archivos .vsct. En su lugar, coloque las directivas en la tabla de símbolos, ubicada en el  **\<símbolo >** elementos, en la parte inferior del archivo .vsct.  
  
- característica de archivos .vsct un  **\<anotación >** etiqueta, que le permite incrustar cualquier información que desee, como notas o incluso imágenes.  
  
- Los valores se almacenan como atributos en el elemento.  
  
- Marcadores de comando se almacenan de manera individual o apiladas.  IntelliSense, sin embargo, no funciona en marcadores de comando apiladas. Para obtener más información acerca de las marcas de comando, consulte el [comando Flag (elemento)](../../extensibility/command-flag-element.md).  
  
- Puede especificar varios tipos, como las listas desplegables de división, cuadro combinado, etcetera.  
  
- No validan los GUID.  
  
- Cada elemento de interfaz de usuario tiene una cadena que representa el texto que se muestra con él.  
  
- Elemento primario es opcional. Si se omite, se usa el valor "Grupo" desconocido".  
  
- El argumento de icono es opcional.  
  
- Archivo de la sección de mapa de bits, el mismo que un .ctc, salvo que ahora se puede especificar un nombre de archivo a través de href que se van a extraer el compilador vsct.exe en tiempo de compilación.  
  
- ResID: el identificador de recurso de mapa de bits anterior se puede usar y funciona igual que en los archivos de CTC.  
  
- HRef--un nuevo método que le permite especificar un nombre de archivo para el recurso de mapa de bits. Se supone que todos se utilizan, por lo que puede omitir la sección que se usa. El compilador buscará en primer lugar los recursos locales para el archivo, a continuación, en los recursos compartidos de red y los recursos definidos por el modificador/i.  
  
- KeyBinding--Ya no es necesario especificar un emulador. Si se especifica uno, el compilador supondrá que el editor y el emulador de son los mismos.  
  
- Keychord: se ha quitado. El nuevo formato es Key1, Mod1, Key2, Mod2.  Puede especificar un carácter, hexadecimal o constante VK.  
  
  El nuevo compilador, vsct.exe, compila los archivos de CTC y .vsct. El compilador ctc.exe antiguo, sin embargo, no reconoce ni compilar archivos .vsct.  
  
  Puede usar el compilador vsct.exe para convertir un archivo .cto existente en un archivo .vsct. Para obtener más información, vea [Cómo: crear una. Archivo de Vsct desde una existente. Archivo CTO](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
## <a name="the-vsct-file-elements"></a>Los elementos del archivo .vsct  
 La tabla de comandos tiene la jerarquía y los elementos siguientes:  
  
 [CommandTable (elemento)](../../extensibility/commandtable-element.md) : representa todos los comandos, grupos de menús y menús asociados con el VSPackage.  
  
 [Extern (elemento)](../../extensibility/extern-element.md) : hace referencia a los archivos .h externo que desea combinar con el archivo .vsct.  
  
 [Elemento de inclusión](../../extensibility/include-element.md) : hace referencia a los archivos de encabezado adicional (. h) que desee compilar junto con el archivo your.vsct. Un archivo .vsct puede incluir archivos .h que contiene las constantes que definen los comandos, grupos de menús y menús que el IDE o en otro VSPackage proporciona.  
  
 [Comandos de elemento](../../extensibility/commands-element.md) : representa todos los comandos individuales que se pueden ejecutar. Cada comando tiene los cuatro elementos secundarios siguientes:  
  
 [Menus (elemento)](../../extensibility/menus-element.md) : representa todos los menús y barras de herramientas en el VSPackage. Los menús son contenedores de grupos de comandos.  
  
 [Elemento Groups](../../extensibility/groups-element.md) : representa todos los grupos en el VSPackage. Los grupos son colecciones de comandos individuales.  
  
 [Botones elemento](../../extensibility/buttons-element.md) : representa todos los botones de comando y los elementos de menú en el VSPackage. Los botones son controles visuales que pueden asociarse con comandos.  
  
 [Elemento de mapas de bits](../../extensibility/bitmaps-element.md) : representa todos los mapas de bits para todos los botones en el VSPackage. Los mapas de bits son imágenes que se muestran junto a o en los botones de comando, dependiendo del contexto.  
  
 [CommandPlacements (elemento)](../../extensibility/commandplacements-element.md) : indica más ubicaciones donde los comandos individuales deben estar ubicados en los menús del paquete VSPackage.  
  
 [VisibilityConstraints (elemento)](../../extensibility/visibilityconstraints-element.md) : Especifica si un comando en absoluto muestra veces o sólo en determinados contextos, como cuando se muestre un cuadro de diálogo determinado o ventana. Menús y comandos que tienen un valor para este elemento se mostrarán solo cuando está activo el contexto especificado. El comportamiento predeterminado consiste en Mostrar el comando en todo momento.  
  
 [Elemento KeyBindings](../../extensibility/keybindings-element.md) : especifica los enlaces de teclado para los comandos. Es decir, una o varias combinaciones de teclas que se deben presionar para ejecutar el comando, como **CTRL+S**.  
  
 [UsedCommands (elemento)](../../extensibility/usedcommands-element.md) : informa el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que, aunque se implementa el comando especificado por otro código, cuando el paquete VSPackage actual está activo, proporciona la implementación de comandos del entorno.  
  
 `Symbols Element` : Contiene los nombres de símbolos y los identificadores GUID para todos los comandos en el paquete.  
  
## <a name="vsct-file-design-guidelines"></a>. Instrucciones de diseño del archivo de Vsct  
 Para diseñar correctamente un archivo .vsct, siga estas instrucciones.  
  
-   Los comandos se pueden colocar solo en grupos, grupos se pueden colocar solo en los menús y menús pueden colocarse únicamente en grupos. Sólo los menús realmente se muestran en el IDE, grupos y los comandos no están.  
  
-   No se puede asignar directamente a un menú submenús, pero deben asignarse a un grupo, que a su vez se asigna a un menú.  
  
-   Comandos, submenús y grupos pueden asignarse a un menú mediante el campo principal de su definición de directiva o grupo de la relación jerárquica.  
  
-   Organización de una tabla de comandos únicamente a través de los campos de elemento primario en las directivas tiene una limitación importante. Las directivas que definen objetos pueden tomar el argumento de un único elemento primario.  
  
-   Volver a usar los comandos, grupos o submenús requiere el uso de una directiva nueva para crear una nueva instancia del objeto con su propio `GUID:ID` par.  
  
-   Cada `GUID:ID` par debe ser único. Volver a usar un comando, por ejemplo, colocados en un menú, una barra de herramientas, o en un menú contextual, se controla mediante el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz.  
  
-   Los comandos y submenús también pueden asignarse a varios grupos y grupos se pueden asignar a varios menús con el [elemento Commands](../../extensibility/commands-element.md).  
  
## <a name="vsct-file-notes"></a>. Notas de archivo de Vsct  
 Si realiza cambios en un archivo .vsct después de que lo compilará y lo coloca en un archivo DLL nativo, debe ejecutar **devenv.exe /setup /nosetupvstemplates**. Esto obliga a los recursos de VSPackage especificados en el registro de experimental a leer y la base de datos interna que describe [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se vuelvan a generar.  
  
 Durante el desarrollo, es posible que varios proyectos de VSPackage que se crean y registran en el subárbol del registro experimental que puede llevar a confusión desorden en el IDE. Para solucionar este problema, puede restablecer el subárbol experimental a la configuración predeterminada para quitar todas las instancias registrados VSPackages y cualquier cambio que pueden haber realizado para el IDE. Para restablecer el subárbol experimental, use la herramienta CreateExpInstance.exe que se incluye con el SDK de Visual Studio. Puede encontrarlo en  
  
 **% PROGRAMFILES (x 86) %\Visual Studio \<versión > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Ejecute la herramienta mediante el uso de la línea de comandos **CreateExpInstance /Reset**. Recuerde que esta herramienta quita el subárbol experimental todos los VSPackages registrados normalmente no se instala con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Ampliación de menús y comandos](../../extensibility/extending-menus-and-commands.md)

