---
title: Enlazar controles a imágenes desde una base de datos | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cb1bdb99db405962f487bc9ec13de961f352ec48
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995496"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Enlazar controles a imágenes desde una base de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Puede utilizar la ventana **Orígenes de datos** para enlazar una imagen de una base de datos a un control de su aplicación. Por ejemplo, puede enlazar una imagen a un control <xref:System.Windows.Controls.Image> de una aplicación WPF o a un control <xref:System.Windows.Forms.PictureBox> de una aplicación de Windows Forms.  
  
 Las imágenes de una base de datos están almacenadas normalmente como matrices de bytes. Los elementos de la ventana **Orígenes de datos** que están almacenados como matrices de bytes tienen su tipo de control establecido de forma predeterminada en **Ninguno**, porque las matrices de bytes pueden contener cualquier cosa, desde una matriz simple de bytes hasta el archivo ejecutable de una aplicación grande. Para crear un control enlazado a datos para un elemento de matriz de bytes en la ventana **Orígenes de datos** que represente una imagen, debe seleccionar el control.  
  
 El procedimiento siguiente supone que la ventana **Orígenes de datos** ya incluye un elemento enlazado con la imagen.
  
## <a name="bind-a-picture-in-a-database-to-a-control"></a>Enlazar una imagen de una base de datos a un control  
  
1.  Asegúrese de que la superficie de diseño a la que va a agregar el control está abierta en WPF Designer o en el Diseñador de Windows Forms.  
  
2.  En la ventana **Orígenes de datos**, expanda la tabla o el objeto deseado para mostrar sus columnas o propiedades.  
  
3.  Seleccione la columna o propiedad que contiene los datos de la imagen y seleccione uno de los siguientes controles de la lista desplegable del control:  
  
    -   Si el diseñador WPF está abierto, seleccione **Imagen**.  
  
    -   Si el diseñador de Windows Forms está abierto, seleccione **PictureBox**.  
  
    -   También puede seleccionar un control diferente que admita el enlace de datos y pueda mostrar imágenes. Si el control que desea utilizar no se encuentra en la lista de controles disponibles, puede agregarlo a la lista y seleccionarlo. Para obtener más información, consulte [agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## <a name="see-also"></a>Vea también  
 [Enlace de controles de WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)
