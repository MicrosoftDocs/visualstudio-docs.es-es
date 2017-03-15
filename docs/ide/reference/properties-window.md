---
title: "Ventana Propiedades | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "propiedades [Visual Studio], ventana Propiedades"
  - "funciones de controlador, ventana Propiedades"
  - "controladores, ventana Propiedades"
  - "mensajes de Windows"
  - "propiedades [Visual Studio], establecer en el tiempo de diseño"
  - "propiedades [Visual Studio], editar"
  - "Examinador de propiedades"
  - "Mensajes de Windows, agregar controladores de mensajes"
  - "Ventana Propiedades, invalidaciones"
  - "funciones virtuales, ventana Propiedades"
  - "Propiedades (ventana)"
ms.assetid: e6e0fa4f-75c4-4a52-af15-281cd61876ca
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Ventana Propiedades
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilice esta ventana para ver y cambiar las propiedades y eventos en tiempo de diseño de los objetos seleccionados que están ubicados en editores y diseñadores.  También puede usar la ventana **Propiedades** para editar y ver las propiedades de los archivos, los proyectos y la solución.  Puede encontrar la ventana **Propiedades** en el menú **Ver**.  También puede abrirla presionando F4 o escribiendo las propiedades en la ventana **Inicio rápido**.  
  
 La ventana **Propiedades** muestra distintos tipos de campos de edición, según las necesidades de una propiedad determinada.  Entre estos campos de edición se incluyen cuadros de edición, listas desplegables y vínculos a cuadros de diálogo de editor personalizado.  Las propiedades que se muestran en gris son de sólo lectura.  
  
## Lista de UIElement  
 Nombre de objeto  
 Enumera el objeto u objetos actualmente seleccionados.  Sólo son visibles los objetos del editor o diseñador activos.  Cuando se seleccionan varios objetos, sólo aparecen las propiedades comunes a todos los objetos seleccionados.  
  
 Por categorías  
 Enumera por categorías todas las propiedades y valores de propiedades para el objeto seleccionado.  Puede contraerse una categoría para reducir el número de propiedades visibles.  Cuando se expande o contrae una categoría, se ve un signo más \(\+\) o menos \(\-\) a la izquierda del nombre de la categoría.  Las categorías están ordenadas alfabéticamente.  
  
 Alfabético  
 Ordena alfabéticamente todas las propiedades y eventos en tiempo de diseño de los objetos seleccionados.  Para editar una propiedad no atenuada, haga clic en la celda situada a su derecha y escriba los cambios.  
  
 Páginas de propiedades  
 Muestra los cuadros de diálogo **Páginas de propiedades** o **Diseñador de proyectos** del elemento seleccionado.  Páginas de propiedades muestra un subconjunto, el mismo o un supraconjunto de las propiedades disponibles en la ventana **Propiedades**.  Utilice este botón para ver y editar propiedades relacionadas con la configuración activa del proyecto.  
  
 Propiedades  
 Muestra las propiedades de un objeto.  Muchos objetos también tienen eventos que se pueden ver utilizando la ventana **Propiedades**.  
  
 Ordenar por origen de propiedad  
 Agrupa las propiedades por origen, como herencia, estilos aplicados y enlaces.  Solo está disponible al editar los archivos XAML en el diseñador.  
  
 Eventos  
 Muestra los eventos de un objeto.  
  
> [!NOTE]
>  Este control de la barra de herramientas de la ventana **Propiedades** solo está disponible cuando hay un formulario o diseñador de controles activo en el contexto de un proyecto de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)].  Al editar archivos XAML, los eventos aparecen en una pestaña independiente de la ventana Propiedades.  
  
 Mensajes  
 Muestra todos los mensajes de Windows.  Permite agregar o eliminar funciones controladoras especificas para los mensajes proporcionados en la clase seleccionada.  
  
> [!NOTE]
>  Este control de la barra de herramientas de la ventana **Propiedades** solo está disponible si la **Vista de clases** es la ventana activa en el contexto de un proyecto de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 Overrides  
 Enumera todas las funciones virtuales de la clase seleccionada y permite agregar o eliminar funciones de reemplazo.  
  
> [!NOTE]
>  Este control de la barra de herramientas de la ventana **Propiedades** solo está disponible si la **Vista de clases** es la ventana activa en el contexto de un proyecto de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].  
  
 Panel Descripción  
 Muestra el tipo de propiedad y una breve descripción de la propiedad.  Se puede activar y desactivar la descripción de la propiedad utilizando el comando Descripción del menú contextual.  
  
> [!NOTE]
>  Este control de la barra de herramientas de la ventana **Propiedades** no está disponible al editar archivos XAML en el diseñador.  
  
 Vista en miniatura  
 Muestra una representación visual del elemento seleccionado actualmente al editar los archivos XAML en el diseñador.  
  
 Buscar  
 Proporciona una función Search para las propiedades y eventos al editar archivos XAML en el diseñador.  El cuadro de búsqueda responde a las búsquedas parciales de palabras y actualiza los resultados de la búsqueda cuando se escribe.  
  
## Vea también  
 [Referencia de propiedades del proyecto](../../ide/reference/project-properties-reference.md)   
 [Personalizar los diseños de ventana](../../ide/customizing-window-layouts-in-visual-studio.md)