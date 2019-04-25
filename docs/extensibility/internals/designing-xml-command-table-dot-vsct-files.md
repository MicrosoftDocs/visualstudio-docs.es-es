---
title: Diseñar la tabla de comandos XML (. Archivos Vsct) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e70a64e01e388af61127fd76f4a2fcee8e5a9b9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091569"
---
# <a name="design-xml-command-table-vsct-files"></a>Diseñar archivos de tabla (.vsct) de comandos XML
Una tabla de comandos XML (*.vsct*) archivo describe el diseño y la apariencia de los elementos de comando para un paquete VSPackage. Elementos de comandos incluyen botones, cuadros combinados, los menús, barras de herramientas y grupos de elementos de comando. En este artículo se describe cómo crearlos, cómo afectan a los menús y elementos de comandos y archivos de la tabla de comandos XML.

## <a name="commands-menus-groups-and-the-vsct-file"></a>El archivo .vsct, grupos, menús y comandos
 El *.vsct* archivos están organizados en torno a grupos de comandos, menús y comandos. Etiquetas XML en el *.vsct* representan cada uno de estos elementos, junto con otros elementos asociados, como botones de comando, la colocación de comandos y los mapas de bits de archivos.

 Cuando crea un nuevo VSPackage mediante la ejecución de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plantilla de paquete, la plantilla genera un *.vsct* archivo con los elementos necesarios para un comando de menú, una ventana de herramientas o un editor personalizado, dependiendo de las selecciones. Esto *.vsct* archivo, a continuación, se puede modificar para cumplir los requisitos de un VSPackage concreto. Para obtener ejemplos de cómo modificar un *.vsct* de archivos, consulte [amplían los menús y comandos](../../extensibility/extending-menus-and-commands.md).

 Para crear un nuevo, en blanco *.vsct* de archivos, vea [Cómo: Crear un *.vsct* archivo](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Una vez creado, agregue elementos, atributos y valores XML al archivo para describir el diseño del elemento de comando. Para un esquema XML detallado, consulte el [referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md).

## <a name="differences-between-ctc-and-vsct-files"></a>Diferencias entre los archivos de CTC y .vsct
 Mientras que el significado de XML de etiquetas en un *.vsct* archivo son las mismas que las etiquetas de ahora en desuso *.ctc* formato de archivo, su implementación es un poco diferente:

- El nuevo  **\<extern >** etiqueta es donde hacen referencia Sí *.h* archivos compilarse, por ejemplo, esos archivos para el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] barra de herramientas.

- Mientras *.vsct* compatibilidad con archivos de la **/ include** instrucción, como *.ctc* hacer archivos, también presenta una nueva  **\<Importar >** elemento. La diferencia es que **/ include** pone *todas* de la información, mientras  **\<Importar >** aporta sólo los nombres.

- Mientras *.ctc* archivos requieren un archivo de encabezado en el que define sus directivas de preprocesador, uno no es necesario para *.vsct* archivos. En su lugar, coloque las directivas en la tabla de símbolos, ubicada en el  **\<símbolo >** elementos, en la parte inferior de la *.vsct* archivo.

- *.vsct* característica de archivos de un  **\<anotación >** etiqueta, que le permite incrustar cualquier información que desee, como notas o incluso imágenes.

- Los valores se almacenan como atributos en el elemento.

- Marcadores de comando se almacenan de manera individual o apiladas.  IntelliSense, sin embargo, no funciona en marcadores de comando apiladas. Para obtener más información acerca de las marcas de comando, consulte el [CommandFlag elemento](../../extensibility/command-flag-element.md).

- Puede especificar varios tipos, como las listas desplegables de división, cuadro combinado, etcetera.

- No validan los GUID.

- Cada elemento de interfaz de usuario tiene una cadena que representa el texto que se muestra con él.

- El elemento primario es opcional. Si se omite, el valor *grupo desconocido* se utiliza.

- El *icono* argumento es opcional.

- Sección de mapa de bits: En esta sección es la misma que en un *.ctc* de archivos, excepto que ahora puede especificar un nombre de archivo a través de Href que se van a extraer por la *vsct.exe* compilador en tiempo de compilación.

- ResID: Identificador puede ser utilizado y aún funciona igual que en el recurso de mapa de bits de la antigua *.ctc* archivos.

- HRef: Un nuevo método que le permite especificar un nombre de archivo para el recurso de mapa de bits. Se supone que todos se utilizan, por lo que puede omitir la sección que se usa. El compilador buscará en primer lugar los recursos locales para el archivo, a continuación, en los recursos compartidos de red y todos los recursos definen por el **/I** cambie.

- Enlace de teclado: Ya no debe especificar un emulador. Si se especifica uno, el compilador supondrá que el editor y el emulador de son los mismos.

- Keychord: Se ha quitado Keychord. Es el nuevo formato *Key1, Mod1, Key2, Mod2*.  Puede especificar un carácter, hexadecimal o constante VK.

El nuevo compilador, *vsct.exe*, compila ambos *.ctc* y *.vsct* archivos. La antigua *ctc.exe* compilador, sin embargo, no se reconoce o compilar *.vsct* archivos.

Puede usar el *vsct.exe* compilador que convierta existente *.cto* el archivo en un *.vsct* archivo. Para obtener más información, vea [Cómo: Crear un archivo .vsct a partir de un archivo .cto existente](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

## <a name="the-vsct-file-elements"></a>Los elementos del archivo .vsct
 La tabla de comandos tiene la jerarquía y los elementos siguientes:

- [CommandTable (elemento)](../../extensibility/commandtable-element.md): Representa todos los comandos, grupos de menús y menús asociados con el VSPackage.

- [Extern (elemento)](../../extensibility/extern-element.md): Hace referencia a los archivos .h externo que desea combinar con el *.vsct* archivo.

- [Elemento de inclusión](../../extensibility/include-element.md): Hace referencia a los archivos de encabezado adicional (. h) que desee compilar junto con su *.vsct* archivo. Un *.vsct* puede incluir el archivo *.h* archivos que contiene las constantes que definen los comandos, grupos de menús y menús que el IDE o en otro VSPackage proporciona.

- [Elemento Commands](../../extensibility/commands-element.md): Representa todos los comandos individuales que se pueden ejecutar. Cada comando tiene los cuatro elementos secundarios siguientes:

- [Menus (elemento)](../../extensibility/menus-element.md): Representa todos los menús y barras de herramientas en el VSPackage. Los menús son contenedores de grupos de comandos.

- [Elemento Groups](../../extensibility/groups-element.md): Representa todos los grupos en el VSPackage. Los grupos son colecciones de comandos individuales.

- [Elemento botones](../../extensibility/buttons-element.md): Representa todos los botones de comando y los elementos de menú en el VSPackage. Los botones son controles visuales que pueden asociarse con comandos.

- [Elemento de mapas de bits](../../extensibility/bitmaps-element.md): Representa todos los mapas de bits para todos los botones en el VSPackage. Los mapas de bits son imágenes que se muestran junto a o en los botones de comando, dependiendo del contexto.

- [CommandPlacements (elemento)](../../extensibility/commandplacements-element.md): Indica más ubicaciones donde los comandos individuales deben estar ubicados en los menús del paquete VSPackage.

- [VisibilityConstraints (elemento)](../../extensibility/visibilityconstraints-element.md): Especifica si un comando se muestra en absoluto veces o sólo en determinados contextos, como cuando se muestre un cuadro de diálogo determinado o ventana. Menús y comandos que tienen un valor para este elemento se mostrarán solo cuando está activo el contexto especificado. El comportamiento predeterminado consiste en Mostrar el comando en todo momento.

- [Elemento KeyBindings](../../extensibility/keybindings-element.md): Especifica los enlaces de teclado para los comandos. Es decir, una o varias combinaciones de teclas que se deben presionar para ejecutar el comando, como **Ctrl**+**S**.

- [UsedCommands (elemento)](../../extensibility/usedcommands-element.md): Informa a la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que, aunque se implementa el comando especificado por otro código, cuando el paquete VSPackage actual está activo, proporciona la implementación de comandos del entorno.

- [Symbols (elemento)](../../extensibility/symbols-element.md): Contiene los nombres de símbolos y los identificadores GUID para todos los comandos en el paquete.

## <a name="vsct-file-design-guidelines"></a>instrucciones de diseño del archivo .vsct
 Diseño correctamente un *.vsct* , siga estas instrucciones.

- Los comandos se pueden colocar solo en grupos, grupos se pueden colocar solo en los menús y menús pueden colocarse únicamente en grupos. Sólo los menús realmente se muestran en el IDE, grupos y los comandos no están.

- No se puede asignar directamente a un menú submenús, pero deben asignarse a un grupo, que a su vez se asigna a un menú.

- Comandos, submenús y grupos pueden asignarse a un menú mediante el campo principal de su definición de directiva o grupo de la relación jerárquica.

- Organización de una tabla de comandos únicamente a través de los campos de elemento primario en las directivas tiene una limitación importante. Las directivas que definen objetos pueden tomar el argumento de un único elemento primario.

- Volver a usar los comandos, grupos o submenús requiere el uso de una directiva nueva para crear una nueva instancia del objeto con su propio `GUID:ID` par.

- Cada `GUID:ID` par debe ser único. Volver a usar un comando, por ejemplo, colocados en un menú, una barra de herramientas, o en un menú contextual, se controla mediante el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz.

- Los comandos y submenús también pueden asignarse a varios grupos y grupos se pueden asignar a varios menús con el [elemento Commands](../../extensibility/commands-element.md).

## <a name="vsct-file-notes"></a>notas del archivo .vsct
 Si realiza los cambios realizados en un *.vsct* archivo después de tanto compilarlo y colocarlo en un archivo DLL nativo, debe ejecutar **devenv.exe /setup /nosetupvstemplates**. Realizar por lo que fuerza los recursos de VSPackage especificados en el registro de experimental a leer y la base de datos interna que describe [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se vuelvan a generar.

 Durante el desarrollo, es posible que varios proyectos de VSPackage que se crean y registran en el subárbol del registro experimental que puede llevar a confusión desorden en el IDE. Para solucionar este problema, puede restablecer el subárbol experimental a la configuración predeterminada para quitar todas las instancias registrados VSPackages y cualquier cambio que pueden haber realizado para el IDE. Para restablecer el subárbol experimental, use la herramienta CreateExpInstance.exe que se incluye con el SDK de Visual Studio. Puede encontrar en:

 *% PROGRAMFILES (x 86) %\Visual Studio\\\<versión > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe*

 Ejecute la herramienta mediante el comando **CreateExpInstance /Reset**. Recuerde que esta herramienta quita el subárbol experimental todos los VSPackages registrados normalmente no se instala con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Vea también
- [Extender los menús y comandos](../../extensibility/extending-menus-and-commands.md)