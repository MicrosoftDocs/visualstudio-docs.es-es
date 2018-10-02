---
title: 'Cómo: agregar consultas globales a un TableAdapter | Microsoft Docs'
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
- global functions, datasets
- scalar functions, datasets
- TableAdapters, global queries
- data [Visual Studio], TableAdapters
- datasets [Visual Basic], scalar functions
- TableAdapter Query Configuration Wizard
- datasets [Visual Basic], global functions
- TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: 4abffd6b-2e9f-4ef3-99b2-6e9ae4ad4679
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 681fea494557e555c745d33c07c4e2c25cfe0f88
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574527"
---
# <a name="how-to-add-global-queries-to-a-tableadapter"></a>Cómo: agregar consultas globales a un TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Consultas globales* son consultas SQL que devuelven un único valor (escalar) o ningún valor. Normalmente, las funciones globales realizan operaciones de base de datos, como inserciones, actualizaciones, eliminaciones y la adición de información, como devolver un recuento de clientes en una tabla o los cargos totales para todos los elementos en un orden concreto.  
  
 Agregar consultas globales mediante la ejecución de la **TableAdapter Query Configuration Wizard** desde el **Diseñador de Dataset**.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-global-query-to-a-dataset"></a>Para agregar una consulta global a un conjunto de datos  
  
1.  Abrir un conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, consulte [Cómo: abrir un conjunto de datos en el Diseñador de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Arrastre un **consulta** desde el **conjunto de datos** pestaña de la **cuadro de herramientas** en un área vacía de la **Diseñador de Dataset**.  
  
     El [editar TableAdapters](../data-tools/editing-tableadapters.md) se abre.  
  
3.  Elegir una conexión para la consulta que se utilizará. Puede elegir uno de la lista o cree una nueva conexión. Si crea una nueva conexión, tendrá la opción de guardarlo en el archivo de configuración de la aplicación. Para obtener más información, consulte [Cómo: guardar y editar las cadenas de conexión](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
4.  Elija si desea usar instrucciones SQL o procedimientos almacenados.  
  
5.  Elija el procedimiento almacenado a utilizar o, en el **elegir un tipo de consulta** página del asistente, elija el tipo de consulta que desee y, a continuación, haga clic en **siguiente**.  
  
6.  Proporcionar una consulta que realiza la tarea deseada, por ejemplo, `SELECT COUNT(*) AS CustomerCount FROM Customers`.  
  
    > [!NOTE]
    >  Al arrastrar una consulta directamente en el **Diseñador de Dataset** crea un método que solo se devolverá un valor escalar (único). Mientras que la consulta o procedimiento almacenado que selecciona puede devolver más de un solo valor, el método creado por el Asistente solo devolverá un valor único. Por ejemplo, la consulta podría devolver la primera columna de la primera fila de los datos devueltos.  
  
7.  Complete el Asistente; la consulta se agrega a la **Diseñador de Dataset**. Para obtener información acerca de cómo ejecutar la consulta, vea [Cómo: ejecutar consultas de TableAdapter](http://msdn.microsoft.com/library/c7518855-f896-41c1-b3de-1a8116280593).  
  
## <a name="see-also"></a>Vea también  
 [Crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md)   
 [Cómo: crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)   
 [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Cómo: desplazarse por datos con el Control BindingNavigator de formularios de Windows](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [Tutorial: Mostrar datos en Windows Forms](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)