---
title: Enlazar controles a imágenes desde una base de datos | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: ab997b01c0155b48cb9dd3033e5bbfd4724d7ba6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579475"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Enlazar controles a imágenes desde una base de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [enlazar controles a imágenes desde una base de datos](https://docs.microsoft.com/visualstudio/data-tools/bind-controls-to-pictures-from-a-database).  
  
  
Puede usar el **orígenes de datos** ventana para enlazar una imagen de una base de datos a un control en la aplicación. Por ejemplo, puede enlazar una imagen a un <xref:System.Windows.Controls.Image> control en una aplicación WPF o a un <xref:System.Windows.Forms.PictureBox> control en una aplicación de Windows Forms.  
  
 Las imágenes de una base de datos están almacenadas normalmente como matrices de bytes. Los elementos de la **orígenes de datos** ventana que se almacenan como matrices de bytes tienen su control de tipo establecido en **ninguno** de forma predeterminada, dado que las matrices de bytes pueden contener cualquier cosa, desde una simple matriz de bytes en el archivo ejecutable de una aplicación grande. Para crear un control enlazado a datos para un elemento de matriz de bytes en el **orígenes de datos** ventana que representa una imagen, debe seleccionar el control que se va a crear.  
  
 El siguiente procedimiento se da por supuesto que el **orígenes de datos** ventana ya se rellena con un elemento que está enlazado a la imagen. Para obtener más información, consulte [Cómo: conectarse a datos en una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md).  
  
### <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Para enlazar una imagen de una base de datos a un control  
  
1.  Asegúrese de que la superficie de diseño a la que va a agregar el control está abierta en WPF Designer o en el Diseñador de Windows Forms.  
  
2.  En el **orígenes de datos** ventana, expanda la tabla deseada o para mostrar sus columnas o propiedades de objeto.  
  
3.  Seleccione la columna o propiedad que contiene los datos de la imagen y seleccione uno de los siguientes controles de la lista desplegable del control:  
  
    -   Si el diseñador WPF está abierto, seleccione **imagen**.  
  
    -   Si el Diseñador de Windows Forms está abierto, seleccione **PictureBox**.  
  
    -   También puede seleccionar un control diferente que admita el enlace de datos y pueda mostrar imágenes. Si el control que desea usar no está en la lista de controles disponibles, puede agregarlo a la lista y, a continuación, selecciónelo. Para obtener más información, consulte [agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## <a name="see-also"></a>Vea también  
 [Enlace de controles de WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)

