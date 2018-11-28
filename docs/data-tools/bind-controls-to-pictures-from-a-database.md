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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d93ca95a67bc3816d8d65a799282dc6c7969e093
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304922"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Enlazar controles a imágenes desde una base de datos

Puede utilizar la ventana Orígenes de datos** para enlazar una imagen de una base de datos a un control de su aplicación. Por ejemplo, puede enlazar una imagen a un control <xref:System.Windows.Controls.Image> de una aplicación WPF o a un control <xref:System.Windows.Forms.PictureBox> de aplicaciones de Windows Forms.

Las imágenes de una base de datos están almacenadas normalmente como matrices de bytes. Los elementos de la ventana Orígenes de datos **que están almacenados como matrices de bytes tienen su tipo de control establecido de forma predeterminada en Ninguno**, porque las matrices de bytes pueden contener cualquier cosa, desde una matriz simple de bytes hasta el archivo ejecutable de una aplicación grande. Para crear un control enlazado a datos para un elemento de matriz de bytes en la ventana Orígenes de datos** que represente una imagen, debe seleccionar el control.

El procedimiento siguiente supone que la ventana Orígenes de datos** ya incluye un elemento enlazado con la imagen.

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Para enlazar una imagen de una base de datos a un control

1.  Asegúrese de que la superficie de diseño a la que va a agregar el control está abierta en WPF Designer o en el Diseñador de Windows Forms.

2.  En la ventana Orígenes de datos **, expanda la tabla o el objeto deseado para mostrar sus columnas o propiedades.

   > [!TIP]
   > Si el **orígenes de datos** ventana no está abierta, ábrala, seleccione **vista** > **Other Windows** > **orígenes de datos**.

3.  Seleccione la columna o propiedad que contiene los datos de la imagen y seleccione uno de los siguientes controles de la lista desplegable del control:

    - Si el diseñador WPF está abierto, seleccione Imagen **.

    - Si el diseñador de Windows Forms está abierto, seleccione PictureBox **.

    - También puede seleccionar un control diferente que admita el enlace de datos y pueda mostrar imágenes. Si el control que desea utilizar no se encuentra en la lista de controles disponibles, puede agregarlo a la lista y, a continuación, seleccionarlo. Para obtener más información, consulte [agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>Vea también

- [Enlace de controles de WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)