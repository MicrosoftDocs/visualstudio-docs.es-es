---
title: "Elemento de indicador de comando | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elemento CommandFlag (esquema VSCT XML)"
  - "Elementos de esquema XML VSCT, CommandFlag"
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Elemento de indicador de comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Modifica su elemento primario.  
  
## Sintaxis  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## Atributos y elementos  
 La siguiente sección describe los valores de elemento válido.  
  
### Atributos  
 Ninguno.  
  
### Elementos secundarios  
  
|Valor|Descripción|  
|-----------|-----------------|  
|AllowParams|Indica que los usuarios pueden especificar parámetros de comando de la **comando** ventana cuando escribe el nombre canónico del comando.<br /><br /> Válido para: `Button`|  
|AlwaysCreate|Se crea el menú incluso si no tiene botones ni grupos.<br /><br /> Válido para: `Menu`|  
|CaseSensitive|Las entradas de usuario distinguen mayúsculas de minúsculas.<br /><br /> Válido para: `Combo`|  
|CommandWellOnly|Este indicador se aplican si el comando no aparece en el menú de nivel superior y desea que esté disponible para la personalización de shell adicionales, por ejemplo, para enlazar a un método abreviado de teclado. Después de instala el paquete VSPackage, puede personalizar estos comandos abriendo el **opciones** cuadro de diálogo y, a continuación, editar la ubicación de comando en el **entorno teclado** categoría. Esta marca no afecta a la ubicación en los menús contextuales, barras de herramientas, controladores de menús o submenús.<br /><br /> Válido para: `Button`, `Combo`|  
|DefaultDisabled|De forma predeterminada, el comando está deshabilitado si no está cargado el VSPackage que lo implementa o `QueryStatus` no se ha llamado al método.<br /><br /> Válido para: `Button`, `Combo`|  
|DefaultDocked|Acoplado de manera predeterminada. Esta configuración ya no se aplica a las barras de herramientas ya que siempre se acoplan.|  
|DefaultInvisible|De forma predeterminada, el comando es invisible si no se ha cargado el VSPackage que lo implementa o `QueryStatus` no se ha llamado al método.<br /><br /> Se recomienda combinar esto con el `DynamicVisibility` marca.<br /><br /> Válido para: `Button`, `Combo`, `Menu`|  
|DontCache|El entorno de desarrollo no almacena en caché el `QueryStatus` resultados del método para este comando.<br /><br /> Para un menú, esto indica que un controlador de menú no almacenar en caché el texto de los elementos de menú. Utilice este indicador cuando el menú contiene elementos dinámicos o los elementos que tengan texto dinámico.<br /><br /> Válido para: `Button`, `Menu`|  
|DynamicItemStart|Indica el principio de una lista dinámica. Esto permite que el entorno compilar una lista llamando sucesivamente la `QueryStatus` método en elementos de la lista hasta que se devuelva el indicador OLECMDERR\_E\_UNSUPPORTED. Esto funciona bien para elementos como usados más recientemente \(MRU\) listas y ventana.<br /><br /> Válido para: `Button`|  
|DynamicVisibility|Se puede cambiar la visibilidad del comando a través de la `QueryStatus` \(método\) o a través de un contexto de GUID que se incluye en la `VisibilityConstraints` sección.<br /><br /> Se aplica a los comandos que aparecen en los menús y barras de herramientas de ventana de herramienta, pero no en barras de herramientas de nivel superior que aparecen en la ventana principal. Elementos de nivel superior de la barra de herramientas se pueden deshabilitar pero no ocultos, cuando se devuelve la marca OLECMDF\_INVISIBLE desde el `QueryStatus` método. Se pueden ocultar comandos de barra de herramientas que aparecen en las barras de herramientas de ventana de herramienta.<br /><br /> En un menú, esta marca indica también que debería ser automáticamente oculta cuando se ocultan todos sus miembros. Este indicador normalmente se asigna a los submenús porque menús de nivel superior ya tienen este comportamiento.<br /><br /> Este indicador debe estar combinado con el `DefaultInvisible` marca.<br /><br /> Válido para: `Button`, `Combo`, `Menu`|  
|FilterKeys|Consulte el tema de filtrado de claves en [Elemento de cuadro combinado](../extensibility/combo-element.md).<br /><br /> Válido para: `Combo`|  
|FixMenuController|Si este comando está situado en un controlador de menú, el comando siempre es el valor predeterminado; es decir, se selecciona el comando cuando se selecciona el botón de controlador del menú. Si el controlador del menú tiene la `TextIsAnchorCommand` marcador establecido, el controlador del menú también toma el texto del comando que tiene el `FixMenuController` marca.<br /><br /> Debe tener un único comando en un controlador del menú la `FixMenuController` marca. Si así se marca más de un comando, el último comando en el menú se convierte en el comando predeterminado.<br /><br /> Válido para: `Button`|  
|IconAndText|Mostrar un icono y texto en el menú y barra de herramientas.<br /><br /> Válido para: `Button`, `Combo`, `Menu`|  
|NoAutoComplete|Característica Autocompletar está deshabilitada.<br /><br /> Válido para: `Combo`|  
|NoButtonCustomize|No deje que el usuario personalice este botón.<br /><br /> Válido para: `Button`, `Combo`|  
|NoKeyCustomize|No habilite la personalización del teclado.<br /><br /> Válido para: `Button`, `Combo`|  
|NoShowOnMenuController|Si este comando está situado en un controlador de menú, el comando no aparece en la lista desplegable.<br /><br /> Válido para: `Button`|  
|NotInTBList|No aparece en la lista de barras de herramientas disponibles. Esto sólo es válido para tipos de menús de la barra de herramientas.<br /><br /> Válido para: `Menu`|  
|NoToolbarClose|Usuario no puede cerrar la barra de herramientas. Esto sólo es válido para tipos de menús de la barra de herramientas.<br /><br /> Válido para: `Menu`|  
|PICT|Mostrar sólo aparecerá un icono en una barra de herramientas, pero únicamente el texto de un menú. Si no se especifica ningún icono, muestra un espacio en blanco donde hacer clic en una barra de herramientas.<br /><br /> Válido para: `Button`|  
|PostExec|Hace que el comando sin bloqueo. El entorno de desarrollo aplaza la ejecución hasta que se completen todas las consultas de procesamiento previo.<br /><br /> Válido para: `Button`|  
|RouteToDocs|El comando se enruta al documento activo.<br /><br /> Válido para: `Button`|  
|StretchHorizontally|Cuando se establece este marcador, el ancho es el ancho mínimo del cuadro combinado y si hay espacio en la barra de herramientas, el cuadro combinado se expande para rellenar el espacio disponible. Esto sólo ocurre si la barra de herramientas está acoplado horizontalmente y sólo un cuadro combinado en la barra de herramientas puede usar la marca \(se omite la marca en todo excepto el primer cuadro combinado\).<br /><br /> Válido para: `Combo`|  
|TextMenuUseButton|Utilice la `ButtonText` campo para los menús. El campo de forma predeterminada es `MenuText` Si se ha especificado.<br /><br /> Válido para: `Button`|  
|TextoCambia|El texto de comando o menú puede cambiarse en tiempo de ejecución, normalmente a través de la `QueryStatus` \(método\).<br /><br /> Válido para: `Button`, `Menu`|  
|TextChangesButton|Válido para: `Button`|  
|TextIsAnchorCommand|Para un controlador de menú, el texto del menú se toma del comando predeterminado \(delimitador\). Un comando de delimitador es el último comando seleccionado o bloqueado. Si no se establece este marcador, el controlador de menú usa su propio `MenuText` campo. Sin embargo, al hacer clic en el controlador de menú permite el último comando seleccionado desde ese controlador.<br /><br /> Se recomienda combinar este indicador con el `TextChanges` marca.<br /><br /> Esta marca sólo aplica a los menús de tipo MenuController o MenuControllerLatched.<br /><br /> Válido para: `Menu`|  
|TextMenuCtrlUseMenu|Utilice la `MenuText` campo en los controladores de menú. El campo predeterminado es `ButtonText`.<br /><br /> Válido para: `Button`|  
|TextMenuUseButton|Utilice la `ButtonText` campo para los menús. El campo de forma predeterminada es `MenuText` Si se ha especificado.<br /><br /> Válido para: `Button`|  
|TextOnly|Mostrar solo texto en una barra de herramientas o un menú, pero no hay ningún icono, incluso si se especifica el icono.<br /><br /> Válido para: `Button`|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Elemento de botones](../extensibility/buttons-element.md)|Proporciona un grupo de [Elemento Button](../extensibility/button-element.md) elementos.|  
|[Elemento de menús](../extensibility/menus-element.md)|Define todos los menús que implementa un VSPackage.|  
  
## Vea también  
 [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)