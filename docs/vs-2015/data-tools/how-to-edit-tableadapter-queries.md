---
title: 'Cómo: editar consultas de TableAdapter | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DbSource
- vbdata.Microsoft.VSDesigner.DataSource.DbSource
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- queries [Visual Basic], editing
- TableAdapters, editing queries
- data [Visual Studio], TableAdapters
- editing queries
ms.assetid: aac7b7b4-bd91-4225-95d4-a07643568c43
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 14157d10f105c6f3a1e95442edfe18bfd3aebd6e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576085"
---
# <a name="how-to-edit-tableadapter-queries"></a>Cómo: Editar consultas de TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editar consultas de TableAdapter con el [editar TableAdapters](../data-tools/editing-tableadapters.md) en el **Diseñador de Dataset**. Debe modificar una consulta de TableAdapter cuando ya no satisfaga las necesidades de su aplicación. (Como alternativa, puede crear consultas adicionales en el TableAdapter. Para obtener más información sobre cómo agregar nuevas consultas, vea [Cómo: crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).)  
  
> [!NOTE]
>  Si el [TableAdapter Configuration Wizard](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8) se abre en lugar de la **TableAdapter Query Configuration Wizard**, es posible que haya seleccionado principal del TableAdapter `Fill` consulta y no uno de los Consultas adicionales de TableAdapter. Para obtener información acerca de cómo modificar el TableAdapter principal `Fill` de consulta, vea [Cómo: editar TableAdapters](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
 ![TableAdapter con varias consultas](../data-tools/media/tableadapter.gif "TableAdapter")  
  
### <a name="to-edit-a-tableadapter-query"></a>Para editar una consulta de TableAdapter  
  
1.  Abra el conjunto de datos en el **Diseñador de Dataset**. Para obtener más información, consulte [Cómo: abrir un conjunto de datos en el Diseñador de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Seleccione la consulta de TableAdapter que desea editar.  
  
3.  Haga clic en la consulta de TableAdapter y seleccione **configurar**.  
  
     El **TableAdapter Query Configuration Wizard** se abre, listo para que se modifique la consulta o procedimiento almacenado para esa consulta.  
  
4.  Completar la **TableAdapter Query Configuration Wizard** con los cambios que desee. Para obtener más información, consulte [editar TableAdapters](../data-tools/editing-tableadapters.md).  
  
## <a name="see-also"></a>Vea también  
 [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar su aplicación para recibir datos](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Captura de datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Edición de datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Guardar datos](../data-tools/saving-data.md)   
 [Tutoriales de datos](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)