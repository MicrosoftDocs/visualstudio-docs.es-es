---
title: "Diseñar la tabla de comandos XML (. Archivos Vsct) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e007ffe8cf3cc893bc9575a3e7c083090b523467
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="designing-xml-command-table-vsct-files"></a>Diseñar la tabla de comandos XML (. Archivos Vsct)
Un archivo de tabla (.vsct) del comando XML describe el diseño y la apariencia de los elementos de comando para un VSPackage. Elementos de comando incluyen botones, cuadros combinados, los menús, barras de herramientas y grupos de elementos de comando. Este tema describe cómo crearlos, cómo afectan a los menús y elementos de comandos y archivos de la tabla de comandos XML.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>Comandos, menús, grupos y el archivo .vsct  
 archivos de vsct se organizan en grupos de comandos, menús y comandos. Etiquetas XML en el archivo .vsct representan cada uno de estos elementos, junto con otros elementos asociados, como botones de comando y ubicación del comando, los mapas de bits.  
  
 Cuando se crea un nuevo paquete de VS mediante la ejecución de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] plantilla de paquete, la plantilla genera un archivo .vsct con los elementos necesarios para un comando de menú, la ventana de herramientas o el editor personalizado, dependiendo de las selecciones. Este archivo .vsct, a continuación, se puede modificar para cumplir los requisitos de un VSPackage específico. Para obtener ejemplos de cómo modificar un archivo .vsct, vea los ejemplos de [extender menús y comandos de](../../extensibility/extending-menus-and-commands.md).  
  
 Para crear un archivo .vsct en blanco, vea [Cómo: crear una. Archivo de Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Una vez creado, agregue elementos, atributos y valores XML en el archivo para describir el diseño de elemento de comando. Para un esquema XML detallado, consulte el [referencia de esquemas XML de VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>Diferencias entre los archivos .ctc y .vsct  
 Aunque el significado a las etiquetas XML en un archivo .vsct es los mismos, como los de ahora obsoleto formato de archivo .ctc, su implementación es un poco diferente.  
  
-   El nuevo  **\<extern >** etiqueta es donde se hacen referencia a otros archivos .h de compilación, como los relativos a la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] barra de herramientas.  
  
-   Al soporte técnico de archivos de vsct el **/ include** (instrucción), igual que los archivos de .ctc, también presenta una nueva característica \< **Importar >** elemento. La diferencia es que **/ include** aporta en **todos los** de la información, pero \< **Importar >** aporta en solo los nombres.  
  
-   Mientras que los archivos de .ctc requieren un archivo de encabezado en el que se definen las directivas de preprocesador, uno que no es necesario para los archivos de vsct. En su lugar, coloque las directivas en la tabla de símbolos, que se encuentra en la  **\<símbolo >** elementos, situados en la parte inferior del archivo vsct.  
  
-   característica de archivos de vsct una  **\<anotación >** etiqueta, que le permite incrustar toda la información que desee, como notas o incluso imágenes.  
  
-   Los valores se almacenan como atributos en el elemento.  
  
-   Marcadores de comando se pueda almacenar individualmente o apiladas.  IntelliSense, sin embargo, no funciona en los marcadores de comando apiladas. Para obtener más información acerca de las marcas de comando, consulte el [comando marca elemento](../../extensibility/command-flag-element.md).  
  
-   Puede especificar varios tipos, como listas desplegables de división, combinaciones, etcetera.  
  
-   GUID no están disponibles.  
  
-   Cada elemento de interfaz de usuario tiene una cadena que representa el texto que se muestra con él.  
  
-   Elemento primario es opcional. Si se omite, se utiliza el valor "Grupo desconocido".  
  
-   El argumento de icono es opcional.  
  
-   Los archivos de la sección de mapa de bits, el mismo que un .ctc, salvo que ahora puede especificar un nombre de archivo a través de href que se van a extraer el compilador vsct.exe en tiempo de compilación.  
  
-   ResID--el identificador de recurso antiguo de mapa de bits se puede utilizar y sigue funcionando del mismo como en archivos de .ctc.  
  
-   HRef--un nuevo método que le permite especificar un nombre de archivo para el recurso de mapa de bits. Se supone que todas se utilizan, por lo que puede omitir la sección que se usa. El compilador buscará primero los recursos locales para el archivo, a continuación, en los recursos compartidos de redes y los recursos definidos por el modificador/i.  
  
-   KeyBinding--Ya no es necesario especificar un emulador. Si especifica uno, el compilador supondrá que el editor y el emulador son los mismos.  
  
-   Keychord: se ha quitado. El nuevo formato es Key1, Mod1, clave2, Mod2.  Puede especificar un carácter, hexadecimal o constante VK.  
  
 El nuevo compilador, vsct.exe, compila los archivos .ctc y vsct. El compilador ctc.exe antiguo, sin embargo, se reconoce ni compilar archivos de vsct.  
  
 Puede usar el compilador vsct.exe para convertir un archivo .cto existente en un archivo .vsct. Para obtener más información sobre esto, vea [Cómo: crear una. Archivo de Vsct desde una existente. Archivo de director de tecnología](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).  
  
## <a name="the-vsct-file-elements"></a>Los elementos del archivo .vsct  
 La tabla de comandos tiene la jerarquía y los elementos siguientes:  
  
 [Elemento CommandTable](../../extensibility/commandtable-element.md) : representa todos los comandos, grupos de menús y menús asociados con el VSPackage.  
  
 [Elemento extern](../../extensibility/extern-element.md) : hace referencia a los archivos .h externos que desea combinar con el archivo .vsct.  
  
 [Incluir elemento](../../extensibility/include-element.md) : hace referencia a los archivos de encabezado adicional (. h) que desea compilar junto con el archivo your.vsct. Un archivo .vsct puede incluir archivos .h que contienen constantes que definen los comandos, grupos de menús y menús que proporciona el IDE o en otro VSPackage.  
  
 [Comandos de elemento](../../extensibility/commands-element.md) : representa todos los comandos individuales que se pueden ejecutar. Cada comando tiene los siguientes cuatro elementos secundarios:  
  
 [Elemento menús](../../extensibility/menus-element.md) : representa todos los menús y barras de herramientas en el VSPackage. Los menús son contenedores para los grupos de comandos.  
  
 [Elemento Groups](../../extensibility/groups-element.md) : representa todos los grupos en el VSPackage. Los grupos son colecciones de comandos individuales.  
  
 [Botones elemento](../../extensibility/buttons-element.md) : representa todos los botones de comando y los elementos de menú en el VSPackage. Botones son controles visuales que pueden asociarse con comandos.  
  
 [Elemento de mapas de bits](../../extensibility/bitmaps-element.md) : representa todos los mapas de bits para todos los botones en el VSPackage. Mapas de bits son imágenes que se muestran junto a o en los botones de comando, dependiendo del contexto.  
  
 [Elemento CommandPlacements](../../extensibility/commandplacements-element.md) : indica más ubicaciones donde los comandos individuales deben estar ubicados en los menús del paquete de VS.  
  
 [Elemento VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) : Especifica si un comando en todos los muestra horas o sólo en algunos contextos, como cuando se muestra un cuadro de diálogo determinado o una ventana. Menús y comandos que tienen un valor para este elemento se mostrará únicamente cuando el contexto especificado está activo. El comportamiento predeterminado consiste en Mostrar el comando en todo momento.  
  
 [Elemento de enlaces de teclado](../../extensibility/keybindings-element.md) : especifica los enlaces de teclado para los comandos. Es decir, una o varias combinaciones de teclas que deben presionar para ejecutar el comando, como **CTRL+S**.  
  
 [Elemento UsedCommands](../../extensibility/usedcommands-element.md) : informa la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno que, aunque el comando especificado se implementa por otro código, cuando el VSPackage actual está activo, proporciona la implementación de comandos.  
  
 `Symbols Element`: Contiene los nombres de símbolos e identificadores de GUID para todos los comandos en el paquete.  
  
## <a name="vsct-file-design-guidelines"></a>. Instrucciones de diseño del archivo de Vsct  
 Para diseñar correctamente un archivo .vsct, siga estas instrucciones.  
  
-   Comandos pueden colocarse únicamente en grupos, grupos se pueden colocar solo en los menús y menús pueden colocarse únicamente en grupos. Sólo los menús realmente se muestran en el IDE, grupos y comandos no están.  
  
-   Submenús no se puede asignar directamente a un menú, pero deben asignarse a un grupo, que a su vez está asignado a un menú.  
  
-   Comandos, submenús y grupos pueden asignarse a un grupo de relación jerárquica o menú mediante el campo primario de la directiva de su definición.  
  
-   Una tabla de comandos únicamente a través de los campos de elemento primario en las directivas de la organización tiene una limitación importante. Las directivas que definen objetos pueden aceptar el argumento de un único elemento primario.  
  
-   Volver a usar los comandos, grupos o submenús requiere el uso de una directiva nueva para crear una nueva instancia del objeto con su propio `GUID:ID` par.  
  
-   Cada `GUID:ID` par debe ser único. Volver a usar un comando que tiene, por ejemplo, se han colocado en un menú, una barra de herramientas, o en un menú contextual, se controla mediante el <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaz.  
  
-   Comandos y submenús también pueden asignarse a varios grupos y grupos pueden asignarse a varios menús mediante la [Commands, elemento](../../extensibility/commands-element.md).  
  
## <a name="vsct-file-notes"></a>. Notas de archivo de Vsct  
 Si realiza cambios en un archivo .vsct después de que lo compilará y lo coloca en un archivo DLL satélite nativo, debe ejecutar **devenv.exe /setup /nosetupvstemplates**. Esto obliga a los recursos de VSPackage especificados en el registro experimental a leer y la base de datos interna que describe [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se vuelvan a generar.  
  
 Durante el desarrollo, es posible que varios proyectos de VSPackage que se creen y se registra en el subárbol del registro experimental que puede dar lugar a confuso desorden en el IDE. Para solucionar este problema, puede restablecer el subárbol experimental a la configuración predeterminada para quitar todos los VSPackages y los cambios que se realizaron en el IDE. Para restablecer el subárbol experimental, use la herramienta CreateExpInstance.exe que se incluye con el SDK de Visual Studio. Puede encontrarlo en  
  
 **% PROGRAMFILES (x 86) %\Visual Studio \<versión > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Ejecute la herramienta mediante la línea de comandos **CreateExpInstance /Reset**. Recuerde que esta herramienta quita el subárbol experimental todos los VSPackages registrados normalmente no se instala con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Ampliación de menús y comandos](../../extensibility/extending-menus-and-commands.md)