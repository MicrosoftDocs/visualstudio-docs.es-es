---
title: Agregar controles personalizados a la ventana de orígenes de datos | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.howtoaddcustomcontrol
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: acdab62754a8cbbe7b97ea9723fba202d5078ac0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578313"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>Agregar controles personalizados a la ventana de orígenes de datos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [agregar controles personalizados a la ventana de orígenes de datos](https://docs.microsoft.com/visualstudio/data-tools/add-custom-controls-to-the-data-sources-window).  
  
  
Cuando se arrastra un elemento desde el **orígenes de datos** ventana a una superficie de diseño para crear un control enlazado a datos, puede seleccionar el tipo de control que se crea. Cada elemento de la ventana tiene una lista desplegable que muestra los controles que puede elegir. El conjunto de controles asociados con cada elemento viene determinada por el tipo de datos del elemento. Si el control que desea crear no aparece en la lista, puede seguir las instrucciones de este tema para agregar el control a la lista.  
  
 Para obtener más información acerca de cómo seleccionar los controles enlazados a datos para crear elementos en el **orígenes de datos** ventana, consulte [establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
> [!NOTE]
>  Los cuadros de diálogo y los comandos de menú que se ven pueden diferir de los descritos en la Ayuda, dependiendo de los valores de configuración o de edición activos. Para cambiar la configuración, en el **herramientas** menú, seleccione **importar y exportar configuraciones**. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
##  <a name="customizinglist"></a> Personalizar la lista de controles enlazables para un tipo de datos  
 Para agregar o quitar controles de la lista de controles disponibles para los elementos de la **orígenes de datos** ventana que tiene un tipo de datos específico, realice los pasos siguientes.  
  
#### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>Para seleccionar los controles que se va a aparecer en un tipo de datos  
  
1.  Asegúrese de que WPF Designer o el Diseñador de Windows Forms está abierto.  
  
2.  En el **orígenes de datos** , haga clic en un elemento que forma parte de un origen de datos agrega a la ventana y, a continuación, haga clic en el menú desplegable para el elemento.  
  
3.  En el menú desplegable, haga clic en **personalizar**. Uno de los siguientes cuadros de diálogo se abre:  
  
    -   Si el Diseñador de Windows Forms está abierto, el **personalización de la interfaz de usuario de datos** página de la **opciones** abre el cuadro de diálogo.  
  
    -   Si el diseñador WPF está abierto, el **Personalizar enlace de Control** abre el cuadro de diálogo.  
  
4.  En el cuadro de diálogo, seleccione un tipo de datos en el **tipo de datos** lista desplegable.  
  
    -   Para personalizar la lista de controles para una tabla u objeto, seleccione **[lista]**.  
  
    -   Para personalizar la lista de controles de una columna de una tabla o una propiedad de un objeto, seleccione el tipo de datos de la columna o propiedad en el almacén de datos subyacente.  
  
    -   Para personalizar la lista de controles para mostrar los objetos de datos que tienen formas definidas por el usuario, seleccione **[otros]**. Por ejemplo, seleccione **[otros]** si la aplicación tiene un control personalizado que muestra los datos de más de una propiedad de un objeto determinado.  
  
5.  En el **asociados controles** cuadro, seleccione cada control que desea que estén disponibles para el tipo de datos seleccionado o anule la selección de todos los controles que desee quitar de la lista.  
  
    > [!NOTE]
    >  Si el control que desea seleccionar no aparece en el **asociados controles** cuadro, debe agregar el control a la lista. Para obtener más información, consulte [agregar controles a la lista de controles asociados para un tipo de datos](#addingcontrols).  
  
6.  Haga clic en **Aceptar**.  
  
7.  En el **orígenes de datos** ventana, haga clic en un elemento de los datos que asoció uno o más controles de tipo y, a continuación, haga clic en el menú desplegable para el elemento.  
  
     Los controles que seleccionó en el **asociados controles** cuadro aparecen ahora en el menú desplegable para el elemento.  
  
##  <a name="addingcontrols"></a> Addcontrols a la lista de controles asociados para un tipo de datos  
 Si desea asociar un control con un tipo de datos, pero el control no aparece en el **asociados controles** cuadro, debe agregar el control a la lista. El control debe encontrarse en la solución actual o en un ensamblado de referencia. También debe estar disponible en el **cuadro de herramientas**, y tener un atributo que especifica el comportamiento de enlace de datos del control.  
  
#### <a name="to-add-controls-to-the-list-of-associated-controls"></a>Para agregar controles a la lista de controles asociados  
  
1.  Agregar el control deseado para el **cuadro de herramientas** haciendo clic con el **cuadro de herramientas** y seleccionando **elegir elementos**.  
  
     El control debe tener uno de los siguientes atributos.  
  
    |Atributo|Descripción|  
    |---------------|-----------------|  
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Implemente este atributo en controles simples que muestran una sola columna (o propiedad) de datos, como un <xref:System.Windows.Forms.TextBox>.|  
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Implemente este atributo en controles que muestren listas (o tablas) de datos, como un <xref:System.Windows.Forms.DataGridView>.|  
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Implemente este atributo en controles que muestren listas (o tablas) de datos, sino también la necesidad de presentar una única columna o propiedad, como un <xref:System.Windows.Forms.ComboBox>.|  
  
2.  Para los formularios de Windows, en el **opciones** cuadro de diálogo, abra el **personalización de la interfaz de usuario de datos** página. O bien, para WPF, abra el **Personalizar enlace de Control** cuadro de diálogo. Para obtener más información, consulte [personalización de la lista de controles enlazables para un tipo de datos](#customizinglist).  
  
3.  En el **asociados controles** cuadro, el control que acaba de agregar a la **cuadro de herramientas** debería aparecer ahora.  
  
    > [!NOTE]
    >  Solo los controles que se encuentran dentro de la solución actual o en un ensamblado que se hace referencia se pueden agregar a la lista de controles asociados. (Los controles también deben implementar uno de los atributos de enlace de datos en la tabla anterior.) Para enlazar datos a un control personalizado que no está disponible en el **orígenes de datos** ventana, arrastre el control desde el **cuadro de herramientas** hasta la superficie de diseño y, a continuación, arrastre el elemento que se enlazará desde el **datos Orígenes** ventana al control.  
  
## <a name="see-also"></a>Vea también  
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

