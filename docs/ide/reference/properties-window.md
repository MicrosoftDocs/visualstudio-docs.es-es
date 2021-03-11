---
description: Use esta ventana para ver y cambiar las propiedades de tiempo de diseño y los eventos de los objetos seleccionados que se encuentran en editores y diseñadores.
title: Ventana Propiedades
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio], Properties Window
- handler functions, Properties window
- handlers, Properties window
- Windows messages
- properties [Visual Studio], setting at design time
- properties [Visual Studio], editing
- Property Browser
- Windows messages, adding message handlers
- Properties window, overrides
- virtual functions, Properties window
- Properties window
ms.assetid: e6e0fa4f-75c4-4a52-af15-281cd61876ca
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ddbfb4d001f73e30296a35c2cff4aae0e0c527f9
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221124"
---
# <a name="properties-window"></a>Propiedades (ventana)

Use esta ventana para ver y cambiar las propiedades de tiempo de diseño y los eventos de los objetos seleccionados que se encuentran en editores y diseñadores. También puede usar la ventana **Propiedades** para editar y ver archivos, proyectos y propiedades de la solución. Puede ver la ventana **Propiedades** en el menú **Ver**. También puede abrirla si presiona **F4** o escribe **Propiedades** en el cuadro de búsqueda.

La ventana **Propiedades** muestra distintos tipos de campos de edición, dependiendo de los requisitos de cada propiedad. Estos campos de edición incluyen cuadros de edición, listas desplegables y vínculos a cuadros de diálogo del editor personalizado. Las propiedades atenuadas son de solo lectura.

## <a name="uielement-list"></a>Lista de UIElement

Object name\
Muestra el objeto o los objetos seleccionados actualmente. Solo están visibles los objetos del editor o diseñador activo. Si selecciona varios objetos, solo aparecen propiedades comunes a todos los objetos seleccionados.

Categorized\
Muestra, por categoría, todas las propiedades y los valores de las propiedades del objeto seleccionado. Una categoría se puede contraer para reducir el número de propiedades visibles. Cuando se contrae o expande una categoría, aparece un signo más (+) o un signo menos (-) a la izquierda del nombre de la categoría. Las categorías se muestran por orden alfabético.

Alphabetical\
Ordena alfabéticamente todas las propiedades y los eventos de tiempo de diseño para los objetos seleccionados. Para editar una propiedad no atenuada, haga clic en la celda a su derecha y escriba los cambios.

Property Pages\
Muestra el cuadro de diálogo **Páginas de propiedades** o el **Diseñador de proyectos** del elemento seleccionado. En Páginas de propiedades, se muestra un subconjunto, el mismo o un superconjunto de las propiedades disponibles en la ventana **Propiedades**. Use este botón para ver y editar propiedades relacionadas con la configuración activa del proyecto.

Properties\
Muestra las propiedades de un objeto. Muchos objetos también tienen eventos que se pueden ver mediante la ventana **Propiedades**.

Sort by Property Source\
Agrupa las propiedades por origen, como herencia, estilos aplicados y enlaces. Solo está disponible al editar archivos XAML en el diseñador.

Events\
Muestra los eventos de un objeto.

> [!NOTE]
> Este control de la barra de herramientas de la ventana **Propiedades** solo está disponible cuando está activo un diseñador de formularios o controles en el contexto de un proyecto de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Al editar archivos XAML, los eventos aparecen en una pestaña independiente de la ventana Propiedades.

Messages\
Muestra todos los mensajes de Windows. Le permite agregar o eliminar funciones del controlador especificado para los mensajes proporcionados para la clase seleccionada.

> [!NOTE]
> Este control de la barra de herramientas de la ventana **Propiedades** solo está disponible cuando **Vista de clases** es la ventana activa en el contexto de un proyecto de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].

Overrides\
Enumera todas las funciones virtuales de la clase seleccionada y permite agregar o eliminar funciones de invalidación.

> [!NOTE]
> Este control de la barra de herramientas de la ventana **Propiedades** solo está disponible cuando **Vista de clases** es la ventana activa en el contexto de un proyecto de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].

Description pane\
Muestra el tipo de propiedad y una breve descripción de la propiedad. Puede activar y desactivar la descripción de la propiedad mediante el comando Descripción del menú contextual.

> [!NOTE]
> Este control de la barra de herramientas de la ventana **Propiedades** no está disponible al editar archivos XAML en el diseñador.

Thumbnail view\
Muestra una representación visual del elemento seleccionado actualmente al editar archivos XAML en el diseñador.

Search\
Proporciona una función de búsqueda de propiedades y eventos al editar archivos XAML en el diseñador. El cuadro de búsqueda responde a búsquedas de palabras parciales y actualiza los resultados de la búsqueda a medida que escribe.

## <a name="see-also"></a>Vea también

- [Referencia de propiedades del proyecto](../../ide/reference/project-properties-reference.md)
- [Personalizar los diseños de ventana](../../ide/customizing-window-layouts-in-visual-studio.md)
