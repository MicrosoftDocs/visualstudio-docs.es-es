---
title: 'Cómo: iniciar el Asistente para configuración de TableAdapter | Microsoft Docs'
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
- TableAdapters, Configuration Wizard
- TableAdapter Configuration Wizard
ms.assetid: 301f2dcd-ed72-4229-80ef-3b59cb062d5d
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 0cf7d3e5ace98ac73f97909b184ce04b86d4b9ee
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576392"
---
# <a name="how-to-start-the-tableadapter-configuration-wizard"></a>Cómo: Iniciar el Asistente para la configuración de TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El **TableAdapter Configuration Wizard** crea y edita adaptadores TableAdapter en conjuntos de datos fuertemente tipados. El asistente crea TableAdapters basados en las instrucciones SQL especificadas en el asistente o en los procedimientos almacenados existentes en la base de datos. El asistente también puede crear nuevos procedimientos almacenados en la base de datos de acuerdo con las instrucciones SQL que se especifican en el asistente.  
  
### <a name="to-start-the-tableadapter-configuration-wizard-to-create-a-new-tableadapter"></a>Para iniciar el Asistente para configuración de TableAdapter para crear un nuevo TableAdapter  
  
1.  Abra el conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, consulte [Cómo: abrir un conjunto de datos en el Diseñador de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
    > [!NOTE]
    >  Si no tiene un conjunto de datos en el proyecto, vea [crear y configurar conjuntos de datos](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
2.  Si va a crear un nuevo TableAdapter, arrastre un **TableAdapter** objeto desde el **conjunto de datos** pestaña de la **cuadro de herramientas** hasta la **delDiseñadordeDataset**.  
  
3.  En el **elegir la conexión de datos** página, seleccione una conexión de datos de la lista de conexiones disponibles o seleccione **nueva conexión** para crear una nueva conexión.  
  
### <a name="to-start-the-tableadapter-configuration-wizard-to-edit-an-existing-tableadapter"></a>Para iniciar el Asistente para configuración de TableAdapter para editar un TableAdapter existente  
  
1.  Abra el conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, consulte [Cómo: abrir un conjunto de datos en el Diseñador de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Haga clic en el TableAdapter en el **Diseñador de Dataset** y elija **configurar**. Se abre el Asistente para la **generar las instrucciones SQL** página o el **enlazar comandos con procedimientos almacenados existentes** página, dependiendo de cómo se configuró originalmente el TableAdapter.  
  
3.  Complete el asistente.  
  
## <a name="see-also"></a>Vea también  
 [Tutoriales de datos](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)   
 [Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Cómo: ordenar y filtrar datos ADO.NET con el componente BindingSource de formularios de Windows](http://msdn.microsoft.com/library/6c206daf-d706-4602-9dbe-435343052063)   
 [Cómo: crear una tabla de búsqueda con el componente BindingSource de formularios de Windows](http://msdn.microsoft.com/library/622fce80-879d-44be-abbf-8350ec22ca2b)   
 [Tutorial: Mostrar datos en Windows Forms](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)