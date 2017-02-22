---
title: "Dise&#241;ar la tabla de comandos XML (. Archivos de Vsct) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Archivos VSCT, diseñar"
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# Dise&#241;ar la tabla de comandos XML (. Archivos de Vsct)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un archivo de tabla \(.vsct\) del comando XML describe el diseño y la apariencia de los elementos de comando para un VSPackage. Elementos de comandos incluyen botones, cuadros combinados, menús, barras de herramientas y los grupos de elementos del comando. Este tema describe cómo crearlos, cómo afectan los menús y elementos de comandos y archivos de la tabla de comandos XML.  
  
## El archivo .vsct, menús, grupos y comandos  
 los archivos .vsct se organizan en torno a grupos de comandos, menús y comandos. Etiquetas XML en el archivo .vsct representan cada uno de estos elementos, junto con otros elementos como botones de comando, la colocación de comandos y los mapas de bits asociados.  
  
 Cuando se crea un nuevo VSPackage ejecutando el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plantilla de paquete, la plantilla genera un archivo de vsct con los elementos necesarios para un comando de menú, la ventana de herramientas o el editor personalizado, dependiendo de las selecciones. Este archivo de vsct, a continuación, se puede modificar para cumplir los requisitos de un paquete VSPackage específico. Para obtener ejemplos de cómo modificar un archivo .vsct, vea los ejemplos en [Comandos y menús de extensión](../../extensibility/extending-menus-and-commands.md).  
  
 Para crear un archivo de vsct en blanco, consulte [Cómo: crear una. Archivo de Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Una vez creado, agregar elementos, atributos y valores XML al archivo para describir el diseño del elemento de comando. Para un esquema XML detallado, consulte el [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
## Diferencias entre los archivos .ctc y .vsct  
 Aunque el significado a las etiquetas XML en un archivo de vsct es iguales a los de ahora en desuso .ctc formato de archivo, su implementación es un poco diferente.  
  
-   El nuevo **\< extern \>** etiqueta es que hacen referencia a otros archivos .h se compile, como los de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] barra de herramientas.  
  
-   Mientras que .vsct archivos de compatibilidad con el **\/ include** instrucción, como archivos .ctc, también incluye un nuevo \<**Importar \>** elemento. La diferencia es **\/ include** pone **todos los** de la información, pero \<**Importar \>** pone en los nombres.  
  
-   Mientras que los archivos .ctc requieren un archivo de encabezado en el que se definen las directivas de preprocesador, uno que no es necesario para los archivos .vsct. En su lugar, coloque las directivas en la tabla de símbolos, ubicada en el **\< símbolo \>** elementos, ubicados en la parte inferior del archivo vsct.  
  
-   característica de archivos .vsct un **\< anotación \>** etiqueta, que le permite incrustar cualquier información que desee, como notas o incluso imágenes.  
  
-   Los valores se almacenan como atributos en el elemento.  
  
-   Indicadores de comando pueden ser almacenados individualmente o apiladas.  IntelliSense, sin embargo, no funciona en los indicadores de comando apiladas. Para obtener más información acerca de los indicadores de comando, consulte el [Elemento de indicador de comando](../../extensibility/command-flag-element.md).  
  
-   Puede especificar varios tipos, como listas desplegables de división, combinación, etc..  
  
-   No validan el GUID.  
  
-   Cada elemento de la interfaz de usuario tiene una cadena que representa el texto que se muestra con él.  
  
-   Elemento primario es opcional. Si se omite, se utiliza el valor "Grupo" desconocido".  
  
-   El argumento del icono es opcional.  
  
-   Archivo de la sección de mapa de bits, el mismo que un .ctc, excepto que ahora puede especificar un nombre de archivo a través de href que se van a extraer el compilador vsct.exe en tiempo de compilación.  
  
-   ResID\-\-el identificador de recurso de mapa de bits anterior se puede usar y sigue funcionando del mismo en .ctc archivos.  
  
-   HRef\-\-un nuevo método que le permite especificar un nombre de archivo para el recurso de mapa de bits. Se supone que todas se utilizan, por lo que puede omitir la sección usada. El compilador buscará primero recursos locales para el archivo, a continuación, en los recursos compartidos de red y los recursos definidos por el modificador\/i.  
  
-   KeyBinding\-\-Ya no tendrá que especificar un emulador. Si se especifica uno, el compilador supondrá que el editor y el emulador son los mismos.  
  
-   Keychord: se ha quitado. El nuevo formato es Key1, Mod1, Key2, Mod2.  Puede especificar un carácter, hexadecimal o constante VK.  
  
 El nuevo compilador, vsct.exe, compila los archivos .ctc y vsct. El compilador ctc.exe antiguo, sin embargo, se reconoce ni compilar archivos .vsct.  
  
 Puede utilizar el compilador vsct.exe para convertir un archivo de .cto existente en un archivo de vsct. Para obtener más información sobre esto, consulte [Cómo: Crear un archivo .vsct a partir de un archivo .cto existente](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
## Los elementos del archivo vsct  
 La tabla de comandos tiene la jerarquía y los elementos siguientes:  
  
 [Elemento CommandTable](../../extensibility/commandtable-element.md) — Representa todos los comandos, grupos de menús y menús asociados con el paquete VSPackage.  
  
 [Elemento extern](../../extensibility/extern-element.md) : Hace referencia a los archivos .h externo que desea combinar con el archivo .vsct.  
  
 [Elemento include](../../extensibility/include-element.md) : Hace referencia a los archivos de encabezado adicional \(. h\) que desee compilar junto con el archivo your.vsct. Un archivo de vsct puede incluir archivos .h que contiene constantes que definen los comandos, grupos de menús y menús que proporciona el IDE o en otro VSPackage.  
  
 [Elemento Commands](../../extensibility/commands-element.md) — Representa todos los comandos individuales que se pueden ejecutar. Cada comando tiene los siguientes cuatro elementos secundarios:  
  
 [Elemento de menús](../../extensibility/menus-element.md) — Representa todos los menús y barras de herramientas de VSPackage. Los menús son contenedores para grupos de comandos.  
  
 [Elemento Groups](../../extensibility/groups-element.md) — Representa todos los grupos de VSPackage. Los grupos son colecciones de comandos individuales.  
  
 [Elemento de botones](../../extensibility/buttons-element.md) — Representa todos los botones de comando y los elementos de menú de VSPackage. Botones son controles visuales que pueden asociarse con comandos.  
  
 [Elemento de mapas de bits](../../extensibility/bitmaps-element.md) — Representa todos los mapas de bits para todos los botones de VSPackage. Mapas de bits son imágenes que se muestran junto a o en los botones de comando, dependiendo del contexto.  
  
 [Elemento CommandPlacements](../../extensibility/commandplacements-element.md) Indica que los otros lugares donde los comandos individuales deben estar ubicados en los menús de su paquete VSPackage.  
  
 [Elemento VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) : Especifica si se permite o no un comando en todos los muestra veces o sólo en determinados contextos, como cuando se muestre un cuadro de diálogo determinado o la ventana. Menús y comandos que tienen un valor para este elemento se mostrarán únicamente cuando el contexto especificado está activo. El comportamiento predeterminado es mostrar el comando en todo momento.  
  
 [Elemento de enlaces de teclado](../../extensibility/keybindings-element.md) : Permite especificar los enlaces de teclado para los comandos. Es decir, una o varias combinaciones de teclas que deben presionar para ejecutar el comando, como **CTRL \+ S**.  
  
 [Elemento UsedCommands](../../extensibility/usedcommands-element.md) : Informa a la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que, aunque se implementa el comando especificado por otro código, cuando está activo el VSPackage actual, proporciona la implementación de comandos del entorno.  
  
 `Symbols Element` : Contiene los nombres de símbolo e identificadores de GUID para todos los comandos en el paquete.  
  
## . Instrucciones de diseño del archivo de Vsct  
 Para diseñar correctamente un archivo de vsct, siga estas instrucciones.  
  
-   Comandos pueden colocarse únicamente en grupos, grupos pueden colocarse únicamente en los menús y los menús pueden colocarse únicamente en grupos. Sólo los menús realmente se muestran en el IDE, grupos y comandos no están.  
  
-   Submenús no pueden asignarse directamente a un menú, pero deben asignarse a un grupo, que a su vez se asigna a un menú.  
  
-   Comandos, submenús y grupos pueden asignarse a un grupo de asociación o menú mediante el campo principal de su definición de directiva.  
  
-   Organización de una tabla de comandos únicamente a través de los campos de elemento primario en las directivas tiene una limitación importante. Las directivas que definen objetos pueden tomar el argumento de un único elemento primario.  
  
-   Volver a utilizar los comandos, grupos o submenús requiere el uso de una directiva nueva para crear una nueva instancia del objeto con su propio `GUID:ID` par.  
  
-   Cada `GUID:ID` par debe ser único. Volver a utilizar un comando, por ejemplo, colocados en un menú, una barra de herramientas o en un menú contextual, se controla mediante la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz.  
  
-   Comandos y submenús también pueden asignarse a varios grupos y grupos se pueden asignar a varios menús mediante el [Elemento Commands](../../extensibility/commands-element.md).  
  
## . Notas del archivo Vsct  
 Si realiza cambios en un archivo de vsct después de que compilarlo y colocarlo en un archivo DLL satélite nativo, debe ejecutar **devenv.exe \/setup \/nosetupvstemplates**. Esto obliga a los recursos de VSPackage especificados en el registro experimental a leer y la base de datos interna que describe [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] volver a generar.  
  
 Durante el desarrollo, es posible que varios proyectos de VSPackage que se crean y registran en el subárbol del registro experimental que puede llevar a confusión desorden en el IDE. Para solucionar este problema, puede restablecer el subárbol experimental a la configuración predeterminada para quitar todos los VSPackages y los cambios que se realizaron en el IDE. Para restablecer el subárbol experimental, use la herramienta CreateExpInstance.exe que viene con el SDK de Visual Studio. Puede encontrarlo en  
  
 **% PROGRAMFILES \(x 86\) %\\Visual Studio \< versión \> SDK\\VisualStudioIntegration\\Tools\\Bin\\CreateExpInstance.exe**  
  
 Ejecutar la herramienta mediante la línea de comandos **CreateExpInstance \/Reset**. Recuerde que esta herramienta quita el subárbol experimental todos los VSPackages registrados normalmente no se instala con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Vea también  
 [Comandos y menús de extensión](../../extensibility/extending-menus-and-commands.md)