---
title: Opciones, Diseñador de Windows Forms, Personalización de UI de datos
description: Obtenga información sobre cómo usar la página Personalización de IU de datos para definir qué controles aparecerán en la lista de controles disponibles para los elementos de la ventana Orígenes de datos.
ms.custom: SEO-VS-2020
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.Data_UI_Customization
helpviewer_keywords:
- Data UI customization options
- Options dialog box, Windows Forms Designer, Data UI Customization
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 46834dea30f41ebf0eb8629fe4dde0525288e82d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932311"
---
# <a name="options-dialog-box-windows-forms-designer--data-ui-customization"></a>Cuadro de diálogo Opciones: Diseñador de Windows Forms > Personalización de UI de datos

En este cuadro de diálogo se definen los controles que aparecerán en la lista de controles disponibles para los elementos de la ventana Orígenes de datos. Para abrirlo, seleccione **Herramientas** > **Opciones** y, luego, seleccione **Diseñador de Windows Forms** > **Personalización de UI de datos**.

Puede seleccionar un control de un elemento en la ventana Orígenes de datos antes de arrastrarlo al formulario en una aplicación de Windows Forms. Los controles disponibles los determina el tipo de datos del elemento. Cada tipo de datos tiene una lista de controles asociados válidos según lo definido en este cuadro de diálogo, incluido un control predeterminado. Cuando arrastra un elemento de la ventana Orígenes de datos a un formulario sin seleccionar un control, el control predeterminado del tipo de datos del elemento seleccionado se agrega al formulario.

Para personalizar la lista de controles asociados, active y desactive las casillas de los controles disponibles para cada tipo de datos. Para agregar un control a la lista, agregue un control que implemente el atributo de enlace de datos <xref:System.ComponentModel.DefaultBindingPropertyAttribute> o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> en el Cuadro de herramientas. El control aparecerá en la lista de controles correspondiente al tipo de datos. Para obtener más información, vea [Cómo: Agregue controles personalizados a la ventana Orígenes de datos](../..//data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="data-type"></a>Tipo de datos

Muestra una lista de los tipos con los que se asocian los controles. Las tablas se representan como el tipo de datos `[List]`. Las columnas se representan como el tipo de datos real de la columna en el almacén de datos subyacente.

## <a name="associated-controls"></a>Controles asociados

Muestra una lista de los controles asociados con el tipo de datos seleccionado. Active o desactive la casilla que está junto al control para asociarlo o desasociarlo. Los controles seleccionados aparecen en la ventana Orígenes de datos de una columna de base de datos que está enlazada al tipo de datos asociado.

## <a name="set-default"></a>Establecimiento del valor predeterminado

Asigna el tipo de control seleccionado como el valor predeterminado del tipo de datos seleccionado. El control predeterminado aparece como la primera selección en el menú contextual de una columna de base de datos de la ventana Orígenes de datos. Cuando arrastra un elemento de la ventana Orígenes de datos a un formulario sin seleccionar un control, el control predeterminado del tipo de datos del elemento seleccionado se agrega al formulario.

Solo se puede asignar un tipo de control como el valor predeterminado de un tipo de datos.

## <a name="clear-default"></a>Eliminación del valor predeterminado

Quita la designación de un control como el valor predeterminado del tipo de datos seleccionado. Si no hay ningún valor predeterminado para el tipo de datos seleccionado, `[None]` aparece como la primera selección en el menú contextual de una columna de base de datos de ese tipo.
