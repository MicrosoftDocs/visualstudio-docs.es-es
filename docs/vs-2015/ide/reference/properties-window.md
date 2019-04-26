---
title: Ventana Propiedades | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 582905042938d79a1885279bd19c18f48b49bb84
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438034"
---
# <a name="properties-window"></a>Ventana Propiedades
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use esta ventana para ver y cambiar las propiedades de tiempo de diseño y los eventos de los objetos seleccionados que se encuentran en editores y diseñadores. También puede usar la ventana **Propiedades** para editar y ver archivos, proyectos y propiedades de la solución. Puede ver la ventana **Propiedades** en el menú **Ver**. También puede abrirla si presiona F4 o escribe **Propiedades** en la ventana **Inicio rápido**.  
  
 En la ventana **Propiedades** se muestran distintos tipos de campos de edición, según las necesidades de una propiedad determinada. Estos campos de edición incluyen cuadros de edición, listas desplegables y vínculos a cuadros de diálogo del editor personalizado. Las propiedades atenuadas son de solo lectura.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 Nombre de objeto  
 Muestra el objeto o los objetos seleccionados actualmente. Solo se pueden ver los objetos del editor o diseñador activo. Si selecciona varios objetos, solo aparecen propiedades comunes a todos los objetos seleccionados.  
  
 Por categorías  
 Muestra todas las propiedades y valores de propiedad del objeto seleccionado, por categoría. Puede contraer una categoría para reducir el número de propiedades visibles. Al expandir o contraer una categoría, aparece un signo más (+) o menos (-) a la izquierda del nombre de la categoría. Las categorías se muestran ordenadas alfabéticamente.  
  
 Alfabético  
 Ordena alfabéticamente todas las propiedades de tiempo de diseño y los eventos de los objetos seleccionados. Para editar una propiedad no atenuada, haga clic en la celda a su derecha y escriba los cambios.  
  
 Páginas de propiedades  
 Muestra el cuadro de diálogo **Páginas de propiedades** o el **Diseñador de proyectos** del elemento seleccionado. En Páginas de propiedades, se muestra un subconjunto, el mismo o un superconjunto de las propiedades disponibles en la ventana **Propiedades**. Use este botón para ver y editar propiedades relacionadas con la configuración activa del proyecto.  
  
 Propiedades  
 Muestra las propiedades de un objeto. Muchos objetos también tienen eventos que se pueden ver mediante la ventana **Propiedades**.  
  
 Ordenar por origen de propiedad  
 Agrupa las propiedades por origen, como herencia, estilos aplicados y enlaces. Solo está disponible al editar archivos XAML en el diseñador.  
  
 Eventos  
 Muestra los eventos de un objeto.  
  
> [!NOTE]
> Este control de la barra de herramientas de la ventana **Propiedades** solo está disponible cuando está activo un diseñador de formularios o controles en el contexto de un proyecto de [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Al editar archivos XAML, los eventos aparecen en una pestaña independiente de la ventana Propiedades.  
  
 Mensajes  
 Muestra todos los mensajes de Windows. Le permite agregar o eliminar funciones del controlador especificado para los mensajes proporcionados para la clase seleccionada.  
  
> [!NOTE]
> Este control de la barra de herramientas de la ventana **Propiedades** solo está disponible cuando **Vista de clases** es la ventana activa en el contexto de un proyecto de [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].  
  
 Overrides  
 Enumera todas las funciones virtuales de la clase seleccionada y permite agregar o eliminar funciones de invalidación.  
  
> [!NOTE]
> Este control de la barra de herramientas de la ventana **Propiedades** solo está disponible cuando **Vista de clases** es la ventana activa en el contexto de un proyecto de [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].  
  
 Panel de descripción  
 Muestra el tipo de propiedad y una breve descripción de la propiedad. Puede activar y desactivar la descripción de la propiedad mediante el comando Descripción del menú contextual.  
  
> [!NOTE]
> Este control de la barra de herramientas de la ventana **Propiedades** no está disponible al editar archivos XAML en el diseñador.  
  
 Vista de miniaturas  
 Muestra una representación visual del elemento seleccionado actualmente al editar archivos XAML en el diseñador.  
  
 Buscar  
 Proporciona una función de búsqueda de propiedades y eventos al editar archivos XAML en el diseñador. El cuadro de búsqueda responde a búsquedas de palabras parciales y actualiza los resultados de la búsqueda a medida que escribe.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de propiedades del proyecto](../../ide/reference/project-properties-reference.md)   
 [Personalizar los diseños de ventana](../../ide/customizing-window-layouts-in-visual-studio.md)
