---
title: Elemento de marca de comando | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39b2377dd1599d58eac4ca967ca540d8ce0e6847
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184363"
---
# <a name="command-flag-element"></a>Command Flag (Elemento)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modifica su elemento primario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En la siguiente sección se describen los valores de elemento válidos.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Value|Descripción|  
|-----------|-----------------|  
|AllowParams|Indica que los usuarios pueden escribir parámetros de comando en la ventana de **comandos** cuando escriben el nombre canónico del comando.<br /><br /> Válido para: `Button`|  
|AlwaysCreate|El menú se crea incluso si no tiene grupos o botones.<br /><br /> Válido para: `Menu`|  
|CaseSensitive|Las entradas de usuario distinguen mayúsculas de minúsculas.<br /><br /> Válido para: `Combo`|  
|CommandWellOnly|Aplique esta marca si el comando no aparece en el menú de nivel superior y desea que esté disponible para la personalización de Shell adicional, por ejemplo, para enlazarlo a un método abreviado de teclado. Una vez instalado el VSPackage, puede personalizar estos comandos; para ello, abra el cuadro de diálogo **Opciones** y, a continuación, edite la ubicación del comando en la categoría **entorno del teclado** . Esta marca no afecta a la colocación en menús contextuales, barras de herramientas, controladores de menú ni submenús.<br /><br /> Válido para: `Button` , `Combo`|  
|DefaultDisabled|De forma predeterminada, el comando se deshabilita si el VSPackage que lo implementa no se carga o no se ha `QueryStatus` llamado al método.<br /><br /> Válido para: `Button` , `Combo`|  
|DefaultDocked|Acoplado de forma predeterminada. Esta configuración ya no se aplica a las barras de herramientas porque siempre están acopladas.|  
|DefaultInvisible|De forma predeterminada, el comando es invisible si el VSPackage que lo implementa no está cargado o no se ha `QueryStatus` llamado al método.<br /><br /> Se recomienda combinar esto con la `DynamicVisibility` marca.<br /><br /> Válido para: `Button` , `Combo` , `Menu`|  
|DontCache|El entorno de desarrollo no almacena en caché los `QueryStatus` resultados del método para este comando.<br /><br /> En un menú, indica a un controlador de menú que no almacene en caché el texto de sus elementos de menú. Use esta marca cuando el menú contenga elementos dinámicos o elementos que tengan texto dinámico.<br /><br /> Válido para: `Button` , `Menu`|  
|DynamicItemStart|Indica el principio de una lista dinámica. Esto permite que el entorno cree una lista mediante una llamada sucesiva al `QueryStatus` método en los elementos de lista hasta que se devuelva la marca OLECMDERR_E_UNSUPPORTED. Esto funciona bien con elementos como listas de ventanas y listas usadas recientemente (MRU).<br /><br /> Válido para: `Button`|  
|DynamicVisibility|La visibilidad del comando se puede cambiar mediante el `QueryStatus` método o a través de un GUID de contexto que se incluye en la `VisibilityConstraints` sección.<br /><br /> Se aplica a los comandos que aparecen en los menús y las barras de herramientas de la ventana de herramientas, pero no en las barras de herramientas de nivel superior que aparecen en la ventana principal. Los elementos de la barra de herramientas de nivel superior se pueden deshabilitar, pero no ocultar, cuando el método devuelve la marca de OLECMDF_INVISIBLE `QueryStatus` . Los comandos de la barra de herramientas que aparecen en las barras de herramientas de la ventana de herramientas se pueden ocultar.<br /><br /> En un menú, esta marca también indica que se debe ocultar automáticamente cuando todos sus miembros están ocultos. Esta marca normalmente se asigna a submenús, ya que los menús de nivel superior ya tienen este comportamiento.<br /><br /> Esta marca debe combinarse con la `DefaultInvisible` marca.<br /><br /> Válido para: `Button` , `Combo` , `Menu`|  
|Activar|Vea el tema filtrar claves en [elemento combinado](../extensibility/combo-element.md).<br /><br /> Válido para: `Combo`|  
|FixMenuController|Si este comando se coloca en un controlador de menú, el comando siempre es el valor predeterminado; es decir, el comando se selecciona cada vez que se selecciona el botón del controlador de menús. Si el controlador de menú tiene la `TextIsAnchorCommand` marca establecida, el controlador de menú también toma el texto del comando que tiene la `FixMenuController` marca.<br /><br /> Solo un comando en un controlador de menú debe tener la `FixMenuController` marca. Si se marca más de un comando, el último comando del menú se convierte en el comando predeterminado.<br /><br /> Válido para: `Button`|  
|IconAndText|Mostrar un icono y texto en el menú y la barra de herramientas.<br /><br /> Válido para: `Button` , `Combo` , `Menu`|  
|NoAutoComplete|La característica Autocompletar está deshabilitada.<br /><br /> Válido para: `Combo`|  
|NoButtonCustomize|No permita que el usuario Personalice este botón.<br /><br /> Válido para: `Button` , `Combo`|  
|NoKeyCustomize|No habilite la personalización del teclado.<br /><br /> Válido para: `Button` , `Combo`|  
|NoShowOnMenuController|Si este comando se coloca en un controlador de menú, el comando no aparece en la lista desplegable.<br /><br /> Válido para: `Button`|  
|NotInTBList|No aparece en la lista de barras de herramientas disponibles. Esto solo es válido para los tipos de menús de la barra de herramientas.<br /><br /> Válido para: `Menu`|  
|NoToolbarClose|El usuario no puede cerrar la barra de herramientas. Esto solo es válido para los tipos de menús de la barra de herramientas.<br /><br /> Válido para: `Menu`|  
|PICT|Mostrar solo un icono en una barra de herramientas, pero solo texto en un menú. Si no se especifica ningún icono, se muestra un espacio en blanco en una barra de herramientas.<br /><br /> Válido para: `Button`|  
|Postexec|Hace que el comando no sea de bloqueo. El entorno de desarrollo pospone la ejecución hasta que se completen todas las consultas de procesamiento previo.<br /><br /> Válido para: `Button`|  
|RouteToDocs|El comando se enruta al documento activo.<br /><br /> Válido para: `Button`|  
|StretchHorizontally|Cuando se establece esta marca, el ancho se convierte en el ancho mínimo del cuadro combinado y, si hay espacio en la barra de herramientas, el cuadro combinado se expande para rellenar el espacio disponible. Esto solo se produce si la barra de herramientas está acoplada horizontalmente y solo un cuadro combinado de la barra de herramientas puede utilizar la marca (la marca se omite en todo excepto en el primer cuadro combinado).<br /><br /> Válido para: `Combo`|  
|TextMenuUseButton|Use el `ButtonText` campo para los menús. El campo predeterminado es `MenuText` si se especifica.<br /><br /> Válido para: `Button`|  
|Textchanges al|El texto del comando o del menú se puede cambiar en tiempo de ejecución, normalmente a través del `QueryStatus` método.<br /><br /> Válido para: `Button` , `Menu`|  
|TextChangesButton|Válido para: `Button`|  
|TextIsAnchorCommand|En el caso de un controlador de menú, el texto del menú se toma del comando predeterminado (delimitador). Un comando de delimitador es el último comando seleccionado o bloqueado. Si no se establece esta marca, el controlador de menú utiliza su propio `MenuText` campo. Sin embargo, al hacer clic en el controlador de menú todavía se habilita el último comando seleccionado en ese controlador.<br /><br /> Se recomienda combinar esta marca con la `TextChanges` marca.<br /><br /> Esta marca solo se aplica a los menús de tipo MenuController o MenuControllerLatched.<br /><br /> Válido para: `Menu`|  
|TextMenuCtrlUseMenu|Use el `MenuText` campo en los controladores de menús. El campo predeterminado es `ButtonText` .<br /><br /> Válido para: `Button`|  
|TextMenuUseButton|Use el `ButtonText` campo para los menús. El campo predeterminado es `MenuText` si se especifica.<br /><br /> Válido para: `Button`|  
|TextOnly|Mostrar solo el texto de una barra de herramientas o un menú, pero sin icono aunque se especifique el icono.<br /><br /> Válido para: `Button`|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Buttons (Elemento)](../extensibility/buttons-element.md)|Proporciona un grupo para los elementos de [elemento de botón](../extensibility/button-element.md) .|  
|[Menus (Elemento)](../extensibility/menus-element.md)|Define todos los menús que implementa un VSPackage.|  
  
## <a name="see-also"></a>Consulte también  
 [Archivos de tabla de comandos de Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
