---
title: Diseño de la tabla de comandos XML (. Vsct) Archivos de la casa de la página de música de Vsct (Vs Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fcd29aee98139bb151c87590b256df6b8370abff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708750"
---
# <a name="design-xml-command-table-vsct-files"></a>Diseñar archivos de tabla de comandos XML (.vsct)
Un archivo de tabla de comandos XML (*.vsct*) describe el diseño y la apariencia de los elementos de comando para un VSPackage. Los elementos de comando incluyen botones, cuadros combinados, menús, barras de herramientas y grupos de elementos de comando. En este artículo se describen los archivos de tabla de comandos XML, cómo afectan a los elementos de comando y los menús y cómo crearlos.

## <a name="commands-menus-groups-and-the-vsct-file"></a>Comandos, menús, grupos y el archivo .vsct
 Los archivos *.vsct* se organizan en torno a comandos, menús y grupos de comandos. Las etiquetas XML del archivo *.vsct* representan cada uno de estos elementos, junto con otros elementos asociados, como botones de comando, ubicación de comandos y mapas de bits.

 Al crear un nuevo VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ejecutando la plantilla de paquete, la plantilla genera un archivo *.vsct* con los elementos necesarios para un comando de menú, ventana de herramientas o editor personalizado, dependiendo de las selecciones. Este archivo *.vsct,* a continuación, se puede modificar para cumplir los requisitos de un VSPackage específico. Para obtener ejemplos de cómo modificar un archivo *.vsct,* consulte [Extender menús y comandos](../../extensibility/extending-menus-and-commands.md).

 Para crear un nuevo archivo *.vsct* en blanco, consulte [Cómo: Crear un archivo *.vsct* ](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Una vez creado, agregue elementos XML, atributos y valores al archivo para describir el diseño del elemento de comando. Para obtener un esquema XML detallado, vea la referencia de [esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md).

## <a name="differences-between-ctc-and-vsct-files"></a>Diferencias entre archivos .ctc y .vsct
 Mientras que el significado detrás de las etiquetas XML en un archivo *.vsct* es el mismo que el de las etiquetas en el formato de archivo *.ctc* ahora en desuso, su implementación es un poco diferente:

- La ** \<** nueva etiqueta de>externo es donde se hace referencia a otros [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] archivos *.h* que se van a compilar, como los archivos de la barra de herramientas.

- Mientras que los archivos *.vsct* admiten la instrucción **/include,** como lo hacen los archivos *.ctc,* también cuenta con un nuevo ** \<** elemento de>de importación. La diferencia es, **/include** trae *toda* la información, mientras que ** \<la importación>** trae solo los nombres.

- Aunque los archivos *.ctc* requieren un archivo de encabezado en el que se definen las directivas de preprocesador, no es necesario uno para los archivos *.vsct.* En su lugar, coloque las directivas ** \<** en la tabla de símbolos, ubicada en los elementos Symbol>, situados en la parte inferior del archivo *.vsct.*

- Los archivos *.vsct* cuentan con una ** \<etiqueta de>de anotación,** que le permite incrustar cualquier información que desee, como notas o incluso imágenes.

- Los valores se almacenan como atributos en el elemento.

- Los indicadores de comando se pueden almacenar individualmente o apilar.  IntelliSense, sin embargo, no funciona en indicadores de comandos apilados. Para obtener más información acerca de los indicadores de comando, vea el [elemento CommandFlag](../../extensibility/command-flag-element.md).

- Puede especificar varios tipos, como listas desplegables divididas, combos, etc.

- Los GUID no se validan.

- Cada elemento de interfaz de usuario tiene una cadena que representa el texto que se muestra con él.

- El elemento primario es opcional. Si se omite, se utiliza el valor *Group Unknown.*

- El *argumento Icon* es opcional.

- Sección de mapa de bits: esta sección es la misma que en un archivo *.ctc,* excepto que ahora puede especificar un nombre de archivo a través de Href que el compilador *vsct.exe* extraerá en tiempo de compilación.

- ResID: el id de recurso de mapa de bits antiguo se puede utilizar y sigue funcionando igual que en los archivos *.ctc.*

- HRef: un nuevo método que permite especificar un nombre de archivo para el recurso de mapa de bits. Se supone que se utilizan todos, por lo que puede omitir la sección Usado. El compilador buscará primero recursos locales para el archivo, luego en los recursos compartidos de red y los recursos definidos por el modificador **/I.**

- Enlace de teclas: ya no es que tenga que especificar un emulador. Si especifica uno, el compilador asumirá que el editor y el emulador son los mismos.

- Keychord: Keychord se ha eliminado. El nuevo formato es *Key1,Mod1,Key2,Mod2*.  Puede especificar una constante de carácter, hexadecimal o VK.

El nuevo compilador, *vsct.exe*, compila archivos *.ctc* y *.vsct.* Sin embargo, el antiguo compilador *ctc.exe* no reconocerá ni compilará archivos *.vsct.*

Puede usar el compilador *vsct.exe* para convertir un archivo *.cto* existente en un archivo *.vsct.* Para obtener más información, consulte [Cómo: crear un archivo .vsct a partir de un archivo .cto existente.](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)

## <a name="the-vsct-file-elements"></a>Los elementos de archivo .vsct
 La tabla de comandos tiene la siguiente jerarquía y elementos:

- [CommandTable elemento](../../extensibility/commandtable-element.md): representa todos los comandos, grupos de menús y menús asociados con el VSPackage.

- [Elemento Externo](../../extensibility/extern-element.md): Hace referencia a los archivos .h externos que desea combinar con el archivo *.vsct.*

- [Incluir elemento](../../extensibility/include-element.md): Hace referencia a cualquier archivo de encabezado adicional (.h) que desee compilar junto con el archivo *.vsct.* Un archivo *.vsct* puede incluir archivos *.h* que contienen constantes que definen comandos, grupos de menús y menús que proporciona el IDE u otro VSPackage.

- [Elemento Commands](../../extensibility/commands-element.md): Representa todos los comandos individuales que se pueden ejecutar. Cada comando tiene los cuatro elementos secundarios siguientes:

- [Elemento Menus](../../extensibility/menus-element.md): Representa todos los menús y barras de herramientas en el VSPackage. Los menús son contenedores para grupos de comandos.

- [Elemento Groups](../../extensibility/groups-element.md): Representa todos los grupos del VSPackage. Los grupos son colecciones de comandos individuales.

- [Elemento Buttons](../../extensibility/buttons-element.md): Representa todos los botones de comando y elementos de menú en el VSPackage. Los botones son controles visuales que se pueden asociar con comandos.

- [Elemento Bitmaps](../../extensibility/bitmaps-element.md): Representa todos los mapas de bits para todos los botones en el VSPackage. Los mapas de bits son imágenes que se muestran junto o en los botones de comando, dependiendo del contexto.

- [Elemento CommandPlacements](../../extensibility/commandplacements-element.md): indica ubicaciones adicionales donde los comandos individuales deben colocarse en los menús de su VSPackage.

- [VisibilityConstraints elemento](../../extensibility/visibilityconstraints-element.md): Especifica si un comando se muestra en todo momento, o sólo en ciertos contextos, como cuando se muestra un cuadro de diálogo o ventana determinado. Los menús y comandos que tienen un valor para este elemento solo se mostrarán cuando el contexto especificado esté activo. El comportamiento predeterminado es mostrar el comando en todo momento.

- [Elemento KeyBindings](../../extensibility/keybindings-element.md): especifica los enlaces de clave para los comandos. Es decir, una o más combinaciones de teclas que se deben presionar para ejecutar el comando, como **Ctrl**+**S**.

- [Elemento UsedCommands](../../extensibility/usedcommands-element.md): [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] informa al entorno de que aunque el comando especificado se implementa mediante otro código, cuando el VSPackage actual está activo, proporciona la implementación del comando.

- [Elemento Símbolos](../../extensibility/symbols-element.md): Contiene los nombres de símbolo y los ID GUID de todos los comandos del paquete.

## <a name="vsct-file-design-guidelines"></a>Directrices de diseño de archivos .vsct
 Para diseñar correctamente un archivo *.vsct,* siga estas directrices.

- Los comandos solo se pueden colocar en grupos, los grupos solo se pueden colocar en los menús y los menús solo se pueden colocar en grupos. Solo los menús se muestran realmente en el IDE, los grupos y los comandos no lo son.

- Los submenús no se pueden asignar directamente a un menú, sino que deben asignarse a un grupo, que a su vez se asigna a un menú.

- Los comandos, submenús y grupos se pueden asignar a un grupo o menú de crianza mediante el campo primario de su directiva de definición.

- Organizar una tabla de comandos únicamente a través de los campos primarios de las directivas tiene una limitación significativa. Las directivas que definen objetos solo pueden tomar un argumento primario.

- La reutilización de comandos, grupos o submenús requiere el uso de una `GUID:ID` nueva directiva para crear una nueva instancia del objeto con su propio par.

- Cada `GUID:ID` par debe ser único. La <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz controla la reutilización de un comando que, por ejemplo, se ha colocado en un menú, una barra de herramientas o en un menú contextual.

- Los comandos y submenús también se pueden asignar a varios grupos, y los grupos se pueden asignar a varios menús mediante el [elemento Comandos](../../extensibility/commands-element.md).

## <a name="vsct-file-notes"></a>Notas de archivo .vsct
 Si realiza cambios en un archivo *.vsct* después de compilarlo y colocarlo en un archivo DLL satélite nativo, debe ejecutar **devenv.exe /setup /nosetupvstemplates**. Al hacerlo, se vuelven a leer los recursos de VSPackage especificados en el registro experimental y se vuelve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a generar la base de datos interna que describe que se va a volver a generar.

 Durante el desarrollo, es posible que varios proyectos de VSPackage se creen y registren en el subárbol del registro experimental que puede provocar un desorden confuso en el IDE. Para solucionar este problema, puede restablecer el subárbol experimental a la configuración predeterminada para quitar todos los VSPackages registrados y los cambios que puedan haber realizado en el IDE. Para restablecer el subárbol experimental, use la herramienta CreateExpInstance.exe que viene con el SDK de Visual Studio. Puedes encontrarlo en:

 *%PROGRAMFILES(x86)%-Visual\\\<Studio versión> SDK-VisualStudioIntegration-Tools-Bin-CreateExpInstance.exe*

 Ejecute la herramienta mediante el comando **CreateExpInstance /Reset**. Recuerde que esta herramienta quita del subárbol experimental todos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]los VSPackages registrados que normalmente no se instalan con .

## <a name="see-also"></a>Vea también
- [Extender menús y comandos](../../extensibility/extending-menus-and-commands.md)
