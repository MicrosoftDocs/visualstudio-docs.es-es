---
title: Enlazar controles a imágenes desde una base de datos
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 803de097d05f472e7a5b585a8b58395c45a924ed
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914999"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Enlazar controles a imágenes desde una base de datos

Puede utilizar la ventana **Orígenes de datos** para enlazar una imagen de una base de datos a un control de su aplicación. Por ejemplo, puede enlazar una imagen a un control <xref:System.Windows.Controls.Image> de una aplicación WPF o a un control <xref:System.Windows.Forms.PictureBox> de una aplicación de Windows Forms.

Las imágenes de una base de datos están almacenadas normalmente como matrices de bytes. Los elementos de la ventana **Orígenes de datos** que están almacenados como matrices de bytes tienen su tipo de control establecido de forma predeterminada en **Ninguno**, porque las matrices de bytes pueden contener cualquier cosa, desde una matriz simple de bytes hasta el archivo ejecutable de una aplicación grande. Para crear un control enlazado a datos para un elemento de matriz de bytes en la ventana **Orígenes de datos** que represente una imagen, debe seleccionar el control.

El procedimiento siguiente supone que la ventana **Orígenes de datos** ya incluye un elemento enlazado con la imagen.

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Para enlazar una imagen de una base de datos a un control

1.  Asegúrese de que la superficie de diseño a la que va a agregar el control está abierta en WPF Designer o en el Diseñador de Windows Forms.

2.  En la ventana **Orígenes de datos**, expanda la tabla o el objeto deseado para mostrar sus columnas o propiedades.

   > [!TIP]
   > Si el **orígenes de datos** ventana no está abierta, ábrala, seleccione **vista** > **Other Windows** > **orígenes de datos**.

3.  Seleccione la columna o propiedad que contiene los datos de la imagen y seleccione uno de los siguientes controles de la lista desplegable del control:

    - Si el diseñador WPF está abierto, seleccione **Imagen**.

    - Si el diseñador de Windows Forms está abierto, seleccione **PictureBox**.

    - También puede seleccionar un control diferente que admita el enlace de datos y pueda mostrar imágenes. Si el control que desea utilizar no se encuentra en la lista de controles disponibles, puede agregarlo a la lista y seleccionarlo. Para obtener más información, consulte [agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>Vea también

- [Enlace de controles de WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)