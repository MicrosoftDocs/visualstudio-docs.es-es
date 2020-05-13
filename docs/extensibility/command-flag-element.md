---
title: Elemento de la bandera de comandos (Command Flag Element) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84138a69dbb42fc349c12276fd7cca4b593e4d47
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649363"
---
# <a name="command-flag-eelement"></a>Bandera de mando Eelement
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

|Valor|Descripción|
|-----------|-----------------|
|AllowParams|Indica que los usuarios pueden introducir parámetros de comando en la ventana **Comando** cuando escriben el nombre canónico del comando.<br /><br /> Válido para:`Button`|
|AlwaysCreate|El menú se crea incluso si no tiene grupos ni botones.<br /><br /> Válido para:`Menu`|
|CaseSensitive|Las entradas de usuario distinguen mayúsculas de minúsculas.<br /><br /> Válido para:`Combo`|
|CommandWellOnly|Aplique esta marca si el comando no aparece en el menú de nivel superior y desea que esté disponible para la personalización de shell adicional, por ejemplo, para enlazarlo a un método abreviado de teclado. Después de instalar el VSPackage, puede personalizar estos comandos abriendo el cuadro de diálogo **Opciones** y, a continuación, editando la ubicación del comando en la categoría Entorno de **teclado.** Esta marca no afecta a la colocación en menús contextuales, barras de herramientas, controladores de menú o submenús.<br /><br /> Válido para: `Button`,`Combo`|
|DefaultDisabled|De forma predeterminada, el comando está deshabilitado si el VSPackage que lo implementa no está cargado o no se ha llamado al `QueryStatus` método.<br /><br /> Válido para: `Button`,`Combo`|
|DefaultDocked|Acoplado de forma predeterminada. Esta configuración ya no se aplica a las barras de herramientas porque siempre están acopladas.|
|DefaultInvisible|De forma predeterminada, el comando es invisible si el VSPackage que lo implementa no está cargado o no se ha llamado al `QueryStatus` método.<br /><br /> Le recomendamos que combine `DynamicVisibility` esto con la bandera.<br /><br /> Válido `Button`para: `Combo`, ,`Menu`|
|DontCache|El entorno de desarrollo `QueryStatus` no almacena en caché los resultados del método para este comando.<br /><br /> Para un menú, esto indica a un controlador de menú que no almacene en caché el texto de sus elementos de menú. Utilice esta marca cuando el menú contenga elementos dinámicos o elementos que tengan texto dinámico.<br /><br /> Válido para: `Button`,`Menu`|
|DynamicItemStart|Indica el comienzo de una lista dinámica. Esto permite al entorno crear una lista `QueryStatus` llamando sucesivamente al método en los elementos de lista hasta que se devuelve la marca OLECMDERR_E_UNSUPPORTED. Esto funciona bien para elementos como las listas y listas de ventanas utilizadas más recientemente (MRU).<br /><br /> Válido para:`Button`|
|DinámicaVisibilidad|La visibilidad del comando se `QueryStatus` puede cambiar a través del `VisibilityConstraints` método o a través de un GUID de contexto que se incluye en la sección.<br /><br /> Se aplica a los comandos que aparecen en los menús y las barras de herramientas de la ventana de herramientas, pero no en las barras de herramientas de nivel superior que aparecen en la ventana principal. Los elementos de la barra de herramientas de nivel superior `QueryStatus` se pueden deshabilitar pero no ocultar cuando se devuelve la marca OLECMDF_INVISIBLE desde el método. Los comandos de la barra de herramientas que aparecen en las barras de herramientas de la ventana de herramientas se pueden ocultar.<br /><br /> En un menú, esta marca también indica que debe ocultarse automáticamente cuando todos sus miembros están ocultos. Esta marca se asigna normalmente a los submenús porque los menús de nivel superior ya tienen este comportamiento.<br /><br /> Esta marca debe combinarse con la `DefaultInvisible` bandera.<br /><br /> Válido `Button`para: `Combo`, ,`Menu`|
|Filterkeys|Consulte el tema Claves de filtrado en [Elemento combinado](../extensibility/combo-element.md).<br /><br /> Válido para:`Combo`|
|FixMenuController|Si este comando se coloca en un controlador de menú, el comando siempre es el predeterminado; es decir, el comando se selecciona cada vez que se selecciona el propio botón del controlador de menú. Si el controlador `TextIsAnchorCommand` de menú tiene el indicador establecido, el controlador `FixMenuController` de menú también toma su texto del comando que tiene la marca.<br /><br /> Solo un comando en un `FixMenuController` controlador de menú debe tener la marca. Si más de un comando está marcado así, el último comando del menú se convierte en el comando predeterminado.<br /><br /> Válido para:`Button`|
|IconAndText|Mostrar un icono y texto en el menú y la barra de herramientas.<br /><br /> Válido `Button`para: `Combo`, ,`Menu`|
|NoAutoComplete|La función de autocompletar está deshabilitada.<br /><br /> Válido para:`Combo`|
|NoButtonCustomize|No permita que el usuario personalice este botón.<br /><br /> Válido para: `Button`,`Combo`|
|NoKeyCustomize|No habilite la personalización del teclado.<br /><br /> Válido para: `Button`,`Combo`|
|NoShowOnMenuController|Si este comando se coloca en un controlador de menú, el comando no aparece en la lista desplegable.<br /><br /> Válido para:`Button`|
|NotInTBList|No aparece en la lista de barras de herramientas disponibles. Esto solo es válido para los tipos de menú de la barra de herramientas.<br /><br /> Válido para:`Menu`|
|NoToolbarClose|El usuario no puede cerrar la barra de herramientas. Esto solo es válido para los tipos de menú de la barra de herramientas.<br /><br /> Válido para:`Menu`|
|Pict|Mostrar solo un icono en una barra de herramientas, pero solo texto en un menú. Si no se especifica ningún icono, muestra un espacio en blanco en el que se puede hacer clic en una barra de herramientas.<br /><br /> Válido para:`Button`|
|PostExec|Hace que el comando no se bloquee. El entorno de desarrollo aplaza la ejecución hasta que se completan todas las consultas de preprocesamiento.<br /><br /> Válido para:`Button`|
|RouteToDocs|El comando se enruta al documento activo.<br /><br /> Válido para:`Button`|
|StretchHorizontally|Cuando se establece esta marca, el ancho se convierte en el ancho mínimo para el cuadro combinado y, si hay espacio en la barra de herramientas, el cuadro combinado se estira para rellenar el espacio disponible. Esto solo se produce si la barra de herramientas está acoplada horizontalmente y solo un cuadro combinado de la barra de herramientas puede utilizar la marca (la marca se omite en todos excepto en el primer cuadro combinado).<br /><br /> Válido para:`Combo`|
|TextChanges|El texto del comando o menú se puede `QueryStatus` cambiar en tiempo de ejecución, normalmente a través del método.<br /><br /> Válido para: `Button`,`Menu`|
|TextChangesButton|Válido para:`Button`|
|TextIsAnchorCommand|Para un controlador de menú, el texto del menú se toma del comando predeterminado (ancla). Un comando de anclaje es el último comando seleccionado o bloqueado. Si no se establece esta marca, `MenuText` el controlador de menú utiliza su propio campo. Sin embargo, al hacer clic en el controlador de menú todavía se habilita el último comando seleccionado de ese controlador.<br /><br /> Se recomienda combinar esta marca `TextChanges` con la marca.<br /><br /> Esta marca solo se aplica a los menús de tipo MenuController o MenuControllerLatched.<br /><br /> Válido para:`Menu`|
|TextMenuCtrlUseMenu|Utilice `MenuText` el campo de los controladores de menú. El campo `ButtonText`predeterminado es .<br /><br /> Válido para:`Button`|
|TextMenuUseButton|Utilice `ButtonText` el campo para los menús. El campo `MenuText` predeterminado es si se especifica.<br /><br /> Válido para:`Button`|
|TextOnly|Mostrar solo texto en una barra de herramientas o en un menú, pero sin icono, incluso si se especifica el icono.<br /><br /> Válido para:`Button`|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Buttons](../extensibility/buttons-element.md)|Proporciona un grupo para Button elementos de [elemento.](../extensibility/button-element.md)|
|[Elemento Menús](../extensibility/menus-element.md)|Define todos los menús que implementa un VSPackage.|

## <a name="see-also"></a>Consulte también
- [Tabla de comandos de Visual Studio (. Vsct) Archivos](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
