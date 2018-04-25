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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 722eb290e9018ef92608c8d554a371c94ba63caa
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Enlazar controles a imágenes desde una base de datos

Puede usar el **orígenes de datos** ventana para enlazar una imagen de una base de datos a un control en la aplicación. Por ejemplo, puede enlazar una imagen a un <xref:System.Windows.Controls.Image> controlar en una aplicación WPF o a un <xref:System.Windows.Forms.PictureBox> control en una aplicación de formularios Windows Forms.

Las imágenes de una base de datos están almacenadas normalmente como matrices de bytes. Los elementos de la **orígenes de datos** ventana que se almacenan como matrices de bytes tienen su control tipo establecido en **ninguno** de forma predeterminada, dado que las matrices de bytes pueden contener cualquier cosa, desde una simple matriz de bytes al archivo ejecutable de una aplicación grande. Para crear un control enlazado a datos para un elemento de matriz de bytes en el **orígenes de datos** ventana que representa una imagen, debe seleccionar el control que desee crear.

El siguiente procedimiento se da por supuesto que el **orígenes de datos** ventana ya se rellena con un elemento que está enlazado a la imagen.

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Para enlazar una imagen de una base de datos a un control

1.  Asegúrese de que la superficie de diseño a la que va a agregar el control está abierta en WPF Designer o en el Diseñador de Windows Forms.

2.  En el **orígenes de datos** ventana, expanda la tabla deseada o el objeto para mostrar sus columnas o propiedades.

3.  Seleccione la columna o propiedad que contiene los datos de la imagen y seleccione uno de los siguientes controles de la lista desplegable del control:

    -   Si el diseñador WPF está abierto, seleccione **imagen**.

    -   Si el Diseñador de formularios Windows Forms está abierto, seleccione **PictureBox**.

    -   También puede seleccionar un control diferente que admita el enlace de datos y pueda mostrar imágenes. Si el control que desea usar no está en la lista de controles disponibles, puede agregar a la lista y, a continuación, selecciónelo. Para obtener más información, consulte [agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>Vea también

- [Enlace de controles de WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)