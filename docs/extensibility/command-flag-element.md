---
title: Elemento de marca de comandos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 036b9658957b76b62e3a9b44b59e07700f276a32
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="command-flag-element"></a>Elemento de marcador de comando
Modifica su elemento primario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En la siguiente sección se describe los valores de elemento válido.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Valor|Descripción|  
|-----------|-----------------|  
|AllowParams|Indica que los usuarios pueden especificar parámetros de comando en el **comando** ventana cuando escribe el nombre canónico del comando.<br /><br /> Válido para: `Button`|  
|AlwaysCreate|Menú se crea aunque no tiene botones ni grupos.<br /><br /> Válido para: `Menu`|  
|CaseSensitive|Usuario distinguen entre mayúsculas y minúsculas.<br /><br /> Válido para: `Combo`|  
|CommandWellOnly|Esta marca se aplica si el comando no aparece en el menú de nivel superior y desea que esté disponible para la personalización de shell adicionales, por ejemplo, para enlazar a un método abreviado de teclado. Después de instala el paquete VSPackage, puede personalizar estos comandos abriendo el **opciones** cuadro de diálogo y, a continuación, editar la ubicación de comando en el **teclado entorno** categoría. Esta marca no afectan a la posición en los menús contextuales, barras de herramientas, controladores de menús o submenús.<br /><br /> Válido para: `Button`, `Combo`|  
|DefaultDisabled|De forma predeterminada, el comando está deshabilitado si no se ha cargado el VSPackage que lo implemente o `QueryStatus` no se ha llamado al método.<br /><br /> Válido para: `Button`, `Combo`|  
|DefaultDocked|Acoplado de forma predeterminada. Esta configuración ya no se aplica a las barras de herramientas ya que siempre están acoplados.|  
|DefaultInvisible|De forma predeterminada, el comando es invisible si no se ha cargado el VSPackage que lo implemente o `QueryStatus` no se ha llamado al método.<br /><br /> Se recomienda combinar con la `DynamicVisibility` marca.<br /><br /> Válido para: `Button`, `Combo`, `Menu`|  
|DontCache|El entorno de desarrollo no almacena en caché el `QueryStatus` resultados del método para este comando.<br /><br /> Para un menú, esto indica un controlador de menú no almacenar en caché el texto de sus elementos de menú. Use esta marca cuando el menú contiene elementos dinámicos o los elementos que tengan texto dinámico.<br /><br /> Válido para: `Button`, `Menu`|  
|DynamicItemStart|Indica el principio de una lista dinámica. Esto permite que el entorno compilar una lista llamando sucesivamente los `QueryStatus` método en elementos de la lista hasta que se devuelva la marca OLECMDERR_E_UNSUPPORTED. Esto funciona bien para elementos como usados más recientemente (MRU) listas y listas de ventanas.<br /><br /> Válido para: `Button`|  
|DynamicVisibility|Se puede cambiar la visibilidad del comando a través de la `QueryStatus` método o a través de un contexto de GUID que se incluye en la `VisibilityConstraints` sección.<br /><br /> Se aplica a los comandos que aparecen en los menús y barras de herramientas de ventana de herramienta, pero no en barras de herramientas de nivel superior que aparecen en la ventana principal. Elementos de nivel superior de la barra de herramientas se pueden deshabilitar pero no ocultos, cuando se devuelve la marca OLECMDF_INVISIBLE desde el `QueryStatus` método. Se pueden ocultar comandos de barra de herramientas que aparecen en las barras de herramientas de ventana de herramienta.<br /><br /> En un menú, esta marca indica también que debería automáticamente ocultarse cuando se ocultan todos sus miembros. Esta marca se asigna normalmente a submenús ya menús de nivel superior ya cuentan con este comportamiento.<br /><br /> Esta marca se debe combinar con el `DefaultInvisible` marca.<br /><br /> Válido para: `Button`, `Combo`, `Menu`|  
|FilterKeys|Vea el tema de las claves de filtrado en [elemento combinado](../extensibility/combo-element.md).<br /><br /> Válido para: `Combo`|  
|FixMenuController|Si este comando está situado en un controlador de menú, el comando siempre es el valor predeterminado; es decir, el comando está activado cuando se selecciona el propio botón de controlador de menú. Si el controlador de menú tiene la `TextIsAnchorCommand` marcador establecido, a continuación, el controlador de menú también toma el texto del comando que tiene el `FixMenuController` marca.<br /><br /> Debe tener un único comando en un controlador de menú el `FixMenuController` marca. Si más de un comando por lo que está marcado, el último comando en el menú se convierte en el comando predeterminado.<br /><br /> Válido para: `Button`|  
|IconAndText|Mostrar un icono y texto en el menú y barra de herramientas.<br /><br /> Válido para: `Button`, `Combo`, `Menu`|  
|NoAutoComplete|Característica Autocompletar está deshabilitada.<br /><br /> Válido para: `Combo`|  
|NoButtonCustomize|No permiten al usuario personalizar este botón.<br /><br /> Válido para: `Button`, `Combo`|  
|NoKeyCustomize|No se debe habilitar la personalización del teclado.<br /><br /> Válido para: `Button`, `Combo`|  
|NoShowOnMenuController|Si este comando está situado en un controlador de menú, el comando no aparece en la lista desplegable.<br /><br /> Válido para: `Button`|  
|NotInTBList|No aparece en la lista de barras de herramientas disponibles. Esto solo es válida para los tipos de menú de barra de herramientas.<br /><br /> Válido para: `Menu`|  
|NoToolbarClose|Usuario no puede cerrar la barra de herramientas. Esto solo es válida para los tipos de menú de barra de herramientas.<br /><br /> Válido para: `Menu`|  
|PICT|Mostrar sólo aparecerá un icono en una barra de herramientas, pero únicamente el texto de un menú. Si no se especifica ningún icono, muestra un espacio en blanco donde hacer clic en una barra de herramientas.<br /><br /> Válido para: `Button`|  
|PostExec|Hace que el comando sin bloqueo. El entorno de desarrollo aplaza la ejecución hasta que se completen todas las consultas previas al procesamiento.<br /><br /> Válido para: `Button`|  
|RouteToDocs|El comando se enruta al documento activo.<br /><br /> Válido para: `Button`|  
|StretchHorizontally|Cuando se establece esta marca, el ancho se convierte en el ancho mínimo del cuadro combinado y, si hay espacio en la barra de herramientas, el cuadro combinado se expande para rellenar el espacio disponible. Esto sucede únicamente si la barra de herramientas está acoplado horizontalmente, y solo un cuadro combinado en la barra de herramientas puede utilizar la marca (la marca se omite en todas excepto en el primer cuadro combinado).<br /><br /> Válido para: `Combo`|  
|TextMenuUseButton|Use la `ButtonText` campo en los menús. El campo de valor predeterminado es `MenuText` si se ha especificado.<br /><br /> Válido para: `Button`|  
|TextoCambia|El texto de menú o comando puede cambiar en tiempo de ejecución, normalmente a través de la `QueryStatus` método.<br /><br /> Válido para: `Button`, `Menu`|  
|TextChangesButton|Válido para: `Button`|  
|TextIsAnchorCommand|Para un controlador de menú, el texto del menú se toma desde el comando predeterminado (delimitador). Un comando de delimitador es el último comando selecciona o se establece. Si no se establece esta marca, el controlador de menú utiliza su propio `MenuText` campo. Sin embargo, al hacer clic en el controlador de menú permite todavía el último comando seleccionado en ese controlador.<br /><br /> Se recomienda que combinar esta marca con la `TextChanges` marca.<br /><br /> Esta marca solo aplica a los menús de tipo MenuController o MenuControllerLatched.<br /><br /> Válido para: `Menu`|  
|TextMenuCtrlUseMenu|Use la `MenuText` campo en los controladores de menú. El campo de valor predeterminado es `ButtonText`.<br /><br /> Válido para: `Button`|  
|TextMenuUseButton|Use la `ButtonText` campo en los menús. El campo de valor predeterminado es `MenuText` si se ha especificado.<br /><br /> Válido para: `Button`|  
|TextOnly|Mostrar solo texto en una barra de herramientas o un menú pero ningún icono incluso si se especifica el icono.<br /><br /> Válido para: `Button`|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Buttons (Elemento)](../extensibility/buttons-element.md)|Proporciona un grupo de [elemento Button](../extensibility/button-element.md) elementos.|  
|[Menus (Elemento)](../extensibility/menus-element.md)|Define todos los menús que implementa un paquete VSPackage.|  
  
## <a name="see-also"></a>Vea también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)