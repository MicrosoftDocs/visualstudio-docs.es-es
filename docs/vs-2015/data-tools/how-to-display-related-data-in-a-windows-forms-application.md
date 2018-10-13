---
title: 'Cómo: mostrar relacionados con la aplicación de datos en un Windows Forms | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
- Windows Forms, displaying data
- displaying data, related data
- related data, displaying
- displaying tables, related data
- data [Windows Forms], displaying
- displaying table data
- data [Windows Forms], related
- displaying data on forms, related data
- displaying table information
ms.assetid: 60b1f1ec-6257-42ab-83f0-06d54ed364fd
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 3fd7a29e1de66a5b5fd57dab1adbcf99128001ac
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215467"
---
# <a name="how-to-display-related-data-in-a-windows-forms-application"></a>Cómo: Mostrar datos relacionados en una aplicación de Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede mostrar datos relacionados arrastrando los elementos que comparten el mismo nodo de tabla principal desde el [ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) al formulario. Por ejemplo, si tiene datos de origen que tiene un `Customers` tabla y un relacionados `Orders` tabla, que vea ambas tablas como nodos de nivel superior (en la vista de árbol) en el **orígenes de datos** ventana. Expanda el nodo `Customers` para que pueda ver las columnas y observará que la última columna de la lista es un nodo expansible que representa la tabla `Orders`. Este nodo representa los pedidos relacionados para un cliente. Esto significa que si desea crear un formulario que permita seleccionar un cliente y a continuación mostrar una lista de pedidos para ese cliente, puede arrastrar los elementos que desea mostrar desde esta jerarquía única.  
  
 ![Ventana de orígenes de datos que muestra la relación](../data-tools/media/datasources2.gif "DataSources2")  
Crear controles enlazados a datos que muestren los registros relacionados  
  
 ![vínculo a vídeo](../data-tools/media/playvideo.gif "PlayVideo") para una versión en vídeo de este tema, consulte [cómo actualizar tablas relacionadas](http://go.microsoft.com/fwlink/?LinkId=143527).  
  
### <a name="to-create-controls-that-display-related-records"></a>Para crear controles que muestren los registros relacionados  
  
1.  Abrir el formulario en el [Diseñador de Windows Forms](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
2.  Abra el **orígenes de datos** ventana. Para obtener más información, consulte [Cómo: abrir la ventana de orígenes de datos](../data-tools/how-to-open-the-data-sources-window.md).  
  
3.  Expanda el nodo que representa la tabla primaria en la relación. (La tabla primaria es la tabla en lado "uno" de una relación uno a varios.)  
  
4.  Arrastre los elementos que desea mostrar de la tabla primaria de la relación desde la **orígenes de datos** ventana hasta su formulario.  
  
5.  Las tablas secundarias relacionadas aparecen como nodos expansibles en la parte inferior de la lista de columnas de la tabla primaria. Arrastre los elementos que desea mostrar de este tipo de nodo relacionado hasta el formulario.  
  
    > [!NOTE]
    >  Arrastrar un elemento desde un nodo de nivel superior crea un no relacionados e independientes [componente BindingSource](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9) que no facilitan la navegación de los registros relacionados. Para enlazar datos relacionados, debe seleccionar las tablas del mismo nodo jerárquico.  
  
## <a name="see-also"></a>Vea también  
 [Tutoriales de datos](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Tutorial: Mostrar datos en un formulario de Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)   
 [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Cómo: Explorar datos con el control BindingNavigator de Windows Forms](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)