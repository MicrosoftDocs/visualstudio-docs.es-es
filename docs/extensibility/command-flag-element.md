---
title: Command Flag (elemento) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea9ba8d42bbc008ecb4664ec167ba60ba4018fc6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62891370"
---
# <a name="command-flag-eelement"></a>Indicador de comando Eelement
Modifica su elemento primario.

## <a name="syntax"></a>Sintaxis

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 La siguiente sección describe los valores de elemento válido.

### <a name="attributes"></a>Atributos
 Ninguno.

### <a name="child-elements"></a>Elementos secundarios

|Valor|Descripción|
|-----------|-----------------|
|AllowParams|Indica que los usuarios pueden especificar parámetros de comando en el **comando** ventana cuando escribe el nombre canónico del comando.<br /><br /> Válido para: `Button`|
|AlwaysCreate|Incluso si no tiene botones ni grupos, se crea el menú.<br /><br /> Válido para: `Menu`|
|CaseSensitive|Las entradas de usuario distinguen mayúsculas de minúsculas.<br /><br /> Válido para: `Combo`|
|CommandWellOnly|Aplicar esta marca si el comando no aparece en el menú de nivel superior y desea que esté disponible para la personalización adicional del shell, por ejemplo, para enlazarlo a un método abreviado de teclado. Después de instala el paquete VSPackage, puede personalizar estos comandos, abra el **opciones** cuadro de diálogo y, a continuación, editar la colocación de comandos en el **teclado entorno** categoría. Esta marca no afectan a la selección en los menús contextuales, barras de herramientas, controladores de menús o submenús.<br /><br /> Válido para: `Button`, `Combo`|
|DefaultDisabled|De forma predeterminada, el comando está deshabilitado si no está cargado el VSPackage que se implementa o la `QueryStatus` no se ha llamado al método.<br /><br /> Válido para: `Button`, `Combo`|
|DefaultDocked|Acoplar de forma predeterminada. Esta configuración ya no se aplica a las barras de herramientas porque siempre se acoplan.|
|DefaultInvisible|De forma predeterminada, el comando es invisible si no se ha cargado el VSPackage que se implementa o la `QueryStatus` no se ha llamado al método.<br /><br /> Se recomienda combinar esto con la `DynamicVisibility` marca.<br /><br /> Válido para: `Button`, `Combo`, `Menu`|
|DontCache|El entorno de desarrollo no almacena en caché el `QueryStatus` resultados del método para este comando.<br /><br /> Para un menú, esto indica a un controlador de menú no almacenar en caché el texto de sus elementos de menú. Use esta marca cuando el menú contiene elementos dinámicos o los elementos que tienen texto dinámico.<br /><br /> Válido para: `Button`, `Menu`|
|DynamicItemStart|Indica el principio de una lista dinámica. Esto permite que el entorno compilar una lista llamando sucesivamente la `QueryStatus` método en elementos de la lista hasta que se devuelve la marca OLECMDERR_E_UNSUPPORTED. Esto funciona bien para los elementos, como los usados recientemente (MRU) listas y ventana.<br /><br /> Válido para: `Button`|
|DynamicVisibility|Se puede cambiar la visibilidad del comando a través de la `QueryStatus` método o a través de un GUID de contexto que se incluye en el `VisibilityConstraints` sección.<br /><br /> Se aplica a los comandos que aparecen en los menús y barras de herramientas de ventana de herramienta, pero no en barras de herramientas de nivel superior que aparecen en la ventana principal. Elementos de nivel superior de la barra de herramientas se pueden deshabilitar pero no ocultos, cuando se devuelve la marca OLECMDF_INVISIBLE desde el `QueryStatus` método. Se pueden ocultar comandos de barra de herramientas que aparecen en las barras de herramientas ventana de herramienta.<br /><br /> En un menú, esta marca indica también que se debe ocultarse automáticamente cuando se ocultan todos sus miembros. Esta marca normalmente se asigna a los submenús porque menús de nivel superior ya tienen este comportamiento.<br /><br /> Esta marca se debe combinar con el `DefaultInvisible` marca.<br /><br /> Válido para: `Button`, `Combo`, `Menu`|
|FilterKeys|Vea el tema de las claves de filtrado en [Combo (elemento)](../extensibility/combo-element.md).<br /><br /> Válido para: `Combo`|
|FixMenuController|Si este comando se coloca en un controlador de menú, el comando es siempre el valor predeterminado; es decir, se selecciona el comando cada vez que se selecciona el botón de controlador de menú. Si el controlador de menú tiene la `TextIsAnchorCommand` marcador establecido, a continuación, el controlador de menús también toma el texto del comando que tiene el `FixMenuController` marca.<br /><br /> Debe tener un único comando en un controlador de menú el `FixMenuController` marca. Si por lo que se marca más de un comando, el último comando en el menú se convierte en el comando predeterminado.<br /><br /> Válido para: `Button`|
|IconAndText|Mostrar un icono y texto en el menú y barra de herramientas.<br /><br /> Válido para: `Button`, `Combo`, `Menu`|
|NoAutoComplete|Característica Autocompletar está deshabilitada.<br /><br /> Válido para: `Combo`|
|NoButtonCustomize|No deje que el usuario personalice este botón.<br /><br /> Válido para: `Button`, `Combo`|
|NoKeyCustomize|No habilite la personalización del teclado.<br /><br /> Válido para: `Button`, `Combo`|
|NoShowOnMenuController|Si este comando se coloca en un controlador de menú, el comando no aparece en la lista desplegable.<br /><br /> Válido para: `Button`|
|NotInTBList|No aparece en la lista de barras de herramientas disponibles. Esto es válido únicamente para tipos de menú de barra de herramientas.<br /><br /> Válido para: `Menu`|
|NoToolbarClose|El usuario no puede cerrar la barra de herramientas. Esto es válido únicamente para tipos de menú de barra de herramientas.<br /><br /> Válido para: `Menu`|
|PICT|Mostrar solo un icono en una barra de herramientas, pero únicamente el texto de un menú. Si no se especifica ningún icono, muestra un espacio en blanco donde hacer clic en una barra de herramientas.<br /><br /> Válido para: `Button`|
|PostExec|Hace que el comando sin bloqueo. El entorno de desarrollo aplaza la ejecución hasta que se completen todas las consultas de procesamiento previo.<br /><br /> Válido para: `Button`|
|RouteToDocs|El comando se enruta al documento activo.<br /><br /> Válido para: `Button`|
|StretchHorizontally|Cuando se establece esta marca, el ancho se convierte en el ancho mínimo del cuadro combinado y, si hay espacio en la barra de herramientas, el cuadro combinado se expande para rellenar el espacio disponible. Esto sucede únicamente si la barra de herramientas está acoplado horizontalmente, y solo un cuadro combinado en la barra de herramientas puede usar la marca (la marca se omite en todos, excepto el primer cuadro combinado).<br /><br /> Válido para: `Combo`|
|TextMenuUseButton|Use el `ButtonText` campo en los menús. El campo de valor predeterminado es `MenuText` si se especifica.<br /><br /> Válido para: `Button`|
|TextoCambia|El texto de menú o comando se puede cambiar en tiempo de ejecución, normalmente mediante la `QueryStatus` método.<br /><br /> Válido para: `Button`, `Menu`|
|TextChangesButton|Válido para: `Button`|
|TextIsAnchorCommand|Para un controlador de menú, el texto del menú se toma del comando predeterminado (delimitador). Un comando de delimitador es el último comando seleccionado o activado. Si no se establece esta marca, el controlador de menús utiliza su propio `MenuText` campo. Sin embargo, al hacer clic en el controlador de menús todavía permite el último comando seleccionado desde ese controlador.<br /><br /> Se recomienda que combine este marcador con el `TextChanges` marca.<br /><br /> Esta marca solo aplica a los menús de tipo MenuController o MenuControllerLatched.<br /><br /> Válido para: `Menu`|
|TextMenuCtrlUseMenu|Use el `MenuText` campo en los controladores de menú. El campo de valor predeterminado es `ButtonText`.<br /><br /> Válido para: `Button`|
|TextMenuUseButton|Use el `ButtonText` campo en los menús. El campo de valor predeterminado es `MenuText` si se especifica.<br /><br /> Válido para: `Button`|
|TextOnly|Mostrar solo texto en un menú o una barra de herramientas, pero ningún icono, incluso si se especifica el icono.<br /><br /> Válido para: `Button`|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Buttons (elemento)](../extensibility/buttons-element.md)|Proporciona un grupo para [elemento Button](../extensibility/button-element.md) elementos.|
|[Menus (elemento)](../extensibility/menus-element.md)|Define todos los menús que implementa un paquete VSPackage.|

## <a name="see-also"></a>Vea también
- [Tabla de comandos de Visual Studio (. Archivos Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)