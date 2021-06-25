---
title: Elemento Command Flag | Microsoft Docs
description: El elemento command flag modifica su elemento primario. Revise sus elementos primarios y secundarios.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6356fd02c8045aee9dc48ebc9d30a346159080bb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902038"
---
# <a name="command-flag-eelement"></a>Marca de comando Eelement
Modifica su elemento primario.

## <a name="syntax"></a>Sintaxis

```
<CommandFlag>DynamicVisibility</CommandFlag>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En la sección siguiente se describen los valores de elemento válidos.

### <a name="attributes"></a>Atributos
 Ninguno.

### <a name="child-elements"></a>Elementos secundarios

|Valor|Descripción|
|-----------|-----------------|
|AllowParams|Indica que los usuarios pueden escribir parámetros de comando en la **ventana** Comando cuando escriben el nombre canónico del comando.<br /><br /> Válido para: `Button`|
|AlwaysCreate|El menú se crea incluso si no tiene grupos ni botones.<br /><br /> Válido para: `Menu`|
|CaseSensitive|Las entradas del usuario distinguen mayúsculas de minúsculas.<br /><br /> Válido para: `Combo`|
|CommandWellOnly|Aplique esta marca si el comando no aparece en el menú de nivel superior y desea que esté disponible para la personalización adicional del shell, por ejemplo, para enlazarlo a un método abreviado de teclado. Una vez instalado el VSPackage, puede personalizar estos  comandos abriendo el cuadro de diálogo Opciones y editando la posición del comando en la categoría **Entorno de** teclado. Esta marca no afecta a la selección de ubicación en menús contextuales, barras de herramientas, controladores de menú o submenús.<br /><br /> Válido para: `Button` , `Combo`|
|DefaultDisabled|De forma predeterminada, el comando está deshabilitado si el VSPackage que lo implementa no está cargado o no se ha `QueryStatus` llamado al método .<br /><br /> Válido para: `Button` , `Combo`|
|DefaultDocked|Acoplado de forma predeterminada. Esta configuración ya no se aplica a las barras de herramientas porque siempre están acopladas.|
|DefaultInvisible|De forma predeterminada, el comando es invisible si el VSPackage que lo implementa no está cargado o no se ha `QueryStatus` llamado al método .<br /><br /> Se recomienda combinar esto con la `DynamicVisibility` marca .<br /><br /> Válido para: `Button` , `Combo` , `Menu`|
|DontCache|El entorno de desarrollo no almacena en caché los `QueryStatus` resultados del método para este comando.<br /><br /> Para un menú, esto indica a un controlador de menús que no debe almacenar en caché el texto de sus elementos de menú. Use esta marca cuando el menú contenga elementos dinámicos o elementos que tengan texto dinámico.<br /><br /> Válido para: `Button` , `Menu`|
|DynamicItemStart|Indica el principio de una lista dinámica. Esto permite al entorno generar una lista llamando sucesivamente al método en los elementos de lista hasta que OLECMDERR_E_UNSUPPORTED `QueryStatus` se devuelve la marca. Esto funciona bien para elementos como listas usadas más recientemente (MRU) y listas de ventanas.<br /><br /> Válido para: `Button`|
|DynamicVisibility|La visibilidad del comando se puede cambiar a través del método o a través de un `QueryStatus` GUID de contexto que se incluye en la sección `VisibilityConstraints` .<br /><br /> Se aplica a los comandos que aparecen en los menús y las barras de herramientas de la ventana de herramientas, pero no en las barras de herramientas de nivel superior que aparecen en la ventana principal. Los elementos de la barra de herramientas de nivel superior se pueden deshabilitar, pero no ocultarse, cuando se devuelve OLECMDF_INVISIBLE marca del `QueryStatus` método . Los comandos de la barra de herramientas que aparecen en las barras de herramientas de la ventana de herramientas se pueden ocultar.<br /><br /> En un menú, esta marca también indica que se debe ocultar automáticamente cuando se ocultan todos sus miembros. Normalmente, esta marca se asigna a submenús porque los menús de nivel superior ya tienen este comportamiento.<br /><br /> Esta marca debe combinarse con la `DefaultInvisible` marca .<br /><br /> Válido para: `Button` , `Combo` , `Menu`|
|Filterkeys|Vea el tema Filtering Keys (Filtrar claves) [en Combo Element (Elemento combinado).](../extensibility/combo-element.md)<br /><br /> Válido para: `Combo`|
|FixMenuController|Si este comando se coloca en un controlador de menú, el comando siempre es el valor predeterminado; es decir, el comando se selecciona cada vez que se selecciona el propio botón del controlador de menús. Si el controlador de menús tiene la marca establecida, el controlador de menús también toma su texto del `TextIsAnchorCommand` comando que tiene la `FixMenuController` marca.<br /><br /> Solo un comando de un controlador de menú debe tener la `FixMenuController` marca . Si hay más de un comando marcado, el último comando del menú se convierte en el comando predeterminado.<br /><br /> Válido para: `Button`|
|IconAndText|Mostrar un icono y texto en el menú y la barra de herramientas.<br /><br /> Válido para: `Button` , `Combo` , `Menu`|
|NoAutoComplete|La característica Autocompletar está deshabilitada.<br /><br /> Válido para: `Combo`|
|NoButtonCustomize|No permita que el usuario personalice este botón.<br /><br /> Válido para: `Button` , `Combo`|
|NoKeyCustomize|No habilite la personalización del teclado.<br /><br /> Válido para: `Button` , `Combo`|
|NoShowOnMenuController|Si este comando se coloca en un controlador de menú, el comando no aparece en la lista desplegable.<br /><br /> Válido para: `Button`|
|NotInTBList|No aparece en la lista de barras de herramientas disponibles. Esto solo es válido para los tipos de menú Barra de herramientas.<br /><br /> Válido para: `Menu`|
|NoToolbarClose|El usuario no puede cerrar la barra de herramientas. Esto solo es válido para los tipos de menú Barra de herramientas.<br /><br /> Válido para: `Menu`|
|Pict|Mostrar solo un icono en una barra de herramientas, pero solo texto en un menú. Si no se especifica ningún icono, muestra un espacio en blanco en el que se puede hacer clic en una barra de herramientas.<br /><br /> Válido para: `Button`|
|PostExec|Hace que el comando no bloquee. El entorno de desarrollo aplaza la ejecución hasta que se completan todas las consultas de procesamiento previo.<br /><br /> Válido para: `Button`|
|RouteToDocs|El comando se enruta al documento activo.<br /><br /> Válido para: `Button`|
|StretchHorizontally|Cuando se establece esta marca, el ancho se convierte en el ancho mínimo del cuadro combinado y, si hay espacio en la barra de herramientas, el cuadro combinado se extiende para rellenar el espacio disponible. Esto solo se produce si la barra de herramientas está acoplada horizontalmente y solo un cuadro combinado de la barra de herramientas puede usar la marca (la marca se omite en todas excepto en el primer cuadro combinado).<br /><br /> Válido para: `Combo`|
|TextChanges|El texto del comando o del menú se puede cambiar en tiempo de ejecución, normalmente a través del `QueryStatus` método .<br /><br /> Válido para: `Button` , `Menu`|
|TextChangesButton|Válido para: `Button`|
|TextIsAnchorCommand|Para un controlador de menús, el texto del menú se toma del comando predeterminado (delimitador). Un comando delimitador es el último comando seleccionado o con bloqueos de bloqueos. Si no se establece esta marca, el controlador de menús usa su propio `MenuText` campo. Sin embargo, al hacer clic en el controlador de menús se habilita el último comando seleccionado desde ese controlador.<br /><br /> Se recomienda combinar esta marca con la `TextChanges` marca .<br /><br /> Esta marca solo se aplica a los menús de tipo MenuController o MenuControllerLatched.<br /><br /> Válido para: `Menu`|
|TextMenuCtrlUseMenu|Use el `MenuText` campo en los controladores de menú. El campo predeterminado es `ButtonText` .<br /><br /> Válido para: `Button`|
|TextMenuUseButton|Use el `ButtonText` campo para los menús. El campo predeterminado `MenuText` es si se especifica.<br /><br /> Válido para: `Button`|
|TextOnly|Mostrar solo texto en una barra de herramientas o un menú, pero sin icono aunque se especifique el icono.<br /><br /> Válido para: `Button`|

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Elemento Buttons](../extensibility/buttons-element.md)|Proporciona un grupo para elementos [Button.](../extensibility/button-element.md)|
|[Elemento Menus](../extensibility/menus-element.md)|Define todos los menús que implementa un VSPackage.|

## <a name="see-also"></a>Consulta también
- [Visual Studio tabla de comandos (. Vsct) Archivos](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
